---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68f40ac3a566280526757bd8b83c784954ba3dde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696863"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|5231|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Texte du message|ID d’objet O_ID (objet 'NAME') : un blocage s’est produit lors de la tentative de verrouillage de cet objet en vue d’une vérification. Cet objet a été ignoré et il ne sera pas traité.|  
  
## <a name="explanation"></a>Explication  
 Un blocage s'est produit lorsque DBCC essayait de verrouiller l'objet et DBCC a été choisi comme victime du blocage. L'objet ne sera pas traité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 None  
  
  
