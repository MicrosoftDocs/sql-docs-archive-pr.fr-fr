---
title: Paramètres d’informations de périphérique XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e642034d445e52485874c71df110bff81b9c1aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704760"
---
# <a name="xml-device-information-settings"></a>Paramètres d'informations de périphérique XML
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu au format XML.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|`XSLT`|Chemin d'accès dans l'espace de noms du serveur de rapports d'un XSLT et destiné au fichier XML, par exemple `/Transforms/myxslt`. Le fichier xsl doit être une ressource publiée sur le serveur de rapports et vous devez y accéder par le biais d'un chemin d'accès de l'élément du serveur de rapports. La valeur de ce paramètre est appliquée après tout XSLT spécifié dans le rapport. Si le paramètre `XSLT` est appliqué, le paramètre `OmitSchema` est ignoré.|  
|**MIMEType**|Type MIME (Multipurpose Internet Mail Extensions) du fichier XML.|  
|**UseFormattedValues**|Indique s'il faut restituer la valeur mise en forme d'une zone de texte lors de la génération des données XML. Une valeur false indique que la valeur sous-jacente de la zone de texte est utilisée.|  
|**Indented**|Indique s'il faut générer du code XML mis en retrait. La valeur par défaut `false` génère un code XML compressé sans mise en retrait.|  
|`OmitNamespace`|Indique s'il faut omettre l'espace de noms XML par défaut.<br /><br /> Si la valeur est True, le XML ne spécifie aucun espace de noms par défaut.<br /><br /> Si la valeur est False, le XML spécifie un espace de noms par défaut avec la valeur de la propriété DataSchema du rapport. La propriété DataSchema utilise par défaut le nom du rapport.<br /><br /> La valeur par défaut est `false`.|  
|`OmitSchema`|Indique s'il faut omettre l'emplacement du schéma XML par défaut. L'emplacement est l'attribut SchemaLocation. La valeur par défaut d'OmitSchema dépend de la valeur d'OmitNamespace :<br /><br /> If OmitNamespace = False, then OmitSchema = `False` par défaut. L'utilisateur peut remplacer la valeur par défaut en attribuant la valeur True à OmitSchema.<br /><br /> If OmitNamespace = True, then OmitSchema fonctionne comme `True` indépendamment de la valeur explicitement configurée pour OmitShema.|  
|**Encodage**|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
|**FileExtension**|Extension de fichier à utiliser pour le fichier généré.|  
|**Schéma**|Indique si la définition de schéma XML (XSD) est restituée ou si les données XML réelles sont restituées. La valeur `true` indique qu'un schéma XML est restitué. La valeur par défaut est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passage de paramètres d’informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
