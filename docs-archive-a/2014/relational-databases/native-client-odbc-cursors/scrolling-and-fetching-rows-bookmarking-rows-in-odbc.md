---
title: Marquer des lignes dans ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: rothja
ms.author: jroth
ms.openlocfilehash: def05f478c16dcbcdc91771925a11b0b91da2e9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707524"
---
# <a name="bookmarking-rows-in-odbc"></a>Création de signets pour des lignes dans ODBC
  Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne.  
  
 Lors de l’extraction de lignes avec [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md), une application peut utiliser un signet comme base pour la sélection de la ligne de départ. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour faire défiler jusqu’à une ligne avec signet, l’application appelle **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet vers lequel pointe l'attribut d'option SQL_ATTR_FETCH_BOOKMARK_PTR. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une application peut spécifier un décalage pour cette opération dans l’argument *FetchOffset* de l’appel à **SQLFetchScroll**. Lorsqu'un décalage est spécifié, la première ligne de l'ensemble de lignes retourné est déterminée par l'ajout du nombre présent dans l'argument FetchOffset au numéro de la ligne identifiée par le signet. Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge uniquement les signets sur les curseurs statiques et les curseurs de jeu de clés. Si un curseur dynamique est demandé lorsque les signets sont définis, un curseur de jeu de clés est ouvert à la place.  
  
 Les signets peuvent également être utilisés avec la fonction **SQLBulkOperations** pour effectuer des opérations sur un ensemble de lignes en commençant par le signet.  
  
## <a name="see-also"></a>Voir aussi  
 [Défilement et récupération (fetch) de lignes](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
