---
title: Compteurs de performance XTP (OLTP en mémoire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698045"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>Compteurs de performance XTP (OLTP en mémoire)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des objets et des compteurs qui peuvent être utilisés par l’Analyseur de performances pour analyser l’activité de l’OLTP en mémoire.  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a>Objets de performance XTP (OLTP en mémoire)  
 Le tableau ci-dessous décrit les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Objet de performance|Description|  
|------------------------|-----------------|  
|[Curseurs XTP](../cursors.md)|L'objet de performance Curseurs XTP contient des compteurs connexes aux curseurs internes du moteur XTP. Les curseurs sont des blocs de construction de bas niveau que le moteur XTP utilise pour traiter les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] . Par conséquent, vous ne pouvez pas les contrôler directement.|  
|[Garbage collection XTP](sql-server-xtp-garbage-collection.md)|L'objet de performance Garbage collection XTP contient les compteurs connexes au garbage collector du moteur XTP.|  
|[Processeur fantôme XTP](sql-server-xtp-phantom-processor.md)|L'objet de performance Processeur fantôme XTP contient des compteurs connexes au sous-système de traitement fantôme du moteur XTP. Ce composant détecte les lignes fantômes dans les transactions exécutées dans le niveau d'isolation SERIALIZABLE.|  
|[Storage XTP](sql-server-xtp-storage.md)|L'objet de performance XTP Storage contient des compteurs associés au stockage XTP dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Journal des transactions XTP](sql-server-xtp-transaction-log.md)|L'objet de performance Journal des transactions XTP contient des compteurs de journalisation des transactions XTP dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Transactions XTP](sql-server-xtp-transactions.md)|L'objet de performance Transactions XTP contient des compteurs connexes aux transactions du moteur XTP dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
  
