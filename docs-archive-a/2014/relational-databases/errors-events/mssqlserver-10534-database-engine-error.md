---
title: MSSQLSERVER_10534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 793bb0bf5048e30624d9566f65e7c6752bd14386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699738"
---
# <a name="mssqlserver_10534"></a>MSSQLSERVER_10534
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|10534|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_INVALID_PARAMS|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car la valeur spécifiée pour `@params` n’est pas valide. Indiquez la valeur sous la forme *nom_paramètre type_paramètre* ou spécifiez Null.|  
  
## <a name="explanation"></a>Explication  
 La valeur spécifiée pour `@params` n'est pas valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez la valeur sous la forme *nom_paramètre type_paramètre* ou spécifiez Null.  
  
## <a name="see-also"></a>Voir aussi  
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
