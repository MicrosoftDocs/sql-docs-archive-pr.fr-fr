---
title: Tuples | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705572"
---
# <a name="tuples"></a>Tuples
  Un tuple identifie de façon unique une coupe de données d'un cube. Le tuple est formé par une combinaison de membres de la dimension, à condition qu'il n'y ait pas deux membres ou plus appartenant à la même hiérarchie.  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a>Membres d'attribut implicites ou par défaut dans un tuple  
 Lorsque vous définissez un tuple dans une requête ou une expression MDX, vous n'avez pas besoin d'inclure le membre d'attribut de chaque hiérarchie d'attribut de manière explicite. Si un membre d'une hiérarchie d'attribut n'est pas explicitement intégré dans une requête ou une expression, le membre par défaut de la hiérarchie d'attribut en question correspond au membre d'attribut inclus implicitement dans le tuple. À moins d'être explicitement défini dans un cube, le membre par défaut de chaque hiérarchie d'attribut est le membre (All) s'il existe. Si un membre (All) n'existe pas dans une hiérarchie d'attribut, le membre par défaut est un membre au niveau supérieur de la hiérarchie d'attribut. La mesure par défaut correspond à la première mesure précisée dans le cube, sauf si une mesure par défaut est explicitement définie. Pour plus d’informations, consultez [Définir un membre par défaut](../attribute-properties-define-a-default-member.md) et [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).  
  
 Par exemple, le tuple suivant permet d'identifier une cellule unique dans la base de données Adventure Works en définissant uniquement un membre unique de la dimension de mesures.  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 L'exemple ci-dessus identifie de manière unique la cellule composée du membre Reseller Sales Amount (volume de vente du revendeur) de la dimension de mesures et du membre par défaut de chaque hiérarchie d'attribut au sein du cube. Le membre par défaut est le membre (All) de chaque hiérarchie d'attribut autre que la hiérarchie d'attribut Destination Currency (devise de destination). Le membre par défaut de la hiérarchie d'attribut Destination Currency est le membre US Dollar (membre par défaut défini dans le script MDX du cube Adventure Works).  
  
 La requête suivante retourne la valeur de la cellule référencée par le tuple spécifié dans l'exemple précédent ($80,450.596.98).  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Lorsque vous spécifiez un axe pour un jeu (composé ici d'un tuple unique) dans une requête, vous devez commencer par spécifier un jeu pour l'axe des colonnes avant de préciser un jeu pour l'axe des lignes. On peut également utiliser le terme *Axes(0)* ou simplement *0*pour désigner l’axe des colonnes. Pour plus d’informations sur les requêtes MDX, consultez [Requête MDX de base &#40;MDX&#41;](mdx-query-the-basic-query.md).  
  
### <a name="tuples-as-values-or-member-references"></a>Tuples qui référencent des valeurs ou des membres  
 Vous pouvez utiliser un tuple dans une requête pour retourner la valeur que référence le tuple dans la cellule, comme dans l'exemple précédent. Vous pouvez aussi recourir à un tuple dans une expression pour désigner de manière explicite les membres spécifiés dans ce tuple. La requête ou l'expression peut alors se servir de fonctions qui permettent de retourner ou de consommer des tuples. Vous pouvez faire appel à un tuple pour soit désigner la valeur de la cellule que le tuple spécifie, soit spécifier une combinaison de membres à utiliser dans le cadre d'une fonction.  
  
### <a name="tuple-dimensionality"></a>Dimensionnalité d'un tuple  
 La *dimensionnalité* d'un tuple désigne le classement ou l'ordre des membres au sein du tuple. Du fait que les membres implicites surviennent toujours dans le même ordre, la dimensionnalité est plus souvent abordée en termes de membres explicitement définis du tuple. Le classement des membres du tuple est primordial lorsque vous définissez un jeu de tuples. L'exemple ci-dessous présente deux membres dans un tuple sur l'axe des colonnes.  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Lorsque vous précisez de manière explicite un membre dans un tuple issu de plusieurs dimensions, vous devez mettre le tuple tout entier entre parenthèses. Lorsque vous spécifiez uniquement un seul membre dans un tuple, l'usage de parenthèses est facultatif.  
  
 Le tuple employé dans la requête de l'exemple ci-avant précise le retour de la cellule du cube à l'intersection de la mesure Reseller Sales Amount de la dimension de mesures et du membre CY 2004 de la hiérarchie d'attribut Calendar Year dans la dimension Date.  
  
> [!NOTE]  
>  Vous pouvez désigner un membre d'attribut selon son nom ou sa clé de membre. Dans l'exemple précédent, vous pouviez remplacer la référence à [CY 2004] par &[2004].  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés dans MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Espace du cube](cube-space.md)   
 [Autoexists](autoexists.md)   
 [Utilisation de membres, de tuples et de jeux &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)  
  
  
