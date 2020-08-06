---
title: Spécifier le type de contenu et de données des colonnes (Assistant Exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
ms.openlocfilehash: e22f46808877391376f721bcab55ea4fd9074186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604169"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a>Spécifier type de contenu et de données des colonnes (Assistant Exploration de données)
  Utilisez la page **Spécifier type de contenu et de données des colonnes** pour spécifier l’utilisation et le type de données de chaque colonne que vous avez sélectionnée dans la page précédente de l’Assistant. Si vous voulez ignorer la colonne, cliquez sur **Précédent** pour revenir à la page **Spécifier les données d’apprentissage**, puis décochez toutes les cases.  
  
 L'utilisation d'une colonne indique la manière dont les données seront utilisées dans le modèle. Une colonne peut être utilisée en tant que clé d'identification d'une série, en tant que valeur d'entrée à utiliser dans l'analyse ou en tant que valeur à prédire. Les colonnes peuvent à la fois être utilisées à des fins de prédiction et de saisie.  
  
 Le type de données spécifie des détails supplémentaires sur le type des données contenues dans la colonne, ainsi que la manière dont les données seront utilisées pendant l'apprentissage. Certains types de contenu requièrent un type de données spécifique, et vice versa. Vous pouvez également avoir besoin de spécifier un type de données particulier selon l'algorithme que vous utilisez lorsque vous créez un modèle d'exploration de données. Pour plus d’informations sur les types de contenu et les types de données dans les modèles et structures d’exploration de données, consultez [Types de contenu &#40;Exploration de données&#41;](data-mining/content-types-data-mining.md).  
  
 **Pour plus d’informations :** [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Colonnes d’un modèle d’exploration de données](data-mining/mining-model-columns.md), [Assistant Exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Créer une structure d’exploration de données relationnelle](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Options  
 **Structure du modèle d'exploration de données**  
 Affiche les colonnes des vues et des tables imbriquées que vous avez sélectionnées dans la page précédente de l'Assistant.  
  
 **Colonnes**  
 Répertorie les colonnes.  
  
 **Type de contenu**  
 Spécifiez le type de contenu de la colonne. Si vous avez spécifié que la colonne est une clé dans la page précédente de l'Assistant, les valeurs suivantes sont disponibles :  
  
|Option|Description|  
|------------|-----------------|  
|Clé|Spécifiez que la colonne contient un identificateur unique pour la série de cas.|  
|Séquence clé|Spécifiez que la colonne contient un identificateur de séquence.|  
|Temps clé|Spécifiez que la colonne contient une date ou un autre nombre continu unique utilisé pour identifier une date ou une série chronologique.|  
  
 Si vous avez sélectionné la colonne en tant que colonne non-clé, les valeurs suivantes sont disponibles, selon le type de données :  
  
|Option|Description|  
|------------|-----------------|  
|Continue|Spécifiez que la colonne contient des valeurs numériques continues.|  
|Discrétisé|Spécifiez que la colonne contient des valeurs numériques qui ont été discrétisées ou qui peut être traitées comme des valeurs discrètes.|  
|Discret|Spécifiez que la colonne contient des valeurs de texte ou d'autres valeurs non numériques.|  
  
 **Type de données**  
 Spécifiez le type de données de la colonne.  
  
 Les valeurs suivantes sont disponibles :  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 **Detect**  
 Analysez un exemple de données dans toutes les colonnes numériques. Remplace les valeurs **Type de contenu** spécifiées par un type de contenu recommandé.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Exploration de données &#40;Analysis Services-exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Suggérer des colonnes associées &#40;l’Assistant Exploration de données&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Spécifier les types de tables &#40;l’Assistant Exploration de données&#41;](specify-table-types-data-mining-wizard.md)   
 [Spécifiez le contenu et le type de données de la colonne &#40;l’Assistant Exploration de données&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
