---
title: "Prepare Active Directory and domains"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: f895e1ce-d766-4352-ac46-ec959c9954a9
description: "Summary: This article tells you how to prepare Active Directory for Exchange 2016."
---

# Prepare Active Directory and domains

 **Summary**: This article tells you how to prepare Active Directory for Exchange 2016.
  
Before you install Microsoft Exchange Server 2016, you need to prepare your Active Directory forest and its domains. Exchange needs to prepare Active Directory so that it can store information about your users' mailboxes and the configuration of Exchange servers in the organization. If you aren't familiar with Active Directory forests or domains, check out [Active Directory Domain Services Overview](https://go.microsoft.com/fwlink/p/?LinkId=399226).
  
> [!NOTE]
> Whether this is the first installation of Exchange in your environment, or you already have earlier versions of Exchange Server running, you need to prepare Active Directory for Exchange 2016. You can see [Exchange 2016 Active Directory schema changes](ad/ad-schema-changes.md) for details on new schema classes and attributes that Exchange 2016 adds to Active Directory, including those made by Cumulative Updates (CUs). 
  
There are a couple of ways you can prepare Active Directory for Exchange. The first is to let the Exchange 2016 Setup wizard do it for you. If you don't have a large Active Directory deployment, and you don't have a separate team that manages Active Directory, we recommend using the wizard. The account you use will need to be a member of both the Schema Admins and Enterprise Admins security groups. For more information about how to use the Setup wizard, check out [Install the Exchange 2016 Mailbox role using the Setup wizard](deploy-new-installations/install-mailbox-role.md).
  
If you have a large Active Directory deployment, or if a separate team manages Active Directory, this topic is for you. Following the steps in this topic gives you much more control over each stage of preparation, and who can do each step. For example, Exchange administrators might not have the permissions needed to extend the Active Directory schema.
  
[What do you need to know before you begin?](prepare-ad-and-domains.md#BYB)
  
[1. Extend the Active Directory schema](prepare-ad-and-domains.md#Step1)
  
[2. Prepare Active Directory](prepare-ad-and-domains.md#Step2)
  
[3. Prepare Active Directory domains](prepare-ad-and-domains.md#Step3)
  
[How do you know this worked?](prepare-ad-and-domains.md#Verify)
  
Curious about what's happening when Active Directory is being prepared for Exchange? Check out [What changes in Active Directory when Exchange 2016 is installed?](ad/ad-changes.md)
  
## What do you need to know before you begin?
<a name="BYB"> </a>

- Estimated time to complete: 10-15 minutes or more (not including Active Directory replication), depending on organization size and the number of child domains.
    
- The computer you use to run these steps needs to meet the [Exchange 2016 system requirements](system-requirements.md). Also, your Active Directory forest needs to meet the requirements in the "Network and directory servers" section in [Exchange 2016 system requirements](system-requirements.md).
    
- If your organization has multiple Active Directory domains, we recommend the following:
    
  - Do the steps below from an Active Directory site that has an Active Directory server from every domain.
    
  - Install the first Exchange server in an Active Directory site with a writeable global catalog server from every domain.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## 1. Extend the Active Directory schema
<a name="Step1"> </a>

The first step in getting your organization ready for Exchange 2016 is to extend the Active Directory schema. Exchange stores a lot of information in Active Directory but before it can do that, it needs to add and update classes, attributes, and other items. If you're curious about what's changed when your schema is extended, check out [Exchange 2016 Active Directory schema changes](ad/ad-schema-changes.md).
  
Before you extend your schema, there are a few things to keep in mind:
  
- The account you're logged in as needs to be a member of the Schema Admins and Enterprise Admins security groups.
    
- The computer where you'll run the command to extend the schema needs to be in the same Active Directory domain and site as the schema master.
    
- If you use the  _DomainController_ parameter, make sure to use the name of the domain controller that's the schema master. 
    
- The only way to extend the schema for Exchange is to use the steps in this topic or use Exchange 2016 Setup. Other ways of extending the schema aren't supported.
    
> [!TIP]
> If you don't have a separate team that manages your Active Directory schema, you can skip this step and go directly to [2. Prepare Active Directory](#Step2.md). If the schema isn't extended in step 1, the commands in step 2 will extend the schema for you. If you decide to skip step 1, the information you need to keep in mind above still applies. 
  
When you're ready, do the following to extend your Active Directory schema. If you have multiple Active Directory forests, make sure you're logged into the right one.
  
1. Make sure the computer is ready to run Exchange 2016 Setup. To see what you need to run Setup, check out the [Active Directory preparation](prerequisites.md#ADPrep) section in [Exchange 2016 prerequisites](prerequisites.md).
    
2. Open a Windows Command Prompt window and go to where you downloaded the Exchange installation files.
    
3. Run the following command to extend the schema.
    
  ```
  Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms
  ```

After Setup finishes extending the schema, you'll need to wait while Active Directory replicates the changes to all of your domain controllers. If you want to check on how replication is going, you can use the  `repadmin` tool.  `Repadmin` is included as part of the Active Directory Domain Services Tools feature in Windows Server 2012 R2 and Windows Server 2012. For more information about how to use it, see [Repadmin](https://go.microsoft.com/fwlink/p/?LinkId=257879).
  
## 2. Prepare Active Directory
<a name="Step2"> </a>

Now that the Active Directory schema has been extended, you can prepare other parts of Active Directory for Exchange 2016. During this step, Exchange will create containers, objects, and other items in Active Directory that it'll use to store information. The collection of all of the Exchange containers, objects, attributes, and so on, is called the Exchange organization.
  
Before you prepare Active Directory for Exchange, there are a few things to keep in mind:
  
- The account you're logged in as needs to be a member of the Enterprise Admins security group. If you skipped step 1 because you want the  _PrepareAD_ command to extend the schema, the account you use also needs to be a member of the Schema Admins security group. 
    
- The computer where you'll run the command needs to be in the same Active Directory domain and site as the schema master. It'll also need to contact all of the domains in the forest on TCP port 389.
    
- Wait until Active Directory has replicated the changes made in step 1 to all of your domain controllers before you do this step.
    
When you run the command below to prepare Active Directory for Exchange, you'll need to name the Exchange organization. This name is used internally by Exchange and isn't normally seen by users. The name of the company where Exchange is being installed is often used for the organization name. The name you use won't affect the functionality of Exchange or determine what you can use for email addresses. You can name it anything you want, as long as you keep the following in mind:
  
- You can use any uppercase or lowercase letters from A to Z.
    
- You can use numbers 0 to 9.
    
- The name can contain spaces as long as they're not at the beginning or end of the name.
    
- You can use a hyphen or dash in the name.
    
- The name can be up to 64 characters but can't be blank.
    
- The name can't be changed after it's set.
    
When you're ready, do the following to prepare Active Directory for Exchange. If the organization name you want to use has spaces, enclose the name in quotation marks (").
  
1. Open a Windows Command Prompt window and go to where you downloaded the Exchange installation files.
    
2. Run the following command:
    
  ```
  Setup.exe /PrepareAD /OrganizationName:"<organization name>" /IAcceptExchangeServerLicenseTerms
  ```

After Setup finishes preparing Active Directory for Exchange, you'll need to wait while Active Directory replicates the changes to all of your domain controllers. If you want to check on how replication is going, you can use the  `repadmin` tool.  `repadmin` is included as part of the Active Directory Domain Services Tools feature in Windows Server 2012 R2 and Windows Server 2012. For more information about how to use the tool, see [Repadmin](https://go.microsoft.com/fwlink/p/?LinkId=257879).
  
## 3. Prepare Active Directory domains
<a name="Step3"> </a>

The final step to get Active Directory ready for Exchange is to prepare each of the Active Directory domains where Exchange will be installed or where mail-enabled users will be located. This step creates additional containers and security groups, and sets permissions so that Exchange can access them.
  
If you have multiple domains in your Active Directory forest, you have a couple of choices in how you prepare them. Select the option that matches what you want to do. If you only have one domain, you can skip this step because the  _PrepareAD_ command in step 2 already prepared the domain for you. 
  
### Prepare all of the domains in my Active Directory forest

To prepare all of your Active Directory domains, you can use the  _PrepareAllDomains_ parameter when you run Setup. Setup will prepare every domain for Exchange in your Active Directory forest for you. 
  
Before you prepare all of the domains in your Active Directory forest, keep the following in mind:
  
- The account you use needs to be a member of the Enterprise Admins security group.
    
- Wait until Active Directory has replicated the changes made in step 2 to all of your domain controllers. If you don't, you might get an error when you try to prepare the domain.
    
When you're ready, do the following to prepare all of the domains in your Active Directory forest for Exchange.
  
1. Open a Windows Command Prompt window and go to where you downloaded the Exchange installation files.
    
2. Run the following command:
    
  ```
  Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms
  ```

### Let me choose which Active Directory domains I want to prepare

If you want to choose which Active Directory domains you want to prepare, you can use the  _PrepareDomain_ parameter when you run Setup. When you use the  _PrepareDomain_ parameter, you need to include the fully qualified domain name (FQDN) of the domain you want to prepare. 
  
Before you prepare the domains in your Active Directory forest, keep the following in mind:
  
- The account you use needs permissions depending on when the domain was created.
    
  - **Domain created before PrepareAD was run** If the domain was created **before** you ran the  _PrepareAD_ command in step 2 above, then the account you use needs to be a member of the Domain Admins group in the domain you want to prepare. 
    
  - **Domain created after PrepareAD was run** If the domain was created **after** you ran the  _PrepareAD_ command in step 2 above, then the account you use needs to 1) be a member of the Organization Management role group and 2) be a member of the Domain Admins group in the domain you want to prepare. 
    
- Wait until Active Directory has replicated the changes made in step 2 to all of your domain controllers. If you don't, you might get an error when you try to prepare the domain.
    
- You need to prepare every domain where an Exchange server will be installed. You'll also need to prepare any domain that'll contain mail-enabled users, even if those domains won't contain any Exchange servers.
    
- You don't need to run the  _PrepareDomain_ command in the domain where the  _PrepareAD_ command was run. The  _PrepareAD_ command prepares that domain automatically. 
    
When you're ready, do the following to prepare an individual domain in your Active Directory forest for Exchange.
  
1. Open a Windows Command Prompt window and go to where you downloaded the Exchange installation files.
    
2. Run the following command. Include the FQDN of the domain you want to prepare. If you want to prepare the domain you're running the command in, you don't have to include the FQDN.
    
  ```
  Setup.exe /PrepareDomain:<FQDN of the domain you want to prepare> /IAcceptExchangeServerLicenseTerms
  ```

3. Repeat the steps for each Active Directory domain where you'll install an Exchange server or where mail-enabled users will be located.
    
## How do you know this worked?
<a name="Verify"> </a>

Once you've done all the steps above, you can check to make sure everything's gone smoothly. To do so, you'll use a tool called Active Directory Service Interfaces Editor (ADSI Edit). ADSI Edit is included as part of the Active Directory Domain Services Tools feature in Windows Server 2012 R2 and Windows Server 2012. If you want to know more about it, check out [ADSI Edit (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=294644).
  
> [!CAUTION]
> Never change values in ADSI Edit unless you're told to do so by Microsoft support. Changing values in ADSI Edit can cause irreparable harm to your Exchange organization and Active Directory. 
  
 After Exchange extends your Active Directory schema and prepares Active Directory for Exchange, several properties are updated to show that preparation is complete. Use the information in the following list to make sure these properties have the right values. Each property needs to match the value in the table below for the release of Exchange 2016 that you're installing. 
  
- In the **Schema** naming context, verify that the **rangeUpper** property on **ms-Exch-Schema-Version-Pt** is set to the value shown for your version of Exchange 2016 in the [Exchange 2016 Active Directory versions ](#ADversions.md) table. 
    
- In the **Configuration** naming context, verify that the **objectVersion** property in the CN=<  _your organization_>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=< _domain_> container is set to the value shown for your version of Exchange 2016 in the [Exchange 2016 Active Directory versions ](#ADversions.md) table. 
    
- In the **Default** naming context, verify that the **objectVersion** property in the **Microsoft Exchange System Objects** container under DC=<  _root domain_ is set to the value shown for your version of Exchange 2016 in the [Exchange 2016 Active Directory versions ](#ADversions.md) table. 
    
You can also check the Exchange setup log to verify that Active Directory preparation has completed successfully. For more information, see [Verify an Exchange 2016 installation](post-installation-tasks/verify-installation.md). You won't be able to use the **Get-ExchangeServer** cmdlet mentioned in the [Verify an Exchange 2016 installation](post-installation-tasks/verify-installation.md) topic until you've completed the installation of at least one Mailbox server role in an Active Directory site. 
  
### Exchange 2016 Active Directory versions
<a name="ADversions"> </a>

The following table shows you the Exchange 2016 objects in Active Directory that get updated each time you install a new version of Exchange 2016. You can compare the object versions you see with the values in the table below to verify that the version of Exchange 2016 you installed successfully updated Active Directory during installation.
  
||**Exchange version**|**rangeUpper**|**objectVersion**|**objectVersion**|
|:-----|:-----|:-----|:-----|:-----|
|**Naming context** <br/> | <br/> |Schema  <br/> |Default  <br/> |Configuration  <br/> |
|**Container** <br/> | <br/> |ms-Exch-Schema-Version-Pt  <br/> |Microsoft Exchange System Objects  <br/> |CN=< _your organization_>, CN=Microsoft Exchange, CN=Services, CN=Configuration, DC=< _domain_>  <br/> |
||Exchange 2016 CU9  <br/> |15332  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU8  <br/> |15332  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU7  <br/> |15332  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU6  <br/> |15330  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU5  <br/> |15326  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU4  <br/> |15326  <br/> |13236  <br/> |16213  <br/> |
||Exchange 2016 CU3  <br/> |15326  <br/> |13236  <br/> |16212  <br/> |
||Exchange 2016 CU2  <br/> |15325  <br/> |13236  <br/> |16212  <br/> |
||Exchange 2016 CU1  <br/> |15323  <br/> |13236  <br/> |16211  <br/> |
||Exchange 2016 RTM  <br/> |15317  <br/> |13236  <br/> |16210  <br/> |
||Exchange 2016 Preview  <br/> |15317  <br/> |13236  <br/> |16041  <br/> |
   

