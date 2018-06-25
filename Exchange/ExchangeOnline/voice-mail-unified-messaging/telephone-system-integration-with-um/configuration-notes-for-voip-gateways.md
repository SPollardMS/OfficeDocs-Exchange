---
title: "Configuration notes for supported VoIP gateways, IP PBXs, and PBXs"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1583674f-5a57-45fd-8125-087d1624e686
description: "This page provides links to configuration notes that have been created and tested by Microsoft or a VoIP gateway partner. When Microsoft or a partner deploys Unified Messaging with a new VoIP gateway and PBX or IP PBX configuration, the prerequisites and configuration settings are documented. This information is used to create a configuration note."
---

# Configuration notes for supported VoIP gateways, IP PBXs, and PBXs

This page provides links to configuration notes that have been created and tested by Microsoft or a VoIP gateway partner. When Microsoft or a partner deploys Unified Messaging with a new VoIP gateway and PBX or IP PBX configuration, the prerequisites and configuration settings are documented. This information is used to create a configuration note. 
  
Each PBX configuration note contains information about how to deploy Unified Messaging with a specific telephony configuration, and includes the manufacturer, model, and firmware version for the VoIP gateways, IP PBXs, or PBXs. In addition, each PBX configuration note includes other information, such as:
  
- Contributors in authoring the configuration note.
    
- Detailed prerequisites, including the following:
    
  - Features that have to be enabled or disabled on the PBX.
    
  - Specialized hardware that has to be installed.
    
  - Whether a VoIP gateway is required.
    
  - Features that must be present on the VoIP gateway, if one is needed.
    
  - Specific cabling requirements between an IP gateway and a PBX.
    
  - A list of Unified Messaging features that may not be available with a given telephony configuration.
    
