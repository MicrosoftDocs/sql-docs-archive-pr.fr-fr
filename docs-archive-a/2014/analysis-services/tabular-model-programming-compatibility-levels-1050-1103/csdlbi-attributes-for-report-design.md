---
title: Attributs CSDLBI pour la conception de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 61ba3a27-790e-43bc-b421-e01bf2fdbda6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee53cb3e4910e988403350bac5c993ef68b5170d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603690"
---
# <a name="csdlbi-attributes-for-report-design"></a>Attributs CSDLBI pour la conception de rapport
  Cette section décrit les attributs des extensions au CSDL pour la modélisation tabulaire qui affectent la création de requête [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
## <a name="model-attributes"></a>Attributs de modèle  
 Ces attributs sont définis sur un sous-élément d'un élément [EntityContainer](https://msdn.microsoft.com/library/bb399169.aspx) CSDL.  
  
|Nom de l’attribut|Type de données|Description|  
|--------------------|---------------|-----------------|  
|Culture|Texte|Indique la culture utilisée pour les formats monétaires. En cas d'omission, EN-US est utilisé.|  
|IsRightToLeft|Boolean|Indique si les valeurs des champs de texte doivent être lues de droite à gauche par défaut|  
  
## <a name="entity-attributes"></a>Attributs d’entité  
 Ces attributs sont définis sur un sous-élément d'un élément EntitySet ou EntityType CSDL.  
  
|Nom de l’attribut|Type de données|Description|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Texte|Identificateur utilisé pour référencer cette entité dans une requête DAX. En cas d'omission, le nom est utilisé.|  
|`Caption`|Texte|Nom complet de l'entité.|  
|`Documentation`|Texte|Texte descriptif pour aider les utilisateurs professionnels à comprendre la signification des données.|  
|`Hidden`|Boolean|Indique si l'entité doit être affichée. Par défaut, il s’agit de `false`.|  
|`CollectionCaption`|Texte|Nom au pluriel pour faire référence à un jeu d'instances de l'entité. En cas d'omission, l'attribut Caption est utilisé.|  
|`DisplayKey`|MemberRef[]|Liste triée de champs utilisés pour désigner une instance d'entité à un utilisateur professionnel. Les références peuvent inclure des propriétés d'instance et des propriétés de navigation. Lorsqu'une propriété de navigation est référencée, la valeur `DisplayKey` de l'entité cible est affichée. Si la valeur `DisplayKey` est omise, le champ Key est utilisé.|  
|`DefaultImage`|MemberRef|Référence au champ contenant une image utilisée pour désigner visuellement une instance d'entité à un utilisateur professionnel. En cas d'omission, le premier champ d'image de l'entité est utilisé, le cas échéant.|  
|`DefaultDetails`|MemberRef[]|Liste triée de champs qui représente l'ensemble par défaut des informations détaillées affichées à un utilisateur professionnel sur une instance de l'entité. En cas d'omission, les cinq (5) premiers champs de l'entité sont utilisés, à l'exception de ceux déjà référencés par `Key`, `DisplayKey` ou `DefaultImage`.|  
|`SortProperties`|MemberRef[]|Liste triée de champs selon lesquels les instances d'entité sont généralement triées. Lors du tri sur ces champs, la valeur `SortDirection` spécifiée sur chaque champ est utilisée. En cas d'omission, les champs `DisplayKey` sont utilisés|  
|`DefaultMeasure`|MemberRef|Référence à une mesure définie dans le modèle, ou à un champ numérique avec une fonction d'agrégation par défaut, pour indiquer que la mesure ou le champ doit être utilisé comme représentation par défaut pour plusieurs instances de l'entité. En cas d'omission, un nombre d'instances de l'entité est utilisé.|  
|`DefaultLocation`|MemberRef|Référence à un champ dont la valeur représente l'emplacement par défaut associé à une instance de l'entité. En cas d'omission, le premier champ d'emplacement de l'entité est utilisé, le cas échéant.|  
  
## <a name="field-attributes"></a>Attributs de champ  
 Ces attributs sont définis sur un sous-élément d'un élément d'une propriété CSDL ou d'un élément [NavigationProperty](https://msdn.microsoft.com/library/bb387104.aspx) .  
  
|Nom de l’attribut|Type de données|Description|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Texte|Identificateur utilisé pour référencer cette entité dans une requête DAX. En cas d'omission, le nom du champ est utilisé.|  
|`Caption`|Texte|Nom complet de l'entité. En cas d’omission, le champ `ReferenceName` est utilisé.|  
|`Documentation`|Texte|Texte descriptif pour aider les utilisateurs professionnels à comprendre la signification du champ.|  
|`Hidden`|Boolean|Indique si le champ doit être affiché. La valeur par défaut est `false`, qui signifie que le champ est affiché.|  
|`DisplayFolder`|Texte|Nom (chemin d'accès complet) du dossier dans lequel ce champ s'affiche. En cas d'omission, le champ s'affiche à la racine du modèle.|  
|`ContextualNameRule`|Énumération|Valeur qui indique si et comment le nom de la propriété doit être modifié en fonction du contexte dans lequel il est utilisé. Les valeurs possibles sont les suivantes : `None`, `Role`, `Merge`.|  
|`Alignment`|Énumération|Valeur indiquant comment les valeurs de champ doivent être alignées dans une présentation tabulaire. Les valeurs possibles sont les suivantes : `Default`, `Center`, `Left`, `Right`. En cas d’omission, la valeur par défaut détermine l’alignement en fonction du type de données du champ.|  
|`FormatString`|Texte|Chaîne de format .NET indiquant comment la valeur du champ doit être mise en forme par défaut. En cas d'omission, le format suivant est utilisé :<br /><br /> -Champs DateTime : date abrégée régionale ou « d »<br />-Les champs à virgule flottante et les champs intégraux avec une fonction d’agrégation par défaut : Numéro régional ou « n »<br />-Entiers sans fonction d’agrégation par défaut : nombre décimal régional ou « d »<br /><br /> Pour tous les autres types de champs, aucune chaîne de format ne s'applique.|  
|`Units`|Texte|Symbole qui est appliqué aux valeurs de champ pour exprimer des unités. En cas d'omission, les unités sont inconnues.|  
|`Width`|Integer|Largeur par défaut en caractères qui doit être réservée pour afficher les valeurs du champ dans une présentation tabulaire. En cas d’omission, une largeur par défaut est basée sur le type de données du champ.|  
|`SortDirection`|Énumération|Valeur indiquant comment les valeurs de champs sont généralement triées. Les valeurs possibles sont les suivantes : `Default`, `Ascending`, `Descending`. En cas d’omission, la valeur par défaut assigne un sens de tri est basée sur le type de données du champ.|  
|`IsRightToLeft`|Boolean|Indique si le champ contient du texte qui doit être lu de droite à gauche. En cas d'omission, le paramètre de modèle est utilisé.|  
|`OrderBy`|MemberRef|Référence à un autre champ dans le modèle qui définit l’ordre de tri pour les valeurs de ce champ. Les valeurs des deux champs doivent avoir un mappage 1:1 sinon, le comportement de tri n'est pas défini. En cas d'omission, le champ est trié selon sa propre valeur.|  
|`Contents`|Énumération|Énumération qui décrit le sous-type ou le contenu du champ. En cas d’omission, aucun sous-type particulier n’est utilisé, sauf si le type de données du champ est Binary, auquel cas l’image est supposée. Pour une liste complète des types de contenu pris en charge, consultez la documentation AMO.|  
|`DefaultAggregateFunction`|Énumération|Valeur qui indique la fonction par défaut, le cas échéant, généralement utilisée pour agréger ce champ. Les valeurs possibles sont les suivantes : `None`, `Sum`, `Average`, `Count`, `Min`, `Max`. En cas d'omission, `Sum` est utilisé pour les champs numériques, `None` pour tous les autres champs.|  
|`IsSimpleMeasure`|Boolean|Indique si une mesure est simplement un agrégat simple d'un champ numérique. De tels agrégats peuvent être facilement définis dans la requête si nécessaire et doivent donc être omis de la définition du modèle pour améliorer les performances. En cas d'omission, `false` est utilisé.|  
|`Kpi`<br /><br /> `KpiGoal`<br /><br /> `KpiStatus`|Sous-élément|Indique que l'élément de mesure doit être utilisé comme indicateur de performance clé. Le sous-élément d'indicateur de performance clé utilise les éléments KpiGoal et KpiStauts pour définir l'image et les plages cibles associées.|  
  
  
