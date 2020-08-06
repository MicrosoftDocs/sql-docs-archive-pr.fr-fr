---
title: Base de données, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2860e1434611393c941a639280343f736073c709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611792"
---
# <a name="database-event-category"></a>Catégorie d'événement Base de données
  La catégorie d’événement **Base de données** contient des classes d’événements pour surveiller le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Data File Auto Grow, classe d’événements](data-file-auto-grow-event-class.md)|Indique que la taille du fichier de données a augmenté automatiquement. Cet événement n'est pas déclenché si la taille du fichier de données augmente de manière explicite par le biais d'ALTER DATABASE.|  
|[Data File Auto Shrink, classe d’événements](data-file-auto-shrink-event-class.md)|Indique que la taille du fichier de données a diminué.|  
|[Database Mirroring Connection, classe d’événements](database-mirroring-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport de la mise en miroir de bases de données.|  
|[Database Mirroring State Change, classe d’événements](database-mirroring-state-change-event-class.md)|Indique l'état des modifications de la base de données en miroir.|  
|[Database Suspect Data Page, classe d’événements](database-suspect-data-page-event-class.md)|Indique qu’une page est ajoutée à la table **suspect_pages** dans la base de données **msdb** .|  
|[Classe d'événements Log File Auto Grow](log-file-auto-grow-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si le fichier journal a été augmenté de manière explicite par le biais d'ALTER DATABASE.|  
|[Log File Auto Shrink, classe d’événements](log-file-auto-shrink-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si la taille du fichier journal diminue explicitement par le biais d'ALTER DATABASE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)  
  
  
