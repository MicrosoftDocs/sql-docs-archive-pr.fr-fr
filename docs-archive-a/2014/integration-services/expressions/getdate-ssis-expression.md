---
title: GETDATE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0acb384a8c3c3dfdae55c7172f341f9e32765e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604052"
---
# <a name="getdate-ssis-expression"></a>GETDATE (expression SSIS)
  Renvoie la date actuelle du système dans un format DT_DBTIMESTAMP. La fonction GETDATE ne prend aucun argument.  
  
> [!NOTE]  
>  La fonction GETDATE retourne un résultat d'une longueur de 29 caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="result-types"></a>Types des résultats  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie l'année de la date actuelle.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 L’exemple suivant renvoie le nombre de jours entre une date de la colonne **ModifiedDate** et la date actuelle.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 L'exemple suivant ajoute trois mois à la date actuelle.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GETUTCDATE &#40;expression SSIS&#41;](getutcdate-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
