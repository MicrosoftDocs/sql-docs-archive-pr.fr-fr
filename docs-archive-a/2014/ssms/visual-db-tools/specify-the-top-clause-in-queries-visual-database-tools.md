---
title: Spécifier la clause TOP dans des requêtes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8228779703b1bbe3753f1e2728e83b4b5c3a3d17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708008"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Spécifier la clause TOP dans des requêtes (Visual Database Tools)
  La clause TOP retourne uniquement les *n premières* lignes ou *n premiers pourcents* des lignes d’une requête. La clause TOP peut être utile si vous souhaitez inspecter une partie de vos résultats afin de déterminer si votre requête se comporte de la manière escomptée, sans devoir utiliser les ressources nécessaires pour retourner tous les résultats de la requête.  
  
### <a name="to-specify-the-top-clause-in-queries"></a>Pour spécifier la clause TOP dans des requêtes  
  
1.  Ouvrez une requête dans l'Explorateur de solutions ou créez-en une nouvelle.  
  
2.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.  
  
3.  Dans la **Fenêtre Propriétés**, recherchez et développez la propriété **Spécification Top** .  
  
4.  Cliquez sur la propriété enfant **(Haut)** et affectez-lui la valeur **Oui**.  
  
5.  Dans la propriété enfant **Expression** , tapez une expression qui a un résultat numérique (par exemple, « 10 » ou « 2*5 »).  
  
6.  Cliquez sur la propriété enfant **Pourcentage** et indiquez si la propriété **Expression** doit être traitée comme un pourcentage de toutes les lignes retournées (Oui) ou comme le nombre absolu de lignes retournées (Non).  
  
7.  Si votre requête utilise la clause ORDER BY, cliquez sur la propriété enfant **With Ties** et sélectionnez **Oui** pour afficher toutes les lignes d’un groupe si seule une partie du groupe est incluse ou **Non** pour les tronquer.  
  
 Au fur et à mesure que vous exécutez la procédure précédente, remarquez que la clause TOP, affichée dans le volet SQL, se modifie pour refléter les valeurs actuelles des propriétés.  
  
> [!NOTE]  
>  Vous pouvez également modifier les valeurs des propriétés enfants de la propriété **Spécification Top** en modifiant la clause TOP dans le volet SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Propriétés de la requête &#40;Visual Database Tools&#41;](query-properties-visual-database-tools.md)  
  
  
