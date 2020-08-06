---
title: Télécharger un fichier ou un rapport (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 119e2b22976dc227e017b81a59b698cf9eb7457f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602732"
---
# <a name="upload-a-file-or-report-report-manager"></a>Télécharger un fichier ou un rapport (Gestionnaire de rapports)
  Le Gestionnaire de rapports fournit une fonctionnalité de téléchargement qui vous permet d'ajouter des rapports, des modèles et d'autres fichiers à un serveur de rapports sans devoir publier ces éléments à partir d'une application cliente. Les fichiers que vous téléchargez à partir du système de fichiers sont stockés en tant qu'éléments sur le serveur de rapports. Le type de fichier téléchargé détermine son mode de stockage :  
  
-   Les fichiers .rdl sont stockés sous forme de rapports.  
  
-   Les fichiers .smdl sont stockés sous forme de modèles de rapports.  
  
-   Tous les autres fichiers, y compris les fichiers de sources de données partagées (.rds), sont téléchargés en tant que ressources. Les ressources ne sont pas traitées par un serveur de rapports mais peuvent être affichées dans le Gestionnaire de rapports si le serveur de rapports prend en charge le type MIME du fichier.  
  
### <a name="to-upload-a-file-or-report"></a>Pour télécharger un fichier ou un rapport  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans Gestionnaire de rapports, accédez à la page **contenu** . Localisez le dossier auquel ajouter un élément.  
  
3.  Cliquez sur **Télécharger un fichier**.  
  
4.  Cliquez sur **Parcourir** pour sélectionner un fichier à charger sur le serveur. Vous pouvez télécharger un fichier de définition de rapport, une image, un document ou tout autre fichier que vous souhaitez rendre accessible sur le serveur de rapports.  
  
5.  Tapez un nom pour le nouvel élément. Ce nom peut comporter des espaces, mais il ne peut pas contenir les caractères réservés suivants : ; ? : \@ & = +, $/* \< > |.  
  
6.  Pour remplacer un élément existant par le nouveau, sélectionnez **Remplacer l’élément s’il existe**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Page contenu &#40;Gestionnaire de rapports&#41;](../contents-page-report-manager.md)   
 [Page charger un fichier &#40;Gestionnaire de rapports&#41;](../upload-file-page-report-manager.md)   
 [Télécharger des fichiers dans un dossier](../report-server/upload-files-to-a-folder.md)  
  
  