To find out more about the Microsoft Unified Communications Open Interoperability Program for enterprise telephony infrastructure, including finding qualified SIP PSTN gateways and IP PBXs and the process telephony infrastructure vendors can use to join and participate in the program, see [Microsoft Unified Communications Open Interoperability Program](https://go.microsoft.com/fwlink/p/?linkId=132071).
  
## VoIP gateway, IP PBX, and PBX configuration notes

Microsoft is working with VoIP gateway partners, AudioCodes and Dialogic, to add to the list of PBXs that are tested. Because we are currently testing many combinations of telephony components, this topic is updated frequently. Please check back if you can't locate the appropriate configuration note for your deployment.
  
### Aastra
<a name="aastra"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Aastra MD110 (formerly Ericsson MD110)  <br/> |MX1 TSW R2A (aka BC13)  <br/> |Analog - Serial MD110  <br/> |Dialogic  <br/> |DMG1008LSW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
| Aastra MD110 (formerly Ericsson MD110)  <br/> |MX1 TSW R2A (aka BC13)  <br/> |E1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
| Aastra MX-ONE  <br/> |4.0  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Aastra  <br/> |[Download](http://www.aastra.com/cps/rde/aareddownload?file_id=4384-14746-_P06_XML&amp;dsproject=aastra&amp;mtype=pdf) <br/> |
   
### Alcatel
<a name="alcatel"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|OmniPCX 4400  <br/> |R4.2-d2.304-4-h-il-c6s2  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Avaya
<a name="avaya"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Aura  <br/> |Communication Manager 5.2.1 with SP 5  <br/> Session Manager 5.2.  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Avaya  <br/> |[Download](https://support.avaya.com/downloads/) <br/> |
|CS 2100  <br/> |CS 2100 SE13  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Avaya  <br/> |[Download](https://support.avaya.com/css/P8/documents/100149819) <br/> |
|Definity G3  <br/> |R009i.05.122.4  <br/> |Digital Set Emulation (DNI7434)  <br/> |Dialogic  <br/> |DMG1008DNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|Definity G3  <br/> |R013i.01.1.628.7  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Definity G3  <br/> |R013i.01.1.628.7  <br/> |T1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Definity G3  <br/> |R013i.01.1.628.7  <br/> |T1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Definity G3  <br/> |R013i.01.1.628.7  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Merlin Magix  <br/> |Release 1.5 v.6.0  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|S8300  <br/> |G3xV11 Communication Manager 1.3  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|S8300  <br/> |R013x.01.2.632.1  <br/> |T1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|S8300  <br/> |R013x.01.2.632.1  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|S8500  <br/> |Communication Manager 3.0 (R013x00.1.346.0)  <br/> |E1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|S8500  <br/> |Communication Manager 3.0 (R013x00.1.346.0)  <br/> |T1 CAS - In-Band DTMF  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|S8500  <br/> |Communication Manager 3.0 (R013x00.1.346.0)  <br/> |T1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|S8700  <br/> |R011x.02.0.110.4  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Cisco
<a name="cisco"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Cisco Call Manager 4.x  <br/> |4.x  <br/> |IP-to-IP  <br/> |AudioCodes  <br/> |AudioCodes  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Cisco Call Manager 5.1  <br/> |5.1.0.9921-12  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Microsoft  <br/> |[Download](https://go.microsoft.com/fwlink/p/?linkId=225083) <br/> |
|Cisco Unified Communications Manager 6.0 and 6.1  <br/> |6.x  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Microsoft  <br/> |[Download](https://go.microsoft.com/fwlink/p/?linkId=225083) <br/> |
|Cisco Unified Communications Manager 7.0  <br/> |7.0.2.20000-5  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Microsoft  <br/> |[Download](https://go.microsoft.com/fwlink/p/?linkId=196361) <br/> |
|Cisco Unified Communications Manager 8.0  <br/> |8.0.3.20000-5  <br/> |Direct SIP Connection  <br/> |N.A.  <br/> |N.A.  <br/> |Microsoft  <br/> |[Download](https://go.microsoft.com/fwlink/p/?linkId=213007) <br/> |
   
### Inter-Tel
<a name="inter-tel"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|5000  <br/> |Inter-Tel 5000 v2.1  <br/> |T1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Axxess  <br/> |Axxess V9.0  <br/> |T1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Intecom
<a name="Intecom"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|PointSpan M6880  <br/> |40PS3.5.K.2  <br/> |T1 CAS - SMDI  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Mitel
<a name="mitel"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|3300  <br/> |5.1.4.8  <br/> |E1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|3300  <br/> |5.1.4.8  <br/> |T1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|SX2000  <br/> |5.0.24  <br/> |Digital Set Emulation (DNISS430)  <br/> |Dialogic  <br/> |DMG1008MTLDNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|3300  <br/> |7  <br/> |T1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### NEC
<a name="nec"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Electra Elite 192  <br/> |SP034V4.5  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|NEAX2400IMX  <br/> |version 7400  <br/> |T1 CAS - serial MCI  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|NEAX2400IMX &amp; IPX  <br/> |version 7400  <br/> |Digital Set Emulation (DNIDtermIII)  <br/> |Dialogic  <br/> |DMG1008DNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|NEAX2400IPX  <br/> |Ver. R18.06.24.000  <br/> |T1 CAS - serial MCI  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|NEAX2400IPX  <br/> |Ver. R18.06.24.000  <br/> |Analog - serial MCI  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|NEAX2400IPX  <br/> |Ver.17 Rel.03.46.001  <br/> |T1 Q.SIG - serial MCI  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
   
### NeXspan
<a name="nexspan"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|S  <br/> |RMS1 version R1.3 E1TA  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Nortel
<a name="nortel"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|CS1000  <br/> |3.0 &amp; 4.5  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Meridian 81C  <br/> |4.5  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Meridian 81C  <br/> |4.5  <br/> |T1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Option11c  <br/> |Release 25  <br/> |Digital Set Emulation (DNI2616)  <br/> |Dialogic  <br/> |DMG1008DNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|Option11c  <br/> |Release 25  <br/> |T1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|Option11c  <br/> |Release 25  <br/> |E1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|CS-1000M (Succession)  <br/> |Release 25.40  <br/> |E1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
   
### Panasonic
<a name="panasonic"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|KX-TDA200  <br/> |001-001  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 1000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|KX-TDA200  <br/> |3  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|KX-TES824  <br/> |2.0.2  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Rolm
<a name="rolm"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|9751  <br/> |9005  <br/> |Digital Set Emulation (DNIRP400)  <br/> |Dialogic  <br/> |DMG1008RLMDNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
   
### ShoreTel
<a name="shoretel"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|IP Telephony System  <br/> |6.1  <br/> |Analog - SMDI  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|IP Telephony System  <br/> |7.5  <br/> |Analog - SMDI  <br/> |AudioCodes  <br/> |Mediant 1000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Siemens
<a name="siemens"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|HiCom 150E  <br/> |Rel. 2.2  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|HiCom 300  <br/> |SA300-V3.05  <br/> |BRI QSIG  <br/> |Dialogic  <br/> |DMG3000  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|HiCom 300  <br/> |9006.4SMR3  <br/> |Digital Set Emulation (DNIOptiset)  <br/> |Dialogic  <br/> |DMG1008DNIW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|HiCom 300  <br/> |9006.4SMR3  <br/> |T1 CAS - In-Band DTMF  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|HiPath 3550  <br/> |Rel. 3  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|HiPath 4000  <br/> |Ver 3.0 SMR5 SMP4  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|HiPath 4000  <br/> |SA300-V3.05  <br/> |BRI QSIG  <br/> |Dialogic  <br/> |DMG3000  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|HiPath 4000  <br/> |Ver 3.0 SMR5 SMP4  <br/> |T1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|HiPath 4000  <br/> |Version 2.0 SMR9 SMP0  <br/> |Analog - In-Band DTMF  <br/> |Dialogic  <br/> |DMG1008LSW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|HiPath 4000  <br/> |Version 2.0 SMR9 SMP0  <br/> |T1 Q.SIG  <br/> |Dialogic  <br/> |DMG2030DTIQ  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
   
### Sonus
<a name="sonus"> </a>

|**VoIP gateway model**|**VoIP gateway software release**|**Supported protocols**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|
|SBC 1000/2000  <br/> |2.2.1 or later  <br/> | TDM Signaling (ISDN): AT&amp;T 4ESS/5ESS, Nortel DMS- 100, Euro ISDN (ETSI 300-102), QSIG, NTT InsNet (Japan), ANSI National ISDN-2 (NI-2)  <br/>  TDM Signaling (CAS): T1 CAS (E&amp;M, Loop start); E1 CAS (R2)  <br/> |Sonus  <br/> |[Download](http://www.sonus.net/sites/default/files/sonussbc1k2kconfigo365.pdf) <br/> |
   
### Tadiran
<a name="tadiran"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Coral Flexicom  <br/> |14.67.49  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP 11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral Flexicom  <br/> |14.67.49  <br/> |BRI QSIG  <br/> |AudioCodes  <br/> |Mediant  <br/> 1000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral Flexicom  <br/> |14.67.49  <br/> |E1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral Flexicom  <br/> |14.67.49  <br/> |E1 Q.SIG  <br/> |AudioCodes  <br/> |Mediant 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral IPX  <br/> |14.67.49  <br/> |Analog - In-Band DTMF  <br/> |AudioCodes  <br/> |MP-11x FXO  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral IPX  <br/> |14.67.49  <br/> |BRI QSIG  <br/> |AudioCodes  <br/> |Mediant 1000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral IPX  <br/> |14.67.49  <br/> |E1 CAS - In-Band DTMF  <br/> |AudioCodes  <br/> |Mediant 2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
|Coral IPX  <br/> |14.67.49  <br/> |E1 QSIG  <br/> |AudioCodes  <br/> |Mediant  <br/> 1000/2000  <br/> |AudioCodes  <br/> |[Download](https://www.audiocodes.com/solutions/microsoft-unified-messaging) <br/> |
   
### Toshiba
<a name="toshiba"> </a>

|**PBX model**|**PBX software release**|**Protocol**|**Gateway vendor**|**Gateway model**|**Configuration author**|**Configuration file download**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|CTX  <br/> |AR1ME021.00  <br/> |Analog - SMDI  <br/> |Dialogic  <br/> |DMG1008LSW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
|CTX  <br/> |AR1ME021.00  <br/> |Analog - In-Band DTMF  <br/> |Dialogic  <br/> |DMG1008LSW  <br/> |Dialogic  <br/> |[Download](https://www.dialogic.com/support/helpweb/mg/integration.md) <br/> |
   

