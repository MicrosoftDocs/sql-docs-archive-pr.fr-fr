---
title: Connexion de diagnostic pour les administrateurs de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], connections
- administrator connections [SQL Server]
- ports [SQL Server], DAC
- DAC
- network connections [SQL Server], dedicated administrator
- diagnostic connections [SQL Server]
- connections [SQL Server], dedicated administrator
- ports [SQL Server]
- dedicated administrator connections [SQL Server]
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d452ca155a5187136c910e81e8bd073e34cad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610856"
---
# <a name="diagnostic-connection-for-database-administrators"></a>Connexion de diagnostic pour les administrateurs de base de données
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit aux administrateurs une connexion de diagnostic spéciale lorsque des connexions standard au serveur sont impossibles. Cette connexion de diagnostic permet aux administrateurs d'accéder à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter des requêtes de diagnostic et résoudre des problèmes, même lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne répond pas à des demandes de connexion standard.  
  
 Cette connexion administrateur dédiée (DAC) prend en charge le chiffrement et d'autres fonctions de sécurité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elle permet uniquement de changer de contexte utilisateur pour un autre administrateur.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue chaque tentative pour établir la connexion DAC, mais cela peut échouer dans des situations extrêmes.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] .|  
  
## <a name="connecting-with-dac"></a>Connexion avec DAC  
 Par défaut, la connexion est uniquement autorisée à partir d'un client s'exécutant sur le serveur. Les connexions réseau sont autorisées uniquement si elles sont configurées en utilisant la procédure stockée sp_configure avec [l’option remote admin connections](remote-admin-connections-server-configuration-option.md).  
  
 Seuls les membres du rôle administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent se connecter à l'aide de la connexion DAC.  
  
 La connexion DAC est disponible et prise en charge par le biais de l’utilitaire d’invite de commandes **sqlcmd** , au moyen d’un commutateur d’administrateur spécial (**-A**). Pour plus d’informations sur l’utilisation de **sqlcmd**, consultez [Utiliser sqlcmd avec des variables de script](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md). Vous pouvez également vous connecter en ajoutant le préfixe `admin:` au nom de l’instance au format **sqlcmd-Sadmin :** _<instance_name>._ Vous pouvez également initier une DAC à partir d’un [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] éditeur de requête en vous connectant à `admin:` \<*instance_name*> .  
  
## <a name="restrictions"></a>Restrictions  
 Comme la connexion DAC n'est prévue que pour diagnostiquer des problèmes de serveur dans de rares circonstances, certaines restrictions sont imposées sur la connexion :  
  
-   Pour garantir que des ressources sont disponibles pour la connexion, une seule connexion DAC est autorisée par instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si une connexion DAC est déjà active, toute nouvelle demande de connexion établie par son intermédiaire est refusée avec l'erreur 17810.  
  
-   Pour préserver les ressources, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] n'écoute pas le port DAC à moins qu'il soit démarré avec l'indicateur de trace 7806.  
  
-   Au départ, la connexion DAC tente une connexion à la base de données par défaut associée à la connexion. Une fois la connexion établie, vous pouvez vous connecter à la base de données master. Si la base de données par défaut est hors connexion ou non disponible pour une raison quelconque, la connexion retourne l'erreur 4060. Cependant, elle réussit si vous remplacez la base de données par défaut pour vous connecter à la base de données master au lieu d'utiliser la commande suivante :  
  
     **sqlcmd-A-d maître**  
  
     Nous vous conseillons de vous connecter à la base de données master avec la connexion DAC, car la disponibilité de la base de données master est garantie en cas de démarrage de l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interdit l'exécution de requêtes ou de commandes parallèles avec la connexion DAC. Par exemple, l'erreur 3637 est générée si vous exécutez l'une des instructions ci-dessous avec la connexion DAC :  
  
    -   RESTORE  
  
    -   BACKUP  
  
-   Seules des ressources limitées sont garanties disponibles avec la connexion DAC. N'utilisez pas la connexion DAC pour exécuter des requêtes à utilisation intensive des ressources (par exemple, une jointure complexe sur une grande table) ou des requêtes pouvant créer des blocages. Cela permet d'éviter que la connexion DAC n'amplifie d'éventuels problèmes de serveur existants. Pour éviter les scénarios de blocages potentiels, si vous devez exécuter des requêtes pouvant créer un blocage, exécutez la requête sous des niveaux d'isolement basés si possible sur un instantané ; sinon, réglez le niveau d'isolement des transactions à READ UNCOMMITTED et attribuez à LOCK_TIMEOUT une valeur faible, par exemple 2 000 millisecondes, ou les deux. Vous éviterez ainsi le blocage de la session DAC. Cependant, selon l'état de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la session DAC pourrait se bloquer sur un verrou. Vous pourriez être en mesure de terminer la session DAC en appuyant sur CTRL-C, mais ce n'est pas garanti. Dans ce cas, la seule option consiste à redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour garantir la connectivité et le dépannage avec la connexion DAC, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réserve des ressources limitées pour traiter les commandes exécutées sur la connexion DAC. Ces ressources ne permettent généralement que de simples fonctions de diagnostic et de dépannage, telles que celles répertoriées ci-dessous.  
  
 Même si vous pouvez théoriquement exécuter toute instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui ne doit pas nécessairement être exécutée en parallèle sur la connexion DAC, nous vous recommandons instamment de n'utiliser que les commandes de diagnostic et de dépannage suivantes :  
  
