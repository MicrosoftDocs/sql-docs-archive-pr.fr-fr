---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602084"
---
# <a name="sql-server-http_storage_object"></a>SQL Server, HTTP_STORAGE_OBJECT
  L’objet de performance **SqlServer : HTTP_STORAGE_OBJECT** est constitué de compteurs de performances qui surveillent le compte de stockage Azure. À l’aide [des fichiers de données SQL Server dans Azure](../databases/sql-server-data-files-in-microsoft-azure.md) , vous pouvez stocker des fichiers de base de données dans des objets BLOB de stockage Azure. Cet objet de performance traite chaque compte de stockage Azure en tant que lecteur différent.  
  
|Nom de compteur|Description|  
|------------------|-----------------|  
|**Octets lus/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture.|  
|**Octets écrits/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations d'écriture.|  
|**Octets totaux/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture et d'écriture.|  
|**Lectures/s**|Nombre de lectures par seconde sur le stockage HTTP.|  
|**logiques/s**|Nombre d'écritures par seconde sur le stockage HTTP.|  
|**Transferts/s**|Nombre d'opérations de lecture et d'écriture par seconde sur le stockage HTTP.|  
|**Durée octets/lecture**|Nombre moyen d'octets transférés du stockage HTTP par lecture.|  
|**Durée octets/écriture**|Nombre moyen d'octets transférés du stockage HTTP par écriture.|  
|**Durée octets/transfert**|Nombre moyen d'octets transférés du stockage HTTP pendant des opérations de lecture ou d'écriture.|  
|**Nbre moyen microsecondes/lecture**|Nombre moyen de microsecondes nécessaires pour chaque lecture à partir du stockage HTTP.|  
|**Nbre moyen microsecondes/écriture**|Nombre moyen de microsecondes nécessaires pour chaque écriture sur le stockage HTTP.|  
|**Nbre moyen micros./transfert**|Nombre moyen de microsecondes nécessaires pour chaque transfert vers le stockage HTTP.|  
|**E/S en attente vers le stockage HTTP**|Nombre total d'E/S en attente vers un stockage HTTP.|  
|**Nouvelle tentative d’e/s de stockage HTTP/s**|Nombre de demandes de nouvelle tentative envoyées au stockage HTTP par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
