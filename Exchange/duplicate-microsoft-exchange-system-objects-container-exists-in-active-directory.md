---
title: Duplicate Microsoft Exchange System Objects container exists in Active Directory [AdInitErrorRule]
ms.prod: EXCHANGE
ms.assetid: cd0f45ab-89de-4653-b50d-c1157c2329d5
---


# Duplicate Microsoft Exchange System Objects container exists in Active Directory [AdInitErrorRule]

Microsoft Exchange Server 2016 Setup can't continue because it found a duplicate Microsoft Exchange System Objects container in Active Directory Domain Naming context. When Setup finds a duplicate Microsoft Exchange System Objects container, you must delete the duplicate container before Setup can continue. When a duplicate Microsoft Exchange System Objects container exists, you can't solve the problem by running **DomainPrep** again. You must identify and delete the duplicate Microsoft Exchange System Objects container.
  
    
    

To resolve this issue, do the following:
1. Log on to the domain controller with administrative credentials.
    
  
2. In **Administrative Tools**, click **Active Directory Users and Computers**.
    
  
3. In the **Active Directory Users and Computers** management console pane, click **View** from the toolbar menu and then select **Advanced Features**.
    
  
4. Locate the duplicate Microsoft Exchange System Objects container.
    
  
5. Verify the duplicate Microsoft Exchange System Objects container doesn't contain valid Active Directory objects.
    
  
6. Right-click the duplicate Microsoft Exchange System Objects container, and then click **Delete**.
    
  
7. Confirm the deletion by clicking **Yes** in the Active Directory dialog box.
    
  

> [!NOTE]
> If you want the change to be replicated immediately, you must manually initiate replication between domain controllers. 
  
    
    

Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
