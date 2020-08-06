---
title: Boîte de dialogue restaurer la base de données (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710887"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Restaurer la base de données (Analysis Services - Données multidimensionnelles)
  La boîte de dialogue **Restaurer la base de données** de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] permet de restaurer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à partir d'un fichier de sauvegarde portant l'extension .abf ([!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File).  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
 **Pour afficher la boîte de dialogue Restaurer la base de données**  
  
-   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou sur une base de données dans **l’Explorateur d’objets**, puis cliquez sur **Restaurer**.  
  
 La boîte de dialogue **Restaurer la base de données** contient les pages suivantes.  
  
## <a name="pages"></a>Pages  
 **Général**  
 Cette page permet de sélectionner la base de données à restaurer, le fichier de sauvegarde, ainsi que les options générales et le mot de passe permettant cette restauration. Pour plus d’informations sur cette page, consultez [Général &#40;boîte de dialogue Restaurer la base de données&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Partitions**  
 Cette page sert à restaurer les partitions locales vers des emplacements spécifiés, ainsi que restaurer les partitions distantes à partir de fichiers de sauvegarde à distance. Pour plus d’informations sur cette page, consultez [Partitions &#40;boîte de dialogue Restaurer la base de données&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
