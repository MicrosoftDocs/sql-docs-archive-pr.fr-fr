---
title: Configurer des instances du moteur de base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614849"
---
# <a name="configure-database-engine-instances-sql-server"></a>Configurer des instances du moteur de base de données (SQL Server)
  Chaque instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être configurée pour répondre aux exigences en matière de performances et de disponibilité définies pour les bases de données hébergées par l'instance. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] comprend des options de configuration qui contrôlent des comportements (tels que l'utilisation des ressources) et la disponibilité de fonctionnalités (telles que l'audit ou la récursivité des déclencheurs).  
  
## <a name="instance-configuration"></a>Configuration de l'instance  
 Lorsqu'une base de données est déployée dans l'environnement de production, il existe souvent un contrat de niveau de service (SLA) qui définit des zones telles que les niveaux de performances requis de la base de données et le niveau de disponibilité requis de la base de données. Les termes du contrat de niveau de service définissent généralement les exigences de configuration pour l'instance.  
  
 Une instance est généralement configurée dès son installation terminée. La configuration initiale est généralement déterminée par les exigences du contrat de niveau de service concernant les types de bases de données dont le déploiement sur l'instance est planifié. Une fois les bases de données déployées, les administrateurs de base de données surveillent les performances de l'instance et règlent les paramètres de configuration en conséquence si les métriques de performances indiquent que l'instance ne répond pas aux spécifications du contrat de niveau de service.  
  
## <a name="configuration-tasks"></a>Tâches de configuration  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit les différentes options de configuration de l'instance et explique comment afficher ou modifier ces options.|[Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)|  
|Explique comment afficher et configurer les emplacements par défaut des nouveaux fichiers de données et fichiers journaux de l'instance.|[Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux &#40;SQL Server Management Studio&#41;](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|Explique comment configurer SQL Server pour utiliser soft-NUMA.|[Configurez SQL Server pour utiliser le &#40;soft-NUMA SQL Server&#41;](soft-numa-sql-server.md)|  
|Explique comment mapper un port TCP/IP à une affinité de nœud NUMA.|[Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|Explique comment activer la stratégie Verrouiller les pages en mémoire de Windows. Cette stratégie détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque.|[Activer l’option Lock Pages in Memory &#40;Windows&#41;](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Instances du moteur de base de données &#40;SQL Server&#41;](database-engine-instances-sql-server.md)  
  
  
