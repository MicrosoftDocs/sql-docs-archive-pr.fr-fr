---
title: Constantes dans les expressions (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603895"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a>Constantes dans les expressions (Générateur de rapports et SSRS)
  Une constante se compose de texte littéral ou de texte prédéfini. Le processeur de rapports a accès aux constantes prédéfinies afin que, lorsque vous les incluez dans une expression, les valeurs qu'elles représentent soient substituées dans l'expression avant son évaluation.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a>Texte littéral  
 Dans une expression, le texte littéral est le texte qui figure entre guillemets doubles. Vous pouvez également taper le texte directement dans une zone de texte sans guillemets doubles s'il ne fait pas partie d'une expression. Si la valeur de la zone de texte ne commence pas par un signe égal (=), le texte est traité comme texte littéral. Le tableau suivant répertorie plusieurs exemples de texte littéral dans une expression.  
  
|Constant|Texte affiché|Texte de l'expression|  
|--------------|------------------|---------------------|  
|Report run at:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Adventure Works Cycles|Adventure Works Cycles|Adventure Works Cycles|  
|[Texte affiché entre crochets]|\\[Texte affiché entre crochets\\]|[Texte affiché entre crochets]|  
  
## <a name="rdl-constants"></a>Constantes RDL  
 Vous pouvez utiliser des constantes définies en RDL (Report Definition Language) dans une expression. Dans la boîte de dialogue **Expression** , les constantes apparaissent lorsque vous créez une expression pour une propriété de rapport qui accepte uniquement certaines valeurs valides, également appelées types énumérés. Le tableau suivant contient deux exemples.  
  
|Propriété|Description|Valeurs|  
|--------------|-----------------|------------|  
|TextAlign|Valeurs valides pour aligner le texte dans une zone de texte.|Général, Gauche, Centre, Droit|  
|BorderStyle|Valeurs valides pour une ligne ajoutée à un rapport.|Par défaut, Aucune, Pointillés, Tirets, Unie, Double, Tiret-point, Tiret-point-point|  
  
## <a name="visual-basic-constants"></a>Constantes Visual Basic  
 Vous pouvez utiliser des constantes définies dans la bibliothèque d'exécutables [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] dans une expression. Par exemple, vous pouvez utiliser la constante `DateInterval.Day`. Pour la date du 10 janvier 2008, l'expression suivante retourne le nombre 10 :  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a>Constantes CLR  
 Vous pouvez utiliser des constantes définies dans les classes CLR (Common Language Runtime) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dans une expression. Le tableau suivant contient un exemple de couleur définie par le système.  
  
|Constant|Description|  
|--------------|-----------------|  
|MistyRose|Lorsque vous créez une expression pour une propriété de rapport basée sur la couleur d'arrière-plan, vous pouvez spécifier une couleur par nom. Les noms valides sont répertoriés dans la boîte de dialogue **Expression** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue expression](../expression-dialog-box.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md)   
 [Boîte de dialogue Expression &#40;Générateur de rapports&#41;](../expression-dialog-box-report-builder.md)  
  
  
