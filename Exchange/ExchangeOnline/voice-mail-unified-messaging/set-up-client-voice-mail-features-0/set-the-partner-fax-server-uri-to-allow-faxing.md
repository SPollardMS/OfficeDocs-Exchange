---
title: "Set the partner fax server URI to allow faxing"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 77a9013b-d76b-4af2-8b2c-cef435cf67af
description: "You can enable and disable inbound faxes for users associated with a Unified Messaging (UM) mailbox policy. By default, when you enable users for UM, users can't receive fax messages until you enable inbound faxing on the UM mailbox policy and specify the URI for the partner fax server. If the URIs are configured on the UM mailbox policy but the option to allow incoming faxes is disabled on the UM dial plan or for an individual user, UM-enabled users linked to the UM mailbox policy still won't be able to receive faxes."
---

# Set the partner fax server URI to allow faxing

You can enable and disable inbound faxes for users associated with a Unified Messaging (UM) mailbox policy. By default, when you enable users for UM, users can't receive fax messages until you enable inbound faxing on the UM mailbox policy and specify the URI for the partner fax server. If the URIs are configured on the UM mailbox policy but the option to allow incoming faxes is disabled on the UM dial plan or for an individual user, UM-enabled users linked to the UM mailbox policy still won't be able to receive faxes. 
  
For more information about fax partners, see [Microsoft PinPoint for Fax Partners](https://go.microsoft.com/fwlink/?LinkId=190238).
  
For additional management tasks related to faxing, see [Faxing procedures](faxing-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to set the fax partner URI

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM dial plan** page, under **UM Mailbox Policies**, select the policy you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM mailbox policy** page \> **General**, in the **Partner fax server URI** box, enter the TCP or TLS URI. For example:  _sip:faxserver1.contoso.com:5060;transport=tcp_ or  _sip:faxserver2.contoso.com:5061;transport=tls_
    
    > [!NOTE]
    > Although the box can contain more than one fax server URI, only one will be used. If you enter two URIs, only the first will be used. 
  
4. Click **Save** to save your changes. 
    
### Use the Shell to set the fax partner URI

This example allows users who are linked with the UM mailbox policy  `UMDialPlan Default Policy` to use TCP with port 5060 for the partner fax server  `faxserver1`.
  
```
Set-UMMailboxPolicy "UMDialPlan Default Policy" -FaxServerURI sip:faxserver1.contoso.com:5060;transport=tcp
```

This example allows users who are linked with the UM mailbox policy  `UMDialPlan Default Policy` to use TLS with port 5061 for the partner fax server  `faxserver2`.
  
```
Set-UMMailboxPolicy "UMDialPlan Default Policy" -FaxServerURI sip:faxserver2.contoso.com:5061;transport=tls
```


