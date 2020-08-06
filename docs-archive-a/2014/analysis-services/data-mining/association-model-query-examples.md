---
title: Exemples de requêtes de modèle d’association | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- content queries [DMX]
ms.assetid: 68b39f5c-c439-44ac-8046-6f2d36649059
author: minewiskan
ms.author: owend
ms.openlocfilehash: a19eb2302639c7f13d48a8778969bbeca4fee18d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613703"
---
# <a name="association-model-query-examples"></a>Exemples de requêtes de modèle d'association
  Lorsque vous créez une requête sur un modèle d'exploration de données, vous pouvez soit créer une requête de contenu qui fournit des détails sur les règles et les jeux d'éléments découverts au cours de l'analyse, soit créer une requête de prédiction qui utilise les associations découvertes dans les données pour faire des prédictions. En général, pour un modèle d'association, les prédictions sont basées sur des règles et peuvent être utilisées pour faire des recommandations, tandis que les interrogations sur du contenu explorent la relation entre les jeux d'éléments. Vous pouvez aussi récupérer des métadonnées sur le modèle.  
  
 Cette section explique comment créer ces types de requêtes pour les modèles basés sur l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).  
  
 **Requêtes de contenu**  
  
 [Obtention de données de métadonnées de modèle avec DMX](#bkmk_Query1)  
  
 [Obtention de métadonnées de l'ensemble de lignes de schéma](#bkmk_Query2)  
  
 [Récupération des paramètres d'origine pour le modèle](#bkmk_Query3)  
  
 [Récupération d'une liste de jeux d'éléments et produits](#bkmk_Query4)  
  
 [Retour de 10 principaux jeux d'éléments](#bkmk_Query5)  
  
 **Requêtes de prédiction**  
  
 [Prédire des éléments associés](#bkmk_Query6)  
  
 [Identification de la confiance pour les jeux d'éléments connexes](#bkmk_Query7)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> Recherche d'informations sur le modèle  
 Tous les modèles d'exploration de données exposent le contenu appris par l'algorithme en fonction d'un schéma standardisé, appelé l'ensemble de lignes de schéma du modèle d'exploration de données. Vous pouvez créer des requêtes sur l'ensemble de lignes de schéma du modèle d'exploration de données en utilisant des instructions DMX (Data Mining Extensions) ou des procédures stockées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez également interroger directement les ensemble de lignes de schéma en tant que tables système en utilisant une syntaxe de type SQL.  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> Exemple de requête 1 : obtention des métadonnées du modèle à l'aide de DMX  
 La requête suivante retourne les métadonnées de base sur le modèle d'association, `Association`, telles que le nom du modèle, la base de données où le modèle est stocké et le nombre de nœuds enfants dans le modèle. Cette requête utilise une requête de contenu DMX pour récupérer les métadonnées du nœud parent du modèle:  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  Vous devez mettre le nom de la colonne, CHILDREN_CARDINALITY, entre parenthèses pour le distinguer du mot clé réservé MDX du même nom.  
  
 Résultats de l'exemple :  
  
|||  
|-|-|  
|MODEL_CATALOG|Association Test|  
|MODEL_NAME|Association|  
|NODE_CAPTION|Association Rules Model|  
|NODE_SUPPORT|14879|  
|CHILDREN_CARDINALITY|942|  
|NODE_DESCRIPTION|Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523|  
  
 Pour connaître la signification de ces colonnes dans un modèle d’association, consultez [Contenu du modèle d’exploration de données pour les modèles d’association &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
 [Retour au début](#bkmk_top2)  
  
###  <a name="sample-query-2-getting-additional-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> Exemple de requête 2 : obtention de métadonnées supplémentaires à partir de l'ensemble de lignes de schéma  
 En interrogeant l'ensemble de lignes de schéma d'exploration de données, vous pouvez obtenir les mêmes informations que celles retournées par une requête de contenu DMX. Toutefois, l'ensemble de lignes de schéma fournit quelques colonnes supplémentaires, telles que la date à laquelle le modèle a été traité pour la dernière fois, la structure d'exploration de données et le nom de la colonne utilisée comme attribut prévisible.  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, SERVICE_NAME, PREDICTION_ENTITY,   
MINING_STRUCTURE, LAST_PROCESSED  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 Résultats de l'exemple :  
  
|||  
|-|-|  
|MODEL_CATALOG|Adventure Works DW Multidimensional 2012|  
|MODEL_NAME|Association|  
|SERVICE_NAME|Association Rules Model|  
|PREDICTION_ENTITY|v Assoc Seq Line Items|  
|MINING_STRUCTURE|Association|  
|LAST_PROCESSED|9/29/2007 10:21:24 PM|  
  
 [Retour au début](#bkmk_top2)  
  
###  <a name="sample-query-3-retrieving-original-parameters-for-model"></a><a name="bkmk_Query3"></a> Exemple de requête 3 : récupération des paramètres d'origine pour le modèle  
 La requête suivante retourne une colonne unique qui contient des détails sur la configuration des paramètres utilisée au moment de la création du modèle.  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 Résultats de l'exemple :  
  
 MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4  
  
 [Retour au début](#bkmk_top2)  
  
## <a name="finding-information-about-rules-and-itemsets"></a>Recherche d'informations sur les règles et les jeux d'éléments  
 En général, un modèle d'association sert à deux choses : découvrir des informations sur les jeux d'éléments fréquents et récupérer des détails sur des règles et des jeux d'éléments particuliers. Par exemple, vous souhaitez peut-être récupérer une liste des règles dont le score indique qu'elles sont particulièrement intéressantes ou créer une liste des jeux d'éléments les plus courants. Vous récupérez de telles informations en utilisant une requête de contenu DMX. Vous pouvez aussi parcourir ces informations à l’aide de la **visionneuse d’associations Microsoft**.  
  
###  <a name="sample-query-4-retrieving-list-of-itemsets-and-products"></a><a name="bkmk_Query4"></a> Exemple de requête 4 : récupération d'une liste de jeux d'éléments et de produits  
 La requête suivante récupère tous les jeux d'éléments, ainsi qu'une table imbriquée qui répertorie les produits inclus dans chaque jeu d'éléments. La colonne NODE_NAME contient l'ID unique du jeu d'éléments dans le modèle, tandis que la colonne NODE_CAPTION fournit une description textuelle des éléments. Dans cet exemple, la table imbriquée est aplatie, de telle sorte qu'un jeu d'éléments contenant deux produits génère deux lignes dans les résultats. Vous pouvez omettre le mot clé FLATTENED si votre client prend en charge des données hiérarchiques.  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
NODE_PROBABILITY, NODE_SUPPORT,  
(SELECT ATTRIBUTE_NAME FROM NODE_DISTRIBUTION) as PurchasedProducts  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 Résultats de l'exemple :  
  
|||  
|-|-|  
|NODE_NAME|37|  
|NODE_CAPTION|Sport-100 = Existing|  
|NODE_PROBABILITY|0.291283016331743|  
|NODE_SUPPORT|4334|  
|PURCHASEDPRODUCTS.ATTRIBUTE_NAME|v Assoc Seq Line Items(Sport-100)|  
  
 [Retour au début](#bkmk_top2)  
  
###  <a name="sample-query-5-returning-top-10-itemsets"></a><a name="bkmk_Query5"></a> Exemple de requête 5 : retour des 10 premiers jeux d'éléments  
 Cet exemple montre comment utiliser une partie des fonctions de regroupement et de classement fournies par défaut par DMX. La requête retourne les 10 premiers jeux d'éléments issus du classement selon la prise en charge pour chaque nœud. Notez que vous n'avez pas besoin de regrouper les résultats explicitement comme vous le feriez dans Transact-SQL ; toutefois, vous pouvez utiliser une seule fonction d'agrégation dans chaque requête.  
  
```  
SELECT TOP 10 (NODE_SUPPORT),NODE_NAME, NODE_CAPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 Résultats de l'exemple :  
  
|||  
|-|-|  
|NODE_SUPPORT|4334|  
|NODE_NAME|37|  
|NODE_CAPTION|Sport-100 = Existing|  
  
 [Retour au début](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a>Exécution de prédictions à l'aide du modèle  
 Un modèle de règles d'association est souvent utilisé pour générer recommandations qui sont basées sur les corrélations découvertes dans les jeux d'éléments. Par conséquent, lorsque vous créez une requête de prédiction basée sur un modèle de règles d'association, vous utilisez en général les règles dans le modèle pour faire des estimations basées sur les nouvelles données.  [PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) est la fonction qui retourne des recommandations et possède plusieurs arguments que vous pouvez utiliser pour personnaliser les résultats de la requête.  
  
 Les requêtes sur un modèle d'association peuvent aussi être utiles pour retourner par exemple la confiance pour des règles et des jeux d'éléments afin de comparer l'efficacité de différentes stratégies de ventes croisées. Les exemples suivants illustrent comment créer de telles requêtes.  
  
###  <a name="sample-query-6-predicting-associated-items"></a><a name="bkmk_Query6"></a> Exemple de requête 6 : prédiction d'éléments associés  
 Cet exemple utilise le modèle d’association créé dans le [Didacticiel sur l’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). Il montre comment créer une requête de prédiction qui indique les produits à recommander à un client ayant acheté un produit particulier. Ce type de requête, dans lequel vous fournissez des valeurs au modèle dans une instruction `SELECT...UNION`, est appelé « requête singleton ». La colonne du modèle prévisible qui correspond aux nouvelles valeurs étant une table imbriquée, vous devez utiliser une clause `SELECT` pour mapper la nouvelle valeur à la colonne de table imbriquée, `[Model]`, et une autre clause `SELECT` pour mapper la colonne de table imbriquée à la colonne de niveau de cas, `[v Assoc Seq Line Items]`. L'ajout du mot clé INCLUDE-STATISTICS à la requête vous permet de voir la probabilité et la prise en charge pour les recommandations.  
  
```  
SELECT PredictAssociation([Association].[vAssocSeqLineItems],INCLUDE_STATISTICS, 3)  
FROM [Association]  
NATURAL PREDICTION JOIN   
(SELECT  
(SELECT 'Classic Vest' as [Model])  
AS [v Assoc Seq Line Items])  
AS t  
```  
  
 Résultats de l'exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283|0.252696|  
|Water Bottle|2866|0.19262|0.175205|  
|Patch kit|2113|0.142012|0.132389|  
  
 [Retour au début](#bkmk_top2)  
  
###  <a name="sample-query-7-determining-confidence-for-related-itemsets"></a><a name="bkmk_Query7"></a> Exemple de requête 7 : identification de la confiance pour les jeux d'éléments connexes  
 Si les règles sont utiles pour générer des recommandations, les jeux d'éléments sont plus intéressants pour effectuer une analyse plus poussée des séquences dans le jeu de données. Par exemple, si vous n'êtes pas satisfait de la recommandation retournée par la requête de l'exemple précédent, vous pouvez examiner d'autres jeux d'éléments qui contiennent le produit A pour savoir avec plus de certitude si le produit A est un accessoire que les gens ont tendance à acheter avec tous les types de produits ou si le produit A est en forte corrélation avec les achats de produits particuliers. Le moyen le plus simple d'explorer ces relations consiste à filtrer les jeux d'éléments dans la Visionneuse d'associations [!INCLUDE[msCoName](../../includes/msconame-md.md)] ; toutefois, vous pouvez récupérer les mêmes informations avec une requête.  
  
 L'exemple de requête suivant retourne tous les jeux d'éléments qui incluent l'élément Water Bottle, y compris l'élément unique Water Bottle.  
  
```  
SELECT TOP 100 FROM   
(  
SELECT FLATTENED NODE_CAPTION, NODE_SUPPORT,   
(SELECT ATTRIBUTE_NAME from NODE_DISTRIBUTION  
WHERE ATTRIBUTE_NAME = 'v Assoc Seq Line Items(Water Bottle)') as D  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
) AS Items  
WHERE [D.ATTRIBUTE_NAME] <> NULL  
ORDER BY NODE_SUPPORT DESC  
```  
  
 Résultats de l'exemple :  
  
|NODE_CAPTION|NODE_SUPPORT|D.ATTRIBUTE_NAME|  
|-------------------|-------------------|-----------------------|  
|Water Bottle = Existing|2866|v Assoc Seq Line Items(Water Bottle)|  
|Mountain Bottle Cage = Existing, Water Bottle = Existing|1136|v Assoc Seq Line Items(Water Bottle)|  
|Road Bottle Cage = Existing, Water Bottle = Existing|1068|v Assoc Seq Line Items(Water Bottle)|  
|Water Bottle = Existing, Sport-100 = Existing|734|v Assoc Seq Line Items(Water Bottle)|  
  
 Cette requête retourne les deux lignes de la table imbriquée qui correspondent aux critères, et toutes les lignes de l’extérieur ou de la table de cas. Par conséquent, vous devez ajouter une condition qui élimine les lignes de table de cas dont le nom d'attribut cible a la valeur Null.  
  
 [Retour au début](#bkmk_top2)  
  
## <a name="function-list"></a>Liste de fonctions  
 Tous les algorithmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] prennent en charge un ensemble commun de fonctions. Toutefois, l'algorithme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association prend en charge les fonctions supplémentaires répertoriées dans le tableau ci-dessous.  
  
|||  
|-|-|  
|Fonction de prédiction|Usage|  
|[IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx)|Détermine si un nœud est un enfant d'un autre nœud dans le graphique de réseau neuronal.|  
|[IsInNode &#40;DMX&#41;](/sql/dmx/isinnode-dmx)|Indique si le nœud spécifié contient le cas courant.|  
|[PredictAdjustedProbability &#40;DMX&#41;](/sql/dmx/predictadjustedprobability-dmx)|Retourne la probabilité pondérée.|  
|[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx)|Prédit l'appartenance à un dataset associatif.|  
|[PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)|Retourne une table des valeurs associées à la valeur prédite actuelle.|  
|[PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx)|Retourne Node_ID pour chaque cas.|  
|[PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx)|Retourne la probabilité pour la valeur prédite.|  
|[PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx)|Retourne la valeur de support pour un état spécifié.|  
|[PredictVariance &#40;DMX&#41;](/sql/dmx/predictvariance-dmx)|Retourne la variance de la valeur prédite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme d’association Microsoft](microsoft-association-algorithm.md)   
 [Référence technique de l’algorithme Microsoft Association](microsoft-association-algorithm-technical-reference.md)   
 [Contenu du modèle d’exploration de données pour les modèles d’association &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
