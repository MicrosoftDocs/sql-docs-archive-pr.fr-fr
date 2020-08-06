---
title: Requête et filtre (onglet navigateur, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603697"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Interroger et filtrer (onglet Navigateur, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Cette zone de l'onglet **Navigateur** dans le Concepteur de cube contient une zone de requête et de filtre qui vous aide à choisir les données du cube à utiliser dans la navigation ou dans les requêtes. Vous pouvez ajouter autant d'objets de cube que vous le souhaitez, puis vous pouvez afficher les résultats dans la zone de données, ou les exporter dans un rapport en utilisant Analyser dans Excel pour visualiser la façon dont les données sont affichées par les utilisateurs finaux.  
  
> [!WARNING]  
>  Lorsque vous travaillez avec des données dans cette zone, par défaut **Navigateur** utilise le mode de création graphique. Toutefois, vous pouvez modifier la requête directement à l'aide de MDX, en cliquant sur le bouton bascule **Mode Création** . Le volet qui vous permet de concevoir des filtres sur les dimensions disparaît. Si vous souhaitez ajouter un filtre, vous pouvez revenir en mode de création graphique.  
  
 Par définition, les informations d'identification de l'utilisateur actuel, et non celles spécifiées dans la page **Informations d'emprunt d'identité** , sont utilisées pour la connexion à la source de données lorsqu'une requête est exécutée. Toutefois, vous pouvez également modifier le contexte de l'utilisateur pour la requête ou le rapport en cliquant sur **Changer d'utilisateur** dans la **Barre d'outils**.  
  
## <a name="options"></a>Options  
 **Dimension**  
 Sélectionnez la dimension sur laquelle trancher le sous-cube.  
  
 **Hierarchy**  
 Sélectionnez la hiérarchie sur laquelle trancher le sous-cube.  
  
 **Opérateur**  
 Sélectionnez l’opérateur qui définit comment l’expression dans **Expression de filtre** est appliquée à la hiérarchie sélectionnée. Le tableau suivant décrit les opérateurs disponibles.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Égal**|Les résultats se limitent à l'ensemble défini dans **Expression de filtre**.|  
|**Différent de**|Les résultats se limitent aux membres n'appartenant pas à l'ensemble défini dans **Expression de filtre**.|  
|**Dans**|Les résultats se limitent à l'ensemble nommé choisi dans **Expression de filtre**.|  
|**Pas dans**|Les résultats se limitent aux membres n'appartenant pas à l'ensemble nommé choisi dans **Expression de filtre**.|  
|**Contains**|Les résultats se limitent aux membres dont le nom contient la chaîne de caractères figurant dans **Expression de filtre**.|  
|**Commence par**|Les résultats se limitent aux membres dont le nom commence par la chaîne de caractères figurant dans **Expression de filtre**.|  
|**Plage (limites incluses)**|Les résultats se limitent à la plage choisie dans **Expression de filtre**.|  
|**Plage (limites exclues)**|Les résultats se limitent aux membres n'appartenant pas à la plage choisie dans **Expression de filtre**.|  
|**MDX**|Les résultats se limitent aux expressions MDX (Multidimensional Expressions) définies dans **Expression de filtre**.|  
  
 **Expression de filtre**  
 Tapez l’expression que doit évaluer **Opérateur**, qui se limite aux résultats à parcourir.  
  
> [!NOTE]  
>  Ce champ est un élément dynamique de saisie des données dont l'aspect change en fonction des types de données nécessaires à l'opérateur sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Navigateur &#40;concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet navigateur, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Analyser dans Excel &#40;onglet navigateur, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Onglets du navigateur &#40;de métadonnées, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
