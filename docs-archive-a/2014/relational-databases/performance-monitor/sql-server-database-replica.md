---
title: SQL Server, réplica de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c8830ae30ad3514e107b718f9a02fef873e20295
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612248"
---
# <a name="sql-server-database-replica"></a>SQL Server, réplica de base de données
  L’objet de performance **SQLServer:Database Replica** contient des compteurs de performances qui communiquent des informations sur les bases de données secondaires d’un groupe de disponibilité AlwaysOn dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Cet objet est valide uniquement sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge un réplica secondaire.  
  
|Nom de compteur|Description|Vue sur…|  
|------------------|-----------------|--------------|  
|**Octets de fichier reçus/s**|Quantité de données FILESTREAM reçue par le réplica secondaire pour la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**Octets de journal reçus/s**|Quantité d'enregistrements du journal reçue par le réplica secondaire pour la base de données au cours de la dernière seconde.|Réplica secondaire|  
|**Taille de journal restante pour l'annulation**|Quantité de journal en kilo-octets restant pour terminer la phase de restauration.|Réplica secondaire|  
|**File d'attente d'envoi du journal**|Quantité d'enregistrements du journal dans les fichiers journaux de la base de données primaire, en kilo-octets, qui n'a pas encore été envoyée au réplica secondaire. Cette valeur est envoyée au réplica secondaire à partir du réplica principal. La taille de file d'attente n'inclut pas les fichiers FILESTREAM envoyés à un réplica secondaire.|Réplica secondaire|  
|**Transactions d'écriture en miroir/s**|Nombre de transactions qui ont été écrites dans la base de données primaire et qui ont ensuite attendu que le journal soit envoyé à la base de données secondaire pour être validées, au cours de la dernière seconde.|Réplica principal|  
|**File de récupération**|Quantité d'enregistrements du journal dans les fichiers journaux du réplica secondaire qui n'a pas encore été réexécutée.|Réplica secondaire|  
|**Restauration par progression bloquée/s**|Nombre de fois que le thread de restauration est bloqué sur des verrous détenus par les lecteurs de la base de données.|Réplica secondaire|  
|**Octets restants de restauration par progression**|Taille de journal restante, en kilo-octets, avant la fin de la phase de restauration.|Réplica secondaire|  
|**Octets réexécutés/s**|Quantité d'enregistrements du journal réexécutée sur la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**Taille totale de journal nécessitant une annulation**|Nombre total de kilo-octets du journal qui doivent être annulés.|Réplica secondaire|  
|**Délai de transaction**|Délai d'attente d'accusé de réception non terminé, en millisecondes.|Réplica principal|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, réplica de disponibilité](sql-server-availability-replica.md)   
 [SQL Server, objet Databases](sql-server-databases-object.md)   
 [Groupes de disponibilité AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
