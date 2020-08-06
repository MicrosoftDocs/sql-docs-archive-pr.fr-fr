---
title: Gérer les extractions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfa25cdc27e707d4be705e66b215130c9d70ce1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614772"
---
# <a name="manage-checkouts"></a>Gérer les extractions
  Une fois un fichier ajouté au contrôle de code source, vous devez l'extraire avant de pouvoir le modifier. Lorsque vous procédez à l'extraction d'un fichier du contrôle de code source, le fournisseur de contrôle de code source copie la dernière version sur votre disque local et désactive l'attribut de lecture seule du fichier. Dans certains cas, il est possible que vous deviez modifier un fichier sans procéder à son extraction. Pour plus d’informations sur la modification d’un fichier sans vérifier le fichier, consultez [modifier les fichiers archivés](../../2014/database-engine/edit-checked-in-files.md).  
  
 Vous pouvez utiliser [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour extraire des fichiers manuellement ou automatiquement. Vous pouvez extraire les fichiers manuellement en ouvrant la solution qui contient les fichiers dans l' [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environnement, puis en cliquant sur la commande **extraire** . Vous pouvez extraire des fichiers automatiquement si vous configurez l'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] à cette fin.  
  
 En fonction des options configurées par votre administrateur, vous pouvez également extraire des fichiers en mode exclusif ou partagé. Lorsque vous procédez à l'extraction d'un fichier de manière exclusive, vous seul pouvez le modifier et aucun autre utilisateur ne peut l'extraire tant que vous ne l'avez pas archivé. Lorsque vous procédez à l'extraction d'un fichier en mode partagé, n'importe quel autre utilisateur peut extraire ce même fichier. À mesure que chaque utilisateur archive le fichier, le fournisseur de contrôle de code source tente de fusionner le fichier avec la dernière version serveur du fichier en question. En cas de conflits entre la version en cours d'archivage et la dernière version, le fournisseur de contrôle de code source demande à l'utilisateur de résoudre ces conflits.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Extraire des fichiers](../../2014/database-engine/check-out-files.md)|Explique comment extraire un fichier de façon à pouvoir le modifier.|  
|[Annuler des extractions](../../2014/database-engine/undo-checkouts.md)|Explique comment annuler une extraction existante.|  
|[Extraire automatiquement des fichiers lors de leur modification](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|Explique comment configurer le contrôle de code source afin d'extraire un fichier lorsque vous commencez à le modifier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les archivages](../../2014/database-engine/manage-checkins.md)   
 [Modifier des fichiers archivés](../../2014/database-engine/edit-checked-in-files.md)  
  
  
