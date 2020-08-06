---
title: Spécifier plusieurs conditions de recherche pour une colonne (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a07322120bd3b3f543e6f54fa50cdf75aa32be59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604803"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a>Spécifier plusieurs conditions de recherche pour une colonne (Visual Database Tools)
  Dans certains cas, vous pouvez souhaiter appliquer plusieurs conditions de recherche à une même colonne de données. Vous pouvez, par exemple, souhaiter effectuer les opérations suivantes :  
  
-   Rechercher plusieurs noms différents dans une table `employee` ou des employés compris dans différentes fourchettes salariales. Ce type de recherche nécessite une condition OR.  
  
-   Rechercher un titre de livre commençant par le mot « La » et comportant le mot « Cuisine ». Ce type de recherche nécessite une condition AND.  
  
> [!NOTE]  
>  Les informations figurant dans cette rubrique s'appliquent aux conditions de recherche des clauses WHERE et HAVING d'une requête. Les exemples sont concentrés sur la création de clauses WHERE, mais les principes s'appliquent aux deux types de conditions de recherche.  
  
 Pour rechercher d'autres valeurs dans une même colonne de données, spécifiez une condition OR. Pour rechercher des valeurs répondant à plusieurs conditions, spécifiez une condition AND.  
  
## <a name="specifying-an-or-condition"></a>Spécification d'une condition OR  
 Une condition OR vous permet de spécifier plusieurs autres valeurs à rechercher dans une colonne. Cette option élargit la portée de la recherche et peut par conséquent retourner plus de lignes que lors de la recherche d'une seule valeur.  
  
> [!TIP]  
>  Vous pouvez souvent utiliser l'opérateur IN à la place de l'opérateur OR pour rechercher plusieurs valeurs dans une même colonne de données.  
  
#### <a name="to-specify-an-or-condition"></a>Pour spécifier une condition OR  
  
1.  Dans le volet [Critères](visual-database-tools.md), ajoutez la colonne dans laquelle vous souhaitez effectuer la recherche.  
  
2.  Dans la colonne **Filtre** de la colonne de données que vous venez d’ajouter, spécifiez la première condition.  
  
3.  Dans la colonne **Ou...** de cette même colonne de données, spécifiez la deuxième condition.  
  
 Le Concepteur de requêtes et de vues crée une clause WHERE comportant une condition OR de ce type :  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a>Spécification d'une condition AND  
 Grâce à une condition AND, vous pouvez spécifier que les valeurs d'une colonne doivent répondre à deux conditions (voire plus) concernant la ligne à inclure au jeu de résultats. Cette option restreint la portée de la recherche et retourne généralement moins de lignes que lors de la recherche d'une seule valeur.  
  
> [!TIP]  
>  Si vous formulez une requête sur une plage de valeurs, vous pouvez utiliser l'opérateur BETWEEN plutôt que de relier deux conditions à l'aide de l'opérateur AND.  
  
#### <a name="to-specify-an-and-condition"></a>Pour spécifier une condition AND  
  
1.  Dans le volet Critères, ajoutez la colonne dans laquelle vous souhaitez effectuer la recherche.  
  
2.  Dans la colonne **Filtre** de la colonne de données que vous venez d’ajouter, spécifiez la première condition.  
  
3.  Ajoutez de nouveau cette même colonne de données au volet Critères, en la plaçant sur une ligne vide de la grille.  
  
4.  Dans la colonne **Filtre** de la deuxième instance de la colonne de données, spécifiez la deuxième condition.  
  
 Le Concepteur de requêtes crée une clause WHERE comportant une condition AND de ce type :  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions pour la combinaison de conditions de recherche dans le volet critères &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
