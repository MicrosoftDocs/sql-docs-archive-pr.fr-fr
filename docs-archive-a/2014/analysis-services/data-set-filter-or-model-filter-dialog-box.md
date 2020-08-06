---
title: Boîte de dialogue filtre de jeu de données ou filtre de modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702151"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a>Boîte de dialogue Filtre de jeu de données ou Filtre de modèle
  Cette boîte de dialogue vous permet de générer les filtres que vous pouvez appliquer à un jeu de données.  Le jeu de données peut être un jeu de données externes utilisé pour le test ou il peut s'agir des données de cas d'un modèle d'exploration de données. Le nom de la boîte de dialogue change selon que le filtre concerne un jeu de données externes ou un modèle d'exploration de données.  
  
 Si vous appliquez le filtre à un nouveau jeu de données, le modèle d'exploration de données est évalué en utilisant uniquement les cas du jeu de données qui remplissent les conditions. Si vous appliquez le filtre au modèle d'exploration de données lui-même, l'apprentissage et le test du modèle seront effectués en utilisant uniquement les cas du jeu de données de test existant qui remplissent les critères de filtre.  
  
-   La boîte de dialogue **Filtre de jeu de données** est disponible sous l’onglet **Sélection d’entrée** du concepteur **Graphique d’analyse de précision de l’exploration de données** .  
  
-   La boîte de dialogue **Filtre de modèle** est disponible sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données.  
  
-   La grille **Conditions** contient des colonnes dans lesquelles vous pouvez spécifier un nom de table ou de colonne, un opérateur et des valeurs cibles. L'utilisation de cette grille permet de créer en fait une clause WHERE.  
  
> [!TIP]  
>  Pour tester la précision sur un sous-ensemble des données d’apprentissage d’origine, vous pouvez ajouter la vue de source de données utilisée pour définir le jeu d’apprentissage en tant que données de test externes, puis ajouter des conditions dans la grille **Filtre de jeu de données**.  
  
 **Pour plus d’informations :** [Test et validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Options  
 **Conditions**  
 Affiche des noms de table, suivis de noms de colonne avec des conditions.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Et/ou**|Choisissez un opérateur pour joindre plusieurs conditions.|  
|**Colonne de la structure d'exploration de données**|Cliquez pour sélectionner une source de données, puis cliquez sur des lignes consécutives dans la grille pour ajouter des colonnes de la source de données.<br /><br /> La première ligne de la grille spécifie la vue de source de données. Une fois que vous avez sélectionné une vue de source de données, la zone **Colonne de la structure d’exploration de données** affiche une icône de table et le champ **Valeur** affiche la combinaison de tous les critères que vous avez définis pour cette source de données.<br /><br /> Une fois que vous avez sélectionné une source de données, la zone **Colonne de la structure d’exploration de données** propose une liste déroulante de colonnes individuelles contenues dans la source de données.|  
|**Opérateur**|Sélectionnez un opérateur dans la liste.|  
|**Valeur**|Pour les tables, le champ **Valeur** affiche la combinaison de tous les filtres appliqués à la source de données. Vous pouvez également cliquer sur le bouton Générer **(...)** à droite de la zone de texte pour ouvrir la boîte de dialogue **filtre** et générer une condition.|  
  
 **Expression**  
 Affiche l'ensemble de critères que vous avez définis à l'aide de la grille.  
  
 **Modifier la requête**  
 Modifie le mode de modification de filtre afin que vous puissiez directement taper une expression de filtre dans la zone de texte **Expression** .  
  
> [!NOTE]  
>  Une fois que vous avez apporté des modifications manuelles à l’expression de filtre, vous ne pouvez pas revenir au mode de modification de grille, même après avoir enregistré l’expression dans la zone **expression de filtre** sous l’onglet **sélection d’entrée** . Si vous souhaitez générer une expression à l’aide de la grille, vous devez supprimer l’expression de filtre existante et recommencer.  
  
 **Rétablir les modifications apportées à la requête**  
 Rétablit l'état précédent de la grille et annule toutes les modifications apportées à l'expression de filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de test et de validation et &#40;d’exploration de données&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Concepteur graphique d’analyse de précision de l’exploration de données &#40;&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
