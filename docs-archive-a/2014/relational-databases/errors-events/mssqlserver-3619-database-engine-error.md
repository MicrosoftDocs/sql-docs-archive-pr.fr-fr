---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2328ee6366d47130a02c444bce65b7b655af7965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612845"
---
# <a name="mssqlserver_3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|3619|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SYS_NOLOG|  
|Texte du message|Impossible d'écrire un enregistrement de point de contrôle dans la base de données ID %d car le journal est saturé. Demandez à l'administrateur de la base de données de tronquer ce journal ou d'allouer davantage d'espace aux fichiers journaux de la base de données.|  
  
## <a name="explanation"></a>Explication  
 Le journal des transactions est saturé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Tronquez le journal pour libérer de l'espace ou allouez plus d'espace au journal. Pour plus d'informations, consultez « Résolution des problèmes en cas de journal des transactions saturé (erreur 9002) » dans la documentation en ligne de SQL Server.  
  
  
