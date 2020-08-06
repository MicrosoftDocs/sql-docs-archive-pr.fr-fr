---
title: Relations d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 122638a2728a8a85ee58661196797383da20eef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702029"
---
# <a name="attribute-relationships"></a>Relations d’attributs
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , les attributs d’une dimension sont toujours liés directement ou indirectement à l’attribut de clé. Quand vous définissez une dimension basée sur un schéma en étoile, c'est-à-dire quand tous les attributs de la dimension sont dérivés de la même table relationnelle, une relation d'attribut est automatiquement définie entre l'attribut clé et chaque attribut non-clé de la dimension. Quand vous définissez une dimension basée sur un schéma en flocon, où les attributs de la dimension sont dérivés de plusieurs tables liées, une relation d'attribut est automatiquement définie comme suit :  
  
-   entre l'attribut clé et chaque attribut non-clé lié aux colonnes de la table de dimension principale ;  
  
-   entre l'attribut clé et l'attribut lié à la clé étrangère dans la table secondaire qui lie les tables de dimension sous-jacentes ;  
  
-   entre l'attribut lié à la clé étrangère de la table secondaire et chaque attribut non-clé lié aux colonnes de la table secondaire.  
  
 Cependant, pour plusieurs raisons, vous pouvez souhaiter modifier ces relations d'attributs par défaut. Par exemple, vous voulez définir une hiérarchie naturelle, un ordre de tri personnalisé ou une granularité de dimension basée sur un attribut non-clé. Pour plus d’informations, consultez [référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md).  
  
> [!NOTE]  
>  Les relations d'attributs sont appelées propriétés de membre dans les expressions MDX (Multidimensional Expressions).  
  
## <a name="natural-hierarchy-relationships"></a>Relations de hiérarchie naturelle  
 Une hiérarchie une hiérarchie naturelle quand chaque attribut inclus dans la hiérarchie définie par l'utilisateur possède une relation un-à-plusieurs avec l'attribut se trouvant immédiatement au-dessous de lui. Imaginons par exemple une dimension Customer basée sur une table source relationnelle avec huit colonnes :  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Age  
  
-   Sexe  
  
-   E-mail  
  
-   City  
  
-   Country  
  
-   Région  
  
 La dimension Analysis Services correspondante a sept attributs :  
  
-   Customer (basée sur CustomerKey, avec CustomerName fournissant les noms des membres)  
  
-   Age, Gender, Email, City, Region, Country  
  
 Les relations représentant des hiérarchies naturelles sont appliquées en créant une relation d'attribut entre l'attribut d'un niveau et l'attribut du niveau qui se trouve au-dessous. Pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ceci spécifie une relation naturelle et une agrégation potentielle. Dans la dimension Customer, une hiérarchie naturelle existe pour les attributs Country, Region, City et Customer. La hiérarchie naturelle pour `{Country, Region, City, Customer}` est décrite en ajoutant les relations d'attributs suivantes :  
  
-   l'attribut Country en tant que relation d'attribut de l'attribut Region ;  
  
-   l'attribut Region en tant que relation d'attribut de l'attribut City ;  
  
-   l'attribut City en tant que relation d'attribut de l'attribut Customer.  
  
 Pour parcourir les données du cube, vous pouvez également créer une hiérarchie définie par l’utilisateur qui ne représente pas une hiérarchie naturelle dans les données (appelée hiérarchie *ad hoc* ou de *création de rapports* ). Par exemple, vous pouvez créer une hiérarchie définie par l'utilisateur basée sur `{Age, Gender}`. Les utilisateurs ne voient aucune différence quant à la façon dont les deux hiérarchies se comportent, bien que la hiérarchie naturelle bénéficie de structures d’agrégation et d’indexation, qui sont masquées par l’utilisateur, ce qui compte pour les relations naturelles dans les données sources.  
  
 La propriété `SourceAttribute` d'un niveau détermine l'attribut utilisé pour décrire le niveau. La propriété `KeyColumns` de l'attribut spécifie la colonne de la vue de source de données qui fournit les membres. La propriété `NameColumn` de l'attribut peut spécifier une colonne de nom différente pour les membres.  
  
 Pour définir un niveau dans une hiérarchie définie par l’utilisateur à l’aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , le **Concepteur de dimensions** vous permet de sélectionner un attribut de dimension, une colonne dans une table de dimension ou une colonne d’une table associée incluse dans la vue de source de données pour le cube. Pour plus d’informations sur la création de hiérarchies définies par l’utilisateur, consultez [créer des hiérarchies définies par l’utilisateur](../multidimensional-models/user-defined-hierarchies-create.md).  
  
 Dans Analysis Services, une hypothèse est généralement faite à propos du contenu des membres. Les membres feuilles n'ont pas de descendants et contiennent des données dérivées des sources de données sous-jacentes. Les membres non-feuilles ont des descendants et contiennent des données dérivées des agrégations effectuées sur les membres enfants. Dans les niveaux agrégés, les membres sont basés sur les agrégations des niveaux inférieurs. Par conséquent, quand la propriété `IsAggregatable` est définie à `False` sur un attribut source pour un niveau, aucun attribut pouvant faire l'objet d'une agrégation ne peut être ajouté en tant que niveau au dessus de cet attribut.  
  
## <a name="defining-an-attribute-relationship"></a>Définition d'une relation d'attribut  
 La principale contrainte lorsque vous créez une relation d'attribut consiste à veiller à ce que l'attribut auquel la relation d'attribut fait référence ne dispose que d'une seule valeur pour chaque membre de l'attribut auquel la relation d'attribut appartient. Par exemple, si vous définissez une relation entre un attribut City (Ville) et un attribut State (État), chaque Ville ne peut être liée qu'à un seul État.  
  
## <a name="attribute-relationship-queries"></a>Requêtes de relations d'attributs  
 Vous pouvez utiliser des requêtes MDX pour extraire des données des relations d'attributs, sous forme de propriétés, avec le mot clé `PROPERTIES` de l'instruction MDX `SELECT`. Pour plus d’informations sur l’utilisation de MDX pour récupérer des propriétés de membre, consultez [utilisation de propriétés de membre &#40;&#41;MDX ](../multidimensional-models/mdx/mdx-member-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](attributes-and-attribute-hierarchies.md)   
 [Référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md)   
 [Hiérarchies utilisateur](user-hierarchies.md)   
 [Propriétés de la hiérarchie définie par l'utilisateur](user-hierarchies-properties.md)  
  
  
