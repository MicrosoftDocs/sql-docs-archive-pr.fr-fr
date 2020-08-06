---
title: Fonctionnalités dépréciées dans SQL Server Reporting Services dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610493"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Fonctions déconseillées dans SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités déconseillées de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Les fonctionnalités sont toujours disponibles dans la version dans laquelle elles sont déconseillées ; toutefois, leur suppression est planifiée dans une version future de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
 Dans cette rubrique :  
  
-   [Fonctions dépréciées dans SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Fonctions déconseillées dans SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Fonctions déconseillées dans SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Fonctions déconseillées dans SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a>SQL Server 2014 Reporting Services fonctionnalités déconseillées  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Fonctionnalités non prises en charge dans la prochaine version de SQL Server  
 Les fonctionnalités suivantes ne seront [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pas prises en charge dans la **prochaine** version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Évitez d'utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>Paramètres d'informations de périphérique d'extension de rendu HTML  
 Les paramètres d'informations de périphérique suivants pour l'extension de rendu HTML sont déconseillés.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Pour plus d'informations sur l'extension de rendu HTML, consultez [HTML Device Information Settings](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendu dans Microsoft Word et Microsoft Excel 1997-2003  
 Les extensions de rendu BIFF8[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] génèrent des rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] au format BIFF (Binary Interchange File Format) pour [!INCLUDE[msCoName](../includes/msconame-md.md)] Word et [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]comprend les extensions qui s’affichent au [!INCLUDE[msCoName](../includes/msconame-md.md)] format Office 2007-2010 Open XML.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Langage RDL (Report Definition Language) version 2005 et antérieures  
 Le langage Report Definition Language (RDL) version 2005 et antérieures est déconseillé. Pour plus d’informations sur le langage RDL, consultez [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Pour plus d'informations sur la mise à niveau des rapports, consultez [Upgrade Reports](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Éléments de rapport personnalisés SQL Server version 2005 et antérieures  
 Les éléments de rapport personnalisés compilés pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 et les versions antérieures sont déconseillés.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Instantanés Reporting Services version 2005 et antérieures  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]les instantanés rendus avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 et les versions antérieures sont déconseillés.  
  
#### <a name="report-models"></a>Modèles de rapport  
 Les modèles de rapport du langage de modélisation sémantique (SMDL) sont déconseillés. Bien que vous puissiez continuer à utiliser des modèles de rapport existants comme sources de données dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] les rapports, vous devez envisager de mettre à jour vos rapports afin de supprimer leur dépendance vis-à-vis des modèles de rapport.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]n’inclut pas les outils permettant de créer ou de mettre à jour des modèles de rapport. Pour plus d’informations, consultez [modifications avec rupture dans SQL Server Reporting Services dans SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Méthodes déconseillées dans le point de terminaison de service Web  
 Les opérations suivantes sont déconseillées dans le point de terminaison de service Web <xref:ReportService2010.ReportingService2010> :  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>Composants WebPart de SharePoint  
 Le fichier CAB d'installation **RSWebParts.cab** et les composants WebPart de SharePoint qui peuvent être extraits du fichier CAB, sont déconseillés. Les composants WebPart déconseillés sont Report Explorer (**SPExplorer.dwp**) et Report Viewer (**SPViewer.dwp**).  
  
 Pour plus d'informations sur les composants WebPart déconseillés, consultez [Afficher et explorer des rapports en mode natif à l'aide de composants WebPart SharePoint (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx).  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Fonctionnalités non prises en charge dans une future version de SQL Server  
 Les fonctions suivantes du [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] seront prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'a pas été déterminée.  
  
 Aucune fonctionnalité [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a été déconseillée dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a>SQL Server 2012 SP1 Reporting Services fonctionnalités déconseillées  
 Cette section décrit les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] déconseillées dans [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Les fonctions suivantes du [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] seront prises en charge dans la prochaine version de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'a pas été déterminée.  
  
### <a name="sharepoint-web-parts"></a>Composants WebPart de SharePoint  
 Le fichier CAB d'installation **RSWebParts.cab** et les composants WebPart de SharePoint qui peuvent être extraits du fichier CAB, sont déconseillés. Les composants WebPart déconseillés sont Report Explorer (**SPExplorer.dwp**) et Report Viewer (**SPViewer.dwp**).  
  
 Pour plus d'informations sur les composants WebPart déconseillés, consultez [Afficher et explorer des rapports en mode natif à l'aide de composants WebPart SharePoint (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx).  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a>SQL Server 2012 Reporting Services fonctionnalités déconseillées  
 Cette section décrit les fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] déconseillées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="html-rendering-extension-device-information-settings"></a>Paramètres d'informations de périphérique d'extension de rendu HTML  
 Les paramètres d'informations de périphérique suivants pour l'extension de rendu HTML sont déconseillés.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Pour plus d'informations sur l'extension de rendu HTML, consultez [HTML Device Information Settings](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendu dans Microsoft Word et Microsoft Excel 1997-2003  
 Les extensions de rendu BIFF8[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] génèrent des rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] au format BIFF (Binary Interchange File Format) pour [!INCLUDE[msCoName](../includes/msconame-md.md)] Word et [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]comprend les extensions qui s’affichent au [!INCLUDE[msCoName](../includes/msconame-md.md)] format Office 2007-2010 Open XML.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Langage RDL (Report Definition Language) version 2005 et antérieures  
 Le langage Report Definition Language (RDL) version 2005 et antérieures est déconseillé. Pour plus d’informations sur le langage RDL, consultez [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Pour plus d'informations sur la mise à niveau des rapports, consultez [Upgrade Reports](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Éléments de rapport personnalisés SQL Server version 2005 et antérieures  
 Les éléments de rapport personnalisés compilés pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 et les versions antérieures sont déconseillés.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Instantanés Reporting Services version 2005 et antérieures  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]les instantanés rendus avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 et les versions antérieures sont déconseillés.  
  
### <a name="report-models"></a>Modèles de rapport  
 Les modèles de rapport du langage de modélisation sémantique (SMDL) sont déconseillés. Bien que vous puissiez continuer à utiliser des modèles de rapport existants comme sources de données dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] les rapports, vous devez envisager de mettre à jour vos rapports afin de supprimer leur dépendance vis-à-vis des modèles de rapport.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]n’inclut pas les outils permettant de créer ou de mettre à jour des modèles de rapport. Pour plus d’informations, consultez [modifications avec rupture dans SQL Server Reporting Services dans SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Méthodes déconseillées dans le point de terminaison de service Web  
 Les opérations suivantes sont déconseillées dans le point de terminaison de service Web <xref:ReportService2010.ReportingService2010> :  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services fonctionnalités déconseillées  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="report-server-web-service-endpoints"></a>Points de terminaison du service Web Report Server  
 Les services Web <xref:ReportService2005.ReportingService2005> et <xref:ReportService2006.ReportingService2006> ont été déconseillés dans cette version. Ces points de terminaison ont été remplacés par un nouveau point de terminaison : <xref:ReportService2010.ReportingService2010>.  
  
 Le nouveau point de terminaison inclut toutes les fonctionnalités disponibles dans les points de terminaison déconseillés et les nouvelles fonctionnalités présentées dans SQL Server 2008 R2.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Compatibilité descendante](../getting-started/backward-compatibility.md)   
 [Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Fonctionnalités supprimées dans SQL Server Reporting Services dans SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
