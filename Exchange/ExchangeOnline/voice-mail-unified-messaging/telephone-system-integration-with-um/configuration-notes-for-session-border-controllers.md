---
title: "Configuration notes for supported session border controllers"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 7/25/2017
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: d161f94a-a243-4294-93b3-2bf1dc17b59f

description: "Session border controllers (SBCs) enable you to connect your on-premises telephony network to a Microsoft datacenter over a dedicated public WAN connection. An SBC sits on the edge of your on-premises IP network and connects to a second SBC in a Microsoft datacenter."
---

# Configuration notes for supported session border controllers

Session border controllers (SBCs) enable you to connect your on-premises telephony network to a Microsoft datacenter over a dedicated public WAN connection. An SBC sits on the edge of your on-premises IP network and connects to a second SBC in a Microsoft datacenter.
  
SBCs require the use of digital certificates to encrypt all traffic between your on-premises organization and the Microsoft datacenter. You must obtain a digital certificate for the network border element, such as a session border controller, that you're using to communicate with Exchange hybrid and online deployments. Digital certificates establish trust between your on-premises organization and the Microsoft datacenter and enable mutual Transport Layer Security (mutual TLS). After this trust is established, the network border elements at your on-premises organization and at the Microsoft datacenter exchange session keys, and use these keys to encrypt the subsequent data traffic.
  
In hybrid or online deployments, a UM IP gateway represents an SBC. The subject common name in the certificate must match the fully qualified domain name (FQDN) value in the Address box on the UM IP gateway that you create. For example, if you specify the FQDN address sbcexternal.contoso.com on your UM IP gateway, make sure that the subject name and subject alternative name in the certificate contain the same value: sbcexternal.contoso.com. The name that you use is case-sensitive, so make sure the case is the same on both the certificate and the UM IP gateway. If you're using an Acme Packet SBC and the common name doesn't match the UM IP gateway's FQDN, the call will be rejected with a 403 error.
  
> [!NOTE]
> Because SBCs are designed to sit on the network edge, they also function as a firewall. If you set up an SBC behind your organization's firewall, it can cause configuration problems and is unsupported for connecting to Office 365. 
  
## Supported session border controllers

The following SBCs have been successfully tested for interoperability with Exchange hybrid and online deployments. Note that the capabilities and compatibilities of SBCs can vary, and the way you set them up can be different depending on other equipment on your network. Consult with the SBC manufacturer to see whether there are specific configuration notes for Unified Messaging in a hybrid or online deployment.
  
> [!NOTE]
> Exchange Online UM support for third-party PBX systems via direct connections from customer operated SBCs will end in July 2018. Please see the Exchange team blog [Discontinuation of support for session border controllers in Exchange Online unified messaging](https://blogs.technet.microsoft.com/exchange/2017/07/18/discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/) for more information. 
  
|||||
|:-----|:-----|:-----|:-----|
|**Vendor** <br/> |**Model** <br/> |**Configuration notes** <br/> |**Comments** <br/> |
|[Acme Packet](http://www.acmepacket.com) <br/> |Net-Net 3820 or 4500  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |Dedicated SBC  <br/> |
|[AudioCodes](https://www.audiocodes.com) <br/> |Mediant 1000B MSBG  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |Dedicated SBC  <br/> |
|[AudioCodes](https://www.audiocodes.com) <br/> |Mediant 1000B MSBG  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |SBC and IP gateway  <br/> |
|[Cisco](https://www.cisco.com/c/dam/en/us/solutions/collateral/enterprise-networks/unified-access/cube-asr-release-10-0.pdf) <br/> |ASR 1000  <br/> > [!NOTE]> Must have IOS 15.4(3)S3 or later installed.           |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |Dedicated SBC  <br/> |
|[Ingate](https://www.ingate.com/) <br/> |SIParator  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |Dedicated SBC  <br/> |
|[NET](http://www.net.com) <br/> |VX1200 &amp; VX1800  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |SBC option for a VoIP gateway product  <br/> |
|[Sonus](http://www.sonus.net/) <br/> |SBC 1000/2000 2.2.1 or later  <br/> |**Please contact the hardware vendor for up to date instructions on how to set up their device.** <br/> |Dedicated SBC  <br/> |
   

