---
title: Hiérarchies utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- members [Analysis Services], hierarchies
- dimensions [Analysis Services], hierarchies
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], attribute
- attributes [Analysis Services], hierarchies
- parent-child hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
- ragged hierarchies [Analysis Services]
- balanced hierarchies [Analysis Services]
- hierarchies [Analysis Services]
- OLAP objects [Analysis Services], hierarchies
- multilevel hierarchies [Analysis Services]
- unbalanced hierarchies [Analysis Services]
ms.assetid: 9394e9a3-2242-4f0e-85e0-25d499d2d3b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 533b244a8a5b6ec5e2866b068cfbf5eb6f31a7a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604229"
---
# <a name="user-hierarchies"></a>Hiérarchies utilisateur
  Les hiérarchies définies par l’utilisateur sont des hiérarchies d’attributs définies par l’utilisateur qui sont utilisées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour organiser les membres d’une dimension en structures hiérarchiques et fournir des chemins de navigation dans un cube. Par exemple, le tableau suivant définit une table de dimension pour une dimension de temps. La table de dimension prend en charge trois attributs nommés Year, Quarter et Month.  
  
|Year (Année)|Quarter (Trimestre)|Month (Mois)|  
|----------|-------------|-----------|  
|1999|Trimestre 1|Jan|  
|1999|Trimestre 1|Fév|  
|1999|Trimestre 1|Mar|  
|1999|Trimestre 2|Avr|  
|1999|Trimestre 2|Mai|  
|1999|Trimestre 2|Juin|  
|1999|Trimestre 3|Jui|  
|1999|Trimestre 3|Aoû|  
|1999|Trimestre 3|Sep|  
|1999|Trimestre 4|Oct|  
|1999|Trimestre 4|Nov|  
|1999|Trimestre 4|Déc|  
  
 Les attributs Year, Quarter et Month sont utilisés pour construire une hiérarchie définie par l'utilisateur, nommée Calendar, dans la dimension de temps. Le diagramme suivant montre la relation entre les niveaux et les membres de la dimension Calendar (dimension régulière).  
  
 ![Niveau et hiérarchie membre d'une dimension de temps](../dev-guide/media/as-levelconcepts.gif "Niveau et hiérarchie membre d'une dimension de temps")  
  
> [!NOTE]  
>  Toute hiérarchie autre qu'une hiérarchie d'attribut à deux niveaux par défaut se nomme hiérarchie définie par l'utilisateur. Pour plus d’informations sur les hiérarchies d’attributs, consultez [attributs et hiérarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)d’attributs.  
  
## <a name="member-structures"></a>Structures de membres  
 À l'exception des hiérarchies parent-enfant, la position des membres d'une hiérarchie est déterminée par l'ordre des attributs dans la définition de la hiérarchie. Chaque attribut inclus dans la définition de la hiérarchie génère un niveau dans la hiérarchie. La position d'un membre à l'intérieur d'un niveau est déterminée par le classement de l'attribut utilisé pour créer le niveau. Les structures de membres des hiérarchies définies par l'utilisateur peuvent prendre l'une des quatre formes de base, selon la façon dont les membres sont liés les uns aux autres.  
  
### <a name="balanced-hierarchies"></a>Hiérarchies équilibrées  
 Dans une hiérarchie équilibrée, toutes les branches aboutissent au même niveau, et le parent logique de chaque membre figure dans le niveau immédiatement supérieur au membre. La hiérarchie Product Categories de la dimension Product dans l'exemple [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], est un bon exemple de hiérarchie équilibrée. Chaque membre du niveau Product Name a un membre parent dans le niveau Subcategory, qui a à son tour un membre parent dans le niveau Category. De plus, chaque branche de la hiérarchie possède un membre feuille dans le niveau Product Name.  
  
### <a name="unbalanced-hierarchies"></a>Hiérarchies déséquilibrées  
 Dans une hiérarchie non équilibrée, les branches aboutissent à des niveaux différents. Les hiérarchies parent-enfant sont des hiérarchies déséquilibrées. Par exemple, la dimension Organization dans l'exemple [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], contient un membre pour chaque employé. Le directeur général est le membre supérieur de la hiérarchie et les directeurs des différents services ainsi que la secrétaire de direction se trouvent immédiatement après lui. Des membres sont subordonnés aux directeurs des différents services, mais pas à la secrétaire de direction.  
  
 Il est parfois impossible pour les utilisateurs finaux de faire la différence entre les hiérarchies non équilibrées et les hiérarchies irrégulières. Toutefois, différentes techniques et propriétés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vous permettent de prendre en charge ces deux types de hiérarchies. Pour plus d’informations, consultez [hiérarchies déséquilibrées](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)et [attributs dans les hiérarchies de parent-enfant](../multidimensional-models/parent-child-dimension-attributes.md).  
  
### <a name="ragged-hierarchies"></a>Hiérarchies déséquilibrées  
 Dans une hiérarchie déséquilibrée, le membre parent logique d'au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Cela peut amener les branches de la hiérarchie à aboutir à des niveaux différents. Par exemple, dans une dimension Geography définie avec les niveaux Continent, CountryRegion et City, dans cet ordre, le membre Europe apparaît au niveau supérieur de la hiérarchie, le membre France apparaît au niveau intermédiaire et le membre Paris apparaît au niveau inférieur. France est plus précis que Europe et Paris l'est davantage que France. Les modifications suivantes sont apportées à cette hiérarchie régulière :  
  
-   Le membre État de la Cité du Vatican est ajouté au niveau CountryRegion.  
  
-   Des membres sont ajoutés au niveau City et sont associés au membre État de la Cité du Vatican dans le niveau CountryRegion.  
  
-   Un niveau, nommé Province, est ajouté entre le niveau CountryRegion et le niveau City.  
  
 Le niveau Province est rempli avec des membres associés à d'autres membres du niveau CountryRegion, et des membres du niveau City sont associés à leurs membres correspondants du niveau Province. Toutefois, le membre État de la Cité du Vatican du niveau CountryRegion n'étant associé à aucun membre du niveau Province, les membres doivent être associés directement du niveau City au membre État de la Cité du Vatican du niveau CountryRegion. En raison de ces modifications, la hiérarchie de la dimension est désormais irrégulière. Le parent de la ville État de la Cité du Vatican est État de la Cité du Vatican du niveau CountryRegion, qui n'est pas inclus dans le niveau immédiatement supérieur au membre État de la Cité du Vatican du niveau City. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
### <a name="parent-child-hierarchies"></a>Hiérarchies parent-enfant  
 Les hiérarchies parent-enfant de dimensions sont définies à l'aide d'un attribut spécial, nommé « attribut parent », pour déterminer la façon dont les membres sont liés les uns aux autres. Un attribut parent décrit une *relation d’auto-référencement*, ou *jointure réflexive*, dans une table de dimension principale. Les hiérarchies parent-enfant sont construites à partir d'un seul attribut parent. Un seul niveau est affecté à une hiérarchie parent-enfant parce que les niveaux présents dans la hiérarchie sont constitués à partir des relations parent-enfant entre les membres associés à l'attribut parent. Le schéma de dimension d'une hiérarchie parent-enfant dépend de la présence d'une relation d'auto-référencement dans la table principale de la dimension. Par exemple, le diagramme suivant illustre la table principale de la dimension **Dimorganisation** dans l' [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] exemple de base de données.  
  
 ![Jointure auto-référencée dans la table DimOrganization](../dev-guide/media/dimorganization.gif "Jointure auto-référencée dans la table DimOrganization")  
  
 Dans cette table de dimension, la colonne **ParentOrganizationKey** a une relation de clé étrangère avec la colonne clé primaire **OrganizationKey** . En d'autres termes, chaque enregistrement dans cette table peut être associé à un autre enregistrement de la table par une relation parent-enfant. Ce type de jointure réflexive est généralement utilisé pour représenter les données d'une entité d'une organisation, telles que la structure de gestion des employés dans un service.  
  
 Lorsque vous créez une hiérarchie parent-enfant, les colonnes représentées par les deux attributs doivent avoir le même type de données. Les deux attributs doivent également figurer dans la même table. Par défaut, tout membre dont la clé de parent est égale à sa clé de membre, à une valeur null, à 0 (zéro) ou à une valeur ne figurant pas dans la colonne des clés de membre, est considéré comme appartenant au niveau supérieur (niveau (Tous) exclu).  
  
 La profondeur d'une hiérarchie parent-enfant peut varier d'une branche à l'autre de sa hiérarchie. En d'autres termes, une hiérarchie parent-enfant est considérée comme étant une hiérarchie déséquilibrée.  
  
 Contrairement aux hiérarchies définies par l'utilisateur, dans lesquelles le nombre de niveaux de la hiérarchie détermine le nombre de niveaux visibles pour les utilisateurs finaux, une hiérarchie parent-enfant est définie avec le niveau unique d'une hiérarchie d'attribut, et les valeurs de ce niveau unique produisent les multiples niveaux visibles pour les utilisateurs. Le nombre de niveaux affichés dépend du contenu des colonnes de table de dimension qui stockent les clés de membre et les clés parentes. Le nombre de niveaux peut changer à mesure que les données des tables de dimension changent. Pour plus d’informations, consultez [hiérarchie parent-enfant](../multidimensional-models/parent-child-dimension.md)et [attributs dans les hiérarchies de parent-enfant](../multidimensional-models/parent-child-dimension-attributes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des hiérarchies définies par l’utilisateur](../multidimensional-models/user-defined-hierarchies-create.md)   
 [Propriétés de la hiérarchie utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
