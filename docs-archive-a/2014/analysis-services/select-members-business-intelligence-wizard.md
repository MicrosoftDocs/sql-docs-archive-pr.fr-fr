---
title: Sélectionner les membres (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd5f184e0d9670725609531b6d0a101f8e7f8647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603077"
---
# <a name="select-members-business-intelligence-wizard"></a>Sélectionner les membres (Assistant Business Intelligence)
  Utilisez la page **Sélectionner les membres** pour déterminer à quels membres l'Assistant Business Intelligence doit appliquer la fonction de conversion monétaire spécifiée à la page **Définir les options de conversion monétaire** .  
  
> [!NOTE]  
>  Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Dimension de mesures**  
 Sélectionnez cette option afin d'appliquer la fonctionnalité de conversion monétaire à une ou plusieurs mesures du cube.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Types de mesure intégrés**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour la mesure spécifiée.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures de taux qui contient le taux de change à utiliser lors de la conversion de la mesure sélectionnée à la section **Types de mesures intégrés** .|  
  
 **Hiérarchie de comptes**  
 Sélectionnez cette option afin d'appliquer la fonctionnalité de conversion monétaire à un ou plusieurs membres dans la hiérarchie de comptes de la dimension incluse dans le cube. La hiérarchie de compte est la hiérarchie dans la dimension de compte dont la `Type` propriété est définie sur *Account*.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Membre du compte**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour le membre spécifié de la hiérarchie de comptes.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures Taux qui contient le taux de change à utiliser lors de la conversion des mesures relatives au membre choisi dans **Membre du compte** .|  
  
 **Hiérarchie de comptes basée sur le type**  
 Sélectionnez afin d'appliquer la fonctionnalité de conversion monétaire à tous les membres d'attributs dans la hiérarchie de comptes dont la propriété `Type` est définie sur le type de compte indiqué.  
  
 Une fois cette option sélectionnée, la grille affiche les options répertoriées dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Type de compte**|Sélectionnez cette option afin d'inclure la fonctionnalité de conversion monétaire pour le type de compte spécifié.|  
|**Mesures**|Sélectionnez la mesure dans le groupe de mesures Taux qui contient le taux de change à utiliser lors de la conversion des mesures relatives aux membres d'attributs dont le type de compte correspond à celui indiqué dans **Type de compte** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services-données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
