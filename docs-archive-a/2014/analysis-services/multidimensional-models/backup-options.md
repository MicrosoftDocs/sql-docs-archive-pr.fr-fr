---
title: Options de sauvegarde | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9fc674e699a3078ebd39d50fde96d632ae20493
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601153"
---
# <a name="backup-options"></a>Options de sauvegarde
  Il existe de nombreuses façons de sauvegarder vos [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de données et elles nécessitent toutes des autorisations d’administrateur de serveur et d’administrateur de base de données. Vous pouvez ouvrir la boîte de dialogue **Sauvegarder** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionner les options appropriées et effectuer la sauvegarde dans la boîte de dialogue elle-même. Ou bien, vous pouvez créer un script en utilisant les paramètres définis dans le fichier, le script pouvant être enregistré et exécuté aussi souvent que nécessaire.  
  
## <a name="backup-and-synchronize"></a>Sauvegarde et synchronisation  
 Si la base de données se trouve sur une instance distante [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser la fonction de synchronisation pour sauvegarder la base de données sur l’instance locale. Les versions de développement d'une base de données peuvent être transférées vers l'environnement de production de cette manière. Vous pouvez également utiliser la sauvegarde et la restauration de fichiers classiques pour transférer la version de développement vers l'environnement de production, mais la synchronisation fournit des fonctions supplémentaires. Vous pouvez, par exemple, disposer de paramètres de sécurité différents pour les ordinateurs de développement et de production ; la synchronisation vous donne la possibilité de gérer ces paramètres et de synchroniser tous les objets autres que les rôles. En outre, la synchronisation met généralement à jour ces objets, qui sont différents pour les ordinateurs sources et les ordinateurs de destination, de manière incrémentielle. Ce type de sauvegarde incrémentielle n'est pas disponible avec la fonction de sauvegarde/restauration. Pour plus d’informations, consultez [Synchroniser des bases de données Analysis Services](synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  Le compte de service Analysis Services doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. Par ailleurs, l'utilisateur doit avoir l'un des rôles suivants : rôle d'administrateur sur l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou membre d'un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue sauvegarder la base de données &#40;Analysis Services-données multidimensionnelles&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](backup-and-restore-of-analysis-services-databases.md)   
 [Élément Backup &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
