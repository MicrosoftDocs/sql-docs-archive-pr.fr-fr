---
title: Modifications importantes apportées à la recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- full-text catalogs [SQL Server], breaking changes
- breaking changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 260b1a303685ad9247154504400ef1519ecaa219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709943"
---
# <a name="breaking-changes-to-full-text-search"></a>Modifications importantes apportées à la recherche en texte intégral
  Cette rubrique décrit les modifications importantes apportées à la recherche en texte intégral. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-full-text-search-in-sssql14"></a>Modifications importantes de la recherche en texte intégral dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informations qui seront fournies par la suite.  
  
## <a name="breaking-changes-in-full-text-search-in-sssql11"></a>Modifications importantes de la recherche en texte intégral dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="collation-changed-for-name-column-in-sysfulltext_languages"></a>Classement modifié pour la colonne de nom dans sys.fulltext_languages  
 Le classement de la colonne **name** de la langue dans l’affichage catalogue [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) est passé d’un classement fixe de la base de données de ressources au classement par défaut sélectionné pour l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Cette modification permet de comparer les valeurs dans la colonne **name** au moment où vous joignez la vue [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) et **sys.fulltext_languages**. Par exemple, vous pouvez définir des requêtes toutes les bases de données dont la langue de texte intégral par défaut est différente de la langue de la base de données par défaut.  
  
## <a name="breaking-changes-in-full-text-search-in-sql-server-2008"></a>Dernières modifications dans la recherche en texte intégral dans SQL Server 2008  
 Les modifications décrites ci-dessous s'appliquent à la recherche en texte intégral entre [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et les versions ultérieures.  
  
