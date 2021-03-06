---
title: SQL Server, objet Backup Device | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3126310ad31dcc153fc79508dbfaccf86f5da78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603952"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, objet Unité de sauvegarde
  L’objet **Unité de sauvegarde** fournit des compteurs permettant de surveiller les unités de sauvegarde de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisées pour les opérations de sauvegarde et de restauration. Surveillez les unités de sauvegarde lorsque vous voulez déterminer le débit ou la progression et les performances de vos opérations de sauvegarde et de restauration par unité. Pour surveiller le débit de l’opération de sauvegarde ou de restauration de l’ensemble de la base de données, utilisez le compteur **Débit de sauvegarde/restauration/s** de l’objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bases de données**. Pour plus d’informations, voir [SQL Server, Databases Object](sql-server-databases-object.md).  
  
 Ce tableau décrit le compteur **Unité de sauvegarde** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs Unité de sauvegarde de SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Débit d'unité en octets/s**|Débit des opérations de lecture et d'écriture (en octets par seconde) pour une unité de sauvegarde utilisée pour la sauvegarde ou la restauration de bases de données. Ce compteur n'existe que lorsque les opérations de sauvegarde ou de restauration sont en cours d'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
