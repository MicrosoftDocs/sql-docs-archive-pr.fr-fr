---
title: Transmission de paramètres d’informations de périphérique aux extensions de rendu | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea50de3955ab152cbd92d5fd50ef8b2281a67eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697491"
---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>Transmission de paramètres d'informations de périphérique aux extensions de rendu
  Dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], les paramètres d'informations de périphérique sont utilisés pour passer les paramètres de rendu à l'extension de rendu définie. Les paramètres du service Web Report Server sont passés comme élément XML **DeviceInfo** , puis sont traités par le serveur de rapports. Des valeurs par défaut étant attribuées aux paramètres d'informations de périphérique, ces paramètres sont considérés comme des arguments facultatifs lors du processus de rendu. Toutefois, vous pouvez utiliser ces paramètres afin de personnaliser le rendu et remplacer les valeurs par défaut fournies par le serveur.  
  
 Les paramètres d'informations de périphérique peuvent être spécifiés de diverses manières. Vous pouvez utiliser la méthode Render dans un programme. Si vous accédez à un rapport à l'aide de son URL, vous pouvez spécifier les informations de périphérique sous la forme de paramètres d'URL. Enfin, vous pouvez modifier les paramètres d'informations de périphérique dans les fichiers de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et ainsi spécifier les paramètres de rendu de manière globale. Pour plus d’informations sur la spécification des paramètres de rendu de manière globale, consultez [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
## <a name="passing-device-information-using-the-render-method"></a>Passage des informations de périphérique à l'aide de la méthode Render  
 Pour passer des paramètres d'informations de périphérique à l'extension de rendu définie, utilisez la méthode <xref:ReportExecution2005.ReportExecutionService.Render%2A>. Par exemple, la chaîne XML suivante peut être passée à la méthode <xref:ReportExecution2005.ReportExecutionService.Render%2A> pour créer un fragment HTML quand le rapport est restitué au format HTML.  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 Lorsqu'un rapport est restitué sous la forme d'un fragment HTML, son contenu est placé dans un élément TABLE et aucun élément HTML ou BODY n'est utilisé. Vous pouvez utiliser ce fragment afin d'intégrer le rapport concerné à un document HTML existant. Pour plus d’informations sur les paramètres d’informations de périphérique utilisés pour le format HTML, consultez [Paramètres d’informations de périphérique HTML](../../html-device-information-settings.md).  
  
## <a name="passing-device-information-using-url-access"></a>Passage d'informations de périphérique à l'aide d'un accès URL  
 Vous pouvez également passer des paramètres d'informations de périphérique en utilisant un accès URL. Les paramètres d'informations de périphérique sont alors passés sous la forme de paramètres d'URL. La chaîne d'accès URL suivante peut être passée au serveur de rapports pour générer un rapport rendu ne comportant pas de barre d'outils de visionneuse HTML.  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 Pour plus d’informations, consultez [Spécifier les paramètres d’informations de périphérique dans une URL](../../specify-device-information-settings-in-a-url.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres d’informations de périphérique pour les extensions de rendu &#40;Reporting Services&#41;](../../device-information-settings-for-rendering-extensions-reporting-services.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../../customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