|Fonctionnalité|Scénario|SQL Server 2005|SQL Server 2008 et versions ultérieures|  
|-------------|--------------|---------------------|----------------------------------------|  
|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) avec des types définis par l’utilisateur (UDT)|La clé de texte intégral est un type défini par l'utilisateur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], par exemple `MyType = char(1)`.|La clé retournée est du type assigné au type défini par l'utilisateur.<br /><br /> Dans l’exemple, il s’agit de **char (1)**.|La clé retournée est du type défini par l'utilisateur. Dans l’exemple, il s’agit de **MyType**.|  
|paramètre *top_n_by_rank* (des instructions CONTAINSTABLE et [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) [!INCLUDE[tsql](../includes/tsql-md.md)] )|*top_n_by_rank* des requêtes en utilisant 0 comme paramètre.|Échec avec un message d'erreur qui signale que vous devez utiliser une valeur supérieure à zéro.|Réussite, retourne zéro ligne.|  
|CONTAINSTABLE et **ItemCount**|Suppression de lignes de table de base avant de pousser les modifications vers MSSearch.|CONTAINSTABLE retourne un enregistrement fantôme. **ItemCount** n’est pas modifié.|CONTAINSTABLE ne retourne pas d'enregistrements fantômes.|  
|**ItemCount**|La table contient des documents ou des colonnes de type Null.|Outre les documents indexés, les documents qui sont null ou qui ont des types Null sont comptés dans la valeur **ItemCount** .|Seuls les documents indexés sont comptés dans la valeur **ItemCount** .|  
|**ItemCount** du catalogue|Colonne blob avec une extension NULL.|Il est compté dans **ItemCount** du catalogue|Elle n’est pas comptabilisée dans **ItemCount** du catalogue.|  
|**UniqueKeyCount**|Interrogation d'un nombre de clés uniques d'un catalogue, par exemple deux tables (table1 et table2) chacune avec trois mots : word1, word2 et word3.|**UniqueKeyCount** = 9. Le tableau suivant résume comment cette valeur est atteinte :<br /><br /> table1 = 3<br /><br /> EOF pour l'index de recherche en texte intégral de table1 = 1<br /><br /> table2 = 3<br /><br /> EOF pour l'index de recherche en texte intégral de table2 = 1<br /><br /> catalogue de texte intégral = 1|Pour chaque table, **UniqueKeyCount** est le nombre de mots clés distincts + 1 (0xFF).  Cela ne traite pas les mêmes mots dans > 1 document en tant que nouvelle clé unique.<br /><br /> Pour un catalogue, **UniqueKeyCount** est la somme de **UniqueKeyCount** de chacune des tables sous le catalogue. Les mots identiques de tables différentes sont traités comme des clés uniques. Dans ce cas, le nombre de clés uniques est 8.|  
|option **précalculer** le niveau du serveur|Optimisation des performances des requêtes FREETEXTTABLE.|Lorsque l’option a la valeur 1, les requêtes FREETEXTTABLE spécifiées avec *top_n_by_rank* utilisent des données de classement précalculées stockées dans les catalogues de texte intégral.|Non prise en charge.|  
|[sp_fulltext_pendingchanges](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql) lors de la mise à jour d’une colonne clé|Mise à jour de la colonne clé de texte intégral sur une ligne d'une table de 2 lignes et exécution de sp_fulltext_pendingchanges.|Les deux lignes apparaissent.|Une seule ligne apparaît.|  
|Fonctions inline|Fonctions inline avec un opérateur de texte intégral|Retournent un message d'erreur.|Retournent les lignes pertinentes.|  
|[sp_fulltext_database](/sql/relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql)|Activation ou désactivation de la recherche en texte intégral à l'aide de sp_fulltext_database.|Aucun résultat n'est retourné pour les requêtes de texte intégral. Si le texte intégral est désactivé pour la base de données, les opérations de texte intégral ne sont pas autorisées.|Retourne des résultats pour les requêtes de texte intégral et les opérations de texte intégral sont autorisées même si le texte intégral est désactivé pour la base de données.|  
|Mots vides spécifiques aux paramètres régionaux|Interroge les variantes spécifiques aux paramètres régionaux d’une langue parente, telles que le français belge et le français canadien.|Requêtes les variantes spécifiques aux paramètres régionaux sont traitées par les composants (analyseurs lexicaux, générateurs de formes dérivées et mots vides) de leur langue parente. Par exemple, les composants Français (France) sont utilisés pour analyser le Français (Belgique).|Vous devez ajouter des mots vides de manière explicite pour chaque identificateur de paramètres régionaux (LCID). Par exemple, vous devriez spécifier un LCID pour la Belgique, le Canada et la France.|  
|Processus d'indexation par radicaux du dictionnaire des synonymes|Utilisation du dictionnaire des synonymes et des formes flexionnelles (indexation par radicaux).|Un mot du dictionnaire des synonymes est ramené automatiquement à son radical après son expansion.|Si vous souhaitez que la forme radicale figure dans l'expansion, vous devez l'ajouter de manière explicite.|  
|Chemin d'accès au catalogue de texte intégral et groupe de fichiers|Utilisation des catalogues de texte intégral.|Chaque catalogue de texte intégral a un chemin d'accès physique et appartient à un groupe de fichiers. Il est traité en tant que fichier de base de données.|Un catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers. Un catalogue de texte intégral est un concept logique qui fait référence à un groupe d'index de recherche en texte intégral.<br /><br /> Remarque : les [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] instructions DDL qui spécifient des catalogues de texte intégral fonctionnent correctement.|  
|[sys. fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)|Utilisation du chemin d'accès, data_space_id et file_id de cet affichage catalogue.|Ces colonnes retournent une valeur spécifique.|Ces colonnes retournent NULL car le catalogue de texte intégral ne se trouve plus dans le système de fichiers.|  
|[sys.sysfulltextcatalogs](/sql/relational-databases/system-compatibility-views/sys-sysfulltextcatalogs-transact-sql)|Utilisation de la colonne de chemin d'accès de cette table système déconseillée.|Retourne le chemin d'accès de système de fichiers du catalogue de texte intégral.|Retourne NULL car le catalogue de texte intégral ne se trouve plus dans le système de fichiers.|  
|[sp_help_fulltext_catalogs](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql)<br /><br /> [sp_help_fulltext_catalogs_cursor](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql)|Utilisation de la colonne PATH de ces procédures stockées déconseillées.|Retourne le chemin d'accès de système de fichiers du catalogue de texte intégral.|Retourne NULL car le catalogue de texte intégral ne se trouve plus dans le système de fichiers.|  
|[sp_help_fulltext_catalog_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql)|Utilisation de sp_help_fulltext_catalog_components de cette procédure stockée.|Retourne la liste de tous les composants (filtres, analyseurs lexicaux et gestionnaires de protocoles) utilisés pour tous les catalogues de texte intégral dans la base de données active.|Retourne des lignes vides.|  
|[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql)|À l’aide de la propriété **IsFullTextEnabled** .|Le paramètre **IsFullTextEnabled** indique si la recherche en texte intégral est activée dans une base de données donnée.|La valeur de cette colonne est sans effet. Les bases de données utilisateur sont toujours activées pour la recherche en texte intégral.|  
  
## <a name="see-also"></a>Voir aussi  
 [Changements de comportement de la recherche en texte intégral](../relational-databases/search/full-text-search.md)   
 [Recherche en texte intégral](../relational-databases/search/full-text-search.md)  
  
  
