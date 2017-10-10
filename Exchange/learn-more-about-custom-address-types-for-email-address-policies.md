---
title: Learn more about custom address types for email address policies
ms.prod: EXCHANGE
ms.assetid: f5c9bbf2-c500-4cf2-aa2a-2c43c993cf6b
---


# Learn more about custom address types for email address policies

When creating an email address policy, you can use the following email address types:
  
    
    


- **Precanned SMTP email address**. Precanned SMTP email addresses are commonly used email address types that are provided for you.
    
  
- **Custom SMTP email address**. If you don't want to use one of the precanned SMTP email addresses, you can specify a custom SMTP email address.
    
    When creating a custom SMTP email address, you can use the variables in the following table to specify alternate values for the local part of the email address.
    

|**Variable**|**Value**|
|:-----|:-----|
|%g  <br/> |Given name (first name)  <br/> |
|%i  <br/> |Middle initial  <br/> |
|%s  <br/> |Surname (last name)  <br/> |
|%d  <br/> |Display name  <br/> |
|%m  <br/> |Exchange alias  <br/> |
|% _x_s  <br/> |Uses the first  _x_ letters of the surname. For example, if _x_ = 2, the first two letters of the surname are used. <br/> |
|% _x_g  <br/> |Uses the first  _x_ letters of the given name. For example, if _x_ = 2, the first two letters of the given name are used. <br/> |
   
- **Non-SMTP email address**. The following types of non-SMTP email addresses are supported:
    
  - EX (Legacy DN Proxy Address Prefix DisplayName)
    
  
  - X.500
    
  
  - X.400
    
  
  - MSMail
    
  
  - CcMail
    
  
  - Lotus Notes
    
  
  - Novell GroupWise
    
  
  - Exchange Unified Messaging proxy address (EUM proxy address)
    
  

    > [!IMPORTANT]
      > In Exchange, all non-SMTP email addresses are considered custom addresses. Exchange doesn't provide unique dialog boxes or property pages for X.400, GroupWise, or Lotus Notes email address types. If you add a non-SMTP custom email address, you must have the appropriate dynamic-link library (DLL) files. If you don't provide the appropriate DLL files, you won't be able to create a customized email address policy. The following error will be logged in Event Viewer: "The email address description object in the Microsoft Exchange directory for the 'SADF' address type on 'i386' machines are missing." 

For detailed instructions about how to create an email address policy, see the following topics:
  
    
    

 [Procedures for email address policies in Exchange 2016](procedures-for-email-address-policies-in-exchange-2016.md) **Create an Email Address Policy By Using Recipient Filters**
