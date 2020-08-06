---
title: Informations techniques de référence sur l’algorithme Microsoft Naive Bayes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614252"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a>Références techniques relatives à l'algorithme MNB (Microsoft Naive Bayes)
  L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme Naive Bayes est un algorithme de classification fourni par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour une utilisation dans la modélisation prédictive. Cet algorithme calcule la probabilité conditionnelle entre les colonnes d'entrée et les colonnes prédictibles, et suppose que les colonnes sont indépendantes. Naive Bayes tire son nom de cette hypothèse d'indépendance.  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a>Implémentation de l'algorithme MNB (Microsoft Naive Bayes)  
 Cet algorithme est informatiquement moins lourd que d’autres algorithmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Ainsi, il est utile pour générer rapidement des modèles d’exploration de données permettant de découvrir les relations entre les colonnes d’entrée et les colonnes prédictibles. L'algorithme prend en considération chaque paire de valeurs d'attribut d'entrée et valeurs d'attribut de sortie.  
  
 La description des propriétés mathématiques du théorème de Bayes n’est pas traitée dans cette documentation. Pour plus d’informations, consultez le document Microsoft Research intitulé [Réseaux bayésiens : connaissance et données statistiques](https://go.microsoft.com/fwlink/?LinkId=207029).  
  
 Pour une description de la façon dont les probabilités dans tous les modèles sont ajustées pour expliquer des valeurs manquantes potentielles, consultez [Valeurs manquantes &#40;Analysis Services - Exploration de données&#41;](missing-values-analysis-services-data-mining.md).  
  
### <a name="feature-selection"></a>Sélection de caractéristiques  
 L’algorithme MNB [!INCLUDE[msCoName](../../includes/msconame-md.md)] effectue une sélection des fonctionnalités automatique pour limiter le nombre de valeurs prises en considération pendant la génération du modèle. Pour plus d’informations, consultez [Sélection des fonctionnalités &#40;Exploration de données&#41;](feature-selection-data-mining.md).  
  
|Algorithm|Méthode d'analyse|Commentaires|  
|---------------|------------------------|--------------|  
|Naive Bayes|Entropie de Shannon<br /><br /> Bayésien avec a priori K2<br /><br /> Équivalent bayésien de Dirichlet avec a priori uniforme (par défaut)|L'algorithme Naive Bayes accepte uniquement les attributs discrets ou discrétisés ; par conséquent, il ne peut pas utiliser le score d'intérêt et de pertinence.|  
  
 L'algorithme est conçu pour réduire le temps de traitement et sélectionner efficacement les attributs qui ont la plus grande importance. Toutefois, vous peut contrôler les données utilisées par l'algorithme en définissant des paramètres comme suit :  
  
-   Pour limiter les valeurs utilisées comme entrées, réduisez la valeur de MAXIMUM_INPUT_ATTRIBUTES.  
  
-   Pour limiter le nombre d'attributs analysés par le modèle, réduisez la valeur de MAXIMUM_OUTPUT_ATTRIBUTES.  
  
-   Pour limiter le nombre de valeurs qui peuvent être prise en considération pour n'importe quel attribut, réduisez la valeur de MINIMUM_STATES.  
  
## <a name="customizing-the-naive-bayes-algorithm"></a>Personnalisation de l'algorithme Naive Bayes  
 L’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) prend en charge plusieurs paramètres qui affectent le comportement, les performances et la précision du modèle d’exploration de données obtenu. Vous pouvez également définir des indicateurs de modélisation sur les colonnes du modèle pour contrôler le mode de traitement des données ou sur la structure d'exploration de données por spécifier la gestion des valeurs manquantes ou Null.  
  
### <a name="setting-algorithm-parameters"></a>Définition des paramètres de l'algorithme  
 L'algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) prend en charge plusieurs paramètres qui affectent les performances et la précision du modèle d'exploration de données obtenu. La table ci-dessous décrit chaque paramètre.  
  
 *MAXIMUM_INPUT_ATTRIBUTES*  
 Spécifie le nombre maximal d'attributs d'entrée que l'algorithme peut traiter avant d'appeler la sélection des fonctionnalités. La valeur 0 désactive la sélection des fonctionnalités pour les attributs d'entrée.  
  
 La valeur par défaut est 255.  
  
 *MAXIMUM_OUTPUT_ATTRIBUTES*  
 Spécifie le nombre maximal d'attributs de sortie que l'algorithme peut traiter avant d'appeler la sélection des fonctionnalités. La valeur 0 désactive la sélection des fonctionnalités pour les attributs de sortie.  
  
 La valeur par défaut est 255.  
  
 *MINIMUM_DEPENDENCY_PROBABILITY*  
 Spécifie la probabilité de dépendance minimale entre les attributs d'entrée et les attributs de sortie. Cette valeur sert à limiter la taille du contenu généré par l'algorithme. Cette propriété peut être définie entre 0 et 1. Les plus grandes valeurs réduisent le nombre d'attributs dans le contenu du modèle.  
  
 La valeur par défaut est 0.5.  
  
 *MAXIMUM_STATES*  
 Spécifie le nombre maximal d'états d'attribut que l'algorithme prend en charge. Si le nombre d’États d’un attribut est supérieur au nombre maximal d’États, l’algorithme utilise les États les plus populaires de l’attribut et traite les autres États comme étant manquants.  
  
 La valeur par défaut est 100.  
  
### <a name="modeling-flags"></a>Indicateurs de modélisation  
 L'algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) prend en charge les indicateurs de modélisation suivants. Lorsque vous créez la structure d'exploration de données ou le modèle d'exploration de données, vous définissez des indicateurs de modélisation pour spécifier la façon dont les valeurs de chaque colonne sont gérées pendant l'analyse. Pour plus d’informations, consultez [Indicateurs de modélisation &#40;Exploration de données&#41;](modeling-flags-data-mining.md).  
  
|Indicateur de modélisation|Description|  
|-------------------|-----------------|  
|MODEL_EXISTENCE_ONLY|Signifie que la colonne sera considérée comme ayant deux états possibles : manquant et existant. Une valeur NULL est une valeur manquante.<br /><br /> S'applique à la colonne de modèle d'exploration de données.|  
|NOT NULL|Indique que la colonne ne peut pas contenir de valeur Null. Une erreur est générée si Analysis Services rencontre une valeur NULL au cours de l'apprentissage du modèle.<br /><br /> S'applique à la colonne de structure d'exploration de données.|  
  
## <a name="requirements"></a>Spécifications  
 Un modèle d'arbre Naive Bayes doit contenir une colonne clé, au moins un attribut prédictible et au moins un attribut d'entrée. Aucun attribut ne peut être continu ; si vos données contiennent des données numériques continues, elles seront ignorées ou discrétisées.  
  
### <a name="input-and-predictable-columns"></a>Colonnes d'entrée et prédictibles  
 L’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) prend en charge les colonnes d’entrée et les colonnes prédictibles répertoriées dans le tableau suivant. Pour plus d’informations sur la signification des types de contenu en cas d’utilisation dans un modèle d’exploration de données, consultez [Types de contenu &#40;Exploration de données&#41;](content-types-data-mining.md).  
  
|Colonne|Types de contenu|  
|------------|-------------------|  
|Attribut d'entrée|Cyclique, Discret, Discrétisé, Clé, Table et Trié|  
|Attribut prédictible|Cyclique, Discret, Discrétisé, Table et Trié|  
  
> [!NOTE]  
>  Les types de contenu Cyclique et Trié sont pris en charge, mais l'algorithme les traite comme des valeurs discrètes et n'effectue pas de traitement spécial.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme Microsoft Naive Bayes](microsoft-naive-bayes-algorithm.md)   
 [Exemples de requêtes de modèle Naive Bayes](naive-bayes-model-query-examples.md)   
 [Contenu du modèle d’exploration de données pour les modèles Naive Bayes &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
