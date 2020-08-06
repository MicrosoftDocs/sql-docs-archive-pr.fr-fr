---
title: Boîte de dialogue visibilité de ligne (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602729"
---
# <a name="row-visibility-dialog-box-report-builder"></a>Boîte de dialogue Visibilité de ligne (Générateur de rapports)
  Utilisez la boîte de dialogue **Visibilité de ligne** pour afficher ou masquer la ligne sélectionnée lorsque le rapport est exécuté pour la première fois ou pour utiliser un autre élément de rapport pour activer/désactiver la visibilité de la ligne.  
  
## <a name="options"></a>Options  
 **Lors de la première exécution du rapport**  
 Sélectionnez une option pour indiquer comment la ligne s'affiche initialement dans le rapport.  
  
 **Afficher**  
 Sélectionnez cette option pour afficher la ligne.  
  
 **Masquer**  
 Sélectionnez cette option pour masquer la ligne.  
  
 **Afficher ou masquer en fonction d'une expression**  
 Sélectionnez cette option pour faire varier la visibilité initiale à l'aide d'une expression.  
  
 Tapez une expression prenant la valeur `Boolean``True` pour masquer l'élément et la valeur `False` pour l'afficher. Cliquez sur le bouton **Expression** (*fx*) pour modifier l’expression.  
  
 **L'affichage peut être activé ou désactivé par cet élément de rapport**  
 Choisissez cette option pour afficher une image bascule qui permet à l'utilisateur d'afficher ou de masquer la ligne de rapport dans une visionneuse de rapports HTML.  
  
 Tapez ou sélectionnez le nom d'une zone de texte du rapport dans laquelle afficher une image bascule, par exemple Textbox1. La zone de texte que vous choisissez doit figurer dans l'étendue actuelle ou contenante de cet élément de rapport. Par exemple, pour afficher ou masquer les lignes associées à un groupe enfant, sélectionnez une zone de texte dans une ligne associée au groupe parent. Pour afficher ou masquer un graphique, sélectionnez une zone de texte qui est dans la même étendue contenante que le graphique, par exemple le corps du rapport ou un rectangle.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ajouter une action développer ou réduire à un élément &#40;Générateur de rapports et SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Aide Générateur de rapports pour les boîtes de dialogue, les volets et les assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Boîte de dialogue Propriétés de l’image, Général &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
