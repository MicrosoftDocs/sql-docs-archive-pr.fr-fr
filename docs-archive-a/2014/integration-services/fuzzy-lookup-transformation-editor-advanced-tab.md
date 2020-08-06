---
title: Éditeur de transformation de recherche floue (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696991"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Éditeur de transformation de recherche floue (onglet Avancé)
  Utilisez l’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de recherche floue** pour définir les paramètres relatifs à une recherche floue.  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Correspondances maximales à afficher par recherche**  
 Indiquez le nombre maximal de correspondances que la transformation peut retourner pour chaque ligne d'entrée. La valeur par défaut est **1**.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au niveau du composant à l'aide du curseur. Plus la valeur est proche de 1, plus la valeur de recherche doit être proche de la valeur source pour constituer une correspondance. Si vous augmentez le seuil, vous pouvez améliorer la vitesse de correspondance étant donné qu'un plus petit nombre d'enregistrements candidats doit être pris en compte.  
  
 **Séparateurs de jetons**  
 Indiquez les séparateurs utilisés par la transformation pour marquer les valeurs de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet de la table de référence&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
