---
title: Référencement d’assemblys dans un fichier RDL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14593717d2319d7d702fd0c414e0c24428006f51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696503"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Référencement d'assemblys dans un Fichier RDL
  Pour prendre en charge l’utilisation d’assemblys de code personnalisés dans les fichiers de définition de rapport, deux éléments RDL (Report Definition Language) sont inclus dans la spécification RDL : l’élément **CodeModules** et l’élément **Classes**.  
  
 L’élément **CodeModules** vous permet de faire référence aux assemblys de code managé dans les expressions de rapport. **CodeModules** est un élément de niveau supérieur qui contient la référence à l’assembly que vous utilisez dans vos fichiers de définition de rapport pour appeler des fonctions spécialisées. Une entrée dans une définition de rapport qui prend en charge l'utilisation d'un assembly personnalisé peut ressembler aux éléments suivants :  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Au lieu d’appeler <xref:System.Reflection.Assembly.Load%2A> de votre code personnalisé, enregistrez vos assemblys personnalisés en ajoutant manuellement des éléments **CodeModule** à votre fichier RDL ou en utilisant l’onglet **Références** de la boîte de dialogue **Propriétés de rapport**. Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 L’élément **Classes** prend en charge l’utilisation de membres d’instance dans une définition de rapport. L’élément **Classes** est un élément de niveau supérieur qui contient une référence au nom de classe et un nom d’instance. Une entrée dans une définition de rapport qui prend en charge l'utilisation de membres d'instance peut ressembler aux éléments suivants :  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Pour plus d’informations, consultez [Accès aux assemblys personnalisés par le biais d’expressions](accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblys personnalisés avec des rapports](using-custom-assemblies-with-reports.md)  
  
  
