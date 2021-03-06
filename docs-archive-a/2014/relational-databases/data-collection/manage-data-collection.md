---
title: Gérer la collecte de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a7d88923bc41939541bedeed2d40908e454e9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603554"
---
# <a name="manage-data-collection"></a>Gérer la collecte de données
  Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou des [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures stockées et des fonctions pour gérer différents aspects de la collecte de données, tels que l’activation ou la désactivation de la collecte de données, la modification de la configuration d’un jeu d’éléments de collecte ou l’affichage des données dans l’entrepôt de données de gestion.  
  
## <a name="manage-data-collection-by-using-sql-server-management-studio"></a>Gérer la collecte de données à l'aide de SQL Server Management Studio  
 Vous pouvez effectuer les tâches suivantes liées au collecteur de données en utilisant l'Explorateur d'objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] :  
  
-   [Configurer l’entrepôt de données de gestion &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [Configurer les propriétés d'un collecteur de données](configure-properties-of-a-data-collector.md)  
  
-   [Activer ou désactiver la collecte de données](data-collection.md)  
  
-   [Démarrer ou arrêter un jeu d’éléments de collecte](start-or-stop-a-collection-set.md)  
  
-   [Utiliser SQL Server Profiler pour créer un jeu d’éléments de collecte Trace SQL &#40;SQL Server Management Studio&#41;](use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [Afficher les journaux de jeu d’éléments de collecte &#40;SQL Server Management Studio&#41;](view-collection-set-logs-sql-server-management-studio.md)  
  
-   [Afficher ou modifier des planifications de jeu d’éléments de collecte &#40;SQL Server Management Studio&#41;](view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [Afficher un rapport de jeu d’éléments de collecte &#40;SQL Server Management Studio&#41;](view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-by-using-transact-sql"></a>Gérer la collecte de données à l'aide de Transact-SQL  
 Le collecteur de données fournit une collection complète de procédures stockées qui vous permettent d'effectuer n'importe quelle tâche du collecteur de données. Par exemple, vous pouvez effectuer les tâches suivantes à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
-   [Configurer des paramètres de collecte de données &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md)  
  
-   [Activer ou désactiver la collecte de données](data-collection.md)  
  
-   [Démarrer ou arrêter un jeu d’éléments de collecte](start-or-stop-a-collection-set.md)  
  
-   [Créer un jeu d’éléments de collecte personnalisé qui utilise le type de collecteur Requête T-SQL générique &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [Ajouter un élément de collecte à un jeu d’éléments de collecte &#40;Transact-SQL&#41;](add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 De plus, vous disposez de fonctions et de vues qui vous permettent d'obtenir des données de configuration pour les bases de données msdb et l'entrepôt de données de gestion, des données du journal des exécutions et des données stockées dans l'entrepôt de données de gestion.  
  
 Vous pouvez utiliser les procédures stockées, les fonctions et les vues fournies pour créer vos propres scénarios de collecte de données de bout en bout.  
  
> [!IMPORTANT]  
>  Contrairement aux procédures stockées standard, les procédures stockées du collecteur de données utilisent des paramètres de type strict et elles ne prennent pas en charge la conversion automatique de type de données. Si ces paramètres ne sont pas appelés à l'aide des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée retourne une erreur.  
  
 Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer et exécuter les exemples de code qui sont fournis. Pour plus d’informations, consultez [Explorateur d’objets](../../ssms/object/object-explorer.md). Vous pouvez également créer la requête dans n'importe quel éditeur et l'enregistrer dans un fichier texte avec une extension de nom de fichier .sql. Vous pouvez exécuter la requête à partir de l'invite de commandes Windows, à l'aide de l'utilitaire `sqlcmd`. Pour plus d’informations, consultez [Utiliser l’utilitaire sqlcmd](../scripting/sqlcmd-use-the-utility.md).  
  
### <a name="stored-procedures-and-views"></a>Procédures stockées et vues  
 **Utilisation du collecteur de données**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec le collecteur de données.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)|Active le collecteur de données.|  
|[sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)|Désactive le collecteur de données.|  
  
 **Utilisation de jeux d'éléments de collecte**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec les jeux d'éléments de collecte.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_run_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql)|Exécute un jeu d'éléments de collecte à la demande.|  
|[sp_syscollector_start_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql)|Démarrer un jeu d'éléments de collecte.|  
|[sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql)|Arrêter un jeu d'éléments de collecte.|  
|[sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql)|Créer un jeu d'éléments de collecte.|  
|[sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql)|Supprimer un jeu de collections.|  
|[sp_syscollector_update_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql)|Modifie la configuration d'un jeu de collections.|  
|[sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql)|Télécharger les données d'un jeu d'éléments de collecte dans l'entrepôt de données de gestion. Il s'agit effectivement d'un téléchargement à la demande.|  
  
 **Utilisation d'éléments de collecte**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec les éléments de collecte.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql)|Créer un élément de collecte.|  
|[sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql)|Supprimer un élément de collecte.|  
|[sp_syscollector_update_collection_item &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql)|Mettre à jour un élément de collecte.|  
  
 **Utilisation de types de collecteurs**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec les types de collecteurs.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql)|Créer un type de collecteur.|  
|[sp_syscollector_update_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql)|Mettre à jour un type de collecteur.|  
|[sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql)|Supprimer un type de collecteur.|  
  
 **Obtention d'informations de configuration**  
  
 Le tableau suivant décrit les vues que vous pouvez utiliser pour obtenir des informations de configuration et des données du journal des exécutions.  
  
|Nom de l’affichage|Description|  
|---------------|-----------------|  
|[syscollector_config_store &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-config-store-transact-sql)|Obtenir la configuration du collecteur de données.|  
|[syscollector_collection_items &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-items-transact-sql)|Obtenir des informations sur des éléments de collecte.|  
|[syscollector_collection_sets &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql)|Obtenir des informations sur des jeux d'éléments de collecte.|  
|[syscollector_collector_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-collector-types-transact-sql)|Obtenir des informations sur des types de collecteurs.|  
|[syscollector_execution_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-transact-sql)|Obtenir des informations sur l'exécution des jeux de collections et des packages.|  
|[syscollector_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql)|Obtenir des informations sur l'exécution des tâches.|  
|[syscollector_execution_log_full &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql)|Obtenir des informations lorsque le journal des exécutions est plein.|  
  
 **Configuration de l'accès à l'entrepôt de données de gestion**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser pour configurer l'accès à l'entrepôt de données de gestion.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql)|Spécifier le nom de base de données défini dans la chaîne de connexion pour l'entrepôt de données de gestion.|  
|[sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql)|Spécifier l'instance définie dans la chaîne de connexion pour l'entrepôt de données de gestion.|  
  
 **Configuration de l'entrepôt de données de gestion**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec la configuration de l'entrepôt de données de gestion.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[core.sp_create_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql)|Créer un instantané de collection dans l'entrepôt de données de gestion.|  
|[core.sp_update_data_source &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql)|Mettre à jour la source de données pour la collecte de données.|  
|[core.sp_add_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql)|Ajouter un type de collecteur à l'entrepôt de données de gestion.|  
|[core.sp_remove_collector_type &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql)|Supprimer un type de collecteur de l'entrepôt de données de gestion.|  
|[core.sp_purge_data &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql)|Supprimer des données de l'entrepôt de données de gestion.|  
  
 **Utilisation de packages de téléchargement**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec les packages de téléchargement.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql)|Configurer le nombre de tentatives de téléchargement de données.|  
|[sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql)|Spécifier le stockage temporaire des données entre les tentatives de téléchargement.|  
  
 **Utilisation du journal des exécutions de la collecte de données**  
  
 Le tableau suivant décrit les procédures stockées que vous pouvez utiliser avec le journal des exécutions de la collecte de données.  
  
|Nom de la procédure|Description|  
|--------------------|-----------------|  
|[sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql)|Supprimer des entrées de jeu de collections du journal des exécutions.|  
  
### <a name="functions"></a>Fonctions  
 Le tableau suivant décrit les fonctions que vous pouvez utiliser pour obtenir des informations d'exécution et de trace.  
  
|Nom de la fonction|Description|  
|-------------------|-----------------|  
|[fn_syscollector_get_execution_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql)|Obtenir les données du journal des exécutions [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour un package spécifique.|  
|[fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql)|Obtenir les statistiques d'exécution d'un jeu d'éléments de collecte ou d'un package. Ces informations incluent les erreurs enregistrées.|  
|[snapshots.fn_trace_getdata &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql)|Obtenir les événements enregistrés lorsque le type de collecteur Trace SQL générique est utilisé pour collecter des données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter une procédure stockée](../stored-procedures/execute-a-stored-procedure.md)   
 [Utiliser SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)   
 [Collecte de données](data-collection.md)  
  
  
