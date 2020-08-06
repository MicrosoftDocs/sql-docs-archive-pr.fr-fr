---
title: Database Mirroring State Change, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- database mirroring [SQL Server], event notifications
- Database Mirroring State Change event class
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
author: stevestein
ms.author: sstein
ms.openlocfilehash: 79669c847a1606ef1e7dcbd2f5e2150d203b8154
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611790"
---
# <a name="database-mirroring-state-change-event-class"></a>Database Mirroring State Change (classe d'événements)
  La classe d’événements **Database Mirroring State Change** indique que l’état d’une base de données mise en miroir change. Incluez cette classe d'événements au sein des traces qui surveillent les conditions d'exécution des bases de données mises en miroir.  
  
 Lorsque la classe d’événements **Database Mirroring State Change** est incluse au sein d’une trace, la surcharge relative est peu élevée. La surcharge peut être plus importante si l'état des bases de données mises en miroir augmente.  
  
## <a name="data-database-mirroring-state-change-event-class-data-columns"></a>Colonnes de données de la classe d'événements Data Database Mirroring State Change  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données mise en miroir.|35|Oui|  
|**EventClass**|**int**|Type d’événement = 167|27|Non|  
|**EventSequence**|**int**|Séquence de la classe d'événements dans le lot.|51|Non|  
|**IntegerData**|**int**|ID de l'état antérieur.|25|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l’affichage catalogue **sys.server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**RequestID**|**int**|ID de la demande contenant l'instruction.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**State**|**int**|ID du nouvel état de la mise en miroir :<br /><br /> 0 = Notification Null<br /><br /> 1 = Principal synchronisé avec témoin<br /><br /> 2 = Principal synchronisé sans témoin<br /><br /> 3 = Miroir synchronisé avec témoin<br /><br /> 4 = Miroir synchronisé sans témoin<br /><br /> 5 = Connexion avec principal perdue<br /><br /> 6 = Connexion avec miroir perdue<br /><br /> 7 =Basculement manuel<br /><br /> 8 = Basculement automatique<br /><br /> 9 = Mise en miroir suspendue<br /><br /> 10 = Pas de quorum<br /><br /> 11 = Synchronisation miroir<br /><br /> 12 = Principal en cours d'exécution exposé|30|Oui|  
|**TextData**|**ntext**|Description du changement d'état.|1|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
