---
title: Fonction CountDistinct (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62fab53d4f26a874ac40e0a915c4242a41c72ce0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605176"
---
# <a name="countdistinct-function-report-builder-and-ssrs"></a>Fonction CountDistinct (Générateur de rapports et SSRS)
  Retourne le nombre de toutes les valeurs non Null distinctes spécifiées par l'expression, évaluée dans le contexte de l'étendue donnée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (`Variant`) Expression sur laquelle effectuer l'agrégation.  
  
 *scope*  
 (`String`) Facultatif. Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
 *recursive*  
 (**Type énuméré**) Facultatif. `Simple` (par défaut) ou `RdlRecursive`. Indique s'il faut effectuer l'agrégation de manière récursive.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un `Integer`.  
  
## <a name="remarks"></a>Notes  
 La valeur du paramètre *scope* doit être une constante de chaîne et ne peut pas être une expression. Pour les agrégats externes ou les agrégats qui ne spécifient pas d'autres agrégats, le paramètre *scope* doit faire référence à l'étendue actuelle ou à une étendue contenante. Pour les agrégats d'agrégats, les agrégats imbriqués peuvent spécifier une étendue enfant.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   L' *expression* ne doit pas contenir `First` de fonctions, `Last` , `Previous` ou `RunningValue` .  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant affiche une expression qui calcule le nombre de valeurs non Null uniques de `Size` pour l’étendue par défaut et pour une étendue de groupe parent. L’expression est ajoutée à une cellule d’une ligne qui appartient au groupe enfant `GroupbySubcategory`. Le groupe parent est `GroupbyCategory`. L’expression affiche les résultats pour `GroupbySubcategory` (étendue par défaut) et pour `GroupbyCategory` (étendue de groupe parent).  
  
> [!NOTE]  
>  Les expressions ne doivent pas contenir de retours chariot ni de sauts de ligne réels ; ceux-ci sont inclus dans l'exemple de code pour prendre en charge des convertisseurs de documentation. Si vous copiez l'exemple suivant, supprimez les retours chariot de chaque ligne.  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
