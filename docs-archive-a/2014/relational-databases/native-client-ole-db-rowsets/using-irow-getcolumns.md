---
title: Utilisation de IRow::GetColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f323dda790946565bc0dbd63c9e1f9d17ac7494b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602817"
---
# <a name="using-irowgetcolumns"></a>Utilisation d'IRow::GetColumns
  L’implémentation **IRow** permet un accès séquentiel de type « avant uniquement » aux colonnes. Vous pouvez accéder à toutes les colonnes d’une ligne avec un appel unique à **IRow::GetColumns**, ou appeler **IRow::GetColumns** chaque fois que vous accédez à plusieurs colonnes de la ligne.  
  
 Les appels multiples à **IRow::GetColumns** ne doivent pas se chevaucher. Par exemple, si le premier appel à **IRow::GetColumns** récupère les données des colonnes 1, 2 et 3, le deuxième appel à **IRow::GetColumns** doit appeler les colonnes 4, 5 et 6. Si des appels ultérieurs à **IRow::GetColumns** se chevauchent, l’indicateur d’état (champ dwstatus dans DBCOLUMNACCESS) a la valeur DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraction d'une ligne unique avec IRow](fetching-a-single-row-with-irow.md)  
  
  
