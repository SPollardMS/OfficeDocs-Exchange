---
title: "Remove a public folder"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 334b831d-e372-4d85-a407-5c8a5d0e78de
description: "You may need to remove public folders that are no longer being used in your organization. To help determine which public folders should be removed, see View statistics for public folders and public folder items."
---

# Remove a public folder

You may need to remove public folders that are no longer being used in your organization. To help determine which public folders should be removed, see [View statistics for public folders and public folder items](view-public-folder-statistics.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Public folders" entry in the [Sharing and collaboration permissions](http://technet.microsoft.com/library/b7fa4b7c-1266-45bd-a14b-f66be0459cc5.aspx) topic. 
    
- You can't delete a mail-enabled public folder. Before you can delete it, you must first disable email for the public folder. For more information, see [Mail-enable or mail-disable a public folder](enable-or-disable-mail-for-public-folder.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to remove a public folder

1. Navigate to **Public folders** \> **Public folders**.
    
2. In the list view, select the public folder you want to delete. Note that clicking on the folder name will display sub-folders within that folder, if there are any. At that point you can click to select a specific sub-folder to remove.
    
     To delete a folder or sub-folder, click anywhere on the folder's row except the underlined name of the folder, and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif). If you click the underlined name of the folder, the **Delete** option will not be available to select. 
    
    ![Selecting a public folder to remove](../../media/8666290d-3f19-4c70-afe3-45569762718b.png)
  
3. A warning box displays asking if you're sure you want to delete the public folder. Click **Yes** to continue. 
    
### Use the Shell to delete a public folder

This example deletes the public folder Help Desk\Resolved. This command assumes that the Resolved public folder doesn't have any subfolders. 
  
```
Remove-PublicFolder -Identity "\Help Desk\Resolved"
```

This example tests the previous command without making any modifications.
  
```
Remove-PublicFolder -Identity "\HelpDesk\Resolved" -WhatIf
```

This example removes the public folder Marketing and all its subfolders because the command runs recursively.
  
```
Remove-PublicFolder -Identity "\Marketing" -Recurse:$True
```

For detailed syntax and parameter information, see [Remove-PublicFolder](http://technet.microsoft.com/library/dda460e0-2601-49ae-a43f-c75c69719196.aspx).
  

