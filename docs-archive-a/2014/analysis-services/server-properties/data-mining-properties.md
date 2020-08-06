---
title: Propriétés d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ed1c47faafeb0c680e6afb6f8e509c426760da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710868"
---
# <a name="data-mining-properties"></a>Propriétés de l'exploration de données
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur d'exploration de données répertoriées dans les tableaux suivants. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S’applique à :** Mode serveur multidimensionnel uniquement  
  
## <a name="non-specific-category"></a>Catégorie non spécifique  
 `AllowSessionMiningModels`  
 Propriété booléenne qui indique s'il est possible de créer des modèles d'exploration de données de session.  
  
 La valeur par défaut de cette propriété, False, indique qu'il n'est pas possible de créer des modèles d'exploration de session.  
  
 `AllowAdHocOpenRowsetQueries`  
 Propriété booléenne qui indique si les requêtes OPENROWSET ad hoc sont autorisées.  
  
 La valeur par défaut de cette propriété, False, indique que les requêtes OPENROWSET ne sont pas autorisées pendant une session.  
  
 `AllowedProvidersInOpenRowset`  
 Propriété de type chaîne qui identifie les fournisseurs autorisés dans une clause OPENROWSET. Il s'agit soit d'une liste de ProgID séparés par des virgules, soit de [Tous].  
  
 `MaxConcurrentPredictionQueries`  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie le nombre maximal de requêtes de prédiction simultanées.  
  
## <a name="algorithms-category"></a>Catégorie algorithmes  
 `Microsoft_Association_Rules\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Association_Rules est activé.  
  
 `Microsoft_Clustering\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Clustering est activé.  
  
 `Microsoft_Decision_Trees\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_DecisionTrees est activé.  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Naive_Bayes est activé.  
  
 `Microsoft_Neural_Network\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Neural_Network est activé.  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Sequence_Clustering est activé.  
  
 `Microsoft_Time_Series\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Time_Series est activé.  
  
 `Microsoft_Linear_Regression\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Linear_Regression est activé.  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 Propriété booléenne qui indique si l'algorithme Microsoft_Logistic_Regression est activé.  
  
> [!NOTE]  
>  En plus des propriétés qui définissent les services d'exploration de données disponibles sur le serveur, il existe des propriétés d'exploration de données définissant le comportement d'algorithmes spécifiques. Vous configurez ces propriétés lorsque vous créez un modèle d'exploration de données individuel, pas au niveau serveur. Pour plus d’informations, consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture physique &#40;Analysis Services d’exploration de données&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
