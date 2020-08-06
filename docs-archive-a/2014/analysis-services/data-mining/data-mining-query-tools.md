---
title: Interfaces de requête d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- predictions [Analysis Services]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: a8952427-fd8c-4300-8f62-25f57ac1be0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1702ad82c65b5a7370a62c4bc31a08007f374c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614261"
---
# <a name="data-mining-query-interfaces"></a>Interface de requête d'exploration de données
  Les requêtes d'exploration de données sont basées sur le langage DMX (Data Mining Extensions). Vous utilisez DMX pour toutes les tâches de prédiction et de modélisation, notamment la classification, l'évaluation des risques, la génération de recommandations et la régression linéaire. Vous pouvez également récupérer les modèles et les statistiques générés lorsque vous avez traité le modèle.  
  
 La syntaxe d'une requête de prédiction utilisant DMX est semblable à la syntaxe d'une requête en langage [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] fournissent des outils qui vous permettent de générer des requêtes de prédiction DMX.  
  
 Cette rubrique décrit les interfaces que vous pouvez utiliser pour créer et exécuter des requêtes d'exploration de données à l'aide de DMX.  
  
 [Outils de requête](#bkmk_Tools)  
  
-   [Générateur de requêtes de prédiction](#bkmk_Builder)  
  
-   [Éditeur de requête](#bkmk_QueryEditor)  
  
-   [Modèles DMX](#bkmk_Templates)  
  
-   [Services d’intégration](#bkmk_SSIS)  
  
 [Interfaces de programmation d’applications](#bkmk_API)  
  
##  <a name="data-mining-query-tools"></a><a name="bkmk_Tools"></a>Outils de requête d’exploration de données  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les outils suivants que vous pouvez utiliser pour générer des requêtes de prédiction, des requêtes de contenu et des requêtes de définition des données sur des objets d'exploration de données :  
  
-   Générateur de requêtes de prédiction  
  
-   Éditeur de requête  
  
-   Modèles DMX  
  
-   Composants d'exploration de données Integration Services  
  
###  <a name="prediction-query-builder"></a><a name="bkmk_Builder"></a>Générateur de requêtes de prédiction  
 Le Générateur de requêtes de prédiction est inclus sous l’onglet **Prévision de modèle d’exploration de données** du Concepteur d’exploration de données, disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lorsque vous utilisez le générateur de requêtes, vous pouvez utiliser des outils graphiques pour sélectionner un modèle d'exploration de données, ajouter de nouvelles données de cas, ainsi que des fonctions de prédiction. Le Générateur de requêtes de prédiction contient un éditeur de texte que vous pouvez utiliser pour modifier la requête manuellement et un volet de **résultats** simple pour afficher les résultats de la requête.  
  
###  <a name="query-editor"></a><a name="bkmk_QueryEditor"></a>Éditeur de requête  
 L’éditeur de requête de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit des outils que vous pouvez utiliser pour générer et exécuter des requêtes DMX. Vous pouvez vous connecter à une instance de SQL Server Analysis Services, puis sélectionner une base de données, des colonnes de structure d'exploration de données, ainsi qu'un modèle d'exploration de données. **L’explorateur de métadonnées** contient une liste des fonctions de prédiction que vous pouvez parcourir.  
  
###  <a name="dmx-templates"></a><a name="bkmk_Templates"></a>Modèles DMX  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit des modèles de requête DMX interactifs que vous pouvez utiliser pour générer des requêtes DMX. Si vous ne voyez pas la liste de modèles, cliquez sur **Vue** dans la barre d’outils, puis sélectionnez **Explorateur de modèles**. Pour voir tous les modèles Analysis Services, y compris les modèles pour DMX, MDX et XMLA, cliquez sur l'icône de cube.  
  
 Pour créer une requête à l'aide d'un modèle, vous pouvez faire glisser le modèle dans une fenêtre de requête ouverte, ou vous pouvez double-cliquer sur le modèle pour ouvrir une nouvelle connexion et un nouveau volet de requête.  
  
 Pour obtenir un exemple de création d’une requête de prédiction à partir d’un modèle, consultez [Créer une requête singleton de prédiction à partir d’un modèle](create-a-singleton-prediction-query-from-a-template.md).  
  
> [!WARNING]  
>  Le complément d'exploration de données pour Microsoft Office Excel contient également plusieurs modèles, avec un générateur de requêtes interactif qui peut vous aider à composer des instructions DMX complexes. Pour utiliser les modèles, cliquez sur **Requête**, puis sur **Avancé** dans le client d’exploration de données.  
  
###  <a name="integration-services-data-mining-components"></a><a name="bkmk_SSIS"></a>Integration Services les composants d’exploration de données  
 Vous pouvez également inclure des requêtes de prédiction dans le cadre d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Package. Les tâches et transformations suivantes dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prennent en charge la création et l’exécution d’instructions DMX et de requêtes de prédiction DMX.  
  
|Composant|Description|  
|---------------|-----------------|  
|Tâche de requête d’exploration de données|Exécute des requêtes DMX et d'autres instructions DMX dans le cadre d'un flux de contrôle.<br /><br /> L'éditeur de tâche fournit le Générateur de requêtes de prédiction, ainsi qu'une zone de texte permettant de modifier manuellement la requête DMX. Toutefois, l'éditeur de tâche ne peut pas valider la requête sur les objets d'une solution [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par conséquent, il est préférable de créer une requête dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ou [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , puis de coller le texte de l'instruction ou de la requête dans l'éditeur de tâche.|  
|transformation de requête d'exploration de données|Exécute une requête de prédiction au sein d'un flux de données, à l'aide des données fournies par une source de flux de données.<br /><br /> L'éditeur de tâche fournit le Générateur de requêtes de prédiction, ainsi qu'une zone de texte permettant de modifier manuellement la requête DMX.<br /><br /> La transformation peut être utilisée uniquement pour créer des requêtes qui utilisent des données dans le flux de données ; autrement dit, les requêtes qui utilisent la syntaxe PREDICTION JOIN. Ce composant ne peut pas être utilisé pour exécuter des requêtes de contenu ou d'autres types d'instructions DMX.|  
  
##  <a name="application-programming-interfaces"></a><a name="bkmk_API"></a>Interfaces de programmation d’applications  
 Vous pouvez créer des applications personnalisées qui exécutent des requêtes sur des modèles d'exploration de données à l'aide de divers langages de programmation, en association avec des protocoles serveur tels que OLE DB ou le client Analysis Services ADOMD. Pour plus d’informations, consultez [Programmation de l’exploration de données](../dev-guide/data-mining-programming.md).  
  
 Toutefois, XMLA constitue le format de message sous-jacent pour toutes les interactions avec un serveur Analysis Service. Dans un message XMLA, les requêtes sont représentées différemment selon que vous envoyez une requête de prédiction basée sur DMX, une requête de contenu ou une requête qui récupère les métadonnées du modèle à l'aide des ensembles de lignes de schéma d'exploration de données.  
  
-   Le texte des **requêtes de prédiction** (et de toutes les autres instructions DMX) est envoyé au format XMLA à l’aide de la [méthode Execute &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute), avec la requête DMX placée en tant que texte dans [l’élément Statement &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) de [l’élément Command &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/command-element-xmla).  
  
-   Pour récupérer le **modèle de contenu** et les **métadonnées de modèle**, telles que le nombre de clusters, les attributs utilisés dans les arbres de décision, la date à laquelle le modèle a été traité pour la dernière fois et les paramètres d’algorithme utilisés pendant la création du modèle, vous pouvez utiliser la [méthode Discover &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) et spécifier l’un des ensembles de lignes de schéma d’exploration de données dans l’en-tête de [l’élément RequestType &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla). Pour limiter la portée de la requête, entrez les critères en tant que restrictions dans [l’élément RestrictionList &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictionlist-element-xmla).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](/sql/dmx/data-mining-extensions-dmx-reference)   
 [Solutions d’exploration de données](data-mining-solutions.md)   
 [Fonctionnement de l’instruction DMX Select](/sql/dmx/understanding-the-dmx-select-statement)   
 [Structure et utilisation des requêtes de prédiction DMX](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)   
 [Créer une requête de prédiction à l’aide de la prédiction Générateur de requêtes](create-a-prediction-query-using-the-prediction-query-builder.md)   
 [Créer une requête DMX dans SQL Server Management Studio](create-a-dmx-query-in-sql-server-management-studio.md)  
  
  
