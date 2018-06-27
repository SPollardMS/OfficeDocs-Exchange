---
title: "Copy eDiscovery search results to a discovery mailbox"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: bff2ce89-9e6f-494a-bd6a-2f2011507845
description: "Summary: Learn how to copy the results of an In-Place eDiscovery search to a discovery mailbox in Exchange 2016."
---

# Copy eDiscovery search results to a discovery mailbox

 **Summary**: Learn how to copy the results of an In-Place eDiscovery search to a discovery mailbox in Exchange 2016.
  
After you create an In-Place eDiscovery search in Exchange Server 2016, you can use the Exchange admin center (EAC) to copy the results to a discovery mailbox. You can also use the Exchange Management Shell to start an eDiscovery search that was created using the **New-MailboxSearch** cmdlet, which will copy the results to the discovery mailbox that was specified when you created the search.
  
## What do you need to know before you begin?

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "In-Place eDiscovery" entry in the [Messaging policy and compliance permissions in Exchange 2016](../../permissions/feature-permissions/policy-and-compliance-permissions.md) topic.
    
- An eDiscovery search has to be created, by using the EAC or the Exchange Management Shell, before you can copy the search results. For details, see [Create an In-Place eDiscovery search in Exchange 2016](create-searches.md).
    
- Exchange 2016 Setup creates a discovery mailbox called **Discovery Search Mailbox** to copy search results. You can create additional discovery mailboxes. For details, see [Create a Discovery Mailbox](http://technet.microsoft.com/library/bc20285d-35e2-4e49-9bd3-38abf96114ba.aspx).
    
- It might take 5 minutes or longer to copy search results to a discovery mailbox, depending on the number of mailbox items returned in the results.
    
- To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
## Use the EAC to copy search results

1. In the EAC, go to **Compliance management** \> **In-Place eDiscovery & Hold**.
    
2. In the list view, select an eDiscovery search.
    
3. Click **Search** ![Search icon](../../media/ITPro_EAC_.png), and then click **Copy search results** from the drop-down list.
    
4. In **Copy Search Results**, select from the following options:
    
  - **Include unsearchable items**: Select this check box to include mailbox items that couldn't be searched (for example, messages with attachments of file types that couldn't be indexed by Exchange Search). For more information, see [Unsearchable Items in Exchange eDiscovery](http://technet.microsoft.com/library/32550081-9af9-474b-ae7b-28f1e68cad41.aspx).
    
  - **Enable de-duplication**: Select this check box to exclude duplicate messages. Only a single instance of a message will be copied to the discovery mailbox.
    
  - **Enable full logging**: Select this check box to include a full log in search results.
    
  - **Send me mail when the copy is completed**: Select this check box to get an email notification when the search is completed.
    
  - **Copy results to this discovery mailbox**: Click **Browse** to select the discovery mailbox where you want the search results copied to.
    ![Copy Search Results](../../media/TA_MRM_CopySearchResults.gif)
  
5. Click **Copy** to start the process to copy the search results to the specified discovery mailbox.
    
6. Click **Refresh** ![Refresh icon](../../media/ITPro_EAC_RefreshIcon.png) to update the information about the copying status that is displayed in the details pane.
    
7. When copying is complete, click **Open** to open the discovery mailbox to view the search results.
    
## Use the Exchange Management Shell to copy search results

After using the **New-MailboxSearch** cmdlet to create an In-Place eDiscovery search, you need to start the search to copy messages to the discovery mailbox you specified in the _TargetMailbox_ parameter. For information about creating eDiscovery searches by using the Exchange Management Shell, see: 
  
- [Create an In-Place eDiscovery search in Exchange 2016](create-searches.md)
    
- [New-MailboxSearch](http://technet.microsoft.com/library/74303b47-bb49-407c-a43b-590356eae35c.aspx)
    
In the following example, you would run the following command to start an eDiscovery search named *Fabrikam Investigation* to copy the search results to the discovery mailbox that was specified by the _TargetMailbox_ parameter when the search was created.
  
```
Start-MailboxSearch "Fabrikam Investigation"
```

If you used the _EstimateOnly_ switch to get an estimate of the search results, you have to remove the switch before you can copy the search results. You also have to specify a discovery mailbox to copy to search results to. For example, say you created an estimate-only search by using the following command: 
  
```
New-MailboxSearch "FY15 Q2 Financial Results" -StartDate "04/01/2015" -EndDate "06/30/2015" -SourceMailboxes "DG-Finance" -SearchQuery '"Financial" AND "Fabrikam"' -EstimateOnly -IncludeUnsearchableItems

```

To copy the results of this search to a discovery mailbox, you would run the following commands:
  
```
Set-MailboxSearch "FY15 Q2 Financial Results" -EstimateOnly $false -TargetMailbox "Discovery Search Mailbox"
```

```
Start-MailboxSearch "FY15 Q2 Financial Results"
```

For more information about these cmdlets, see the following topics:
  
- [Set-Mailboxsearch](http://technet.microsoft.com/library/23201ff0-e30a-4efd-9384-ab0af5815701.aspx)
    
- [Start-MailboxSearch](http://technet.microsoft.com/library/f0c4e047-7eca-4310-bfad-1ecfe1420ceb.aspx)
    
## More information

- After you copy search results to the discovery mailbox, you can also export those search results to a PST file. For more information, see [Export eDiscovery search results to a PST file](export-results-to-pst.md). Note that you can export search results without having to copy them to a discovery mailbox. You can create an estimate-only search, start it, and then export the search results.
    
- For more information about unsearchable items, see [Unsearchable Items in Exchange eDiscovery](http://technet.microsoft.com/library/32550081-9af9-474b-ae7b-28f1e68cad41.aspx).
    
- If you're copying all mailbox content within a specific date range (by not specifying any keywords in the search criteria), then all unsearchable items within that date range will be automatically included in the search results. Therefore, don't select the **Include unsearchable items** checkbox when copying search results. Otherwise, a duplicate copy of all unsearchable items will be copied to the discovery mailbox.
    
- In addition to copying the search results to a discovery mailbox, you can also estimate or preview the search results for a selected search.
    
  - **Estimate search results**: This option returns an estimate of the total size and number of items that will be returned by the search based on the criteria you specified. Estimates are displayed in the details pane in the EAC.
    
  - **Preview search results**: This option lets you preview the search results returned by the search instead of having to copy them to a discovery mailbox to view. This lets you quickly determine whether the search results are relevant. After you preview the results, you can revise your search query to narrow the search results and rerun the search. Items in the preview page are read-only versions of the actual search results, so you can't move, edit, delete or forward on the preview page.
    
    For more information, see [Use the EAC to estimate or preview search results](create-searches.md#estimate).
    

