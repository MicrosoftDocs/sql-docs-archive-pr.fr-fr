---
title: Interrogation de données multidimensionnelles avec MDX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b7589a98636e56e8c592cef213785544e18f4ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612563"
---
# <a name="querying-multidimensional-data-with-mdx"></a>Interrogation de données multidimensionnelles à l'aide de MDX
  Les expressions multidimensionnelles (MDX) sont le langage de requête que vous utilisez pour travailler avec et récupérer des données multidimensionnelles dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . MDX est basé sur la spécification XMLA (XML for Analysis), avec des extensions spécifiques pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . MDX utilise des expressions composées d’identificateurs, de valeurs, d’instructions, de fonctions et d’opérateurs qu’ [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] peut évaluer pour extraire un objet (par exemple, un jeu ou un membre) ou une valeur scalaire (par exemple, une chaîne ou un nombre).  
  
 Les requêtes et les expressions MDX dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sont utilisées pour effectuer les opérations suivantes :  
  
-   Retourner des données à une application cliente à partir d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] cube.  
  
-   Mettre en forme les résultats des requêtes.  
  
-   Effectuer des tâches de conception liées aux cubes, notamment la définition de membres calculés, de jeux nommés, d'attributions d'étendues et d'indicateurs de performance clés (KPI).  
  
-   Effectuer des tâches administratives, notamment les tâches liées à la sécurité des dimensions et des cellules.  
  
 À plusieurs égards, MDX s'apparente en surface à la syntaxe SQL généralement adoptée pour les bases de données relationnelles. Toutefois, MDX n'est pas une extension du langage SQL et présente de nombreuses différences par rapport à SQL. Pour être en mesure de créer des expressions MDX destinées à concevoir ou sécuriser des cubes, ou bien de créer des requêtes MDX en vue de retourner et de mettre en forme des données multidimensionnelles, vous devez maîtriser les concepts de base du langage MDX, la modélisation dimensionnelle, les éléments de syntaxe MDX, ainsi que les opérateurs, les instructions et les fonctions MDX.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez la section ressources supplémentaires de la page [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) sur le site Web Microsoft TechNet. Pour plus d’informations sur les problèmes de performances liés aux calculs et requêtes MDX, consultez la section « écriture d’expressions MDX efficaces » dans le [Guide des performances SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Concepts clés de MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)|Vous pouvez utiliser des expressions multidimensionnelles (MDX) pour interroger des données multidimensionnelles ou créer des expressions MDX à utiliser dans un cube, mais vous devez d’abord comprendre les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] concepts et la terminologie de la dimension.|  
|[Principes de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)|La syntaxe MDX (Multidimensional Expressions) vous permet d'interroger les objets multidimensionnels, tels que des cubes, et de retourner des ensembles de cellules multidimensionnels contenant les données du cube. Cette rubrique et ses sous-rubriques donnent une vue d'ensemble des requêtes MDX.|  
|[Principes de base des scripts MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)|Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un script MDX (Multidimensional Expressions) est constitué d’une ou plusieurs expressions ou instructions MDX qui remplissent un cube avec des calculs.<br /><br /> Un script MDX définit le processus de calcul pour un cube. Il est également considéré comme un élément du cube proprement dit. Par conséquent, la modification d'un script MDX associé à un cube entraîne immédiatement la modification de son processus de calcul.<br /><br /> Pour créer des scripts MDX, vous pouvez utiliser le Concepteur de cube disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de syntaxe MDX &#40;&#41;MDX](/sql/mdx/mdx-syntax-elements-mdx)   
 [Guide de référence du langage MDX &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
