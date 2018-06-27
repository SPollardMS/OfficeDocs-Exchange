---
title: "DLP policy templates supplied in Exchange"
ms.author: stephow
author: stephow-msft
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7e1917ab-1920-4a52-97d1-7dfe2add6198
description: "In Microsoft Exchange Server 2013 and Exchange Online, you can use data loss prevention (DLP) policy templates as a starting point for building DLP policies that help you meet your specific regulatory and business policy needs. You can modify the templates to meet the specific needs of your organization."
---

# DLP policy templates supplied in Exchange

In Microsoft Exchange Server 2013 and Exchange Online, you can use data loss prevention (DLP) policy templates as a starting point for building DLP policies that help you meet your specific regulatory and business policy needs. You can modify the templates to meet the specific needs of your organization.
  
> [!CAUTION]
> You should enable your DLP policies in test mode before running them in your production environment. During such tests, it is recommended that you configure sample user mailboxes and send test messages that invoke your test policies in order to confirm the results. > Use of these policies does not ensure compliance with any regulation. After your testing is complete, make the necessary configuration changes in Exchange so the transmission of information complies with your organization's policies. For example, you might need to configure TLS with known business partners or add more restrictive transport rule actions, such as adding rights protection to messages that contain a certain type of data. 
  
## Templates available for DLP

The following table lists the DLP policy templates in Exchange. To learn more about customizing these templates to create DLP policies, see [Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx).
  
