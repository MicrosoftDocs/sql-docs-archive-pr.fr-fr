---
title: MSSQLSERVER_41396 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699618"
---
# <a name="mssqlserver_41396"></a>MSSQLSERVER_41396
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41396|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MAX_SORT_ROWS_EXCEEDED|  
|Texte du message|L'opération de tri a dépassé la limite de la mémoire tampon. L'exécution de la procédure stockée a été abandonnée. Consultez la documentation en ligne de SQL Server pour plus d'informations.|  
  
## <a name="explanation"></a>Explication  
 Les procédures stockées compilées en mode natif effectuent des opérations de tri en mémoire. Il existe une limite sur la taille du tampon de tri. Cette erreur indique que la taille du tampon de tri dépasse cette limite. L'opération de tri et l'exécution de la procédure stockée ont été abandonnées.  
  
 La taille de chaque ligne ou entrée dans le tampon de tri est déterminée par le nombre de lignes triées ainsi que par le nombre de jointures et le nombre et le type de fonctions d'agrégation dans la requête. En simplifiant la requête, vous pouvez réduire la taille de chaque ligne, afin de pouvoir faire tenir plus de lignes dans le tampon de tri. La taille des lignes dans les tables de base n'affecte pas la taille de chaque ligne ou entrée dans le tampon de tri.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Sélectionnez moins de lignes ou diminuez la complexité de la requête en supprimant des jointures ou des fonctions d'agrégation.  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
