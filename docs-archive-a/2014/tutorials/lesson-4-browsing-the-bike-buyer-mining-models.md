---
title: 'Leçon 4 : exploration des modèles d’exploration de données Bike Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604329"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a>Leçon 4 : Exploration des modèles d’exploration de données Bike Buyer
  Dans cette leçon, vous allez utiliser l’instruction [Select (DMX)](/sql/dmx/select-dmx) pour explorer le contenu des modèles d’exploration de données d’arbre de décision et de clustering que vous avez créés au cours de la [leçon 2 : ajout de modèles d’exploration de données à la structure d’exploration de données prédictive](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 Les colonnes figurant dans un modèle d'exploration de données ne sont pas les colonnes définies par la structure d'exploration de données ; elles forment plutôt un ensemble spécifique de colonnes décrivant des tendances et des modèles identifiés par l'algorithme. Ces colonnes de modèle d’exploration de données sont décrites dans l’ensemble de lignes de schéma d' [ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) . Par exemple, la colonne MODEL_NAME située dans l'ensemble de lignes du schéma contient le nom du modèle d'exploration de données. Dans le cadre d'un modèle d'exploration de données clustering, la colonne NODE_CAPTION renferme le nom de chaque cluster et la colonne NODE_DESCRIPTION contient une description des caractéristiques de chacun de ces clusters. Vous pouvez parcourir ces colonnes à l’aide de l’option SELECT FROM \<model> . Instruction CONTENT dans DMX. Le recours à cette instruction est également possible si vous souhaitez explorer les données utilisées pour la création du modèle d'exploration de données. Pour utiliser cette instruction, vous devez activer la fonction d'extraction dans la structure d'exploration de données. Pour plus d’informations sur l’instruction, consultez [SELECT FROM &#60;model&#62;. CAS &#40;&#41;DMX ](/sql/dmx/select-from-model-content-dmx).  
  
 Vous pouvez également afficher tous les états d'une colonne discrète par le biais de l'instruction SELECT DISTINCT. Par exemple, si vous effectuez cette opération sur une colonne Sexe, la requête retourne les valeurs `male` et `female`.  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   explorer le contenu des modèles d'exploration de données ;  
  
-   retourner les cas des données source utilisées pour l'apprentissage des modèles d'exploration de données ;  
  
-   explorer les différents états disponibles pour une colonne discrète donnée.  
  
## <a name="returning-the-content-of-a-mining-model"></a>Retour du contenu d'un modèle d'exploration de données  
 Dans cette leçon, vous allez utiliser le [&#62; de modèle SELECT FROM &#60;. Instruction CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx) pour retourner le contenu du modèle de clustering.  
  
 Voici un exemple générique de l’option SELECT FROM \<model> . Instruction de contenu :  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 La première ligne du code définit les colonnes à retourner à partir du contenu du modèle d'exploration de données et le modèle d'exploration de données auquel elles sont associées :  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 La clause .CONTENT en regard du nom du modèle d'exploration de données précise que le contenu est retourné à partir du modèle d'exploration de données. Pour plus d’informations sur les colonnes contenues dans le modèle d’exploration de données, consultez [DMSCHEMA_MINING_MODEL_CONTENT rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
 Vous pouvez éventuellement exploiter la dernière ligne du code pour filtrer les résultats retournés par l'instruction :  
  
```  
WHERE <where clause>  
```  
  
 Par exemple, si vous souhaitez restreindre les résultats de la requête uniquement aux clusters abritant un grand nombre de cas, vous pouvez ajouter la clause WHERE suivante à l'instruction SELECT :  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 Pour plus d’informations sur l’utilisation de l’instruction WHERE, consultez [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a>Pour retourner le contenu du modèle d'exploration de données clustering  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l’exemple générique de SELECT FROM \<model> . Instruction CONTENT dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    *  
    ```  
  
     Vous pouvez également remplacer * par la liste des colonnes contenues dans l’ensemble de [lignes DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Clustering]  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
6.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `SELECT_CONTENT.dmx` .  
  
7.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne le contenu du modèle d'exploration de données.  
  
## <a name="use-drillthrough"></a>Utilisation de la fonction d'extraction  
 L'étape suivante consiste à utiliser l'instruction d'extraction pour retourner un éventail de cas utilisés pour l'apprentissage du modèle d'exploration de données d'arbre de décision. Dans cette leçon, vous allez utiliser le [&#62; de modèle SELECT FROM &#60;. CAS &#40;instruction DMX&#41;](/sql/dmx/select-from-model-content-dmx) pour retourner le contenu du modèle d’arbre de décision.  
  
 Voici un exemple générique de l’option SELECT FROM \<model> . Instruction CASES :  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 La première ligne du code définit les colonnes à retourner depuis les données source et le modèle d'exploration de données qui les contient :  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 La clause .CASES indique que vous exécutez une requête d'extraction. Pour recourir à l'extraction, vous devez l'activer au moment de créer le modèle d'exploration de données.  
  
 La dernière ligne de code est facultative et spécifie le nœud du modèle d'exploration de données duquel vous souhaitez obtenir les cas :  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 Pour plus d’informations sur l’utilisation de l’instruction WHERE avec IsInNode, consultez [SELECT FROM &#60;model&#62;. CAS &#40;&#41;DMX ](/sql/dmx/select-from-model-content-dmx).  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a>Pour retourner les cas utilisés pour l'apprentissage du modèle d'exploration de données  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l’exemple générique de SELECT FROM \<model> . Instruction CASES dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    *  
    ```  
  
     Vous pouvez remplacer * par une liste de colonnes issues des sources de données (par exemple, [Bike Buyer]).  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Decision Tree]  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
6.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `SELECT_DRILLTHROUGH.dmx` .  
  
7.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne les données source utilisées pour l'apprentissage du modèle d'exploration de données d'arbre de décision.  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a>Retour des états d'une colonne discrète du modèle d'exploration de données  
 L'étape suivante consiste à utiliser l'instruction SELECT DISTINCT pour retourner les différents états possibles dans la colonne de modèle d'exploration de données spécifiée.  
  
 L'exemple générique suivant utilise l'instruction SELECT DISTINCT :  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 La première ligne du code définit les colonnes du modèle d'exploration de données pour lesquelles les états sont retournés :  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 Vous devez inclure l'instruction DISTINCT pour être en mesure de retourner tous les états de la colonne. Si vous l'excluez, l'instruction DISTINCT complète se transforme en un raccourci de création de prédiction et retourne l'état le plus probable de la colonne spécifiée. Pour plus d’informations, consultez [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a>Pour retourner les états d'une colonne discrète  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction SELECT DISTINCT dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    [<column,name>   
    ```  
  
     par :  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Decision Tree]  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
6.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `SELECT_DISCRETE.dmx` .  
  
7.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne les états possibles de la colonne Bike Buyer.  
  
 Au cours de la leçon suivante, vous allez évaluer si des clients potentiels sont des acheteurs de vélos à l'aide du modèle d'exploration de données d'arbre de décision.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 5 : Exécution des requêtes de prédiction](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
