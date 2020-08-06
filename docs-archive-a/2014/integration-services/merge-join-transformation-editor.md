---
title: Éditeur de transformation de jointure de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0d15d1233c2e0ff836e9dbd17459e56c48183f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611159"
---
# <a name="merge-join-transformation-editor"></a>Éditeur de transformation de jointure de fusion
  La boîte de dialogue **Éditeur de transformation de jointure de fusion** permet de préciser le type de jointure, les colonnes qui composent cette dernière et les colonnes de sortie, afin de pouvoir fusionner deux entrées combinées par une opération de jointure.  
  
> [!IMPORTANT]  
>  La transformation de jointure de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Pour en savoir plus sur la transformation de jointure de fusion, consultez [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).  
  
## <a name="options"></a>Options  
 **Type de jointure**  
 Permet de préciser l'utilisation d'une jointure interne, externe gauche ou entière.  
  
 **Échanger les entrées**  
 Permet d’intervertir l’ordre des entrées par le bouton **Échanger les entrées** . Ceci peut s'avérer utile dans le cas de jointure externe gauche.  
  
 **Entrée**  
 Permet de sélectionner, dans la liste des entrées disponibles, chaque colonne à inclure à la sortie fusionnée.  
  
 Les entrées se présentent sous forme de deux tables distinctes. Permet de choisir les colonnes à inclure dans la sortie. Pour créer une jointure entre tables, faites glisser les colonnes. Pour supprimer une jointure, sélectionnez-la et appuyez sur la touche Suppr.  
  
 **Colonne d'entrée**  
 Permet de choisir une colonne à inclure à la sortie fusionnée d'après la liste de colonnes disponibles dans l'entrée sélectionnée.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Trier des données pour les transformations de fusion et de jointure de fusion](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Étendre un DataSet à l’aide de la transformation de jointure de fusion](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Transformation de fusion](data-flow/transformations/merge-transformation.md)   
 [Transformation d'union totale](data-flow/transformations/union-all-transformation.md)  
  
  
