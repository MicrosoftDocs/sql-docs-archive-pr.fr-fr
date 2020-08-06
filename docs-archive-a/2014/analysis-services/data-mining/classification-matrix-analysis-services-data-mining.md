---
title: Matrice de classification (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- displaying mining accuracy
- confusion matrix [data mining]
- classification matrix [Analysis Services]
- accuracy testing [data mining]
ms.assetid: 5c12f202-2ed9-41fa-bee2-0f7ab3ff058a
author: minewiskan
ms.author: owend
ms.openlocfilehash: d880eb48e249d5e26611765fea7c9bd3b3e2216f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612635"
---
# <a name="classification-matrix-analysis-services---data-mining"></a>Matrice de classification (Analysis Services - Exploration de données)
  Une *matrice de classification* trie tous les cas du modèle en catégories, en déterminant si la valeur prédite correspondait à la valeur réelle. Tous les cas dans chaque catégorie sont ensuite comptés et les totaux sont affichés dans la matrice. La matrice de classification est un outil standard d’évaluation des modèles statistiques et est parfois appelée *matrice de confusion*.  
  
 Le graphique qui est créé quand vous choisissez l’option **Matrice de classification** compare les valeurs réelles aux valeurs prédites pour chaque état prédit que vous spécifiez. Les lignes de la matrice représentent les valeurs prédites pour le modèle, tandis que les colonnes représentent les valeurs réelles. Les catégories utilisées dans l’analyse sont *faux positif*, *vrai positif*, *faux négatif*et *vrai négatif*  
  
 Une matrice de classification est un outil important pour évaluer les résultats d'une prédiction car elle facilite la compréhension et explique les effets des prédictions incorrectes. En consultant le montant et les pourcentages de chaque cellule de cette matrice, vous pouvez rapidement consulter la fréquence à laquelle le modèle a effectué des prédictions précises.  
  
 Cette section explique comment créer une matrice de classification et comment interpréter les résultats.  
  
## <a name="understanding-the-classification-matrix"></a>Fonctionnement de la matrice de classification  
 Prenons le modèle que vous avez créé dans le cadre du didacticiel sur l'exploration de données de base. Le modèle [TM_DecisionTree], qui sert à créer une campagne de publipostage ciblée, peut être utilisé pour prédire quels clients sont les plus susceptibles d'acheter un vélo. Pour tester l'utilité estimée de ce modèle, vous utilisez un jeu de données pour lequel les valeurs de l'attribut de résultats, [Bike Buyer], sont déjà connues. En général, vous utiliseriez le jeu de données de test que vous avez mis de côté lors de la création de la structure d'exploration de données utilisée pour l'apprentissage du modèle.  
  
 Il existe deux effets possibles : oui (le client est susceptible d'acheter un vélo), et non (le client n'achètera probablement pas de vélo). Par conséquent, la matrice de classification obtenue est relativement simple.  
  
## <a name="interpreting-the-results"></a>Interprétation des résultats  
 Le tableau suivant présente la matrice de classification pour le modèle TM_DecisionTree. N'oubliez pas que pour cet attribut prédictible, 0 signifie Non et 1 Oui.  
  
|Prédite|0 (Réel)|1 (Réel)|  
|---------------|------------------|------------------|  
|0|362|144|  
|1|121|373|  
  
 La première cellule de résultat, qui contient la valeur 362, indique le nombre de *vrais positifs* pour la valeur 0. Étant donné que 0 indique que le client n'a pas acheté de vélo, cette statistique vous dit que le modèle a prédit la valeur correcte pour les non-acheteurs de vélo dans 362 cas.  
  
 La cellule immédiatement au-dessous de celle-ci, qui contient la valeur 121, vous indique le nombre de *faux positifs*, c’est-à-dire le nombre de fois que le modèle a prédit à tort qu’une personne achèterait un vélo.  
  
 La cellule qui contient la valeur 144 indique le nombre de *faux positifs* pour la valeur 1. Étant donné que 1 signifie que le client a acheté un vélo, cette statistique vous indique que dans 144 cas, le modèle a prédit qu'une personne n'achèterait pas de vélo alors qu'en réalité, elle l'a fait.  
  
 Enfin, la cellule qui contient la valeur 373 indique le nombre de vrais positifs pour la valeur cible 1. En d'autres termes, dans 373 cas, le modèle a prédit correctement qu'une personne achèterait un vélo.  
  
 En additionnant les valeurs dans les cellules qui sont adjacentes en diagonale, vous pouvez déterminer la précision globale du modèle. Une diagonale vous indique le nombre total de prédictions exactes, et l'autre diagonale vous indique le nombre total de prédictions erronées.  
  
### <a name="using-multiple-predictable-values"></a>Utilisation de plusieurs valeurs prévisibles  
 Le cas [Bike Buyer] est particulièrement simple à interpréter car il n'y a que deux valeurs possibles. Lorsque l'attribut prédictible a plusieurs valeurs possibles, la matrice de classification ajoute une nouvelle colonne pour chaque valeur réelle possible, puis compte le nombre de correspondances pour chaque valeur prédite. Le tableau suivant présente les résultats sur un modèle différent, où trois valeurs (0, 1, 2) sont possibles.  
  
|Prédite|0 (Réel)|1 (Réel)|2 (Réel)|  
|---------------|------------------|------------------|------------------|  
|0|111|3|5|  
|1|2|123|17|  
|2|19|0|20|  
  
 Bien que l'ajout de plusieurs colonnes rende la disposition du rapport plus complexe, les détails supplémentaires peuvent être très utiles lorsque vous voulez évaluer le coût cumulé d'une prédiction incorrecte. Pour créer des sommes sur les diagonales ou comparer les résultats de différentes combinaisons de lignes, vous pouvez cliquer sur le bouton **Copier** sous l’onglet **Matrice de classification** et coller le rapport dans Excel. Vous pouvez aussi utiliser un client tel que le Client d’exploration de données pour Excel, qui prend en charge [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures, pour créer, directement dans Excel, un rapport de classification qui inclut des nombres et des pourcentages. Pour plus d’informations, consultez [SQL Server Data Mining](https://go.microsoft.com/fwlink/?LinkID=77733)(en anglais).  
  
## <a name="restrictions-on-the-classification-matrix"></a>Restrictions relatives à la matrice de classification  
 Une matrice de classification peut être utilisée uniquement avec des attributs prédictibles discrets.  
  
 Bien que vous puissiez ajouter plusieurs modèles au moment de sélectionner des modèles sous l’onglet **Sélection d’entrée** du concepteur **Graphique d’analyse de précision de l’exploration de données** , l’onglet **Matrice de classification** présente une matrice distincte pour chaque modèle.  
  
## <a name="related-content"></a>Contenu associé  
 Les rubriques suivantes contiennent davantage d'informations sur la façon dont vous pouvez créer et utiliser des matrices de classification et d'autres graphiques.  
  
|Rubriques|Liens|  
|------------|-----------|  
|Propose une procédure pas à pas permettant de créer un graphique de courbes d'élévation pour le modèle de publipostage ciblé.|[Didacticiel d’exploration de données de base](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [Test de la précision à l’aide de graphiques de courbes d’élévation &#40;Didacticiel sur l’exploration de données de base&#41;](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|Explique les types de graphique associés.|[Graphique de courbes d’élévation &#40;Analysis Services - Exploration de données&#41;](lift-chart-analysis-services-data-mining.md)<br /><br /> [Graphique des bénéfices &#40;Analysis Services - Exploration de données&#41;](profit-chart-analysis-services-data-mining.md)<br /><br /> [Nuage de points &#40;Analysis Services - Exploration de données&#41;](scatter-plot-analysis-services-data-mining.md)|  
|Décrit les utilisations de la validation croisée pour les modèles et les structures d'exploration de données.|[Validation croisée &#40;Analysis Services - Exploration de données&#41;](cross-validation-analysis-services-data-mining.md)|  
|Décrit les étapes permettant de créer des graphiques de courbes d'élévation et d'autres graphiques d'analyse de précision.|[Tâches de test et validation et procédures &#40;exploration des données&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Test et validation &#40;exploration de données&#41;](testing-and-validation-data-mining.md)  
  
  
