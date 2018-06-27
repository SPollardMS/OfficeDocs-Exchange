---
title: "Hybrid Configuration wizard FAQs"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 12/9/2016
ms.audience: Developer
ms.topic: overview
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection:
- Hybrid
- Ent_O365_Hybrid
ms.assetid: e911e6e0-e36e-4430-ac36-c745a10d6c26
description: "Microsoft has released a new Hybrid Configuration wizard that simplifies the configuration of a hybrid deployment, allows for more flexibility with your hybrid configuration, and ensures you are always running the most up to date versions of the experience. This version of the hybrid wizard is built into Exchange 2016 and releases of Exchange 2013 starting with Cumulative Update 10, but even if you're running an older Exchange 2013 cumulative update (CU) or Exchange 2010 Service Pack 3 (SP3), you can still download the new wizard."
---

# Hybrid Configuration wizard FAQs

Microsoft has released a new Hybrid Configuration wizard that simplifies the configuration of a hybrid deployment, allows for more flexibility with your hybrid configuration, and ensures you are always running the most up to date versions of the experience. This version of the hybrid wizard is built into Exchange 2016 and releases of Exchange 2013 starting with Cumulative Update 10, but even if you're running an older Exchange 2013 cumulative update (CU) or Exchange 2010 Service Pack 3 (SP3), you can still download the new wizard.
  
For more information about the Office 365 Hybrid Configuration wizard, check out [Introducing the Microsoft Office 365 Hybrid Configuration Wizard](https://go.microsoft.com/fwlink/?LinkId=717122) and [Office 365 Hybrid Configuration Wizard for Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=730687) on the Exchange Team Blog. 
  
To download the Office 365 Hybrid Configuration wizard go to [https://aka.ms/HybridWizard](https://aka.ms/HybridWizard).
  
## Questions frequently asked by customers

Q: What versions of Exchange support the new Hybrid Configuration wizard?
  
> A: You need to have at least one server that meets the following requirements: 
    
- **Exchange 2010** Exchange 2010 SP3 needs to be installed on at least one server running the Mailbox, Hub Transport, and Client Access server roles. We also strongly recommend that you install the latest available Update Rollup available for Exchange 2010 SP3. 
    
- **Exchange 2013** The latest Exchange 2013 CU needs to be installed on at least one server running both the Mailbox and Client Access server roles. If you can't install the latest CU, the immediately previous release is also supported. Older CUs aren't supported. 
    
- **Exchange 2016** The latest release of Exchange 2016 needs to be installed on at least one server running the Mailbox server role. 
    
For example, assume you've installed Exchange 2013 CU8 in your on-premises organization, and the latest available release of Exchange 2013 is CU10. To remain in a supported hybrid configuration, you need to upgrade your Exchange 2013 servers to at least CU9. However, we'd strongly recommend you upgrade to CU10. 
    
Cumulative updates are released on a quarterly cadence. Keeping your servers on the latest cumulative update gives you some additional flexibility if you periodically need extra time to complete upgrades. 
    
Q: Will this Hybrid Configuration wizard work with Exchange 2007? 
  
> A: You can configure a hybrid deployment with Exchange 2007 in your organization. However, to do so you need to deploy at least one server running Exchange 2013 that meets the requirements above.
    
Q: Can I opt out of the new Hybrid Configuration wizard?
  
> A: No. The new Hybrid Configuration wizard is the only wizard that's supported in Exchange 2010, Exchange 2013 and Exchange 2016 today. 
    
Q: Can I upgrade my current Exchange 2010 hybrid configuration to Exchange 2013 or Exchange 2016 using the new Hybrid Configuration wizard? 
  
> A: Yes. Make sure you have at least one server that meets the current Hybrid Configuration wizard requirements and then run it. The wizard will know the current state of your hybrid configuration and seamlessly take you through the upgrade process.
    

