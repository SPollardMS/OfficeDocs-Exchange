---
title: "Recreating arbitration mailboxes"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: b9004562-b0f2-4460-a623-94883834f73f
description: "Summary: About arbitration mailboxes in Exchange 2016 and how to re-create them."
---

# Recreating arbitration mailboxes

 **Summary**: About arbitration mailboxes in Exchange 2016 and how to re-create them.
  
Exchange 2016 comes with five system mailboxes known as *arbitration mailboxes*. Arbitration mailboxes are used for storing different types of system data and for managing messaging approval workflow. The below chart lists each type of arbitration mailbox and their responsibilities.
  
|**Arbitration mailbox Name**|**Display name**|**Persisted capabilities**|**Function**|
|:-----|:-----|:-----|:-----|
|FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042  <br/> |Microsoft Exchange Federation Mailbox  <br/> |{}  <br/> |This mailbox stores data used to maintain federation between different Exchange organizations. This includes Rights Management Services, cross-premises mail-flow monitoring probes and responses, notifications, online archives, messaging records management, and cross-premises free/busy information.  <br/> |
|SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109}  <br/> |Microsoft Exchange Approval Assistant  <br/> |{}  <br/> |This mailbox is provisioned for use by the Exchange approval framework for recipient moderation and auto group approval requests.  <br/> |
|Migration.8f3e7716-2011-43e4-96b1-aba62d229136  <br/> |Microsoft Exchange Migration  <br/> |{OrganizationCapabilityManagement}  <br/> |Stores data for the Exchange migration service to use when moving mailboxes in batches.  <br/> |
|SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}  <br/> |Microsoft Exchange  <br/> |{OrganizationCapabilityUMDataStorage}  <br/> |Discovery system mailbox.  <br/> Provisioned for use by e-Discovery feature, which is used by compliance officers to locate messages that match specified selection criteria. This mailbox is also used by Unified Messaging for storing UM console attending files and other information.  <br/> |
|SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}  <br/> |Microsoft Exchange  <br/> |{OrganizationCapabilityUMGrammarReady, OrganizationCapabilityPstProvider, OrganizationCapabilityMessageTracking, OrganizationCapabilityMailRouting, OrganizationCapabilityClientExtensions, OrganizationCapabilityGMGen, OrganizationCapabilityOABGen, OrganizationCapabilityUMGrammar}  <br/> |This is known as an organization mailbox. It is used for creating offline address books (OABs). To load-balance OAB generation across your organization, including across geographically separate sites, you can create additional organization mailboxes.  <br/> |
   
If you need to re-create one of more of these arbitration mailboxes, see the instructions that follow.
  
## What you should know before you begin

- Estimated time to complete: 10 minutes per procedure.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Recipients Permissions](../../permissions/feature-permissions/recipient-permissions.md) topic.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
## Use Exchange Management Shell to re-create an arbitration mailbox

Use the following instructions to re-create a particular type of arbitration mailbox.
  
> [!NOTE]
> All steps in the following sections must be run from the same directory where you extracted the Exchange installation media.
  
### Re-create the Microsoft Exchange Federation Mailbox

To re-create the arbitration mailbox FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042:
  
1. If any arbitration mailboxes are missing, run the following command:
    
    ```
    .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2. In the Exchange Management Shell, run the following:
    
    ```
    Enable-Mailbox -Arbitration -Identity   "FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042"
    ```

### Re-create the Microsoft Exchange Approval Assistant mailbox

To re-create the arbitration mailbox SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109}:
  
1. If any arbitration mailboxes are missing, run the following command:
    
    ```
    .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2. In the Exchange Management Shell, run the following:
    
    ```
    Get-User | Where-Object {$_.Name -like "SystemMailbox{1f05a927-7709-4e35-9dbe-d0f608fb781a}"} | Enable-Mailbox -Arbitration
    ```

### Re-create the Microsoft Exchange Migration mailbox

To re-create the arbitration mailbox Migration.8f3e7716-2011-43e4-96b1-aba62d229136:
  
1. If any arbitration mailboxes are missing, run the following command:
    
    ```
    .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2. In the Exchange Management Shell, run the following:
    
    ```
    Enable-Mailbox -Arbitration -Identity "Migration.8f3e7716-2011-43e4-96b1-aba62d229136"
    ```

3. In the Exchange Management Shell, set the Persisted Capabilities (msExchCapabilityIdentifiers) by running the following command:
    
    ```
    Set-Mailbox "Migration.8f3e7716-2011-43e4-96b1-aba62d229136" -Arbitration -Management:$True -Force
    ```

### Re-create the Microsoft Exchange Discovery system mailbox

To re-create the arbitration mailbox SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}:
  
1. Run the following command:
    
    ```
    .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

### Re-create the Microsoft Exchange organization mailbox for OABs

To re-create the arbitration mailbox SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}:
  
1. If any arbitration mailboxes are missing, run the following command:
    
    ```
    .\Setup /preparead /IAcceptExchangeServerLicenseTerms
    ```

2. In the Exchange Management Shell, run the following:
    
    ```
    Enable-Mailbox -Arbitration -Identity "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}"
    ```

3. In the Exchange Management Shell, set the Persisted Capabilities (msExchCapabilityIdentifiers) by running the following command:
    
    ```
    Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration | Set-Mailbox -Arbitration -UMGrammar:$True -OABGen:$True -GMGen:$True -ClientExtensions:$True -MessageTracking:$True -PstProvider:$True -MaxSendSize 1GB -Force
    ```

After you're finished, if you run the following command, you'll see that 46, 47, and 51 are missing.

```
$OABMBX = Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration (Get-ADUser $OABMBX.SamAccountName -Properties *).msExchCapabilityIdentifiers
```

Run the following command to add all of the capabilities back: 
  
```
Set-ADUser $OABMBX.SamAccountName -Add @{"msExchCapabilityIdentifiers"="40","42","43","44","47","51","52","46"}
```

## How do I know this worked?

To verify that you have successfully re-created the arbitration mailbox, use the **Get-Mailbox** cmdlet with the _Arbitration_ switch to retrieve system mailboxes.
  
```
Get-Mailbox -Arbitration | Format-Table Name, DisplayName
```

View the results of the command to verify that appropriate system mailbox, either by Name or Display Name from the above table, has been re-created.
  
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  

