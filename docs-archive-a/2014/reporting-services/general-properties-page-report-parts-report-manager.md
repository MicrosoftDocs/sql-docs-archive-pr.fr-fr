---
title: Page Propriétés générales, parties de rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 93ddce72-31f1-42f7-abd5-8191acbb00c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 320f123ddcaca1f5258d8b9e0bfd9da03fe2c548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613844"
---
# <a name="general-properties-page-report-parts-report-manager"></a>Page Propriétés générales, parties de rapport (Gestionnaire de rapports)
  Utilisez la page Propriétés pour afficher et gérer les propriétés générales d'une partie de rapport.  
  
 Dans le Gestionnaire de rapports, vous ne pouvez pas afficher ou modifier l'apparence et les fonctionnalités de la partie de rapport. Pour modifier la conception, vous devez utiliser un outil de création qui permet d'ouvrir et de modifier la conception, puis de la publier à nouveau sur le serveur.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-properties-page-for-a-report-part"></a>Pour ouvrir la page des propriétés d'une partie de rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez la partie du rapport dont vous souhaitez configurer les propriétés.  
  
2.  Pointez sur la partie de rapport et cliquez sur la flèche déroulante.  
  
3.  Dans la liste déroulante, cliquez sur **Gérer**. La page des propriétés générales s'affiche.  
  
## <a name="options"></a>Options  
 **Date de modification**  
 Date et heure de dernière modification des propriétés de la partie de rapport sur le serveur, ou date et heure de publication d'une nouvelle version de la partie de rapport sur le serveur. Lecture seule.  
  
 **Modifié par**  
 Nom de l'utilisateur auteur des dernières modifications apportées à la partie de rapport. Lecture seule.  
  
 **Date de création**  
 Date et heure auxquelles la partie de rapport a été publiée pour la première fois sur le serveur. Lecture seule.  
  
 **Créé par**  
 Nom de l'utilisateur qui a créé la partie de rapport. Lecture seule.  
  
 **Taille**  
 Taille de fichier de la partie de rapport. Lecture seule.  
  
 **Nom**  
 Permet de taper un nom pour identifier la partie de rapport.  
  
 **Description**  
 Permet de fournir des informations sur la partie de rapport. La description s'affiche dans la page Contenu du Gestionnaire de rapports. Un utilisateur peut lancer une recherche sur le texte de la description lorsqu'il recherche des parties de rapport dans un outil de création de rapports.  
  
 **Masquer en mode Liste**  
 Sélectionnez cette option pour que les utilisateurs qui recourent au mode Liste dans le Gestionnaire de rapports ne puissent pas voir la partie de rapport. Le mode Liste est le format d'affichage utilisé par défaut lors de l'exploration de l'arborescence des dossiers du serveur de rapports. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Type**  
 Type de la partie de rapport. Lecture seule.  
  
 **Appliquer**  
 Enregistrez vos modifications.  
  
 **Supprimer**  
 Permet de supprimer la partie de rapport de la base de données du serveur de rapports. La suppression d'une partie de rapport du serveur n'empêche pas le rendu des rapports existants auxquels la partie de rapport a été ajoutée.  
  
 **Déplacer**  
 Ouvre la page Déplacer des éléments qui permet de déplacer une partie de rapport dans l'arborescence des dossiers du serveur de rapports. Pour plus d’informations, consultez [page déplacer des éléments &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Télécharger**  
 Permet d'extraire une copie de la définition de partie de rapport à enregistrer en tant que fichier .rsc. Le fichier .rsc peut être soit téléchargé dans un dossier du serveur de rapports, soit utilisé pour remplacer une partie de rapport existante dans un dossier du serveur de rapports.  
  
 **Replace**  
 Permet de remplacer la définition de partie de rapport par une autre à partir d'un fichier .rsc.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des parties de rapports](report-design/managing-report-parts.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page contenu &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Parties de rapport &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Aide (F1) Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Parties de rapports et datasets dans le Générateur de rapports](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
