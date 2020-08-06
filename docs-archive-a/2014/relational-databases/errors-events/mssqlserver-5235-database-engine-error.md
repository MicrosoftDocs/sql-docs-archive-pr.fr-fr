---
title: MSSQLSERVER_5235 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5235 (Database Engine error)
ms.assetid: 1aa7e6a5-7ccb-43c8-a1fd-d50e92e0a798
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 42c807944d7506a6a118de97ccd8c2c488942c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707592"
---
# <a name="mssqlserver_5235"></a>MSSQLSERVER_5235
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|5235|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_ERRORLOG_SUMMARY_PREMATURE_TERMINATION|  
|Texte du message|[EMERGENCY] DBCC DBCC_COMMAND_DETAILS exécuté par USER_NAME s'est terminé anormalement à cause de l'état d'erreur ERROR_STATE. Temps écoulé : HOURS heures MINUTES minutes SECONDS secondes.|  
  
## <a name="explanation"></a>Explication  
 Il s'agit du message de synthèse que DBCC inscrit dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsqu'un arrêt inattendu se produit au cours de l'exécution de la commande. L'état d'erreur signalé dans le message définit le type d'arrêt inattendu.  
  
 Le tableau ci-dessous liste et définit les états d'erreur.  
  
|État d'erreur|Définition|  
|-----------------|----------------|  
|État 0|L'instruction a pris fin en raison d'une altération des métadonnées qui s'est avérée fatale. Ce message sera accompagné d’une ou de plusieurs instances de l’erreur 8930.|  
|État 1|L'instruction a pris fin en raison d'un échec de contrôle interne. Ce message sera accompagné d'une ou plusieurs instances de l'erreur 8967.|  
|État 2|Les contrôles de table système basiques effectués par les principales tables système du moteur de stockage ont échoué. Ce message sera accompagné d’une ou de plusieurs instances des erreurs [7984](mssqlserver-7984-database-engine-error.md), 7985, [7986](mssqlserver-7986-database-engine-error.md), [7987](mssqlserver-7987-database-engine-error.md) ou [7988](mssqlserver-7988-database-engine-error.md).|  
|État 3|La réparation en mode urgence DBCC a échoué parce que la base de données n'a pas pu être démarrée après la reconstruction du journal des transactions. Ce message sera accompagné de l'erreur 7909.|  
|État 4|Un échec d'assertion ou une violation d'accès se sont produits au cours de l'exécution de la commande.|  
|État 5|Une panne inconnue s'est produite et a arrêté la commande DBCC de manière inattendue.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Le tableau ci-dessous décrit les actions que l'utilisateur doit effectuer pour l'état d'erreur spécifié.  
  
|État d'erreur|Action requise|  
|-----------------|-----------------|  
|État 0|Procédez à une restauration à partir d'une sauvegarde.|  
|État 1|Contactez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service clientèle et le Support technique.|  
|État 2|Procédez à une restauration à partir d'une sauvegarde.|  
|État 3|Procédez à une restauration à partir d'une sauvegarde.|  
|État 4|Contactez le Service clientèle et le Support technique.|  
|État 5|Réexécutez la commande. Si le problème persiste, contactez le Service clientèle et le Support technique.|  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)  
  
  
