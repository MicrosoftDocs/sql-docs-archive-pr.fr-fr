---
title: Spécifier le nombre d’objets (Assistant conception d’agrégation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66b972395f86746b2d08df234db8aa0c71d03fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611338"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a>Spécifier le nombre d'objets (Assistant Conception d'agrégation)
  La page **Spécifier le nombre d'objets** permet de calculer automatiquement le nombre d'objets inclus dans le cube ou d'entrer une estimation manuellement. L'Assistant Conception d'agrégation utilise le nombre d'objets pour évaluer la capacité de stockage nécessaire.  
  
## <a name="options"></a>Options  
 **Objets de cube**  
 Affiche les dimensions et les attributs du cube. Seuls les attributs dont la propriété a la `AggregationUsage` valeur `None` dans la page **vérifier l’utilisation** de l’agrégation de l’Assistant sont affichés, car il s’agit des seuls attributs qui nécessitent la spécification des nombres.  
  
 **Nombre estimé**  
 Affiche le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les dimensions de base de données. Vous pouvez taper une valeur à utiliser comme nombre estimé ou vous pouvez calculer les valeurs du compteur estimées. Pour calculer les valeurs de nombre, tapez `0` dans le champ, puis cliquez sur **nombre**. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
 **Nombre de partitions**  
 (Facultatif) Tapez le nombre estimé de lignes dans le groupe de mesures et tapez l'estimation du nombre de membres d'attribut dans les partitions.  
  
 **Count**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Analysis Services assistants &#40;&#41;de données multidimensionnelles](analysis-services-wizards-multidimensional-data.md)  
  
  
