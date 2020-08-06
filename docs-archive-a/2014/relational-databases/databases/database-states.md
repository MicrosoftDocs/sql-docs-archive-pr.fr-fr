---
title: États d’une base de données | Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASESTATES.F1
helpviewer_keywords:
- emergency database state [SQL Server]
- verifying database states
- viewing database states
- displaying database states
- database states [SQL Server]
- current database state
- offline database state [SQL Server]
- suspect database state
- recovery pending database state [SQL Server]
- states [SQL Server], databases
- online database state
- states [SQL Server]
- restoring database state [SQL Server]
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0aec4e5fb367f5fe9bf8fca5ed056269930cf2db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709567"
---
# <a name="database-states"></a>États d'une base de données
  Une base de données est toujours dans un état spécifique. Par exemple, elle peut être dans l'état ONLINE, OFFLINE ou SUSPECT. Pour vérifier l’état actuel d’une base de données, sélectionnez la colonne **state_desc** de la vue du catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) ou la propriété **Status** de la fonction [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) .  
  
## <a name="database-state-definitions"></a>Définition des états d'une base de données  
 Le tableau ci-dessous définit les états de la base de données.  
  
|State|Définition|  
|-----------|----------------|  
|ONLINE|La base de données est accessible. Le groupe de fichiers primaire est en ligne, mais il est possible que la phase de restauration de la récupération n'ait pas été réalisée.|  
|OFFLINE|La base de données n'est pas disponible. Une base de données est mise hors connexion par une action explicite de l'utilisateur et reste dans cet état jusqu'à une nouvelle action de l'utilisateur. Par exemple, la base de données peut être mise hors connexion pour déplacer un fichier sur un nouveau disque. La base de données est ensuite ramenée en ligne une fois que le déplacement a eu lieu.|  
|RESTORING|Un ou plusieurs fichiers du groupe de fichiers primaire sont en cours de restauration ou un ou plusieurs fichiers secondaires sont en cours de restauration hors connexion. La base de données n'est pas disponible.|  
|RECOVERING|La base de données est en cours de récupération. Le processus de restauration est un état transitoire ; elle sera mise automatiquement en ligne si la récupération réussit. Si la récupération échoue, la base de données devient suspecte. La base de données n'est pas disponible.|  
|RECOVERY PENDING|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a rencontré une erreur liée aux ressources pendant la récupération. La base de données n'est pas endommagée, mais des fichiers peuvent être absents ou des restrictions de ressources système peuvent l'empêcher de démarrer. La base de données n'est pas disponible. Une action de l'utilisateur est nécessaire pour résoudre l'erreur et permettre la poursuite du processus de récupération.|  
|SUSPECT|Le groupe de fichiers primaire au moins est suspect et peut être endommagé. La base de données ne peut pas être récupérée au démarrage de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La base de données n'est pas disponible. Une action de l'utilisateur est nécessaire pour résoudre le problème.|  
|EMERGENCY|L'utilisateur a modifié la base de données et défini son état sur EMERGENCY. La base de données est en mode mono-utilisateur et peut être réparée ou restaurée. La base de données est marquée READ_ONLY, la journalisation est désactivée et l’accès est restreint aux membres du rôle serveur fixe **sysadmin** . EMERGENCY est principalement utilisé à des fins de dépannage. Par exemple, une base de données marquée SUSPECT peut être définie sur l'état EMERGENCY. Ceci peut permettre à l'administrateur système d'accéder en lecture seule à la base de données. Seuls les membres du rôle serveur fixe **sysadmin** peuvent définir l’état EMERGENCY pour une base de données.|  
  
## <a name="related-content"></a>Contenu associé  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [États de la mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [États des fichiers](file-states.md)  
  
  
