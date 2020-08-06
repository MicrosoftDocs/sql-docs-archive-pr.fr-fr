---
title: Télécharger des fichiers dans un dossier | Microsoft Docs
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
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605065"
---
# <a name="upload-files-to-a-folder"></a>Télécharger des fichiers dans un dossier
  Vous pouvez télécharger des fichiers à partir du système de fichiers, puis les stocker comme éléments gérés dans une base de données de serveur de rapports. Ce qui se produit lorsque vous téléchargez un fichier dépend du type du fichier.

-   Le téléchargement d'un fichier .rdl équivaut à la publication d'un rapport.

-   Le téléchargement de n'importe quel autre fichier l'ajoute à la base de données du serveur de rapports en tant qu'objet binaire unique. Ces fichiers sont publiés sur un serveur de rapports en tant que ressource. Les ressources peuvent être n'importe quel type de fichier. Si l'extension de fichier correspond à un type MIME connu, une icône associée à ce type MIME est utilisée pour identifier le type de la ressource. Sinon, une icône de fichier générique indique la présence d'une ressource.

> [!NOTE]
>  Vous pouvez télécharger un fichier de source de données de rapports (.rds) pour créer une source de données partagée. Les fichiers .rds sont utilisables uniquement dans le Générateur de rapports. Ils ne peuvent en aucun cas fournir le contenu d'un élément de source de données partagée que vous définissez et gérez via le Gestionnaire de rapports. Outre le téléchargement, vous pouvez écrire un script qui crée une source de données partagée en se basant sur un fichier .rds.

 La taille de fichier maximale des éléments téléchargés est déterminée par [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Par défaut, la taille maximale est de 4 mégaoctets (Mo).

 Sur un plan visuel, les fichiers que vous téléchargez dans une base de données de serveur de rapports s'affichent dans l'arborescence des dossiers avec les icônes suivantes.

 Icône rapport ![icône](../media/hlp-16doc.gif "Icône Rapport") rapport

 Icône ![de modèle icône](../media/model-icon.gif "Icône Modèle") de modèle de rapport

 icône de ressource générique icône ![de ressource générique](../media/hlp-16file.gif "icône de ressource générique")

 Lorsque vous téléchargez un fichier, il est toujours placé dans le dossier en cours de sélection. Vous pouvez soit naviguer d'abord vers le dossier où l'élément sera stocké, soit télécharger un fichier puis le déplacer ultérieurement vers son emplacement définitif.

 Pour télécharger un fichier, utilisez le Gestionnaire de rapports. Votre possibilité de télécharger des fichiers sur un serveur de rapports dépend des tâches incluses dans votre attribution de rôle. Si vous utilisez la sécurité par défaut, les administrateurs locaux peuvent ajouter des éléments à un serveur de rapports. Si la fonctionnalité Mes rapports est activée, tout utilisateur disposant d'un dossier Mes rapports est autorisé à télécharger des éléments dans ce dossier. Si vous utilisez des attributions de rôle personnalisées, l'attribution de rôle doit inclure les tâches prenant en charge la gestion de dossiers.

|Action à réaliser|Incluez ces tâches|
|----------------|-------------------------|
|Télécharger un fichier .rdl dans un dossier|Gérer les rapports|
|Télécharger un fichier en tant qu'objet binaire|Gestion des ressources|
|Afficher le contenu d'un dossier|Afficher les ressources, afficher les rapports|

## <a name="see-also"></a>Voir aussi
 [Gestionnaire de rapports &#40;&#41; en mode natif SSRS].. /report-manager-ssrs-native-mode.md) l’octroi d’autorisations sur [les tâches et les autorisations](../security/tasks-and-permissions.md) [du serveur de rapports en mode natif](../security/granting-permissions-on-a-native-mode-report-server.md) [charge un fichier ou un rapport &#40;gestionnaire de rapports&#41;](../reports/upload-a-file-or-report-report-manager.md)