-   Interrogation de vues de gestion dynamique (DMV) pour des diagnostics de base tels que sys.dm_tran_locks pour l'état de verrouillage, sys.dm_os_memory_cache_counters pour vérifier l'état des mémoires caches, et sys.dm_exec_requests et sys.dm_exec_sessions pour des sessions et des demandes actives. Évitez les DMV à utilisation intensive des ressources (par exemple, sys.dm_tran_version_store analyse le magasin de versions complet et peut provoquer des E/S intensives et soutenues) ou qui utilisent des jointures complexes. Pour plus d'informations sur les implications sur les performances, consultez la documentation relative à la [vue de gestion dynamique](../../relational-databases/views/views.md)spécifique.  
  
-   Interrogation d'affichages catalogue.  
  
-   Les commandes DBCC de base telles que DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS`,` et DBCC SQLPERF. N’exécutez pas de commandes gourmandes en ressources telles que **DBCC** CHECKDB, DBCC DBREINDEX ou DBCC SHRINKDATABASE.  
  
-   Commande [!INCLUDE[tsql](../../includes/tsql-md.md)] KILL *\<spid>* . Selon l'état de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la commande KILL risque de ne pas toujours aboutir ; dans ce cas, la seule option consiste à redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Voici quelques directives générales :  
  
    -   Vérifiez que le SPID a été supprimé en interrogeant `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`. S'il ne retourne aucune ligne, la session a été supprimée.  
  
    -   Si la session est toujours active, vérifiez si des tâches sont affectées à cette session en exécutant la requête `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`. Si vous y voyez la tâche, votre session est très probablement en cours de fermeture. Notez que cette opération peut prendre beaucoup de temps et risque même d'échouer.  
  
    -   En l'absence de tâches dans le sys.dm_os_tasks associé à cette session, mais si la session est maintenue dans sys.dm_exec_sessions après l'exécution de la commande KILL, vous ne disposez d'aucun thread de travail. Sélectionnez l'une des tâches en cours d'exécution (une tâche répertoriée dans la vue sys.dm_os_tasks avec un `sessions_id <> NULL`), puis supprimez la session qui lui est associée pour libérer le thread de travail. Notez que la suppression d'une session unique ne sera peut-être pas suffisante : vous devrez éventuellement en supprimer plusieurs.  
  
## <a name="dac-port"></a>Port DAC  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est à l'écoute de la connexion DAC sur le port TCP 1434 s'il est disponible ou un port TCP attribué dynamiquement lors du démarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Le journal des erreurs contient le numéro de port sur lequel la connexion DAC écoute. Par défaut, l'écouteur DAC n'accepte une connexion que sur le port local. Pour voir un exemple de code qui active des connexions d’administration à distance, consultez [remote admin connections (option de configuration de serveur)](remote-admin-connections-server-configuration-option.md).  
  
 Une fois que la connexion d'administration distante est configurée, l'écouteur DAC est activé sans nécessiter un redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; un client peut maintenant se connecter à la DAC à distance. Vous pouvez permettre à l'écouteur DAC d'accepter des connexions à distance même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne répond pas en vous connectant d'abord à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant la DAC localement, et en exécutant ensuite la procédure stockée sp_configure pour accepter la connexion à partir de connexions distantes.  
  
 Sur les configurations cluster, la connexion DAC est désactivée par défaut. Les utilisateurs peuvent exécuter l'option remote admin connection de sp_configure pour permettre à l'écouteur DAC d'accéder à une connexion distante. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne répond pas et si l'écouteur DAC n'est pas activé, vous risquez de devoir redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour établir une connexion avec la DAC. Nous recommandons par conséquent d'activer l'option de configuration remote admin connections sur les systèmes en cluster.  
  
 Le port DAC est affecté dynamiquement par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant le démarrage. Lors d’une connexion à l’instance par défaut, la DAC évite d’utiliser une demande SSRP ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol) à SQL Server Browser Service lors de la connexion. Elle se connecte d'abord sur le port TCP 1434. Si cette tentative échoue, elle effectue un appel SSRP pour obtenir le port. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser n'écoute pas les demandes SSRP, la demande de connexion retourne une erreur. Reportez-vous au journal des erreurs pour trouver le numéro de port que la DAC écoute. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter les connexions d'administration distante, la DAC doit être initialisée avec un numéro de port explicite :  
  
 **sqlcmd-STCP :** _ \<server> , \<port> _  
  
 Le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indique le numéro de port de la connexion DAC, qui est 1434 par défaut. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter uniquement des connexions DAC locales, connectez-vous au moyen de l'adaptateur de bouclage en utilisant la commande suivante :  
  
 **sqlcmd-s 127.0.0.1**,`1434`  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un administrateur note que le serveur `URAN123` ne répond pas et souhaite diagnostiquer le problème. Pour ce faire, l'utilisateur active l'utilitaire de ligne de commande `sqlcmd` et se connecte au serveur `URAN123` en utilisant `-A` pour indiquer la connexion DAC.  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> -A`  
  
 L'administrateur peut maintenant exécuter des requêtes pour diagnostiquer le problème et éventuellement terminer les sessions sans réponse.  
  
## <a name="related-tasks"></a>Tâches associées  
  
## <a name="related-content"></a>Contenu associé  
 [Utiliser sqlcmd avec des variables de script](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)  
  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)  
  
 [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)  
  
 [sp_lock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql)  
  
 [KILL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/kill-transact-sql)  
  
 [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)  
  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [DBCC OPENTRAN &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-opentran-transact-sql)  
  
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-inputbuffer-transact-sql)  
  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
 [Fonctions et vues de gestion dynamique relatives aux transactions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql)  
  
 [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