|**Template**|**Description**|
|:-----|:-----|
|Australia Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial data in Australia, including credit cards, and SWIFT codes.  <br/> |
|Australia Health Records Act (HRIP Act)  <br/> |Helps detect the presence of information commonly considered to be subject to the Health Records and Information Privacy (HRIP) act in Australia, like medical account number and tax file number.  <br/> |
|Australia Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Australia, like tax file number and driver's license.  <br/> |
|Australia Privacy Act  <br/> |Helps detect the presence of information commonly considered to be subject to the privacy act in Australia, like driver's license and passport number.  <br/> |
|Canada Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial data in Canada, including bank account numbers and credit cards.  <br/> |
|Canada Health Information Act (HIA)  <br/> |Helps detect the presence of information subject to Canada Health Information Act (HIA) for Alberta, including data like passport numbers and health information.  <br/> |
|Canada Personal Health Act (PHIPA) - Ontario  <br/> |Helps detect the presence of information subject to Canada Personal Health Information Protection Act (PHIPA) for Ontario, including data like passport numbers and health information.  <br/> |
|Canada Personal Health Information Act (PHIA) - Manitoba  <br/> |Helps detect the presence of information subject to Canada Personal Health Information Act (PHIA) for Manitoba, including data like health information.  <br/> |
|Canada Personal Information Protection Act (PIPA)  <br/> |Helps detect the presence of information subject to Canada Personal Information Protection Act (PIPA) for British Columbia, including data like passport numbers and health information.  <br/> |
|Canada Personal Information Protection Act (PIPEDA)  <br/> |Helps detect the presence of information subject to Canada Personal Information Protection and Electronic Documents Act (PIPEDA), including data like passport numbers and health information.  <br/> |
|Canada Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Canada, like health ID number and social insurance number.  <br/> |
|France Data Protection Act  <br/> |Helps detect the presence of information commonly considered to be subject to the Data Protection Act in France, like the health insurance card number.  <br/> |
|France Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial information in France, including information like credit card, account information, and debit card numbers.  <br/> |
|France Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in France, including information like passport numbers.  <br/> |
|Germany Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial data in Germany like EU debit card numbers.  <br/> |
|Germany Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Germany, including information like driver's license and passport numbers.  <br/> |
|Israel Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial data in Israel, including bank account numbers and SWIFT codes.  <br/> |
|Israel Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Israel, like national ID number.  <br/> |
|Israel Protection of Privacy  <br/> |Helps detect the presence of information commonly considered to be subject to the Protection of Privacy in Israel, including information like bank account numbers or national ID.  <br/> |
|Japan Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial information in Japan, including information like credit card, account information, and debit card numbers.  <br/> |
|Japan Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Japan, including information like driver's license and passport numbers.  <br/> |
|Japan Protection of Personal Information  <br/> |Helps detect the presence of information subject to Japan Protection of Personal Information, including data like resident registration numbers.  <br/> |
|PCI Data Security Standard (PCI DSS)  <br/> |Helps detect the presence of information subject to PCI Data Security Standard (PCI DSS), including information like credit card or debit card numbers.  <br/> |
|Saudi Arabia - Anti-Cyber Crime Law  <br/> |Helps detect the presence of information commonly considered to be subject to the Anti-Cyber Crime Law in Saudi Arabia, including international bank account numbers and SWIFT codes.  <br/> |
|Saudi Arabia Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial data in Saudi Arabia, including international bank account numbers and SWIFT codes.  <br/> |
|Saudi Arabia Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in Saudi Arabia, like national ID number.  <br/> |
|U.K. Access to Medical Reports Act  <br/> |Helps detect the presence of information subject to United Kingdom Access to Medical Reports Act, including data like National Health Service numbers.  <br/> |
|U.K. Data Protection Act  <br/> |Helps detect the presence of information subject to United Kingdom Data Protection Act, including data like national insurance numbers.  <br/> |
|U.K. Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial information in United Kingdom, including information like credit card, account information, and debit card numbers.  <br/> |
|U.K. Personal Information Online Code of Practice (PIOCP)  <br/> |Helps detect the presence of information subject to United Kingdom Personal Information Online Code of Practice, including data like health information.  <br/> |
|U.K. Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in United Kingdom, including information like driver's license and passport numbers.  <br/> |
|U.K. Privacy and Electronic Communications Regulations  <br/> |Helps detect the presence of information subject to United Kingdom Privacy and Electronic Communications Regulations, including data like financial information.  <br/> |
|U.S. Federal Trade Commission (FTC) Consumer Rules  <br/> |Helps detect the presence of information subject to U.S. Federal Trade Commission (FTC) Consumer Rules, including data like credit card numbers.  <br/> |
|U.S. Financial Data  <br/> |Helps detect the presence of information commonly considered to be financial information in United States, including information like credit card, account information, and debit card numbers.  <br/> |
|U.S. Gramm-Leach-Bliley Act (GLBA)  <br/> |Helps detect the presence of information subject to Gramm-Leach-Bliley Act (GLBA), including information like social security numbers or credit card numbers.  <br/> |
|U.S. Health Insurance Act (HIPAA)  <br/> |Helps detect the presence of information subject to United States Health Insurance Portability and Accountability Act (HIPAA),including data like social security numbers and health information.  <br/> |
|U.S. Patriot Act  <br/> |Helps detect the presence of information commonly subject to U.S. Patriot Act, including information like credit card numbers or tax identification numbers.  <br/> |
|U.S. Personally Identifiable Information (PII) Data  <br/> |Helps detect the presence of information commonly considered to be personally identifiable information (PII) in the United States, including information like social security numbers or driver's license numbers.  <br/> |
|U.S. State Breach Notification Laws  <br/> |Helps detect the presence of information subject to U.S. State Breach Notification Laws, including data like social security and credit card numbers.  <br/> |
|U.S. State Social Security Number Confidentiality Laws  <br/> |Helps detect the presence of information subject to U.S. State Social Security Number Confidentiality Laws, including data like social security numbers.  <br/> |
   
## For more information

[Data loss prevention](data-loss-prevention.md)
  
[Create a DLP policy from a template](create-dlp-policy-from-template.md)
  
[Sensitive Information Types Inventory](http://technet.microsoft.com/library/98b81f9c-87bb-4905-8e53-04621c3ae74d.aspx)
  

