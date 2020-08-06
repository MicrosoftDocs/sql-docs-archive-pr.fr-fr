---
title: Parcourir un modèle à l’aide de Microsoft Naive Bayes Viewer | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614939"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a>Explorer un modèle à l'aide de la visionneuse de l'algorithme MNB (Microsoft Naive Bayes)
  La [!INCLUDE[msCoName](../../includes/msconame-md.md)] visionneuse Naive Bayes dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d’exploration de données générés à l’aide de l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme Bayes Naive. L'algorithme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes est un algorithme de classification qui est fortement adaptable aux tâches de modélisation prédictive. Pour plus d’informations sur cet algorithme, consultez [Algorithme MNB (Microsoft Naive Bayes)](microsoft-naive-bayes-algorithm.md).  
  
 Comme l’une des principales finalités d’un modèle Naive Bayes est de fournir un moyen rapide d’explorer les données d’un dataset, la Visionneuse de l’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) propose plusieurs méthodes d’affichage de l’interaction entre les attributs prédictibles et les attributs d’entrée.  
  
> [!NOTE]  
>  Si vous voulez afficher des informations détaillées sur les équations utilisées dans le modèle et les motifs détectés, vous pouvez basculer vers la visionneuse de l’arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a>Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. La Visionneuse de l’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) fournit les onglets suivants pour explorer les données :  
  
-   [Réseau de dépendances](#BKMK_Dependency)  
  
-   [Profils d'attribut](#BKMK_Profiles)  
  
-   [Caractéristiques d’attribut](#BKMK_Characteristics)  
  
-   [Discrimination d’attribut](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a>Réseau de dépendances  
 L’onglet **Réseau de dépendances** affiche les dépendances entre les attributs d’entrée et les attributs prédictibles d’un modèle. Le curseur situé à gauche de la visionneuse agit comme un filtre lié à la force des dépendances. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
 Lorsque vous sélectionnez un nœud, la visionneuse met en surbrillance les dépendances propres à ce nœud. Par exemple, si vous choisissez un nœud prévisible, la visionneuse met également en surbrillance chacun des nœuds permettant de prédire le nœud prévisible.  
  
 La légende en bas de la visionneuse associe des codes de couleur au type de dépendance apparaissant dans le graphique. Par exemple, lorsque vous sélectionnez un nœud prévisible, le nœud prévisible est surligné en turquoise et les nœuds permettant de prédire le nœud sélectionné sont surlignés en orange.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a>Profils d’attribut  
 L’onglet **Profils d’attribut** affiche des histogrammes dans une grille. Vous pouvez utiliser cette grille pour comparer l’attribut prédictible que vous sélectionnez dans la zone **Prédictible** à tous les autres attributs figurant dans le modèle. Chaque colonne de l'onglet représente un état de l'attribut prévisible. Si l’attribut prédictible possède un grand nombre d’états, vous pouvez modifier le nombre d’états affichés dans l’histogramme à l’aide de l’option **Barres de l’histogramme**. Si le nombre que vous définissez est inférieur au nombre total d'états de l'attribut, les états sont répertoriés par ordre de prise en charge et le reste des états est regroupé dans un compartiment gris unique.  
  
 Pour afficher une légende d’exploration de données qui associe les couleurs de l’histogramme aux états d’un attribut, cochez la case **Afficher la légende** . La légende d'exploration de données affiche également la distribution des cas pour chaque paire attribut/valeur que vous sélectionnez.  
  
 Pour copier le contenu de la grille en tant que table HTML dans le Presse-papiers, cliquez avec le bouton droit sur l’onglet **Profils d’attribut** puis sélectionnez **Copier**.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a> Caractéristiques d'attribut  
 Pour utiliser l’onglet **Caractéristiques d’attribut** , sélectionnez un attribut prédictible dans la liste **Attribut** , puis sélectionnez un état de l’attribut sélectionné dans la liste **Valeur** . Quand vous définissez ces variables, l’onglet **Caractéristiques d’attribut** affiche les états des attributs qui sont associés au cas sélectionné de l’attribut sélectionné. Les attributs sont triés par ordre d'importance.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a> Discrimination d'attribut  
 Pour utiliser l’onglet **Discrimination d’attribut** , sélectionnez un attribut prédictible et deux de ses états dans les listes **Attribut**, **Valeur 1**et **Valeur 2** . La grille de l’onglet **Discrimination d’attribut** affiche alors les informations suivantes dans des colonnes :  
  
 **Attribut**  
 Répertorie les autres attributs du jeu de données contenant un état qui privilégie fortement l'un des états de l'attribut prévisible.  
  
 **Valeurs**  
 Affiche la valeur de l’attribut dans la colonne**Attribut**.  
  
 **Privilégie\<value 1>**  
 Affiche une barre de couleur qui indique à quel degré la valeur d’attribut favorise la valeur d’attribut prédictible affichée dans **Valeur 1**.  
  
 **Privilégie\<value 2>**  
 Affiche une barre de couleur qui indique à quel degré la valeur d’attribut favorise la valeur d’attribut prédictible affichée dans **Valeur 2**.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme Microsoft Naive Bayes](microsoft-naive-bayes-algorithm.md)   
 [Tâches de la visionneuse de modèle d’exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)   
 [Outils d’exploration de données](data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](data-mining-model-viewers.md)  
  
  
