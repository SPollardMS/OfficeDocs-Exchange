---
title: Learn more about creating UM dial plans
ms.prod: EXCHANGE
ms.assetid: 66245356-637c-4844-a630-9e1dd7e971f9
---


# Learn more about creating UM dial plans

A Unified Messaging (UM) dial plan contains configuration information related to your telephony network. A UM dial plan establishes a link from a user's telephone extension number to a UM-enabled mailbox. When you create a UM dial plan, you can configure the number of digits in the extension numbers, the Uniform Resource Identifier (URI) type, and the Voice over IP (VoIP) security setting for the dial plan. Each time that you create a UM dial plan, a UM mailbox policy is also created. The UM mailbox policy is named < _DialPlanName_> Default Policy.
  
    
    


## Creating a new dial plan

When you are creating a new UM dial plan, you will need to provide the following information:
  
    
    

- **Name**: Type the name of the dial plan. A UM dial plan name is required and must be unique. However, it's used only for display in the EAC and the Shell. If you have to change the display name of the dial plan after it's been created, you must first delete the existing UM dial plan and then create another dial plan that has the appropriate name. If your organization uses multiple UM dial plans, we recommend that you use meaningful names for your UM dial plans. The maximum length of a UM dial plan name is 49 characters, and it can include spaces. However, it can't include any of the following characters: " / \\ [ ] : ; | = , + * ? < >.
    
    > [!IMPORTANT]
      > Although the field for the name of the dial plan can accept 64 characters, the name of the dial plan can't be longer than 49 characters. If you try to create a dial plan name that contains more than 49 characters, you will receive an error message. This happens because when you create a dial plan, a default UM mailbox policy is also created that has the name  _<DialPlanName>_ Default Policy. Therefore, the name of the UM mailbox policy is 15 characters longer than the name of the dial plan. The _name_ parameter for the UM mailbox policy is limited to 64 characters, and if the dial plan name exceeds 49 characters, the policy name will be too long.
- **Extension length**: Enter the number of digits for the dial plan. The number of digits for extension numbers is based on the telephony dial plan created on a PBX or IP PBX. For example, if a user associated with a telephony dial plan dials a four-digit extension to call another user in the same PBX or IP PBX dial plan, you would select 4 as the number of digits for the length of the extension. 
    
    This is a required field that has a value range from 1 through 20. The typical extension length is from 3 through 7. If your existing telephony environment includes extension numbers, you must specify a number of digits that matches the number of digits in those extensions.
    
    When you create a Session Initiation Protocol (SIP) or an E.164 dial plan and associate a UM-enabled user with the dial plan, you must still input an extension number to be used by the user. This number is used by Outlook Voice Access users when they access their mailboxes.
    
  
- **Dial plan type** A Uniform Resource Identifier (URI) is a string of characters that identifies or names a resource. The main purpose of this identification is to enable VoIP devices to communicate with other devices over a network using specific protocols. URIs are defined in schemes that define a specific syntax and format and the protocols for the call. In simple terms, this format is passed from the IP PBX or PBX. After you create a UM dial plan, you won't be able to change the URI type without deleting the dial plan, and then re-creating the dial plan to include the correct URI type. You can select one of the following URI types for the dial plan:
    
  - **Telephone extension** This is the most common URI type. The calling and called party information from the VoIP gateway or IP Private Branch eXchange (PBX) is listed in one of the following formats: Tel:512345 or 512345@< _IP address_>. This is the default URI type for dial plans.
    
  
  - **SIP URI** Use this URI type if you must have a Session Initiation Protocol (SIP) URI dial plan such as an IP PBX that supports SIP routing or if you're integrating Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server and Unified Messaging. The calling and called party information from the VoIP gateway. IP PBX, or Communications Server 2007 R2 or Lync Server is listed as a SIP address in the following format: sip:< _username_>@< _domain_ or _ IP address_>:Port.
    
  
  - **E.164** E.164 is an international numbering plan for public telephone systems in which each assigned number contains a country code, a national destination code, and a subscriber number. The calling and called party information sent from the VoIP gateway or IP PBX is listed in the following format: Tel:+14255550123.
    
  

    > [!CAUTION]
      > After you create a dial plan, you will be unable to change the URI type without deleting the dial plan, and then re-creating the dial plan to include the correct URI type. 
- **VoIP security mode** Use this drop-down list to select the VoIP security setting for the UM dial plan. You can select one of the following security settings for the dial plan:
    
  - **Unsecured** By default, when you create a UM dial plan, it is set to not encrypt the SIP signaling or RTP traffic. In unsecured mode, the Client Access and Mailbox servers associated the UM dial plan send and receive data from VoIP gateways, IP PBXs, SBCs and other Client Access and Mailbox servers using no encryption. In unsecured mode, neither the Realtime Transport Protocol (RTP) media channel nor the SIP signaling information is encrypted.
    
  
  - **SIP secured** When you select **SIP secured**, only the SIP signaling traffic is encrypted, and the RTP media channels still use TCP, which isn't encrypted. With SIP secured, Mutual Transport Layer Security (TLS) is used to encrypt the SIP signaling traffic and VoIP data.
    
  
  - **Secured** When you select **Secured**, both the SIP signaling traffic and the RTP media channels are encrypted. Both the secure signaling media channel that uses Secure Realtime Transport Protocol (SRTP) and the SIP signaling traffic use mutual TLS to encrypt the VoIP data.
    
  
- **Audio language**: Select the language that you want callers to hear when they call into an Outlook Voice Access number. To use multiple languages for Outlook Voice Access users, install the required UM language packs. For more information about installing UM language packs, see  [UM Languages, Prompts, and Greetings](http://technet.microsoft.com/library/d48df962-9669-420b-838f-44bfe1012e2f.aspx).
    
  
- **Country/Region code**: Use this field to type the country/region code number used for outgoing calls. This number will precede the telephone number dialed. This field accepts from 1 through 4 digits. For example, in the United States, the country/region code is 1. In the United Kingdom, it's 44.
    
  

## For more information
<a name="fmi"> </a>

 [Manage a UM Dial Plan](http://technet.microsoft.com/library/a89735e4-36ec-49fb-ad0f-192fad37e801.aspx)
  
    
    

