---
title: MSSQLSERVER_32044 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604523"
---
# <a name="mssqlserver_32044"></a>MSSQLSERVER_32044
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|32044|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum32044|  
|Texte du message|L'alerte relative au temps de traitement de validation de miroir s'est déclenchée. La valeur actuelle de '%d' dépasse le seuil '%d'.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de mise en miroir de bases de données est émis sur l'instance du serveur principal pour indiquer que le délai d'attente de la validation d'agrégation a atteint ou dépassé la valeur de seuil définie par l'utilisateur à cause de la mise en miroir de bases de données. Le délai d'attente correspond au produit du nombre de transactions et de la durée de chaque transaction. Par exemple, le délai d’attente est de 1 000 millisecondes dans les deux cas suivants : 1 000 transactions * 1 milliseconde et 1 transaction \* 1 000 millisecondes. Le délai d'attente de la validation peut augmenter en raison d'une brusque augmentation du nombre de transactions, de retards dans l'envoi du journal ou de retards dans le vidage du journal sur l'instance du serveur miroir.  
  
 La durée du temps de traitement de validation de miroir est une mesure de performance qui peut vous aider à évaluer l'impact actuel du fonctionnement synchrone sur les performances. Cette mesure n'est utile qu'en mode haute sécurité. Étant donné que le mode haute sécurité est synchrone, l'instance du serveur principal envoie un enregistrement de journal à l'instance du serveur miroir et ne valide la transaction qu'après avoir reçu la confirmation que l'instance du serveur miroir a écrit cet enregistrement sur le disque. L'enregistrement de journal reste sur le disque sur l'instance du serveur miroir en attendant d'être restauré dans la base de données miroir.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez les charges incombant aux instances du serveur principal et du serveur miroir et à leur connexion réseau pour déterminer la cause du problème.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Utiliser des seuils d’avertissement et d’alertes sur des métriques de performances de mise en miroir &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
