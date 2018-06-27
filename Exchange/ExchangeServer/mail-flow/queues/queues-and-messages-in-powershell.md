---
title: "Find queues and messages in queues in the Exchange Management Shell"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 5433c1d3-ad2e-4f82-b50d-b67964b32f26
description: "Summary: Learn about identity, filtering, and command output for queues and messages in queues in the Exchange Management Shell in Exchange 2016."
---

# Find queues and messages in queues in the Exchange Management Shell

 **Summary**: Learn about identity, filtering, and command output for queues and messages in queues in the Exchange Management Shell in Exchange 2016.
  
As in previous versions of Exchange, you can use the Exchange Management Shell in Exchange Server 2016 to view information about queues and messages, and use that information to take action on queues and messages. Typically, an active Exchange contains a large number of queues and messages to be delivered, so it's important to understand how to identify the queues or messages that you want to manage.
  
Note that you can also use Queue Viewer in the Exchange Toolbox to manage queues and messages in queues. However, the queue and message viewing cmdlets in the Exchange Management Shell support more filterable properties and filter options than Queue Viewer. For more information about using Queue Viewer, see [Queue Viewer](queue-viewer.md).
  
Also remember that queues exist on Mailbox servers and Edge Transport servers (the Transport service). For more information about queues and messages in queues, see [Queues and messages in queues](queues.md).
  
## Queue filtering parameters
<a name="QueueFilters"> </a>

The following table summarizes the filtering parameters that are available on the queue management cmdlets.
  
|**Cmdlet**|**Filtering parameters**|**Comments**|
|:-----|:-----|:-----|
|**Get-Queue** <br/> | _Exclude_ <br/> _Filter_ <br/> _Identity_ <br/> _Include_ <br/> _Server_ <br/> |You can use the _Include_ and _Exclude_ parameters with the other filtering parameters in the same command.  <br/> You can't use the _Identity_ and _Filter_ parameters in the same command.  <br/> The _Server_ parameter specifies the server where you want to run the command. You can't use the _Server_ and _Identity_ parameters in the same command, but you can use the _Server_ parameter with the other filtering parameters in the same command.  <br/> |
|**Resume-Queue** <br/> **Retry-Queue** <br/> **Suspend-Queue** <br/> | _Identity_ <br/> _Filter_ <br/> _Server_ <br/> |You can't use the _Identity_ parameter with the other filtering parameters in the same command.  <br/> The _Server_ parameter specifies the server where you want to run the command. You can use the _Server_ and _Filter_ parameters in the same command.  <br/> |
|**Get-QueueDigest** <br/> | _Dag_ <br/> _Filter_ <br/> _Forest_ <br/> _Server_ <br/> _Site_ <br/> |You need to use one of the _Dag_, _Site_, _Server_, or _Forest_ parameters, but you can't use any of them together in the same command.  <br/> You can use the _Filter_ parameter with any of the other filtering parameters.  <br/> |
   
### Queue identity
<a name="QueueIdentity"> </a>

The _Identity_ parameter uses the basic syntax _\<Server\>_\ _\<Queue\>_. Typically, this value uniquely identifies the queue, so you can't use other filtering parameters with the _Identity_ parameter. The exception is the **Get-Queue** cmdlet, where you can use the _Include_ and _Exclude_ parameters with the _Identity_ parameter.
  
The following table explains the _Identity_ parameter syntax on the queue management cmdlets.
  
