---
title: Omission de valeurs pour les objets de service web facultatifs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697495"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>Omission de valeurs pour les objets de service Web facultatifs
  Les propriétés de plusieurs des types complexes du services web Report Server sont souvent suivies d’une propriété appelée Specified. Lorsque c'est le cas, le nom des propriétés se compose de leur nom original suivi de la mention « Specified ». La présence de cette mention signifie que certaines valeurs des propriétés peuvent parfois être omises. Ce phénomène est la conséquence directe de la conversion à partir du langage WSDL (Web Service Description Language) dans une classe proxy du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Par exemple, la propriété de service Web <xref:ReportService2010.DataSourceDefinition.Enabled%2A> de type complexe <xref:ReportService2010.DataSourceDefinition> est suivie d'une propriété intitulée <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Lorsque vous développez une application et que vous ne souhaitez pas définir de valeur pour la propriété <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, vous n'avez pas à attribuer de valeur à <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, la valeur par défaut `true` étant en effet utilisée. Toutefois, pour que cette opération se vérifie, vous devez au préalable définir <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> sur `false`. Lorsque vous attribuez une valeur à la propriété <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, vous devez définir <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> sur `true`. Seules les propriétés accessibles en écriture nécessitent de respecter cette condition. En revanche, les propriétés en lecture seule ne requièrent aucune action de votre part.  
  
> [!IMPORTANT]  
>  Si vous ne parvenez pas à spécifier une propriété en suivant la procédure mentionnée ci-avant, le comportement du service Web peut se révéler imprévisible.  
  
 Les types de données qui requièrent généralement la gestion de la propriété spécifiée supplémentaire sont `Boolean` , `DateTime` et `Enumeration` .  
  
 Pour obtenir un exemple, consultez la méthode <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
