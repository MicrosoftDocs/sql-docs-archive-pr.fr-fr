---
title: Colonnes de texte et d’image liées et non liées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: rothja
ms.author: jroth
ms.openlocfilehash: 20a91d26ac8c2d1201386cb19bde13b49a3dbada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709308"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Colonnes de texte et d'image liées et non liées
  Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données des colonnes de **texte**, **ntext**ou **image** non liées au moment où **SQLFetch** est exécutée. Les données **Text**, **ntext**ou **image** ne sont pas réellement récupérées à partir du serveur tant que l’application n’émet pas [SQLGetData](../native-client-odbc-api/sqlgetdata.md) pour la colonne.  
  
 De nombreuses applications peuvent être écrites de sorte qu’aucune donnée **Text**, **ntext**ou **image** ne soit affichée alors qu’un utilisateur fait simplement défiler la liste vers le haut et vers le haut dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut ensuite appeler **SQLGetData** pour extraire les données **Text**, **ntext**ou **image** . Cela empêchera la transmission des données **Text**, **ntext**ou **image** pour les lignes que l’utilisateur ne sélectionne pas et peut donc empêcher la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](managing-text-and-image-columns.md)   
 [Comportements des curseurs](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
