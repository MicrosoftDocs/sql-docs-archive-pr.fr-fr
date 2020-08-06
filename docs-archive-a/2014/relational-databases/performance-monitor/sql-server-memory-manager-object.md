---
title: SQL Server, objet Buffer Manager | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06b58b9b6bb8a5c13e0b220ba9eeea5818682abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602075"
---
# <a name="sql-server-memory-manager-object"></a>Objet SQLServer:Memory Manager
  L'objet **Gestionnaire de mémoire** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'utilisation globale de la mémoire du serveur. La surveillance globale de l'utilisation de la mémoire du serveur afin de mesurer l'activité de l'utilisateur et son exploitation des ressources peut être utile pour détecter les goulots d'étranglement des performances. La surveillance de la mémoire utilisée par une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous aide à déterminer :  
  
-   si des goulots d'étranglement existent en raison d'une quantité de mémoire physique disponible inadéquate pour le stockage de données fréquemment accédées dans le cache ; Si tel est le cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit extraire les données du disque.  
  
-   si les performances des requêtes peuvent être améliorées en ajoutant de la mémoire ou en mettant plus de mémoire à la disposition du cache des données ou des structures internes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="memory-manager-counters"></a>Compteurs du Gestionnaire de mémoire  
 Ce tableau décrit les compteurs **Gestionnaire de mémoire** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs du Gestionnaire de mémoire de SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Mémoire de connexion (Ko)**|Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour maintenir les connexions.|  
|**Mémoire du cache de base de données (Ko)**|Spécifie la quantité de mémoire actuellement utilisée par le serveur pour le cache de la base de données.|  
|**Mémoire disponible (Ko)**|Spécifie la quantité de mémoire allouée actuellement non utilisée par le serveur.|  
|**Mémoire réservée de l'espace de travail (Ko)**|Spécifie la quantité totale de mémoire actuellement réservée à l'exécution de processus tels que les opérations de hachage, de tri, de copie en bloc et de créations d'index.|  
|**Blocs de verrous**|Spécifie le nombre actuel de blocs de verrous utilisés sur le serveur (mis à jour régulièrement). Un bloc de verrous représente une ressource individuelle verrouillée, comme une table, une page ou une ligne.|  
|**Blocs de verrous alloués**|Spécifie le nombre actuel de blocs de verrous alloués. Au démarrage du serveur, le nombre de blocs de verrous alloués plus le nombre de blocs propriétaires de verrous alloués dépendent de l’option de configuration **Verrous** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si un plus grand nombre de blocs de verrous est nécessaire, cette valeur augmente.|  
|**Mémoire des verrous (Ko)**|Spécifie la quantité totale de mémoire dynamique qu'utilise le serveur pour les verrous.|  
|**Blocs propriétaires de verrous**|Spécifie le nombre actuel de blocs propriétaires de verrous utilisés sur le serveur (mis à jour régulièrement). Un bloc propriétaire de verrous représente l'appropriation d'un objet par un verrou via un thread individuel. Par conséquent, si trois threads disposent chacun d'un verrou partagé sur une page, il y aura trois blocs propriétaires de verrous.|  
|**Blocs propriétaires de verrous alloués**|Spécifie le nombre actuel de blocs propriétaires de verrous alloués. Au démarrage du serveur, le nombre de blocs propriétaires de verrous alloués et le nombre de blocs de verrous alloués dépendent de l’option de configuration **Verrous** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si un plus grand nombre de blocs propriétaires de verrous est nécessaire, cette valeur augmente dynamiquement.|  
|**Mémoire maximale de l'espace de travail (Ko)**|Indique la quantité maximale de mémoire disponible pour exécuter des processus, tels que les opérations de hachage, de tri, de copie en bloc et de création d'index.|  
|**Demandes de mémoire satisfaites**|Spécifie le nombre total de processus qui ont acquis avec succès une allocation de mémoire de l'espace de travail.|  
|**Demandes de mémoire en attente**|Spécifie le nombre total de processus en attente d'une allocation de mémoire de l'espace de travail.|  
|**Mémoire de l'optimiseur (Ko)**|Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour l'optimisation des requêtes.|  
|**Mémoire réservée du serveur (Ko)**|Indique la quantité de mémoire réservée par le serveur pour un usage futur. Ce compteur affiche la quantité actuellement inutilisée de **Mémoire réservée de l’espace de travail (Ko)** octroyée initialement.|  
|**Mémoire du cache SQL (Ko)**|Spécifie la quantité totale de mémoire dynamique utilisée par le serveur pour le cache SQL dynamique.|  
|**Mémoire détournée du serveur (Ko)**|Spécifie la quantité de mémoire utilisée par le serveur à d'autres fins que les pages de bases de données.|  
|**Mémoire du serveur cible (Ko)**|Indique la quantité idéale de mémoire que le serveur peut consommer.|  
|**Mémoire totale du serveur (Ko)**|Spécifie la quantité de mémoire allouée par le serveur à l'aide du Gestionnaire de mémoire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet Gestionnaire de tampons](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
