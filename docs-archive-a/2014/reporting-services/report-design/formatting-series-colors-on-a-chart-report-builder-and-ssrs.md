---
title: Mise en forme des couleurs des séries sur un graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql12.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql12.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0e4f526e32ba38b94c5707c1ce3acc3cd073626
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695356"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a>Mise en forme des couleurs des séries sur un graphique (Générateur de rapports et SSRS)
  Reporting Services fournit plusieurs palettes intégrées pour les graphiques. Vous pouvez également définir une palette personnalisée. Par défaut, les graphiques utilisent la palette de couleurs intégrée **pastel brillant** pour remplir chaque série. Ces couleurs sont également présentes dans la légende. Lorsque plusieurs séries sont ajoutées au graphique, le graphique assigne une couleur à chaque série, dans l'ordre dans lequel les couleurs ont été définies dans la palette.  
  
 Si le nombre de séries est plus élevé que le nombre de couleurs dans la palette, le graphique réutilise des couleurs. Deux séries peuvent donc avoir la même couleur. Cela se produit fréquemment si vous utilisez un graphique à base de formes, où une couleur de la palette est assignée à chaque point de données. Pour éviter toute confusion, définissez une palette personnalisée comportant au moins autant de couleurs qu'il y a de séries dans votre graphique.  
  
 Vous pouvez sélectionner une nouvelle palette ou définir une palette personnalisée à partir du volet Propriétés. Pour plus d’informations, consultez [Définir les couleurs d’un graphique à l’aide d’une palette &#40;Générateur de rapports et SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a>Utilisation des palettes intégrées  
 Reporting Services fournit la liste des palettes intégrées prédéfinies que vous pouvez utiliser afin de définir un jeu de couleurs pour les séries de votre graphique. Toutes les palettes intégrées contiennent entre 10 et 16 valeurs de couleur. Vous ne pouvez pas inclure de nouvelles couleurs dans une palette intégrée. Par conséquent, si vous avez besoin de plus de 16 couleurs, vous devez définir une palette personnalisée.  
  
 Si vous imprimez un rapport, utilisez plutôt la palette **Nuances de gris** . Cette palette utilise des nuances de noir et de blanc pour représenter chaque série des graphiques.  
  
 La palette nommée Par défaut a été utilisée comme palette de graphique par défaut dans les versions antérieures de Reporting Services. Pour des raisons de cohérence, elle a été conservée (avec le même nom). La mise à niveau des graphiques s'effectue de façon transparente à l'aide de la palette Par défaut. Toutefois, après la mise à niveau, envisagez de changer de palette.  
  
## <a name="using-custom-palettes"></a>Utilisation des palettes personnalisées  
 Pour appliquer vos propres couleurs au graphique, utilisez une palette personnalisée. Les palettes personnalisées vous permettent d'ajouter vos propres couleurs dans l'ordre dans lequel vous souhaitez qu'elles apparaissent sur le graphique. Les palettes personnalisées sont particulièrement utiles si le nombre de séries de votre graphique est inconnu au moment de la conception. Pour plus d’informations, consultez [Définir les couleurs d’un graphique à l’aide d’une palette &#40;Générateur de rapports et SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).  
  
## <a name="using-a-color-fill-on-each-series"></a>Utilisation d'une couleur de remplissage pour chaque série  
 Vous pouvez également définir vos propres couleurs en spécifiant une couleur pour chaque série du graphique. Pour ce faire, ouvrez la boîte de dialogue **Propriétés de la série** et définissez la propriété **Couleur** du paramètre **Remplissage**. Cette opération remplace toutes les palettes définies. En général, mieux vaut utiliser une palette personnalisée pour définir vos propres couleurs. En effet, le nombre de séries dans votre dataset peut ne pas être connu jusqu'au traitement du rapport.  
  
 Cette approche est particulièrement adaptée si vous souhaitez définir une couleur de série conditionnelle, basée sur une expression.  Pour plus d’informations, consultez [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Spécifier des couleurs cohérentes pour plusieurs graphiques à base de formes &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
 [Définir les couleurs d’un graphique à l’aide d’une palette &#40;Générateur de rapports et SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)  
  
 [Mettre en surbrillance des données de graphique en ajoutant des bandes &#40;Générateur de rapports et SSRS&#41;](highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Ajouter des styles de biseau, de relief et de texture à un graphique &#40;Générateur de rapports et SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-formatting-report-builder.md)  
  
  
