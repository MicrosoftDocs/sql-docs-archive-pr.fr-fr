---
title: Boîte de dialogue visibilité de ligne | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.rowvisibility.f1
- "10126"
ms.assetid: 557ecf70-62b1-47f5-9322-0ebdc809d018
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21977982cfe58a5b096b249b012a59aa9363f56c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602730"
---
# <a name="row-visibility-dialog-box"></a>Boîte de dialogue Visibilité de ligne
  Utilisez la boîte de dialogue **Visibilité de ligne** pour afficher ou masquer la ligne sélectionnée lorsque le rapport est exécuté pour la première fois ou pour utiliser un autre élément de rapport pour activer/désactiver la visibilité de la ligne.  
  
## <a name="options"></a>Options  
 **Lors de la première exécution du rapport**  
 Sélectionnez une option pour indiquer le mode d'affichage initial de l'élément de rapport dans le rapport.  
  
 **Afficher**  
 Sélectionnez cette option pour afficher l'élément de rapport.  
  
 **Masquer**  
 Sélectionnez cette option pour masquer l'élément de rapport.  
  
 **Afficher ou masquer en fonction d'une expression**  
 Sélectionnez cette option pour faire varier la visibilité initiale à l'aide d'une expression.  
  
 Tapez une expression prenant la valeur `Boolean``True` pour masquer l'élément et la valeur `False` pour l'afficher. Cliquez sur le bouton Expression (**fx**) pour modifier l’expression.  
  
 **L'affichage peut être activé ou désactivé par cet élément de rapport**  
 Choisissez cette option pour afficher une image bascule qui permet à l'utilisateur d'afficher ou de masquer cet élément de rapport dans une visionneuse de rapports HTML.  
  
 Tapez ou sélectionnez le nom d'une zone de texte du rapport dans laquelle afficher une image bascule, par exemple Textbox1. La zone de texte que vous choisissez doit figurer dans l'étendue actuelle ou contenante de cet élément de rapport. Par exemple, pour afficher ou masquer les lignes associées à un groupe enfant, sélectionnez une zone de texte dans une ligne associée au groupe parent. Pour afficher ou masquer un graphique, sélectionnez une zone de texte qui est dans la même étendue contenante que le graphique, par exemple le corps du rapport ou un rectangle.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ajouter une action développer ou réduire à un élément &#40;Générateur de rapports et SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Aide sur le Concepteur de rapports via la touche F1](tools/report-designer-f1-help.md)  
  
  
