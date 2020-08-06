---
title: Éditeur de transformation de recherche de terme (onglet recherche de terme) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bb8c0bd0477d9883640cc3e4d3cb25c2a3a8b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614163"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Éditeur de transformation de recherche de terme (onglet Recherche de terme)
  L'onglet **Recherche de terme** de la boîte de dialogue **Éditeur de transformation de recherche de terme** permet de mapper une colonne d'entrée à une colonne de recherche dans une table de référence et de fournir un alias pour chaque colonne de sortie.  
  
 Pour en savoir plus sur la transformation de recherche de terme, consultez [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 À l'aide des cases à cocher, sélectionnez les colonnes d'entrées à transmettre telles quelles à la sortie. Faites glisser une colonne d'entrée vers la liste **Colonnes de référence disponibles** pour la mapper sur une colonne de recherche dans la table de référence. Les types de données prises en charge par les colonnes d'entrée et de recherche doivent correspondre et avoir pour valeur  DT_NTEXT ou DT_WSTR. Sélectionnez une ligne de mappage et cliquez avec le bouton droit pour modifier les mappages dans la boîte de dialogue [Créer des relations](data-flow/transformations/create-relationships.md) .  
  
 **Colonnes de référence disponibles**  
 Affiche les colonnes disponibles dans la table de référence. Choisissez la colonne qui contient la liste de termes correspondants.  
  
 **Colonne SQL directe**  
 Permet de sélectionner des colonnes dans la liste des colonnes d'entrée disponibles. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 **Alias de colonne de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. La valeur par défaut correspond au nom de la colonne. Cependant, vous pouvez choisir un nom unique descriptif.  
  
 **Configurer la sortie d’erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../../2014/integration-services/configure-error-output.md) pour spécifier les options de gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche de terme &#40;onglet de la table de référence&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche de terme &#40;onglet Avancé&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Transformation d'extraction de terme](data-flow/transformations/term-extraction-transformation.md)  
  
  
