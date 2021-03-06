---
title: "CA2212: Do not mark serviced components with WebMethod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-code-analysis"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# CA2212: Do not mark serviced components with WebMethod
|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Cause  
 A method in a type that inherits from <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> is marked with <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Rule Description  
 <xref:System.Web.Services.WebMethodAttribute> applies to methods within an XML Web service that were created by using ASP.NET; it makes the method callable from remote Web clients. The method and class must be public and executing in an ASP.NET Web application. <xref:System.EnterpriseServices.ServicedComponent> types are hosted by COM+ applications and can use COM+ services. <xref:System.Web.Services.WebMethodAttribute> is not applied to <xref:System.EnterpriseServices.ServicedComponent> types because they are not intended for the same scenarios. Specifically, adding the attribute to the <xref:System.EnterpriseServices.ServicedComponent> method does not make the method callable from remote Web clients. Because <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.EnterpriseServices.ServicedComponent> method have conflicting behaviors and requirements for context and transaction flow, the behavior of the method will be incorrect in some scenarios.  
  
## How to Fix Violations  
 To fix a violation of this rule, remove the attribute from the <xref:System.EnterpriseServices.ServicedComponent> method.  
  
## When to Suppress Warnings  
 Do not suppress a warning from this rule. There are no scenarios where combining these elements is correct.  
  
## See Also  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>