---
title: Exchange 2016 Setup - Exchange Organization
ms.prod: EXCHANGE
ms.assetid: 8c28f2f1-2c4b-4c79-8758-9b9519ccf0a0
---


# Exchange 2016 Setup - Exchange Organization

On the **Exchange Organization** page, type a name for your Microsoft Exchange Server 2016 organization. The Exchange organization name can contain only the following characters:
  
    
    


- A through Z
    
  
- a through z
    
  
- 0 through 9
    
  
- Space (not leading or trailing)
    
  
- Hyphen or dash
    
    > [!NOTE]
      > The organization name can't contain more than 64 characters. The organization name can't be blank. 

## Permissions models

Exchange gives you the choice of the following permissions models: 
  
    
    

- **Shared permissions** Theshared permissions model allows administrators using the Exchange management tools to create security principals in Active Directory. It doesn't separate the management of Exchange and Active Directory objects from within the Exchange management tools. This is the default permissions model.
    
  
- **Split permissions** Organizations that separate the management of Exchange 2016 objects and Active Directory objects use what's called asplit permissions model. Split permissions enable organizations to assign specific permissions and related tasks to specific groups within the organization. This separation of work helps to maintain standards and workflows, and helps to control change in the organization.
    
    If you're interested in split permissions, Exchange 2016 gives you the option of implementing split permissions in two different ways:
    
  - **RBAC split permissions** Permissions to create security principals in the Active Directory domain partition are controlled by Role Based Access Control (RBAC). Only Exchange servers, services, and those who are members of the appropriate role groups can create security principals. For more information, see "RBAC Split Permissions" in [Understanding Split Permissions](http://technet.microsoft.com/library/2b709e15-63a2-4841-94bc-b289b71166d0.aspx).
    
  
  - **Active Directory split permissions** Permissions to create security principals in the Active Directory domain partition are completely removed from any Exchange user, service, or server. No option is provided in RBAC to create security principals. Creation of security principals in Active Directory must be performed using Active Directory management tools. For more information, see "Active Directory Split Permissions" in [Understanding Split Permissions](http://technet.microsoft.com/library/2b709e15-63a2-4841-94bc-b289b71166d0.aspx).
    
  
Most organizations don't need to implement a split permissions model. If the administrators in your organization share Active Directory and Exchange management duties, you should use the default shared permissions model. However, if your organization chooses to use a split permissions model instead of shared permissions, we recommend that you use the RBAC split permissions model. The RBAC split permissions model provides significantly more flexibility while providing nearly the same administration separation as Active Directory split permissions, with the exception that Exchange servers and services can create security principals in the RBAC split permissions model.
  
    
    
If, after reading  [Understanding Split Permissions](http://technet.microsoft.com/library/2b709e15-63a2-4841-94bc-b289b71166d0.aspx), you want to completely separate Active Directory and Exchange management, select **Apply Active Directory split permission security model to the Exchange organization**. If you want to use shared permissions, or RBAC split permissions, don't select this option.
  
    
    

> [!IMPORTANT]
> You can't enable Active Directory split permissions if you've installed Exchange 2016 on a domain controller. 
  
    
    

Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
    
    
Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  
    
    

