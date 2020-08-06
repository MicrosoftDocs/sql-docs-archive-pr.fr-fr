---
title: Choisir un type de graphique d’exactitude et définir des options de graphique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33c2b5e8a1e228a86328ef6df1b636742d3614ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604302"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a>Choisir un type de graphique d'analyse de précision et définir des options de graphique
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]fournit plusieurs méthodes pour déterminer la validité de vos modèles d’exploration de données. Le type de graphique d'analyse de précision que vous pouvez créer pour chaque modèle ou structure dépend des facteurs suivants :  
  
-   Le type d'algorithme utilisé pour créer le modèle  
  
-   Le type de données de l'attribut prédictible  
  
-   Le nombre d'attributs prédictibles à mesurer  
  
 Cette rubrique fournit une vue d'ensemble des différents graphiques d'analyse de précision.  
  
 **Remarque** Les graphiques et leurs définitions ne sont pas enregistrés. Si vous fermez la fenêtre qui contient un graphique, vous devez créer à nouveau le graphique.  
  
## <a name="accuracy-chart-types"></a>Types de graphiques d'analyse de précision  
 En fonction du type de graphique que vous choisissez, vous avez la possibilité de configurer d'autres options, de parcourir le graphique ou de copier le graphique dans le Presse-papiers et de travailler avec les données dans Excel.  
  
#### <a name="lift-chart"></a>Graphique de courbes d’élévation  
 Une fois que vous avez configuré les options des modèles et les données de test, cliquez sur l’onglet **Graphique de courbes d’élévation** pour afficher les résultats. Vous pouvez également copier le graphique dans le Presse-papiers, ou afficher les détails de courbes de tendance ou de points de données individuels dans la légende d'exploration de données.  
  
#### <a name="profit-chart"></a>Graphique des bénéfices  
 Une fois que vous avez configuré les options des modèles et les données de test, cliquez sur l’onglet **Graphique de courbes d’élévation** , sélectionnez **Graphique des bénéfices** dans la liste **Type de graphique** pour définir des options de graphique des bénéfices, puis cliquez sur **OK** pour afficher les résultats.  
  
 Vous pouvez utiliser la boîte de dialogue **Paramètres du graphique des bénéfices** autant de fois que vous le souhaitez pour essayer différentes options de coût et réafficher le graphique. La légende d'exploration de données contient des informations détaillées sur les bénéfices estimés pour chaque modèle. Vous pouvez également copier le graphique et le contenu de la légende d'exploration de données dans le Presse-papiers pour les utiliser dans Excel.  
  
#### <a name="scatter-plot"></a>Nuage de points  
 Si vous avez sélectionné le type de modèle approprié, quand vous cliquez sur l’onglet **Graphique de courbes d’élévation** , le type de graphique est défini automatiquement sur **Nuage de points** et un nuage de points s’affiche. Aucune configuration supplémentaire n'est possible. Vous pouvez également copier le graphique dans le Presse-papiers et coller le graphique en tant que graphique dans Excel ou une autre application.  
  
#### <a name="classification-matrix"></a>Matrice de classification  
 Pour une matrice de classification, utilisez l’onglet **Sélection d’entrée** pour choisir les modèles et les données de test, puis cliquez sur l’onglet **Matrice de classification** pour afficher les résultats.  
  
 Le contenu d'une matrice de classification est identique pour tous les types de modèles et ne peut pas être configuré. Vous pouvez copier les données du graphique dans le Presse-papiers, puis les utiliser dans Excel.  
  
#### <a name="cross-validation-report"></a>Rapport de validation croisée  
 Pour un rapport de validation croisée, après avoir sélectionné une structure d’exploration de données ou un modèle d’exploration de données dans l’Explorateur de solutions, cliquez sur l’onglet **Validation croisée** , configurez toutes les options pertinentes, puis cliquez sur **Obtenir les résultats** pour générer le rapport. Aucune configuration supplémentaire n'est possible.  
  
 Le format du rapport de validation croisée est le même pour tous les types de modèles, et ne peut pas être configuré. Toutefois, le contenu du rapport diffère en fonction du type de modèle que vous analysez et du type de données de l'attribut prévisible. Vous pouvez également copier les résultats du rapport dans le Presse-papiers et utiliser les données dans Excel.  
  
  
