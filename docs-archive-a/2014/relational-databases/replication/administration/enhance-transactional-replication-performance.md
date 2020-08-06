---
title: Améliorer les performances de la réplication transactionnelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709232"
---
# <a name="enhance-transactional-replication-performance"></a>Améliorer les performances de la réplication transactionnelle
  Après avoir tenu compte des conseils de performances générales décrites dans [Amélioration des performances générales de la réplication](enhance-general-replication-performance.md), envisagez ces domaines supplémentaires spécifiques à la réplication transactionnelle.  
  
## <a name="database-design"></a>Création de bases de données  
  
-   Réduisez la taille de transaction dans la conception de votre application.  
  
     Par défaut, la réplication transactionnelle propage les modifications en fonction des limites des transactions. Si les transactions sont plus petites, il est moins probable que l'Agent de distribution doive renvoyer une transaction à cause de problèmes réseau. S'il est demandé à l'Agent de renvoyer une transaction, la quantité de données envoyée est moins importante.  
  
## <a name="distributor-configuration"></a>Configuration du serveur de distribution  
  
-   Configurez le serveur de distribution sur un serveur dédié.  
  
     Vous pouvez réduire la charge de traitement sur le serveur de publication en configurant un serveur de distribution distant. Pour plus d'informations, voir [Configure Distribution](../configure-distribution.md).  
  
-   Dimensionnez correctement la base de données de distribution.  
  
     Testez la réplication avec une charge normale pour votre système afin de déterminer l'espace nécessaire au stockage des commandes. Assurez-vous que la base de données est suffisamment volumineuse pour stocker les commandes sans avoir fréquemment recours à l'extension automatique. Pour plus d’informations sur la modification de la taille d’une base de données, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="publication-design"></a>Conception de la publication  
  
-   Répliquez l'exécution d'une procédure stockée lors de mises à jour par lot de tables publiées.  
  
     Si des mises à jour par lots concernent parfois de nombreuses lignes sur l'abonné, vous devez envisager la mise à jour de la table publiée à l'aide d'une procédure stockée puis publier l'exécution de la procédure stockée. Au lieu d'envoyer une mise à jour ou une suppression pour chaque ligne affectée, l'Agent de distribution exécute la même procédure sur l'Abonné à partir des mêmes valeurs de paramètres. Pour plus d’informations, consultez [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Répartissez les articles à travers plusieurs publications.  
  
     Si vous ne pouvez pas utiliser le paramètre **-SubscriptionStreams** (décrit ultérieurement dans cette rubrique), envisagez de créer plusieurs publications. La répartition d'articles sur ces publications permet à la réplication d'appliquer en parallèle les modifications sur les abonnés.  
  
## <a name="subscription-considerations"></a>Considérations sur les abonnements  
  
