---
title: Mettre à jour une ressource (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- updating resources
- resources [Reporting Services], updating
ms.assetid: d21f7493-bcf7-4e9e-9886-55ebdc1f1037
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0fca59e476c2820b715ff46729784edc562f74d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605066"
---
# <a name="update-a-resource-report-manager"></a>mise à jour d'une ressource (Gestionnaire de rapports)
  Vous pouvez mettre à jour une ressource en la remplaçant par une nouvelle version. Les ressources sont des éléments stockés sur un serveur de rapports qui tirent leur contenu des fichiers que vous téléchargez. Vous pouvez remplacer une ressource existante en important du contenu de fichier inédit ou différent dans la ressource existante. La mise à jour d'une ressource permet d'actualiser du contenu tout en préservant les propriétés existantes et les paramètres de sécurité définis sur la ressource.  
  
### <a name="to-update-a-resource"></a>Pour mettre à jour une ressource  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la ressource à mettre à jour ou effectuez une recherche pour la localiser.  
  
3.  Cliquez sur la ressource pour l’ouvrir dans la page **Vue** .  
  
4.  Cliquez sur **Propriétés** pour ouvrir la page de propriétés **Général** .  
  
5.  Cliquez sur **Remplacer** pour ouvrir la page **Importer une ressource** .  
  
6.  Cliquez sur **Parcourir**.  
  
7.  Sélectionnez le fichier que vous voulez substituer à la ressource actuelle. Vous pouvez utiliser une version mise à jour du fichier de ressources ou spécifier un fichier avec un nom ou un type de fichier différent.  
  
8.  Cliquez sur **OK** pour charger le fichier de ressources, fermez la page **Importer une ressource** et enregistrez les modifications sur le serveur de rapports.  
  
 Si la ressource en cours de mise à jour contient une image utilisée dans un rapport, vous devez actualiser le rapport pour afficher l'image mise à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Page contenu &#40;Gestionnaire de rapports&#41;](../contents-page-report-manager.md)   
 [Page charger un fichier &#40;Gestionnaire de rapports&#41;](../upload-file-page-report-manager.md)   
 [Charger des fichiers dans un dossier](upload-files-to-a-folder.md)   
 [Aide F1 du Gestionnaire de rapports](../report-manager-f1-help.md)  
  
  
