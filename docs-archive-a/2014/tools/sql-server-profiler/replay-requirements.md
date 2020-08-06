---
title: Conditions requises pour la relecture | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65546f6820765286b558d2043e0155a79a07eb58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705735"
---
# <a name="replay-requirements"></a>Conditions préalables à la relecture
  Pour relire les données de trace avec [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ou Distributed Replay Utility, un jeu spécifique de classes et de colonnes d'événements doit être capturé dans la trace. Ces paramètres sont activés par défaut si le modèle de trace **TSQL_Replay** est utilisé pour configurer une trace utilisée ultérieurement pour la relecture. Cette rubrique décrit ces paramètres et d’autres configurations préalables à la relecture.  
  
> [!NOTE]  
>  Nous recommandons d'utiliser Distributed Replay Utility pour relire des applications OLTP exigeantes (avec de nombreuses connexions simultanées actives ou un débit élevé). Distributed Replay Utility peut relire les données de trace de plusieurs ordinateurs, en simulant mieux les charges de travail sensibles. Pour plus d'informations, consultez [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).  
  
## <a name="event-classes-required-for-replay"></a>Classes d'événements nécessaires à la relecture  
 Pour être relus par [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], les jeux de classes d'événements suivants doivent être capturés dans la trace, en plus de toutes les autres classes d'événements que vous souhaitez surveiller :  
  
-   **CursorClose (** nécessaire uniquement pour la relecture de curseurs côté serveur)  
  
-   **CursorExecute** (nécessaire uniquement pour la relecture de curseurs côté serveur)  
  
-   **CursorOpen** (nécessaire uniquement pour la relecture de curseurs côté serveur)  
  
-   **CursorPrepare** (nécessaire uniquement pour la relecture de curseurs côté serveur)  
  
-   **CursorUnprepare** (nécessaire uniquement pour la relecture de curseurs côté serveur)  
  
-   **Audit Login**  
  
-   **Audit Logout**  
  
-   **ExistingConnection**  
  
-   **RPC Output Parameter**  
  
-   **RPC:Completed**  
  
-   **RPC:Starting**  
  
-   **Exec Prepared SQL** (nécessaire uniquement pour la relecture d’instructions SQL préparées côté serveur)  
  
-   **Prepare SQL** (nécessaire uniquement pour la relecture d’instructions SQL préparées côté serveur)  
  
-   **SQL:BatchCompleted**  
  
-   **SQL:BatchStarting**  
  
## <a name="data-columns-required-for-replay"></a>Colonnes de données nécessaires à la relecture  
 En plus des autres colonnes de données que vous voudrez peut-être capturer, les colonnes de données suivantes doivent être capturées dans une trace pour permettre la relecture de la trace en question :  
  
-   **Classe d'événements**  
  
-   **EventSequence**  
  
-   **TextData**  
  
-   **Nom d’application**  
  
-   **LoginName**  
  
-   **DatabaseName**  
  
-   **ID de base de données**  
  
-   **ClientProcessID**  
  
-   **HostName**  
  
-   **ServerName**  
  
-   **Binary Data**  
  
-   **SPID**  
  
-   **Start Time**  
  
-   **EndTime**  
  
-   **IsSystem**  
  
-   **NTDomainName**  
  
-   **NTUserName**  
  
-   **Error**  
  
> [!NOTE]  
>  Utilisez le modèle de trace **TSQL_Replay** pour les traces qui capturent des données à des fins de relecture.  
  
## <a name="other-replay-requirements"></a>Autres conditions préalables à la relecture  
 Dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la relecture vérifie la présence des événements et des colonnes nécessaires. Cette nouveauté permet d'améliorer la précision de la relecture en supprimant tout travail de devinette dans la réparation des relectures qui échouent en raison de données manquantes. La relecture renvoie une erreur et s'arrête lorsque des données nécessaires sont manquantes dans une trace.  
  
 Pour relire une trace portant sur un serveur (cible) qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et qui n'est pas le serveur tracé au départ (source), vérifiez que les conditions suivantes sont réunies :  
  
-   Tous les utilisateurs et connexions contenus dans la trace doivent déjà être créés sur la cible et dans la même base de données que la source.  
  
-   Toutes les connexions d'accès et tous les utilisateurs contenus dans la cible doivent avoir les mêmes autorisations que dans la source.  
  
-   Tous les mots de passe de connexion doivent être identiques à ceux de l'utilisateur qui exécute la relecture.  
  
-   Les ID de base de données sur la cible doivent idéalement être identiques à ceux qui sont sur la source. Si ce n’est pas le cas, la mise en correspondance peut être effectuée sur la base du **DatabaseName** s’il est présent dans la trace.  
  
-   La base de données par défaut de chaque connexion d'accès contenue dans la trace doit être définie (sur la cible) en tant que base de données cible relative à la connexion. Par exemple, la trace à relire contient les activités de la connexion **Fred**dans la base de données **Fred_Db** située sur la source. Ainsi, sur la cible, la base de données par défaut de la connexion **Fred**doit être la base de données correspondant à **Fred_Db** (même si le nom de la base de données est différent). Pour définir la base de données par défaut de la connexion, utilisez la procédure stockée **sp_defaultdb** .  
  
 La relecture d'événements associés à des connexions manquantes ou incorrectes va entraîner des erreurs de relecture, mais l'opération de relecture va se poursuivre.  
  
 Pour savoir quelles autorisations sont nécessaires pour relire une trace, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](sql-server-profiler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Relire une table de trace &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)   
 [Relire un fichier de trace &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)   
 [Informations de référence sur la classe d’événements SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql)   
 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)  
  
  
