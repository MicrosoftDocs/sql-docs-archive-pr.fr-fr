---
title: Spécifier la clé et le type de la dimension (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612518"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Spécifier la clé et le type de la dimension (Assistant Dimension)
  Utilisez la page **Spécifier la clé et le type de la dimension** pour définir l’attribut de clé de la dimension et indiquer si celle-ci est une dimension à variation lente (SCD).  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Construire la dimension sans utiliser de source de données** dans la page **Sélectionner la méthode de construction** et **Dimension standard** dans la page **Sélectionner le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Attribut clé**  
 Sélectionnez l'attribut clé de la dimension.  
  
> [!NOTE]  
>  Si aucun attribut n’est défini pour la dimension, la seule valeur disponible pour cette option est **Créez automatiquement l’attribut clé**. Cette valeur n'est pas disponible si un ou plusieurs attributs sont définis pour la dimension.  
  
 **Il s'agit d'une dimension variable**  
 Indique que la dimension est une dimension à variation lente. Cette option crée des colonnes et des attributs supplémentaires utilisables pour suivre dans le temps le mouvement des membres dans les hiérarchies de la dimension.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
