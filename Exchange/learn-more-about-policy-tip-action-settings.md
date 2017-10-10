---
title: Learn more about Policy Tip action settings
ms.prod: EXCHANGE
ms.assetid: 61685a89-ac20-4a27-b502-e83f5f8c60f4
---


# Learn more about Policy Tip action settings

When you configure a custom DLP Policy Tip notification message, there are four types of Policy Tips that you can customize. You can save many custom messages, each in a separate language, for each type of Policy Tip. For more information about working with Policy Tips, see  [Configure Policy Tips](http://technet.microsoft.com/library/cec50a35-1d00-47b3-b72f-ac1bb0fd630e.aspx). You are not required to create your own customized notification messages because Microsoft Exchange contains default Policy Tip notifications. Email senders in your company will only see your custom notifications if there is a rule within a DLP policy that causes the Policy Tip notification to appear.
  
    
    


## Policy Tip actions and their effects

The following four Policy Tip actions can be configured with custom text. In order for any of your custom text to appear, a DLP policy rule must include the **Notify the sender with a Policy Tip** action. You can configure this action in the DLP rules editor.
  
    
    

|||
|:-----|:-----|
|Policy Tip Notification Action  <br/> |Meaning  <br/> |
|**Notify the sender** <br/> |Your text only appears when a **Notify the sender, but allow them to send** action is initiated. This type of action can be configured in the DLP rules editor. <br/> |
|**Allow the sender to override** <br/> |Your text only appears when **Block the message, but allow the sender to override and send** action is initiated. This action can be configured in the DLP rules editor. <br/> |
|**Block the message** <br/> |Your text only appears when the following actions are initiated: **Block the message** or **Block the message unless it's a false positive**. These actions can be configured in the DLP rules editor.  <br/> |
|**Link to compliance URL** <br/> |This link to more information appears in all notifications.  <br/> |
   

## For more information

 [Data loss prevention in Exchange 2016](data-loss-prevention-in-exchange-2016.md)
  
    
    
 [Policy Tips](http://technet.microsoft.com/library/4266b83c-dd8a-4b3d-99ff-402e68fc810c.aspx)
  
    
    

