---
title: Learn more about user call logs
ms.prod: EXCHANGE
ms.assetid: 9b602497-de6b-43fe-a0d6-88b2151592a8
---


# Learn more about user call logs

Use user call logs to view the following information about specific Unified Messaging (UM) users:
  
    
    


- Details about the UM calls for a user over the last 90 days.
    
  
- Audio quality of each call. Audio quality metrics might not be available for all calls, because the metrics depend on several factors, such as the type and length of the call. 
    
  

## How do I interpret the UM user call log?

The user call log includes the following information for each call:
  
    
    

- **DATE AND TIME:** The date and time of the call, in the time zone that the selected user has set in Outlook Web App.
    
  
- **DURATION:** How long the call lasted, in minutes (MM) and seconds (SS) in the following format: MM:SS.
    
  
- **CALL TYPE:** The type of call:
    
  - **Call Answering:** The call wasn't answered and was forwarded to the UM servers, and the caller left a voice message.
    
  
  - **Call Answering Missed Call:** The call wasn't answered and was forwarded to the UM servers, and the caller didn't leave a voice message.
    
  
  - **Subscriber Access:** A call to the subscriber access number, where the caller signed in and was authenticated to UM with their extension and password to access email, calendars, and voice messages over the phone.
    
  
  - **Auto Attendant:** The call was answered by an UM auto attendant. These calls are typically calls in which the caller dialed your organization's main phone number.
    
  
  - **Fax:** A call in which a fax tone was detected. If you have configured fax partners, this call would be sent to the partner.
    
  
  - **PlayonPhone:** A call placed by UM because the user clicked the Play On Phone button in a voice message in either Outlook Web App or Outlook.
    
  
  - **FindMe:** An outbound call placed by UM as a result of a Find Me rule in a personal auto attendant.
    
  
  - **Unauthenticated Pilot Number:** A call to the Outlook Voice Access number where the caller didn't sign in and wasn't authenticated.
    
  
  - **Greetings Recording:** A call placed by UM to record personal greetings for a user.
    
  
  - **None:** A call where the type wasn't defined.
    
  
- **CALLING NUMBER:** The phone number or SIP address (for users in SIP dial plans, such as Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server users) of the intended recipient of the call.
    
  
- **CALLED NUMBER:** The phone number or SIP address of the caller.
    
  
- **UM IP GATEWAY:** The UM IP gateway that took the call.
    
  
- **AUDIO QUALITY:** The overall audio quality of the call. For more details about audio quality, select the row and click **Audio Quality Details**.
    
  

