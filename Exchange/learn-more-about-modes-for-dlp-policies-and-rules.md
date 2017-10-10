---
title: Learn more about modes for DLP policies and rules
ms.prod: EXCHANGE
ms.assetid: 5f9476c8-ad16-49d7-9bba-f903752b7cdb
---


# Learn more about modes for DLP policies and rules

You can change whether you want a DLP policy or its rules to be fully active by changing the mode setting. The mode, or disposition, for an entire policy can be set separately from the mode of each rule with a policy. When the mode for a policy and its related rules are not identical, the mode of a rule has the highest priority. You audit the actions within a rule every time a message is inspected, regardless of the mode that you have selected. When actions are audited, they are evaluated and compared with the messages that are being inspected. The mode setting restricts the effects of your policy actions, but the term audit only implies that the rules are evaluated. For more information about the procedures to change modes, see [Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx). The following modes are available:
  
    
    



  
    
    
> **Enforce** Rules within the policy are evaluated for all messages and supported file types. Mail flow can be disrupted if data is detected that meets the conditions of the policy. All actions described within the policy are taken.
    
  

  
    
    
> **Test DLP policy with Policy Tips** Rules within the policy are evaluated for all messages and supported file types. Mail flow will not be disrupted if data is detected that meets the conditions of the policy. That is, messages are not blocked. If Policy Tips are configured, they are shown to users.
    
  

  
    
    
> **Test DLP policy without Policy Tips** Rules within the policy are evaluated for all messages and supported file types. Mail flow will not be disrupted if data is detected that meets the conditions of the policy. That is, messages are not blocked. If Policy Tips are configured, they are not shown to users.
    
  

## For more information

 [Data loss prevention in Exchange 2016](data-loss-prevention-in-exchange-2016.md)
  
    
    
 [Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx)
  
    
    
 [Policy Tips](http://technet.microsoft.com/library/4266b83c-dd8a-4b3d-99ff-402e68fc810c.aspx)
  
    
    

