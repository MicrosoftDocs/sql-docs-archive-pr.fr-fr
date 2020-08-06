---
title: Page filtres, boîtes de dialogue graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01d5054ce7d0c3e02d960885f149bd0ef209dc34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700854"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a>Page Filtres, boîtes de dialogue Graphique (Générateur de rapports et SSRS)
  Cliquez sur **filtres** dans :  
  
-   la boîte de dialogue**Propriétés du groupe de catégories** pour filtrer les points de données dans une série regroupée par catégorie ;  
  
-   la boîte de dialogue**Propriétés du graphique** pour définir les options de filtrage du graphique ;  
  
-   la boîte de dialogue**Propriétés du groupe de séries** pour limiter le nombre de séries dans le groupe sélectionné.  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Cliquez pour ajouter une nouvelle clause de filtre à la liste.  
  
 **Supprimer**  
 Cliquez pour supprimer la clause de filtre sélectionnée de la liste.  
  
 **Flèche haut**  
 Cliquez pour déplacer le filtre sélectionné vers le haut de la liste.  
  
 **Flèche bas**  
 Cliquez pour déplacer le filtre sélectionné vers le bas dans la liste.  
  
 **Expression**  
 Tapez ou choisissez l'expression à laquelle vous souhaitez appliquer un filtre. Cliquez sur le bouton Expression (**fx**) pour modifier l’expression.  
  
 **Type de données**  
 Sélectionnez le type de données du champ **Valeur**. Lorsque cela est possible, sélectionnez un type de données correspondant à celui du champ **Expression**.  
  
 Les valeurs dans **Expression** et **Valeur** doivent s’évaluer au même type de données. Par exemple, si **Expression** a pour valeur un champ du type de données System.Int32 et que **Valeur** a pour valeur 7, sélectionnez **Entier**dans la liste déroulante.  
  
 Si le type de données recherché ne figure pas dans la liste déroulante, écrivez une expression permettant de convertir la valeur en type de données correct. Pour plus d’informations, consultez [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
 **Opérateur**  
 Choisissez l'opérateur à utiliser pour comparer l'expression et la valeur.  
  
 **Valeur**  
 Tapez l’expression ou la valeur à comparer au contenu de l’expression dans **Expression**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupe &#40;Générateur de rapports et SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
