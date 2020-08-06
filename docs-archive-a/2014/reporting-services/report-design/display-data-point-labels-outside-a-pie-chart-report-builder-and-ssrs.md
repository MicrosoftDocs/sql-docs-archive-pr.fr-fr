---
title: Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dd4f38f24d2729acacfa3520635b93d8af2e9433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704928"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a>Afficher des étiquettes de points de données à l'extérieur d'un graphique à secteurs (Générateur de rapports et SSRS)
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], l'étiquetage de graphiques à secteurs est optimisé pour afficher des étiquettes uniquement sur plusieurs tranches de données. Les étiquettes peuvent se chevaucher si le graphique à secteurs contient trop de secteurs. Une solution consiste à afficher les étiquettes à l'extérieur du graphique à secteurs, ce qui peut libérer de l'espace pour de plus longues étiquettes de données. Si les étiquettes continuent de se chevaucher, vous pouvez créer davantage d'espace pour elles en activant l'affichage 3D. Le diamètre du graphique à secteurs est ainsi réduit, ce qui libère de l'espace autour du graphique.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a>Pour afficher des étiquettes de points de données à l'intérieur d'un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, consultez [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Sur l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a>Pour afficher des étiquettes de points de données à l'extérieur d'un graphique à secteurs  
  
1.  Créez un graphique à secteurs et affichez les étiquettes de données.  
  
2.  Ouvrez le volet Propriétés.  
  
3.  Dans l’aire de conception, cliquez sur le graphique à secteurs lui-même pour afficher les propriétés de **Catégorie** dans le volet Propriétés.  
  
4.  Développez le nœud **CustomAttributes** . Une liste des attributs du graphique à secteurs s'affiche.  
  
5.  Affectez à la propriété **PieLabelStyle** la valeur **Extérieur**.  
  
6.  Affectez la valeur `PieLineColor` **Black**à la propriété. La propriété PieLineColor définit les lignes de légende de chaque étiquette de point de données.  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a>Pour empêcher les étiquettes qui se chevauchent de s'afficher à l'extérieur d'un graphique à secteurs  
  
1.  Créez un graphique à secteurs avec des étiquettes externes.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit à l’extérieur du graphique à secteurs, mais à l’intérieur des bordures du graphique, puis sélectionnez **Propriétés de la zone de graphique**. La boîte de dialogue **Propriétés de la zone de graphique** s’affiche.  
  
3.  Sous l’onglet **Options 3D** , sélectionnez **Afficher en 3D**.  
  
4.  Si vous souhaitez que le graphique dispose de davantage d’espace pour les étiquettes tout en s’affichant en deux dimensions, affectez aux propriétés **Rotation** et **Inclinaison** la valeur **0**.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques à secteurs &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Regrouper des petits secteurs sur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Afficher des valeurs en pourcentage dans un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
