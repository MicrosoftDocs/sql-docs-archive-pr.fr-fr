---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702943"
---
# <a name="mssqlserver_17884"></a>MSSQLSERVER_17884
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17884|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_SCHEDULER_DEADLOCK|  
|Texte du message|Les nouvelles requêtes à traiter sur le nœud %d n'ont pas été sélectionnées par un thread de travail au cours des %d dernières secondes. Les requêtes qui provoquent des blocages ou dont l'exécution est longue peuvent causer cette situation ainsi qu'une dégradation du temps de réponse du client. Utilisez l'option de configuration "max worker threads" pour augmenter le nombre de threads autorisés, ou optimisez les requêtes en cours d'exécution.  Utilisation du processus SQL : %d%%. Système inactif : %d%%.|  
  
## <a name="explanation"></a>Explication  
 Il n'y a aucun signe de progression dans chacun des planificateurs, ce qui pourrait être causé par des blocages où aucun thread ne peut avancer et/ou aucun nouveau travail ne peut être sélectionné et traité. Si l'utilisation du processus est faible, d'autres processus sur l'ordinateur entraînent peut-être une insuffisance du processus de serveur au niveau du microprocesseur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Déterminez la cause du blocage et l'absence de progression, et résolvez la situation en conséquence. Si l'utilisation du processus est faible, vérifiez la charge sur le système générée par d'autres processus.  
  
  
