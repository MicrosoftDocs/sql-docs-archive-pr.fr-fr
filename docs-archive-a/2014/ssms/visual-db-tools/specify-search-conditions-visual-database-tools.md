---
title: Spécifier des conditions de recherche (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa5dab8326de079c385a3a508bc1b01b1ee1247d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604801"
---
# <a name="specify-search-conditions-visual-database-tools"></a>Spécifier des conditions de recherche (Visual Database Tools)
  Vous pouvez spécifier les lignes de données figurant dans votre requête en spécifiant des conditions de recherche. Par exemple, si vous formulez une requête sur une table `employee` , vous pouvez spécifier que vous ne souhaitez rechercher que les employés travaillant dans une région donnée.  
  
 Vous spécifiez des conditions de recherche à l'aide d'une expression. La plupart du temps, cette expression comporte un opérateur et une valeur de recherche. Pour rechercher, par exemple, les employés d'une région commerciale donnée, vous pouvez spécifier le critère de recherche suivant pour la colonne `region` :  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  Si vous utilisez plusieurs tables, le Concepteur de requêtes et de vues étudie chaque condition de recherche, afin de déterminer si la comparaison que vous établissez donne lieu à une jointure. Si tel est le cas, le Concepteur de requêtes et de vues convertit alors automatiquement la condition de recherche en jointure. Pour plus d’informations, consultez [Joindre automatiquement des tables &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
### <a name="to-specify-search-conditions"></a>Pour spécifier des conditions de recherche  
  
1.  Si vous ne l'avez pas encore effectué, ajoutez les colonnes ou les expressions que vous souhaitez utiliser dans votre condition de recherche au volet Critères.  
  
     Si vous créez une requête Select et si vous ne souhaitez pas que les expressions ou les colonnes de recherche figurent dans le résultat de la requête, effacez chaque expression ou colonne de recherche de la colonne **Sortie** pour les exclure des colonnes de sortie.  
  
2.  Localisez la ligne comportant l’expression ou la colonne de données à rechercher, puis entrez une condition de recherche dans la colonne **Filtres** .  
  
    > [!NOTE]  
    >  Si vous n'entrez pas d'opérateur, le Concepteur de requêtes et de vues insère automatiquement l'opérateur d'égalité « = ».  
  
 Le Concepteur de requêtes et de vues met à jour l’instruction SQL dans le [volet SQL](sql-pane-visual-database-tools.md) en ajoutant ou en modifiant la clause WHERE.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles pour l’entrée de valeurs de recherche &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
