---
title: 'Leçon 2 : ajout de modèles d’exploration de données à la structure d’exploration de données Market panier | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702207"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a>Leçon 2 : Ajout de modèles d’exploration de données à la structure d’exploration de données Market Basket
  Dans cette leçon, vous allez ajouter deux modèles d’exploration de données à la structure d’exploration de données Market panier que vous avez créée au cours de [la leçon 1 : création de la structure d’exploration de données Market panier](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md). Ces modèles d'exploration de données vous permettent de créer des prédictions.  
  
 Pour prédire les types de produits que les clients ont tendance à acheter en même temps, vous allez créer deux modèles d’exploration de données à l’aide de l' [algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) et deux valeurs différentes pour le paramètre *MINIMUM_PROBABILTY* .  
  
 *MINIMUM_PROBABILTY* est un [!INCLUDE[msCoName](../includes/msconame-md.md)] paramètre d’algorithme d’association qui permet de déterminer le nombre de règles qu’un modèle d’exploration de données contiendra en spécifiant la probabilité minimale qu’une règle doit avoir. Par exemple, la valeur 0,4 spécifie qu'une règle peut être générée uniquement si la combinaison des produits que la règle décrit présente une probabilité d'occurrence d'au moins quarante pour cent.  
  
 Vous allez voir l’effet de la modification du paramètre *MINIMUM_PROBABILTY* dans une leçon ultérieure.  
  
## <a name="alter-mining-structure-statement"></a>Instruction ALTER MINING STRUCTURE  
 Pour ajouter un modèle d’exploration de données qui contient une table imbriquée à une structure d’exploration de données, vous utilisez l’instruction [ALTER Mining structure &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) . Le code de l’instruction peut être divisé en plusieurs parties :  
  
-   Identification de la structure d'exploration de données  
  
-   Attribution d'un nom au modèle d'exploration de données  
  
-   Définition de la colonne clé  
  
-   Définition des colonnes d'entrée et des colonnes prédictibles  
  
-   Définition des colonnes de la table imbriquée  
  
-   Identification des modifications d'algorithme et de paramètre  
  
 L'exemple générique suivant utilise l'instruction `ALTER MINING STRUCTURE` qui ajoute un modèle d'exploration de données à une structure comportant des colonnes de tables imbriquées :  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 La première ligne du code identifie la structure d'exploration de données existante à laquelle le modèle d'exploration de données sera ajouté :  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 La ligne suivante du code désigne le modèle d'exploration de données qui sera ajouté à la structure d'exploration de données :  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Pour plus d’informations sur l’attribution d’un nom à un objet dans les extensions DMX (Data Mining Extensions), consultez [identificateurs &#40;dmx&#41;](/sql/dmx/identifiers-dmx).  
  
 Les lignes suivantes du code définissent les colonnes de la structure d’exploration de données qui seront utilisées par le modèle d’exploration de données :  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 Vous pouvez utiliser uniquement des colonnes qui existent déjà dans la structure d'exploration de données.  
  
 La première colonne dans la liste de colonnes de modèle d'exploration de données doit être la colonne clé dans la structure d'exploration de données. Toutefois, il n’est pas nécessaire de taper `KEY` après la colonne clé pour spécifier l’utilisation. En effet, vous avez déjà défini la colonne en tant que clé lorsque vous avez créé la structure d'exploration de données.  
  
 Les lignes restantes spécifient l'utilisation des colonnes dans le nouveau modèle d'exploration de données. Vous pouvez spécifier qu’une colonne dans le modèle d’exploration de données sera utilisée pour la prédiction à l’aide de la syntaxe suivante :  
  
```  
<column name> PREDICT,  
```  
  
 Si vous ne spécifiez pas d'utilisation, vous n'avez pas besoin d'inclure une colonne de structure d'exploration de données dans la liste. Toutes les colonnes utilisées par la structure d'exploration de données référencée sont automatiquement mises à la disposition des modèles d'exploration de données basés sur cette structure. Toutefois, le modèle n'utilisera pas les colonnes pour la formation à moins que vous ne spécifiiez l'utilisation.  
  
 La dernière ligne du code définit l'algorithme et les paramètres d'algorithme employés pour générer le modèle d'exploration de données.  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   ajouter un modèle d'exploration de données Association à la structure à l'aide de la probabilité par défaut ;  
  
-   ajouter un modèle d'exploration de données Association à la structure à l'aide d'une probabilité modifiée.  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a>Ajout d'un modèle d'exploration de données Association à la structure en utilisant le paramètre MINIMUM_PROBABILITY par défaut  
 La première tâche consiste à ajouter un nouveau modèle d’exploration de données à la structure d’exploration de données Market panier basée sur l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme d’association, en utilisant la valeur par défaut pour *MINIMUM_PROBABILITY*.  
  
#### <a name="to-add-an-association-mining-model"></a>Pour ajouter un modèle d'exploration de données Association  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
    > [!NOTE]  
    >  Pour créer une requête DMX sur une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] spécifique, cliquez avec le bouton droit sur la base de données au lieu de l'instance.  
  
2.  Copiez l'exemple générique de l'instruction `ALTER MINING STRUCTURE` dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <mining structure name>   
    ```  
  
     par :  
  
    ```  
    [Market Basket]  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining model name>   
    ```  
  
     par :  
  
    ```  
    [Default Association]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     par :  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     Dans ce cas, la table `[Products]` a été désignée comme colonne prédictible `.`. Par ailleurs, la colonne `[Model]` est incluse dans la liste des colonnes de la table imbriquée car il s'agit de la colonne clé de la table imbriquée.  
  
    > [!NOTE]  
    >  N'oubliez pas qu'une clé imbriquée est différente d'une clé de cas. Une clé de cas est un identificateur unique du cas, alors que la clé imbriquée est un attribut que vous souhaitez modéliser.  
  
6.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     par :  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     L'instruction obtenue doit se présenter comme suit :  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
8.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Default_Association_Model.dmx` .  
  
9. Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a>Ajout d'un modèle d'exploration de données Association à la structure en modifiant le paramètre MINIMUM_PROBABILITY par défaut  
 La tâche suivante consiste à ajouter un nouveau modèle d'exploration de données à la structure d'exploration de données Market Basket en partant de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association, puis en attribuant la valeur par défaut 0,01 au paramètre MINIMUM_PROBABILITY. La modification du paramètre force alors l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association à créer d'autres règles.  
  
#### <a name="to-add-an-association-mining-model"></a>Pour ajouter un modèle d'exploration de données Association  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction `ALTER MINING STRUCTURE` dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <mining structure name>   
    ```  
  
     par :  
  
    ```  
    Market Basket  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining model name>   
    ```  
  
     par :  
  
    ```  
    [Modified Association]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     par :  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     Dans ce cas, la table `[Products]` est désignée en tant que colonne prédictible. Par ailleurs, la colonne `[MODEL]` est incluse dans la liste car il s'agit de la colonne clé dans la table imbriquée.  
  
6.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     par :  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     L'instruction obtenue doit se présenter comme suit :  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
8.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Modified Association_Model.dmx` .  
  
9. Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
 Dans la leçon suivante, vous allez traiter la structure d'exploration de données Market Basket et ses modèles d'exploration de données associés.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Traitement de la structure d'exploration de données Market Basket](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
