---
title: Sélection du disque du cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604955"
---
# <a name="cluster-disk-selection"></a>Sélection du disque du cluster
  Utilisez la page **Sélection du disque du cluster** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner la ressource disque de cluster partagée pour votre cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un disque de cluster partagé n’est pas obligatoire pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installations de cluster. Un serveur de fichiers SMB est un stockage pris en charge pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installations de cluster de basculement et peut être spécifié à l’aide de la page **moteur de base de données-répertoires de données** avant d’effectuer l’installation.  
  
> [!WARNING]  
>  Si vous avez sélectionné Analysis Services pour l'installer, vous devez spécifier un disque de cluster partagé.  
>   
>  Si vous envisagez d'activer FILESTREAM sur cette instance du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez spécifier un disque de cluster partagé.  
  
## <a name="options"></a>Options  
 **Disques partagés**  
 Sélectionnez un disque dans la liste. Le disque de cluster est l'emplacement où les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seront placées.  
  
 Un seul disque peut être spécifié. Si vous sélectionnez le groupe contenant la ressource quorum du cluster, un avertissement s'affiche. Il est recommandé de ne pas procéder à l'installation dans cette ressource.  
  
 **Disques partagés disponibles**  
 Affiche une liste de disques disponibles, indique si chacun d'eux est qualifié en tant que disque partagé et fournit une description de chaque ressource de disque.  
  
  
