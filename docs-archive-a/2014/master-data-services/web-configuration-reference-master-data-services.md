---
title: Référence de la configuration web (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 71e72bdb45a29c29c2187c381f67a525f0bd51c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707639"
---
# <a name="web-configuration-reference-master-data-services"></a>Référence de la configuration Web (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] utilise un fichier Web.config pour contenir les paramètres de configuration qui permettent à Internet Information Services (IIS) d’héberger l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] et le service web. Ce fichier Web.config se trouve dans le dossier WebApplication du chemin d'installation de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations sur le chemin et les autorisations, consultez [Autorisations d’accès aux dossiers et aux fichiers &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Éléments Web.Config  
 Le fichier Web.config contient un [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] élément personnalisé, **\<masterDataServices>** , en plus des éléments de configuration IIS, .NET Framework, ASP.NET et Windows Communication Foundation (WCF) standard. Le tableau suivant décrit les éléments inclus dans le fichier Web.config.  
  
|Élément de configuration|Description|  
|---------------------------|-----------------|  
|`masterDataServices`|Élément personnalisé. Connecte le service Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|`connectionStrings`|Élément ASP.NET. Pour plus d’informations, consultez [connectionStrings, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178347) dans MSDN Library.|  
|`system.web`|Élément ASP.NET. Pour plus d’informations, consultez [system.web, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178348) dans MSDN Library.|  
|`startup`|Élément .NET Framework. Pour plus d’informations, consultez l' [ \<startup> élément](https://go.microsoft.com/fwlink/?LinkId=178349) dans MSDN Library.|  
|`runtime`|Élément .NET Framework. Pour plus d’informations, consultez l' [ \<runtime> élément](https://go.microsoft.com/fwlink/?LinkId=178350) dans MSDN Library.|  
|`system.codedom`|Élément .NET Framework. Pour plus d’informations, consultez l' [ \<system.codedom> élément](https://go.microsoft.com/fwlink/?LinkId=178351) dans MSDN Library.|  
|`system.web.extensions`|Élément ASP.NET. Pour plus d’informations, consultez [system.web.extensions, élément (Schéma des paramètres ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178352) dans MSDN Library.|  
|`system.webServer`|Groupe de sections qui contient des éléments IIS. Pour plus d’informations, consultez [system.webServer, groupe de sections \[Schéma des paramètres IIS 7\]](https://go.microsoft.com/fwlink/?LinkId=178353) dans MSDN Library.|  
|`system.serviceModel`|Élément WCF. Pour plus d’informations, consultez [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) dans MSDN Library.|  
|`system.diagnostics`|Élément .NET Framework. Pour plus d’informations, consultez l' [ \<system.diagnostics> élément](https://go.microsoft.com/fwlink/?LinkId=178355) dans MSDN Library.|  
|`appSettings`|Élément ASP.NET. Pour plus d’informations, consultez [appSettings, élément (Schéma des paramètres généraux)](https://go.microsoft.com/fwlink/?LinkId=178356) dans MSDN Library.|  
  
## <a name="masterdataservices-element"></a>Élément masterDataServices  
 L' **\<masterDataServices>** élément est un élément personnalisé qui permet de connecter un [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] service Web à une [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Éléments et attributs  
  
|Élément|Description|  
|----------|-----------------|  
|`instance`|Élément enfant. Contient des attributs qui spécifient les informations concernant le service Web et la chaîne de connexion à la base de données.|  
|`virtualPath`|Attribut. Spécifie le chemin d'accès virtuel de l'application Web et du service Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Cela correspond à l' `path` attribut de l' **\<application>** élément sous l' **\<site>** élément dans le fichier de ApplicationHost.config IIS.|  
|`siteName`|Attribut. Spécifie le nom du site qui héberge l'application Web et le service Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Cela correspond à l' `name` attribut de l' **\<site>** élément sous **\<sites>** dans le fichier de ApplicationHost.config IIS.|  
|`connectionName`|Attribut. Spécifie le nom de la connexion à utiliser. Cela correspond à l' `name` attribut de l' **\<add>** élément sous l' **\<connectionStrings>** élément dans Web.config.|  
|`serviceName`|Attribut. Spécifie le nom du service Web. Cela correspond à l' `name` attribut de l' **\<service>** élément sous l' **\<services>** élément dans Web.config.|  
  
### <a name="example"></a>Exemple  
 L'exemple suivant présente un service nommé MDS1 sur le site Contoso et le chemin d'accès /MDS, utilisant une chaîne de connexion spécifiée par MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
