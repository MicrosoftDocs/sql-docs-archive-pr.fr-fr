---
title: Services web Report Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bb43a0fa52a243bd250f70fac16e18d949f8197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605093"
---
# <a name="report-server-web-service"></a>service Web Report Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]permet d’accéder aux fonctionnalités complètes du serveur de rapports par le biais du service Web Report Server. Le service Web Report Server est un service Web XML avec une API SOAP. Il utilise SOAP sur HTTP et agit comme une interface de communication entre les programmes clients et le serveur de rapports. Le service Web fournit deux points de terminaison (un pour l'exécution des rapports et l'autre pour la gestion des rapports) avec des méthodes qui exposent les fonctionnalités du serveur de rapports et qui vous permettent de créer des outils personnalisés pour n'importe quelle partie du cycle de vie du rapport.  
  
 Trois méthodes principales s’offrent à vous pour développer des applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] basées sur le service web. Vous pouvez :  
  
-   Développez des applications à l’aide [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de et du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK. Pour plus d’informations sur l’utilisation du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour générer des applications de service web, consultez [Génération d’applications à l’aide du service web et du .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Développer des applications à l’aide de l’utilitaire **rs** (RS.exe), l’environnement de script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Avec les scripts [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], vous pouvez exécuter n’importe laquelle des opérations de service web Report Server. Pour plus d’informations sur les scripts dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Écrire des scripts avec l’utilitaire rs.exe et le service web](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Développer des applications à l'aide de n'importe quel jeu SOAP d'outils de développement. Pour plus d’informations, consultez [Rôle de SOAP dans Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Diagramme de programmation  
 ![Options de développement du service web Report Server](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Options de développement du service web Report Server")  
Options de développement de service Web disponibles dans Reporting Services  
  
## <a name="in-this-section"></a>Dans cette section  
 [Méthodes du service web Report Server](../report-server-web-service/methods/report-server-web-service-methods.md)  
 Décrit les fonctionnalités et les méthodes de chaque service Web Report Server.  
  
 [Rôle de SOAP dans Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Fournit une vue d'ensemble du protocole SOAP et de la manière dont il est utilisé dans les services Web Report Server.  
  
 [Accès à l'API  SOAP](../report-server-web-service/accessing-the-soap-api.md)  
 Décrit le langage WSDL (Web Service Description Language) et fournit des URL pour accéder à un fichier WSDL Reporting Services.  
  
 [Création d’applications à l’aide du service web et du .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Contient des informations sur le développement d'applications et de services Web qui appellent l'API SOAP Reporting Services.  
  
 [Écrire des scripts avec l'utilitaire rs.exe et le service Web](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Fournit une vue d'ensemble de l'environnement de script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [Informations techniques de référence &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)  
 Contient les documents de référence spécifiques aux méthodes des services Web Report Server et aux types complexes correspondants.  
  
## <a name="user-requirements-for-web-service-development"></a>Conditions requises liées à l'utilisateur pour le développement du service Web  
 Pour développer des applications à l'aide du service Web Report Server, vous devez posséder :  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 ou version ultérieure, installé sur un ordinateur doté d’une connexion Internet et ayant accès au serveur de rapports ;  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ou le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installé sur un ordinateur si vous souhaitez développer et déployer des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications à l’aide de l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
-   Une compréhension approfondie des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalités et des fonctionnalités.  
  
-   de solides acquis concernant SOAP et les [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)];  
  
-   Expérience de développement dans un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] langage compatible, tel que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , si vous envisagez d’utiliser [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] en tant que plateforme de développement.  
  
## <a name="see-also"></a>Voir aussi  
 [Service Web des serveurs de rapports](../report-server-web-service/report-server-web-service.md)  
  
  
