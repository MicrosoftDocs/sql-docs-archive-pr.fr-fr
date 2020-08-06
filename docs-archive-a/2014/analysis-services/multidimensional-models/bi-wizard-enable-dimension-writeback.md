---
title: Activer l’écriture différée de la dimension | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
ms.openlocfilehash: cba4a54e8a51d022c6f84a4c81d32f359a95692a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603109"
---
# <a name="enable-dimension-writeback"></a>Activer l'écriture différée de la dimension
  Ajoutez la fonctionnalité d'écriture en différé de la dimension à un cube ou à une dimension afin de permettre aux utilisateurs de modifier manuellement la structure et les membres de la dimension. Les mises à jour dans une dimension activée en écriture sont enregistrées directement dans la table de la dimension. Cette amélioration modifie la définition de la propriété `WriteEnabled` pour une dimension.  
  
 Pour ajouter l’écriture différée de la dimension, utilisez l’Assistant Business Intelligence, puis sélectionnez l’option **Activer l’écriture différée de la dimension** dans la page **Choisir des améliorations** . Cet Assistant vous guide tout au long des étapes de sélection d'une dimension à laquelle vous souhaitez appliquer l'écriture en différé et de définition de cette option pour la dimension sélectionnée.  
  
> [!NOTE]  
>  L'écriture différée est prise en charge uniquement pour les mini-Data Warehouse et les bases de données relationnelles SQL Server.  
  
## <a name="selecting-a-dimension"></a>Sélection d'une dimension  
 Dans la première page **Activer l’écriture différée de la dimension** de l’Assistant, vous spécifiez la dimension à laquelle vous souhaitez appliquer l’écriture différée. L'amélioration que constitue l'écriture différée ajoutée à cette dimension se traduit par des modifications de la dimension. Ces modifications seront héritées par tous les cubes contenant la dimension sélectionnée.  
  
## <a name="setting-dimension-writeback-capability"></a>Définition de la fonctionnalité d'écriture en différé de la dimension  
 Dans la deuxième page **Activer l’écriture différée de la dimension** de l’Assistant, vous paramétrez réellement l’option **Activer l’écriture différée de la dimension** . Lorsque cette option est automatiquement sélectionnée, la propriété `WriteEnabled` de la dimension a la valeur `True`. Lorsque cette option est automatiquement désactivée, la propriété a la valeur `False`.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous créez un membre, vous devez inclure chaque attribut dans une dimension. Vous ne pouvez pas insérer un membre sans définir la valeur de l'attribut clé de la dimension. Par conséquent, la création de membres est soumise aux contraintes (telles que valeurs de clés non NULL) définies dans la table de dimension. Vous devez également tenir compte des colonnes éventuellement spécifiées par les propriétés de dimension, telles que les colonnes spécifiées dans les propriétés de dimension `CustomRollupColumn`, `CustomRollupPropertiesColumn` ou `UnaryOperatorColumn`.  
  
> [!WARNING]  
>  Si vous utilisez SQL Azure comme source de données pour effectuer une écriture différée dans une base de données Analysis Services, l'opération échoue. Il s'agit d'un comportement par défaut, car l'option de fournisseur qui active plusieurs jeux de résultats actifs MARS n'est pas activée par défaut.  
>   
>  La solution consiste à ajouter le paramètre suivant dans la chaîne de connexion, afin de prendre en charge MARS et d'activer l'écriture différée :  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Pour plus d’informations, consultez [utilisation de plusieurs jeux de résultats actifs &#40;&#41;mars ](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
