---
title: 'Leçon 2 : ajout de modèles d’exploration de données à la structure d’exploration de données vélo Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702212"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>Leçon 2 : Ajout de modèles d’exploration de données à la structure d’exploration de données Bike Buyer
  Dans cette leçon, vous allez ajouter deux modèles d’exploration de données à la structure d’exploration de données Bike Buyer que vous avez créée [leçon 1 : création de la structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md). Vous pourrez utiliser ces modèles pour explorer des données avec l'un et créer des tâches de prédiction avec l'autre.  
  
 Pour découvrir comment les clients potentiels peuvent être catégorisés par leurs caractéristiques, vous allez créer un modèle d’exploration de données basé sur l' [algorithme de clustering Microsoft](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md). Au cours d'une autre leçon, vous découvrirez comment cet algorithme recherche des clusters de clients partageant les mêmes caractéristiques. Par exemple, vous découvrirez peut-être que certains clients vivent proches les uns des autres, se déplacent à vélo et présentent le même parcours éducatif. Vous pouvez recourir à ces clusters pour mieux comprendre les relations entre différents clients et exploiter les informations recueillies pour mettre sur pied une stratégie marketing ciblant des clients spécifiques.  
  
 Pour prédire si un client potentiel est susceptible d’acheter un vélo, vous allez créer un modèle d’exploration de données basé sur l' [algorithme MDT (Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)). Cet algorithme examine les informations relatives à chaque client potentiel et recherche des caractéristiques à même de l'aider à prévoir et identifier d'éventuels acheteurs de vélos. Il compare alors les valeurs des caractéristiques de précédents acheteurs avec celles de potentiels nouveaux clients pour déterminer si ces derniers sont susceptibles d'acheter un vélo.  
  
## <a name="alter-mining-structure-statement"></a>Instruction ALTER MINING STRUCTURE  
 Pour ajouter un modèle d’exploration de données à la structure d’exploration de données, vous utilisez l’instruction [ALTER Mining structure &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) . Le code de l’instruction peut être divisé en plusieurs parties :  
  
-   Identification de la structure d'exploration de données  
  
-   Attribution d'un nom au modèle d'exploration de données  
  
-   Définition de la colonne clé  
  
-   Définition des colonnes d'entrée et des colonnes prédictibles  
  
-   Identification des modifications d'algorithme et de paramètre  
  
 L'exemple générique suivant utilise l'instruction ALTER MINING MODEL :  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 La première ligne du code identifie la structure d'exploration de données existante à laquelle les modèles d'exploration de données seront ajoutés :  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 La ligne suivante du code désigne le modèle d'exploration de données qui sera ajouté à la structure d'exploration de données :  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Pour plus d’informations sur l’attribution d’un nom à un objet dans DMX, consultez [identificateurs &#40;dmx&#41;](/sql/dmx/identifiers-dmx).  
  
 Les lignes suivantes du code définissent les colonnes de la structure d'exploration de données employées dans le modèle d'exploration de données :  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 Vous pouvez uniquement utiliser les colonnes déjà existantes dans la structure d'exploration de données ; de même, la première colonne de la liste doit correspondre à la colonne clé issue de la structure d'exploration de données.  
  
 La ligne suivante du code définit l'algorithme d'exploration de données chargé de générer le modèle d'exploration de données ainsi que les paramètres d'algorithme que vous pouvez définir dans l'algorithme :  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 Pour plus d’informations sur les paramètres d’algorithme que vous pouvez ajuster, consultez [algorithme MDT (Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) ) et [algorithme de clustering Microsoft](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).  
  
 Vous pouvez spécifier l'utilisation d'une colonne du modèle d'exploration de données à des fins de prédiction en utilisant la syntaxe suivante :  
  
```  
<mining model column> PREDICT  
```  
  
 La dernière ligne du code, qui est facultative, définit un filtre appliqué lors de l'apprentissage du modèle et de son test. Pour plus d’informations sur la façon d’appliquer des filtres à des modèles d’exploration de données, consultez [filtres pour les modèles d’exploration de données &#40;Analysis Services&#41;d’exploration de données ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   ajouter un modèle d'exploration de données d'arbre de décision à la structure Bike Buyer à l'aide de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees (MDT) ;  
  
-   ajouter un modèle d'exploration de données clustering à la structure Bike Buyer à l'aide de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering.  
  
-   Puisque vous souhaitez consulter des résultats pour tous les cas, n'ajoutez pas encore de filtre aux modèles.  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>Ajout d’un modèle d’exploration de données d’arbre de décision à la structure  
 La première étape consiste à ajouter un modèle d'exploration de données à l'aide de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees (MDT)  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>Pour ajouter un modèle d'exploration de données d'arbre de décision  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête et une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction ALTER MINING STRUCTURE dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <mining structure name>   
    ```  
  
     par :  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining model name>   
    ```  
  
     par :  
  
    ```  
    Decision Tree  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    <mining model columns>,  
    ```  
  
     par :  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     Dans ce cas, la colonne `[Bike Buyer]` est désignée en tant que colonne PREDICT.  
  
6.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     par :  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     L'instruction WITH DRILLTHROUGH vous permet d'explorer les cas utilisés pour la création du modèle d'exploration de données.  
  
     L'instruction obtenue doit se présenter comme suit :  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
8.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `DT_Model.dmx` .  
  
9. Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>Ajout d'un modèle d'exploration de données clustering à une structure  
 Vous pouvez maintenant ajouter un modèle d'exploration de données à la structure d'exploration de données Bike Buyer fondé sur l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering. Du fait que le modèle d'exploration de données clustering exploite l'ensemble des colonnes définies dans la structure d'exploration de données, vous pouvez utiliser un raccourci pour ajouter le modèle à la structure en omettant la définition des colonnes d'exploration de données.  
  
#### <a name="to-add-a-clustering-mining-model"></a>Pour ajouter un modèle d'exploration de données clustering  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête et une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction ALTER MINING STRUCTURE dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <mining structure name>   
    ```  
  
     par :  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining model>   
    ```  
  
     par :  
  
    ```  
    Clustering Model  
    ```  
  
5.  Supprimez le code suivant :  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     par :  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
8.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Clustering_Model.dmx` .  
  
9. Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
 Dans la leçon suivante, vous allez traiter les modèles et la structure d'exploration de données.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Traitement de la structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
