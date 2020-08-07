---
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11302f882846c49c6e9998608967e7042ac9860c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611108"
---
# <a name="mssqlserver_1803"></a>MSSQLSERVER_1803
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1803|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NO_SPACE|  
|Texte du message|Échec de CREATE DATABASE. Le fichier primaire doit être doté d’une capacité minimale de %d Mo pour recevoir une copie de la base de données model.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une base de données en effectuant une copie de la base de données model. Ensuite, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renomme la copie et agrandit la nouvelle base de données à la taille demandée. Dans le cas présent, l'utilisateur a essayé de créer une base de données plus petite que la base de données model. L'opération a échoué car la copie de la base de données model ne correspondait pas au fichier de données primaire, parce que le fichier était plus petit que la base de données model.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Créez la base de données en utilisant une plus grande taille pour le fichier de base de données. Réduisez ensuite si vous le souhaitez la base de données en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou l'instruction DBCC SHRINKDATABASE.  
  
  
