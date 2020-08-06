---
title: MSSQLSERVER_10539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fd1f190b8f5d3ab9755409bdd034fa374ea5314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699713"
---
# <a name="mssqlserver_10539"></a>MSSQLSERVER_10539
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10539|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NO_PLAN_FOR_STMT|  
|Texte du message|Impossible de créer le repère de plan '%.*ls' à partir du cache, car aucun plan de requête n'est disponible pour l'instruction avec l'offset de démarrage %d. Ce problème peut se produire si l'instruction dépend des objets de base de données qui n'ont pas encore été créés. Assurez-vous que tous les objets de base de données nécessaires existent, puis exécutez l'instruction avant de créer le repère de plan.|  
  
## <a name="explanation"></a>Explication  
 Aucun plan de requête n'est disponible dans le cache du plan pour l'instruction avec l'offset de démarrage spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que tous les objets de base de données nécessaires existent, puis exécutez l'instruction avant de créer le repère de plan.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