|**Identity parameter value**|**Description**|
|:-----|:-----|
| `<Server>\<PersistentQueueName>` or `<PersistentQueueName>` <br/> |A persistent queue on the specified or local server.  <br/> `<PersistentQueueName>` is `Submission`, `Unreachable`, or `Poison`.  <br/> For more information about persistent queues, see [Types of queues](queues.md#QueueTypes).  <br/> |
| `<Server>\<NextHopDomain>` or `<NextHopDomain>` <br/> |A delivery queue on the specified or local server.  <br/> `<NextHopDomain>` is the name of the queue from the value of the **NextHopDomain** property of the queue. For example, the address space of a Send connector, the name of an Active Directory site, or the name of a DAG. For more information, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |
| `<Server>\<QueueInteger>` or `<QueueInteger>` <br/> |A delivery queue on the specified or local server.  <br/> `<QueueInteger>` is the unique integer value that's assigned to a delivery queue or a shadow queue in the queue database. However, you need to run the **Get-Queue** cmdlet to find this value in the **Identity** or **QueueIdentity** properties.  <br/> |
| `<Server>\Shadow\<QueueInteger>` or `Shadow\<QueueInteger>` <br/> |A shadow queue on the specified or local server. For more information about shadow queues and shadow redundancy, see [Shadow redundancy in Exchange 2016](../../mail-flow/transport-high-availability/shadow-redundancy.md).  <br/> |
| `<Server>\*` or `*` <br/> |All queues on the specified or local server.  <br/> **Note**: _Identity_ is a positional parameter, which means you can specify the value without specifying the `-Identity` qualifier. For example, the following commands produce the same result:  <br/> `Get-Queue -Identity *` <br/> `Get-Queue *` <br/> `Get-Queue` <br/> |
   
### Filter parameter on queue cmdlets
<a name="QueueFilterParam"> </a>

You can use the _Filter_ parameter on all of the queue management cmdlets to identify one or more queues based on the properties of the queues. The _Filter_ parameter creates an OPath filter with comparison operators to restrict the command to queues that meet the filter criteria. You can use the logical operator `-and` to specify multiple conditions for the match. Here's a generic example of the syntax: 
  
 `Get-Queue -Filter {<Property1> -<ComparisonOperator> '<Value1>' -and <Property2> -<ComparisonOperator> '<Value2>'...}`
  
For a complete list of queue properties you can use with the _Filter_ parameter, see [Queue properties](queues.md#QueueProperties).
  
For a list of comparison operators you can use with the _Filter_ parameter, see the [Comparison operators to use when filtering queues or messages](queues-and-messages-in-powershell.md#ComparisonOperators) section in this topic.
  
For examples of procedures that use the _Filter_ parameter to view and manage queues, see [Procedures for queues](queue-procedures.md).
  
### Include and Exclude parameters on Get-Queue
<a name="IncludeAndExclude"> </a>

You can use the _Include_ and _Exclude_ parameters on the **Get-Queue** cmdlet by themselves, with each othe , or with the other filtering parameters to fine-tune your results. For example, you can: 
  
- Exclude empty queues.
    
- Exclude queues to external destinations.
    
- Include queues that have a specific value of **DeliveryType**.
    
The _Include_ and _Exclude_ parameters use the following queue properties to filter queues: 
  
|**Value**|**Description**|**Example**|
|:-----|:-----|:-----|
| `DeliveryType` <br/> |Includes or excludes queues based on the **DeliveryType** property that defines how the message will be transmitted to the next hop. The valid values are described in [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> You can specify multiple values separated by commas.  <br/> |Returns all delivery queues on the local server where the next hop is a Send connector that's hosted on the local server and is configured for smart host routing.  <br/> `Get-Queue -Include SmartHostConnectorDelivery` <br/> |
| `Empty` <br/> |Includes or excludes empty queues. Empty queues have the value `0` in the **MessageCount** property.  <br/> |Returns all queues on the local server that contain messages.  <br/> `Get-Queue -Exclude Empty` <br/> |
| `External` <br/> |Includes or excludes queues that have the value `External` in the **NextHopCategory** property.  <br/> External queues always have one of the following values for **DeliveryType**:  <br/> • `DeliveryAgent` <br/> • `DnsConnectorDelivery` <br/> • `NonSmtpGatewayDelivery` <br/> • `SmartHostConnectorDelivery` <br/> For more information, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |Returns all internal queues on the local server.  <br/> `Get-Queue -Exclude External` <br/> |
| `Internal` <br/> |This value includes or excludes queues that have the value `Internal` in the **NextHopCategory** property. Note that a message for an external recipient may require multiple internal hops before it reaches a gateway server where it's delivered externally.  <br/> |Returns all internal queues on the local server.  <br/> `Get-Queue -Include Internal` <br/> |
   
Note that you can duplicate the functionality of the _Include_ and _Exclude_ parameters by using the _Filter_ parameter. For example, the following commands produce the same result: 
  
- `Get-Queue -Exclude Empty`
    
- `Get-Queue -Filter {MessageCount -gt 0}`
    
However, as you can see, the syntax of the _Include_ and _Exclude_ parameters is simpler and easier to remember.
  
## Get-QueueDigest
<a name="GetQueueDigest"> </a>

The **Get-QueueDigest** cmdlet allows you to view information about some or all of the queues in your organization by using a single command. Specifically, the **Get-QueueDigest** cmdlet allows you to view information about queues based on their location on servers, in DAGs, in Active Directory sites, or in the whole Active Directory forest.
  
Note that queues on a subscribed Edge Transport server aren't included in the results. Also, **Get-QueueDigest** is available on an Edge Transport server, but the results are restricted to local queues on the Edge Transport server.
  
> [!NOTE]
> By default, the **Get-QueueDigest** cmdlet displays delivery queues that contain ten or more messages, and the results are between one and two minutes old. For instructions on how to change these default values, see **Configure Get-QueueDigest**.
  
The following table describes the filtering and sorting parameters that are available on the **Get-QueueDigest** cmdlet.
  
|**Parameter**|**Description**|
|:-----|:-----|
| _Dag_, _Server_, or _Site_ <br/> |These parameters are mutually exclusive (can't be used in the same command), and set the scope for the cmdlet. You need to specify one of these parameters or the _Forest_ switch. Typically, you would use the name of the server, DAG or Active Directory site, but you can use any value that uniquely identifies the server, DAG, or site. You can specify multiple servers, DAGs, or sites separated by commas.  <br/> |
| _Forest_ <br/> |This switch is required if you aren't using the _Dag_, _Server_, or _Site_ parameters. You don't specify a value with this switch. By using this switch, you get queues from all Exchange 2016 or Exchange 2013 Mailbox servers in the local Active Directory forest. You can't use this switch to view queues in remote Active Directory forests.  <br/> |
| _DetailsLevel_ <br/> | `Normal` is the default value. The following properties are returned in the results:  <br/> • **QueueIdentity** <br/> • **ServerIdentity** <br/> • **MessageCount** <br/> `Verbose` returns the following additional properties in the results:  <br/> • **DeferredMessageCount** <br/> • **LockedMessageCount\*** <br/> • **IncomingRate** <br/> • **OutgoingRate** <br/> • **Velocity** <br/> • **NextHopDomain** <br/> • **NextHopCategory** <br/> • **NextHopConnector** <br/> • **DeliveryType** <br/> • **Status** <br/> • **RiskLevel\*** <br/> • **OutboundIPPool\*** <br/> • **LastError** <br/> • **TlsDomain** <br/> `None` omits the queue name from the **Details** column in the results.  <br/> \* These properties are reserved for internal Microsoft use, and aren't used in on-premises Exchange organizations. For more information about all properties in this list, see [Queue properties](queue-properties.md).  <br/> |
| _Filter_ <br/> |Filter queues based on the queue properties as described in the [Filter parameter on queue cmdlets](queues-and-messages-in-powershell.md#QueueFilterParam) section. You can use any of the filterable queue properties as described in the [Queue properties](queue-properties.md) topic.  <br/> |
| _GroupBy_ <br/> |Groups the queue results. You can group the results by one of the following properties:  <br/> • **DeliveryType** <br/> • **LastError** <br/> • **NextHopCategory** <br/> • **NextHopDomain** <br/> • **NextHopKey** <br/> • **Status** <br/> • **ServerName** <br/> By default, the results are grouped by **NextHopDomain**. For information about these queue properties, see [Queue properties](queue-properties.md).  <br/> |
| _ResultSize_ <br/> |Limits the queue results to the value you specify. The queues are sorted in descending order based on the number of messages in the queue, and grouped by the value specified by the _GroupBy_ parameter. The default value is 1000. This means that by default, the command displays the top 1000 queues grouped by **NextHopDomain**, and sorted by the queues containing the most messages to the queues containing the least messages.  <br/> |
| _Timeout_ <br/> |The parameter specifies the number of seconds before the operation times out. The default value is `00:00:10` or 10 seconds.  <br/> |
   
This example returns all non-empty external queues on the servers named Mailbox01, Mailbox02, and Mailbox03.
  
```
Get-QueueDigest -Server Mailbox01,Mailbox02,Mailbox03 -Include External -Exclude Empty
```

## Message filtering parameters
<a name="MessagesFilters"> </a>

The following table summarizes the filtering parameters that are available on the message management cmdlets.
  
|**Cmdlet**|**Filtering parameters**|**Comments**|
|:-----|:-----|:-----|
|**Get-Message** <br/> | _Filter_ <br/> _Identity_ <br/> _Queue_ <br/> _Server_ <br/> |You can't use the _Filter_, _Identity_, or _Queue_ parameters in the same command.  <br/> The _Server_ parameter specifies the server where you want to run the command. You can use the _Server_ and _Filter_ parameters in the same command.  <br/> |
|**Remove-Message** <br/> **Resume-Message** <br/> **Suspend-Message** <br/> | _Filter_ <br/> _Identity_ <br/> _Server_ <br/> |You need to use either the _Identity_ parameter or the _Filter_ parameter, but you can't use them both in the same command.  <br/> The _Server_ parameter specifies the server where you want to run the command. You can use the _Server_ and _Filter_ parameters in the same command.  <br/> |
|**Redirect-Message** <br/> | _Server_ <br/> |This cmdlet drains active messages from all delivery queues on the specified server, so _Server_ is the only filtering parameter that's available. For more information, see [Redirect messages in queues](message-procedures.md#Redirect).  <br/> |
|**Export-Message** <br/> | _Identity_ <br/> |This parameter isn't really a filter, because it uniquely identifies the message. To identify multiple messages for this cmdlet, use **Get-Message** and pipe the results to **Export-Message**. For more information and examples, see [Export messages from queues](export-messages.md).  <br/> |
   
### Message identity
<a name="MessageIdentity"> </a>

The _Identity_ parameter on the message management cmdlets uniquely identifies a message in one or more queues, so you can't use any other message filtering parameters. The _Identity_ parameter uses the basic syntax `<Server>\<Queue>\<MessageInteger>`.
  
The following table describes the syntax you can use with _Identity_ parameter on the message management cmdlets.
  
|**Identity parameter value**|**Description**|
|:-----|:-----|
| `<Server>\<Queue>\<MessageInteger>` or `<Queue>\<MessageInteger>` <br/> |A message in a specific queue on the specified or local server.  <br/> `<Queue>` is the identity of the queue as described in the [Queue identity](queues-and-messages-in-powershell.md#QueueIdentity) section:  <br/> • **Persistent queue name** <br/> • **Delivery queue name** <br/> • **Queue integer** <br/> • **Shadow queue identity** <br/> `<MessageInteger>` is the unique integer value that's assigned to the message when it first enters the queue database on the server. If the message is sent to multiple recipients that require multiple queues, all copies of the message in all queues in the queue database have the same integer value. However, you need to run the **Get-Message** cmdlet to find this value in the **Identity** or **MessageIdentity** properties.  <br/> |
| `<Server>\*\<MessageInteger>` or `*\<MessageInteger>` or `<MessageInteger>` <br/> |All copies of the message in all queues in the queue database on the specified or local server.  <br/> |
   
### Filter parameter on message cmdlets
<a name="MessageFilterParam"> </a>

You can use the _Filter_ parameter with the **Get-Message**, **Remove-Message**, **Resume-Message**, and **Suspend-Message** cmdlets to identify one or more messages based on the properties of the messages. The _Filter_ parameter creates an OPath filter with comparison operators to restrict the command to messages that meet the filter criteria. You can use the logical operator `-and` to specify multiple conditions for the match. Here's a generic example of the syntax: 
  
 `Get-Message -Filter {<Property1> -<ComparisonOperator> '<Value1>' -and <Property2> -<ComparisonOperator> '<Value2>'...}`
  
For a complete list of message properties you can use with the _Filter_ parameter, see [Message properties](queues.md#MessageProperties).
  
For a list of comparison operators you can use with the _Filter_ parameter, see the [Comparison operators to use when filtering queues or messages](queues-and-messages-in-powershell.md#ComparisonOperators) section in this topic.
  
For examples of procedures that use the _Filter_ parameter to view and manage messages, see [Procedures for messages in queues](message-procedures.md).
  
### Queue parameter
<a name="QueueParam"> </a>

The _Queue_ parameter is available only on the **Get-Message** cmdlet. You can use this parameter to get all messages in a specific queue, or all messages from multiple queues by using the wildcard character (\*). When you use the _Queue_ parameter, use the queue identity format `<Server>\<Queue>` as described in the [Queue identity](queues-and-messages-in-powershell.md#QueueIdentity) section in this topic.
  
## Comparison operators to use when filtering queues or messages
<a name="ComparisonOperators"> </a>

When you create a queue or message filter expression by using the _Filter_ parameter, you need to include an comparison operator for the property value to match. The comparison operators that you can use, and how each operator functions are described in the following table. For all operators, the values compared aren't case sensitive.
  
|**Operator**|**Function**|**Code example**|
|:-----|:-----|:-----|
| `-eq` <br/> |Exact match of the specified value.  <br/> |Show all queues that have a status of Retry:  <br/> `Get-Queue -Filter {Status -eq "Retry"}` <br/> Show all messages that have a status of Retry:  <br/> `Get-Message -Filter {Status -eq "Retry"}` <br/> |
| `-ne` <br/> |Does not match the specified value.  <br/> |Show all queues that don't have a status of Active:  <br/> `Get-Queue -Filter {Status -ne "Active"}` <br/> Show all messages that don't have a status of Active:  <br/> `Get-Message -Filter {Status -ne "Active"}` <br/> |
| `-gt` <br/> |Greater than the specified integer or date/time value.  <br/> |Show queues that currently contain more than 1,000 messages:  <br/> `Get-Queue -Filter {MessageCount -gt 1000}` <br/> Show messages that currently have a retry count that's more than 3:  <br/> `Get-Message -Filter {RetryCount -gt 3}` <br/> |
| `-ge` <br/> |Greater than or equal to the specified integer or date/time value.  <br/> |Show queues that currently contain 1,000 or more messages:  <br/> `Get-Queue -Filter {MessageCount -ge 1000}` <br/> Show messages that currently have a retry count that's 3 or more:  <br/> `Get-Message -Filter {RetryCount -ge 3}` <br/> |
| `-lt` <br/> |Less than the specified integer or date/time value.  <br/> |Show queues that currently contain less than 1,000 messages:  <br/> `Get-Queue -Filter {MessageCount -lt 1000}` <br/> Show messages that have an SCL that's less than 6:  <br/> `Get-Message -Filter {SCL -lt 6}` <br/> |
| `-le` <br/> |Less than or equal to the specified integer or date/time value.  <br/> |Show queues that currently contain 1,000 or fewer messages:  <br/> `Get-Queue -Filter {MessageCount -le 1000}` <br/> Show messages that have an SCL that's 6 or less:  <br/> `Get-Message -Filter {SCL -le 6}` <br/> |
| `-like` <br/> |Contains the specified text. You need to include the wildcard character (\*) in the text string.  <br/> |Show queues that have a destination to any SMTP domain that ends in Contoso.com:  <br/> `Get-Queue -Filter {Identity -like "*contoso.com"}` <br/> Show messages that have a subject that contains the text "payday loan":  <br/> `Get-Message -Filter {Subject -like "*payday loan*"}` <br/> |
   
You can specify a filter that evaluates multiple expressions by using the logical operator `-and`. The queues or messages must match all of the filter conditions to be included in the results.
  
This example displays a list of queues that have a destination to any SMTP domain name that ends in Contoso.com and that currently contain more than 500 messages.
  
```
Get-Queue -Filter {Identity -like "*contoso.com*" -and MessageCount -gt 500}
```

This example displays a list of messages that are sent from any email address in the contoso.com domain that have an SCL value that's greater than 5.
  
```
Get-Message -Filter {FromAddress -like "*Contoso.com*" -and SCL -gt 5}
```

## Advanced paging parameters
<a name="PagingParameters"> </a>

When you use the Exchange Management Shell to view queues and messages in queues, your query retrieves one page of information at a time. The advanced paging parameters control the size of the results, and the order that the results are displayed in. All advanced paging parameters are optional and can be used with or without other filtering parameters on the **Get-Queue** and **Get-Message** cmdlets. If you don't specify any advanced paging parameters, the query returns the results in ascending order of identity.
  
By default, when you specify a sort order, the **Identity** property is always included and sorted in ascending order, because the other available queue or message properties aren't unique.
  
You can use the _BookmarkIndex_ and _BookmarkObject_ parameters to mark a position in the sorted results. If the bookmark object no longer exists when you retrieve the next page of results, the results start with the closest item to the bookmark, which depends on the sort order that you specify.
  
The advanced paging parameters are described in the following table.
  
**Advanced paging parameters**

|**Parameter**|**Description**|
|:-----|:-----|
| _BookmarkIndex_ <br/> |Specifies the position in the results where the displayed results start. The value of this parameter is a 1-based index in the total results. If the value is less than or equal to zero, the first complete page of results is returned. If the value is set to `Int.MaxValue`, the last complete page of results is returned.  <br/> You can't use this parameter with the _BookmarkObject_ parameter.  <br/> |
| _BookmarkObject_ <br/> |Specifies the object in the results where the displayed results start. If you specify a bookmark object, that object is used as the point to start the search. The rows before or after that object (depending on the value of the _SearchForward_ parameter) are retrieved.  <br/> You can't use this parameter with the _BookmarkIndex_ parameter.  <br/> |
| _IncludeBookmark_ <br/> |Specifies whether to include the bookmark object in the results. Valid values are:  <br/> `$true`: The bookmark object is included in the results. This is the default value.  <br/> `$false`: The bookmark object isn't included in the results. Use this value when you run a query for a limited result size, and then specify the last item as the bookmark for the next query. This prevents the bookmark object from being included in both results.  <br/> |
| _ResultSize_ <br/> |Specifies the number of results to display per page. If you don't specify a value, the default result size of 1,000 objects is used. Exchange limits the results to 250,000.  <br/> |
| _ReturnPageInfo_ <br/> |This is a hidden parameter. It returns information about the total number of results and the index of the first object of the current page. The default value is `$false`.  <br/> |
| _SearchForward_ <br/> |Specifies the direction of the search.  <br/> **Bookmark specified**: Search forward or backward in the results relative to the bookmark index or object.  <br/> **No bookmark specified**: Search forward or backward in the results from the first or last item in the results.  <br/> Valid values are:  <br/> `$true`: Search forward from the first item in the results, or from the specified bookmark. If there are no results beyond the bookmark, the query returns the last full page of results. This is the default value.  <br/> `$false`: Search backward from the last item in the results, or from the specified bookmark. If there is less than a full page of results beyond the bookmark, the query returns the first full page of results.  <br/> |
| _SortOrder_ <br/> |Specifies the message properties that control the sort order of the results. The order that the properties are specified indicates a descending order of precedence (the results are sorted by the first property, then those results are sorted by the second property, and son on).  <br/>  This parameter uses the syntax: `<+|-><Property1>,<+|-><Property2>...`, where `+` sorts the property in ascending order, and `-` sorts the property in descending order.  <br/> If you don't use this parameter, the results are sorted by the **Identity** property in ascending order.  <br/> |
   
This example shows how to use the advanced paging parameters in a query. The command returns the first 500 messages on the specified server. The results are sorted first in ascending order by sender address, and then in descending order by message size.
  
```
Get-Message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size
```

This example returns the first 500 messages on the specified server in the specified sort order, sets a bookmark object, excludes the bookmark object from the results, and retrieves the next 500 messages in the same sort order.
  
1. Run the following command to retrieve the first page of results.
    
  ```
  $Results=Get-Message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size
  ```

2. To set the bookmark object, run the following command to save the last element of the first page to a variable.
    
  ```
  $Temp=$Results[$results.length-1]
  ```

3. To retrieve the next 500 objects on the specified server, and to exclude the bookmark object, run the following command.
    
  ```
  Get-Message -Server mailbox01.contoso.com -BookmarkObject:$Temp -IncludeBookmark $false -ResultSize 500 -SortOrder +FromAddress,-Size
  ```


