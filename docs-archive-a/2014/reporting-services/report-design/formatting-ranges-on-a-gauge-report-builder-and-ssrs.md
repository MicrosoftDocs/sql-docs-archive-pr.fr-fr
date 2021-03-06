---
title: Mise en forme de plages sur une jauge (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29574c58eef6f18d685b48dd8d695a5fc42c3e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695367"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>Mise en forme de plages sur une jauge (Générateur de rapports et SSRS)
  Une plage de jauge est une zone ou une partie de l'échelle de la jauge qui indique une sous-section importante de valeurs sur la jauge. Une plage de jauge vous permet d'indiquer visuellement lorsque la valeur de pointeur entre dans une certaine plage de valeurs. Les plages sont délimitées par une valeur de début et une valeur de fin.  
  
 Vous pouvez également utiliser des plages pour définir des différentes sections d'une jauge. Par exemple, sur une jauge dont les valeurs vont de 0 à 10, vous pouvez définir une plage rouge pour les valeurs de 0 à 3, une plage jaune pour les valeurs de 4 à 7 et une plage verte pour les valeurs de 8 à 10. Si la valeur de début que vous avez spécifiée est supérieure à la valeur de fin spécifiée, les valeurs sont inversées, la valeur de début devenant alors la valeur de fin et vice versa.  
  
 Vous pouvez positionner la plage comme vous positionnez des pointeurs sur une échelle. Les propriétés **Position** et **Distance par rapport à l’échelle** déterminent la position de la plage. Pour plus d’informations, consultez [Jauges &#40;Générateur de rapports et SSRS&#41;](gauges-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des échelles sur une jauge &#40;Générateur de rapports et SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Mise en forme des pointeurs sur une jauge &#40;Générateur de rapports et SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Définir un minimum ou un maximum sur une jauge &#40;Générateur de rapports et SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [Didacticiel : ajout d’un indicateur de performance clé à un rapport &#40;Générateur de rapports&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [Jauges &#40;Générateur de rapports et SSRS&#41;](gauges-report-builder-and-ssrs.md)  
  
  