-   Utilisez les agents indépendants plutôt que les agents partagés si vous avez plusieurs publications sur le même serveur de publication (valeur par défaut pour l'Assistant Nouvelle publication).  
  
-   Exécutez les agents en mode continu et non par l'intermédiaire de planifications très fréquentes.  
  
     Le fait de configurer les agents afin qu'ils s'exécutent en mode continu au lieu de planifier de fréquentes exécutions (par exemple, toutes les minutes) permet d'améliorer les performances de la réplication, car l'Agent n'a pas besoin de démarrer et de s'arrêter. Lorsque vous configurez l'Agent de distribution pour qu'il s'exécute en mode continu, les modifications sont diffusées avec une faible latence aux autres serveurs de la topologie qui sont connectés. Pour plus d'informations, consultez les pages suivantes :  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [Spécifier des planifications de synchronisation](../specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Paramètres de l'Agent de distribution et de l'Agent de lecture du journal  
  
-   Pour résoudre les goulets d’étranglement accidentels, utilisez le paramètre **-MaxCmdsInTran** pour l’agent de lecture du journal.  
  
     Le paramètre **-MaxCmdsInTran** spécifie le nombre maximal d’instructions regroupées dans une transaction lorsque le lecteur du journal écrit des commandes dans la base de données de distribution. L'utilisation de ce paramètre permet à l'Agent de lecture du journal et à l'Agent de distribution de scinder les transactions importantes (constituées de plusieurs commandes) sur le serveur de publication en plusieurs transactions plus petites, lors de l'application des commandes sur l'Abonné. La spécification de ce paramètre permet de réduire les contentions sur le serveur de distribution et de réduire la latence entre le serveur de publication et l'Abonné. Du fait que la transaction d'origine est appliquée en plusieurs morceaux, l'Abonné peut accéder aux lignes d'une importante transaction logique du serveur de publication avant la fin de la transaction d'origine, ce qui rompt la stricte atomicité transactionnelle. La valeur par défaut est **0**, ce qui permet de conserver les limites de la transaction du serveur de publication. Ce paramètre ne s'applique pas aux serveurs de publication Oracle.  
  
    > [!WARNING]  
    >  `MaxCmdsInTran` n'a pas été conçu pour rester toujours activé. Il permet de contourner le problème lorsqu'un utilisateur a accidentellement exécuté un grand nombre d'opérations DML dans une seule transaction (provoquant un retard dans la distribution des commandes jusqu'à ce que la transaction entière soit dans la base de données de distribution, le maintien de verrous, etc.). Si vous rencontrez régulièrement ce problème, vous devriez vérifier vos applications et trouver un moyen de réduire la taille des transactions.  
  
-   Utilisez le paramètre **-SubscriptionStreams** pour l’agent de distribution.  
  
     Le paramètre **-SubscriptionStreams** peut améliorer le débit de la réplication globale. Il autorise plusieurs connexions à l'Abonné pour appliquer des traitements de modifications en parallèle, tout en conservant la plupart des caractéristiques transactionnelles présentes lors de l'utilisation d'un thread unique. Si l'une des connexions ne réussit pas à s'exécuter ou n'est pas validée, toutes les connexions abandonneront le lot actuel, et l'Agent utilisera un flux unique pour une nouvelle tentative sur les lots ayant échoué. Avant que cette phase de nouvelle tentative ne se termine, il peut se produire des incohérences transactionnelles temporaires sur l'Abonné. Une fois que les lots ayant échoué sont validés avec succès, l'Abonné retrouve un état de cohérence transactionnelle.  
  
     Vous pouvez spécifier une valeur pour ce paramètre d’agent à l’aide de l' ** \@ subscriptionstreams** de [SP_ADDSUBSCRIPTION &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).  
  
-   Augmentez la valeur du paramètre **-ReadBatchSize** pour l’Agent de lecture du journal.  
  
     L'Agent de lecture du journal et l'Agent de distribution prennent en charge des tailles de traitements pour les opérations de lecture et de validation des transactions. Par défaut, la taille de traitement est de 500 transactions. Dans ce cas, l'Agent de lecture du journal ne lit dans le journal que le nombre de transactions indiqué, que celles-ci soient marquées ou non pour réplication. Quand de nombreuses transactions sont enregistrées dans une base de données de publication, mais que seules quelques-unes d’entre elles sont marquées pour réplication, vous avez intérêt à utiliser le paramètre **-ReadBatchSize** pour augmenter la taille de traitement de l’Agent de lecture du journal. Ce paramètre ne s'applique pas aux serveurs de publication Oracle.  
  
-   Augmentez la valeur du paramètre **-CommitBatchSize** pour l’Agent de distribution.  
  
     La validation d'un ensemble de transactions comporte une charge fixe ; en validant un grand nombre de transactions moins fréquemment, la charge est répartie sur un volume de données plus important. Cependant, l'avantage obtenu par l'augmentation de ce paramètre disparaît car le coût d'application des modifications est lié à d'autres facteurs, comme l'E/S maximum du disque contenant le journal. De plus, un compromis peut être envisagé : toute défaillance entraînant le redémarrage de l'Agent de distribution doit restaurer et appliquer à nouveau une grande quantité de transactions. Pour les réseaux non fiables, il peut résulter d'une valeur moins importante une diminution des défaillances et un nombre de transactions moins élevé à restaurer et à réappliquer si une défaillance se produit.  
  
-   Réduisez la valeur du paramètre **-PollingInterval** pour l’Agent de lecture du journal.  
  
     Le paramètre **-PollingInterval** indique la fréquence d’interrogation du journal des transactions d’une base de données publiée pour que les transactions soient répliquées. La valeur par défaut est 5 secondes. Si vous réduisez cette valeur, le journal est interrogé plus fréquemment, ce qui peut entraîner une latence plus faible pour la remise des transactions de la base de données de publication sur la base de données de distribution. Cependant, vous devriez équilibrer les besoins d'une latence plus faible en fonction de l'augmentation de la charge sur le serveur causée par une interrogation plus fréquente.  
  
 Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez les pages suivantes :  
  
-   [Utiliser des profils d’agent de réplication](../agents/replication-agent-profiles.md)  
  
-   [Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [Concepts des exécutables de l'agent de réplication](../concepts/replication-agent-executables-concepts.md)  
  
  
