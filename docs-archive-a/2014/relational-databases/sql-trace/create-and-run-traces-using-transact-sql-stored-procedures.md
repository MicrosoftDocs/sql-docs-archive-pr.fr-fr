---
title: Créer et exécuter des traces à l’aide de procédures stockées Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2905ce2822598502ef6337d1a083fb6fde001c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611005"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a>Créer et exécuter des traces à l'aide de procédures stockées Transact-SQL.
  Le processus de trace à l'aide de la trace SQL varie en fonction de la façon dont vous avez créé et exécuté votre trace, à savoir au moyen du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] de Microsoft ou via les procédures stockées système.  
  
 Une alternative au [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]est représentée par les procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] qui permettent de créer et d'exécuter des traces. La procédure de trace à l'aide des procédures stockées système est la suivante :  
  
1.  Créez une trace en exécutant **sp_trace_create**.  
  
2.  Ajoutez des événements à l’aide de **sp_trace_setevent**.  
  
3.  (Facultatif) Définissez un filtre avec **sp_trace_setfilter**.  
  
4.  Démarrez la trace avec **sp_trace_setstatus**.  
  
5.  Arrêtez la trace avec **sp_trace_setstatus**.  
  
6.  Fermez la trace avec **sp_trace_setstatus**.  
  
    > [!NOTE]  
    >  L'utilisation des procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] crée une trace serveur qui garantit qu'aucun événement ne sera perdu aussi longtemps qu'il restera de la place sur le disque et qu'aucune erreur d'écriture ne se produira. Si le disque est plein ou s'il présente une défaillance, l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] continuera à s'exécuter, mais la trace s'arrêtera. Si l'option **c2 audit mode** est définie et qu'il se produit une erreur d'écriture, la trace cesse et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête. Pour plus d’informations sur le paramètre **Mode d’audit c2** , consultez [Mode d’audit C2 (option de configuration de serveur)](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Optimiser Trace SQL](sql-trace.md)|Contient des informations sur les manières de réduire les effets de la trace sur les performances du système.|  
|[Filtrer une trace](filter-a-trace.md)|Contient des informations sur l'utilisation de filtres pour la trace.|  
|[Limiter les tailles de fichier et de table de trace](limit-trace-file-and-table-sizes.md)|Contient des informations sur la façon de limiter la taille des fichiers et des tables où les données de trace sont écrites. Notez que seul le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] peut écrire les données de trace dans des tables.|  
|[Planifier les traces](schedule-traces.md)|Contient des informations sur la façon de définir l'heure de démarrage et l'heure de fin de la trace.|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
  
