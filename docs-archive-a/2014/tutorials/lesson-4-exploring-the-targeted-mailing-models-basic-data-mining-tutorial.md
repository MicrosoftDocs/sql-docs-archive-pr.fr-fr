---
title: 'Leçon 4 : exploration des modèles de publipostage ciblés (didacticiel sur l’exploration de données de base) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8659350b126164e06550acdbecec04bb07499c55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704455"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a>Leçon 4 : Exploration des modèles de publipostage ciblé (Didacticiel sur l'exploration de données de base)
  Une fois que les modèles inclus dans votre projet sont traités, vous pouvez les explorer pour rechercher des tendances intéressantes. Étant donné que les motifs peuvent être complexes et difficiles en examinant simplement des nombres, l'exploration de données SQL Server fournit des outils visuels qui vous aident à analyser les données et à comprendre les règles et les relations que les algorithmes ont découvert dans les données. Utilisez également un large éventail de tests de précision pour valider votre dataset ou découvrir quel modèle est le plus performant avant de le déployer.  
  
 Lorsque vous utilisez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour explorer vos modèles, chaque modèle que vous avez créé est listé dans l’onglet **visionneuse de modèle d’exploration** de données du concepteur d’exploration de données. Vous pouvez utiliser les visionneuses pour explorer les modèles. Ces visionneuses sont également disponibles dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Chaque algorithme que vous avez utilisé pour créer un modèle dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retourne un type différent de résultat. Par conséquent, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit des visionneuses personnalisées pour chaque type de modèle d'apprentissage automatique.  
  
 Si vous souhaitez obtenir des détails, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit également une visionneuse HTML, appelée **visionneuse de l’arborescence de contenu générique**, qui affiche des informations détaillées sur les données du modèle et les modèles trouvés, dans un format semi-tabulaire. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
 Dans cette leçon, vous allez examiner les résultats de vos trois modèles. Chaque type de modèle est basé sur un algorithme différent et fournit un aperçu différent des données.  
  
-   Le modèle Decision Tree vous indique les facteurs qui influencent l'achat de vélos.  
  
-   Le modèle Clustering regroupe vos clients selon des attributs qui incluent leur comportement d'achat de vélo et d'autres attributs sélectionnés.  
  
-   Le modèle Naive Bayes vous permet d'explorer la relation entre différents attributs.  
  
 Consultez les rubriques suivantes pour en savoir plus sur les visionneuses de modèles d'exploration de données.  
  
-   [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle de clustering &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle Naive Bayes &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 Les trois modèles peuvent être affichés à l’aide de la **visionneuse de l’arborescence de contenu générique**, pour extraire des formules, des valeurs de données, etc.  
  
## <a name="first-task-in-lesson"></a>Première tâche de la leçon  
 [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
 [Leçon 3 : Ajout et traitement des modèles](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 5 : tester les modèles &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d’exploration de données et procédures](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Visionneuses de modèle d’exploration de données](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
