---
title: Propriétés des fonctionnalités | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 08001a172c1b39fb912ef042ed85effd4f8ededa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710864"
---
# <a name="feature-properties"></a>Propriétés de fonctionnalité
  Les propriétés de fonctionnalité se rapportent à des fonctionnalités de produit, le plus souvent de caractère avancé. Il s'agit notamment de propriétés qui contrôlent les liaisons entre les instances de serveur.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur répertoriées dans le tableau suivant. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S’applique à :** Mode serveur multidimensionnel uniquement  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Default|Description|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|1|Propriété booléenne qui indique si les procédures de stockage du Common Language Runtime sont activées.|  
|`LinkInsideInstanceEnabled`|1|Propriété booléenne qui indique si un objet lié peut être créé dans la même instance du serveur.|  
|`LinkToOtherInstanceEnabled`|0|Propriété booléenne qui indique s'il est possible d'établir des liens à des objets résidant sur des serveurs distants.|  
|`LinkFromOtherInstanceEnabled`|0|Propriété booléenne qui indique s'il est possible d'établir des liens à des objets à partir d'autres instances du serveur.|  
|`ConnStringEncryptionEnabled`|1|Propriété booléenne qui indique si la chaîne de connexion est chiffrée dans le fichier de configuration du serveur.|  
|`UseCachedPageAllocators`|0|Propriété booléenne qui indique si les allocateurs de pages en cache sont activés.|  
|`ComUdfEnabled`|0|Propriété booléenne qui indique si les fonctions définies comme objets COM par l'utilisateur sont activées.|  
|`SQMSupportEnabled`|1|Propriété booléenne qui indique si des rapports d'erreurs et d'utilisation de fonctionnalités sont envoyés automatiquement à [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|  
|`ResourceMonitoringEnabled`|1|Propriété booléenne qui indique si des compteurs d'analyse des ressources internes sont activés. Cette propriété est activée par défaut. Lorsqu'elle est activée, cette propriété permet aux compteurs de recueillir des données d'utilisation relatives au processeur, à la mémoire et aux activités d'E/S.<br /><br /> Des compteurs d'analyse des ressources internes sont utilisés par les vues de gestion dynamique (DMV) qui s'intéressent à l'utilisation des ressources. Si vous désactivez cette propriété, les requêtes DMV continuent à s'exécuter, mais le jeu de résultats ne sera pas valide. Les vues DMV qui dépendent de cette propriété sont notamment :<br />**DISCOVER_OBJECT_ACTIVITY**<br />**DISCOVER_COMMAND_OBJECTS**<br />**DISCOVER_SESSIONS** (pour SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Sur un système multicœur qui présente une architecture NUMA, la désactivation de cette propriété peut améliorer les performances de requête, notamment pour les charges de travail multi-utilisateur élevées. Vous devrez effectuer des tests de comparaison afin de déterminer si les performances de requête sont améliorées lorsque vous modifiez cette propriété. Pour connaître les meilleures pratiques concernant l'exécution de tests de comparaison, y compris l'effacement du cache et les erreurs courantes à éviter, consultez le document [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d’une instance de Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Utiliser des vues de gestion dynamique &#40;DMV&#41; pour surveiller Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
