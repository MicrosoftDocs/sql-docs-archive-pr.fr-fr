---
title: Examiner l’utilisation de l’agrégation (Assistant conception d’agrégation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: afbb02dae64f3f7ebd57065c3ff8a7d1e202dcf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602380"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a>Passer en revue l'utilisation d'agrégation (Assistant Conception d'agrégation)
  Utilisez la page **Passer en revue l'utilisation d'agrégation** pour configurer des paramètres d'utilisation d'agrégation.  
  
## <a name="options"></a>Options  
 **Par défaut**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut possède la valeur Par défaut. En utilisant ce paramètre, le concepteur applique une règle par défaut selon le type d'attribut et de dimension.  
  
 `Full`  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit `Full`. En utilisant ce paramètre, chaque agrégation pour le cube doit inclure cet attribut ou un attribut associé qui est inférieur dans la chaîne d'attribut. Le paramètre d'utilisation d'agrégation `Full` doit être évité lorsqu'un attribut contient de nombreux membres. S'il est spécifié pour plusieurs attributs ou pour des attributs qui ont de nombreux membres, ce paramètre peut empêcher la conception d'agrégations en raison d'une taille excessive.  
  
 **Aucun**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit Aucun. En utilisant ce paramètre, aucune agrégation pour le cube ne peut inclure cet attribut.  
  
 `Unrestricted`  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit `Unrestricted`. En utilisant ce paramètre, aucune restriction n'est placée sur le concepteur d'agrégations ; toutefois, l'attribut doit encore être évalué pour déterminer s'il constitue un candidat d'agrégation important.  
  
 **Définir tout à la valeur par défaut**  
 Sélectionnez pour définir les paramètres d'utilisation d'agrégation de tous les attributs avec la valeur par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Analysis Services assistants &#40;&#41;de données multidimensionnelles](analysis-services-wizards-multidimensional-data.md)  
  
  
