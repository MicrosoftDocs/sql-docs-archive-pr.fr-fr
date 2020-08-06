---
title: Améliorer les performances des requêtes de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 0658dc74-25eb-4486-bbd6-e85c1f92c272
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a1437f710725df5c87d31f6a80939a5d7869b412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702635"
---
# <a name="improve-the-performance-of-full-text-queries"></a>Améliorer les performances des requêtes de texte intégral
  La liste suivante comprend des recommandations destinées à améliorer les performances des requêtes de texte intégral.  
  
 Les performances des requêtes de texte intégral sont également influencées par les ressources matérielles telles que la mémoire, la vitesse du disque et du processeur, ainsi que par l'architecture de l'ordinateur.  
  
-   Défragmentez l’index de la table de base à l’aide de [ALTER INDEX REORGANIZE](/sql/t-sql/statements/alter-index-transact-sql).  
  
-   Réorganisez le catalogue de texte intégral à l’aide de [ALTER FULLTEXT CATALOG REORGANIZE](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql). Assurez-vous d'effectuer ces opérations avant de tester les performances car l'exécution de cette instruction entraîne une fusion principale des index de texte intégral dans ce catalogue.  
  
-   Limitez le choix de vos colonnes clés de texte intégral à une petite colonne. Même si une colonne de 900 octets est prise en charge, il est recommandé d'utiliser une colonne clé inférieure à cette taille dans un index de recherche en texte intégral. `int` et `bigint` offrent les meilleures performances.  
  
-   L’utilisation d’une clé de texte intégral de type entier évite une jointure avec la table de mappage **docid** . Par conséquent, une clé de texte intégral de type entier améliore considérablement les performances des requêtes et renforce les performances d'analyse. Des avantages en matière de performances supplémentaires peuvent résulter si la clé de texte intégral est également une clé d'index cluster.  
  
-   Regroupez plusieurs prédicats [CONTAINS](/sql/t-sql/queries/contains-transact-sql) dans un seul prédicat CONTAINS. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez spécifier une liste de colonnes dans la requête CONTAINS.  
  
-   Utilisez [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) ou [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) au lieu de CONTAINS ou FREETEXT respectivement, si vous n’avez besoin que d’informations sur la clé de texte intégral ou le rang.  
  
-   Pour limiter les résultats et augmenter les performances, utilisez le paramètre *top_n_by_rank* des fonctions FREETEXTTABLE et CONTAINSTABLE. *top_n_by_rank* vous permet de rappeler uniquement les accès les plus pertinents. Utilisez ce paramètre uniquement si votre scénario d’entreprise ne nécessite pas de rappeler tous les accès possibles (autrement dit, s’il ne nécessite pas un *rappel total*).  
  
    > [!NOTE]  
    >  Le rappel total est généralement requis pour les scénarios juridiques, mais il peut être moins important que les performances pour les scénarios d'entreprise tels qu'un e-business.  
  
-   Vérifiez le plan de requête de texte intégral pour vous assurer que le plan de jointure adéquat a été sélectionné. Utilisez un indicateur de jointure ou un indicateur de requête si nécessaire. Si un paramètre est utilisé dans la requête de texte intégral, la valeur initiale du paramètre détermine le plan de requête. Vous pouvez utiliser l’ [indicateur de requête](/sql/t-sql/queries/hints-transact-sql-query) OPTIMIZE FOR pour forcer la requête à une compilation avec la valeur souhaitée. Il est ainsi possible d'obtenir un plan de requête déterministe et de meilleures performances.  
  
-   Trop de fragments d'index de recherche en texte intégral dans l'index de texte intégral peut conduire à une dégradation substantielle dans les performances des requêtes. Pour réduire le nombre de fragments, réorganisez le catalogue de texte intégral en utilisant l’option REORGANIZE de l’instruction [ALTER FULLTEXT CATALOG](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] . Cette instruction fusionne essentiellement tous les fragments en un plus grand fragment unique et supprime toutes les entrées obsolètes de l'index de recherche en texte intégral.  
  
-   Dans la recherche en texte intégral , les opérateurs logiques spécifiés dans CONTAINSTABLE (AND, OR) peuvent être implémentés en tant que jointures SQL ou bien dans des fonctions table de diffusion d'exécution de texte intégral (STVF). En général, les requêtes avec un seul type d'opérateur logique sont implémentées exclusivement par l'exécution de texte intégral, alors que les requêtes qui combinent des opérateurs logiques possèdent également des jointures SQL. L'implémentation d'un opérateur logique dans la fonction table multi-diffusion d'exécution de texte intégral utilise quelques propriétés d'index spéciales qui la rendent beaucoup plus rapide que les jointures SQL. Pour cette raison, nous recommandons que, dans toute la mesure du possible, vous encadrez des requêtes en utilisant seulement un type unique d'opérateur logique.  
  
-   Pour les applications qui contiennent des prédications de relation sélectives, les requêtes qui utilisent des prédicats relationnels sélectifs et des prédicats de texte intégral non sélectifs peuvent s'exécuter de manière optimale lorsqu'elles sont écrites pour utiliser l'optimiseur de requête. Cela permet à l'optimiseur de requête de déterminer s'il peut exploiter le prédicat ou le menu déroulant de plage pour produire un plan de requête effectif. Cette approche est plus simple et souvent plus efficace que l'indexation des données relationnelles comme données de texte intégral.  
  
## <a name="related-resources"></a>Ressources associées  
 [SQL Server 2008 Full-Text Search: Internals and Enhancements (en anglais)](https://go.microsoft.com/fwlink/?LinkId=129544)  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)   
 [sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
  
