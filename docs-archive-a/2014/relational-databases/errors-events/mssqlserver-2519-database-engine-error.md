---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8577b07586553f4b03714cd31451ac755faf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600979"
---
# <a name="mssqlserver_2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2519|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_NO_EXPRESSION_EVALUATOR|  
|Texte du message|Impossible de vérifier les colonnes calculées et les types définis par l'utilisateur pour l'ID d'objet O_ID (objet « O_NAME ») car l'évaluateur d'expression interne n'a pas pu être initialisé.|  
  
## <a name="explanation"></a>Explication  
 Ce message d'information indique que le processeur de requêtes n'a pas pu fournir à DBCC un objet interne pour permettre l'évaluation de colonnes calculées et de types clr (common language runtime) définis par l'utilisateur. Cela signifie que l'exactitude des colonnes calculées et des types clr définis par l'utilisateur ne sera pas vérifiée et que ceux-ci ne seront pas utilisés lorsque DBCC vérifiera la cohérence entre les index et les tables de base.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 None  
  
## <a name="see-also"></a>Voir aussi  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
