---
title: Éditeur de transformation d’extraction de terme (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703120"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Éditeur de transformation d'extraction de terme (onglet Avancé)
  Utilisez l’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation d’extraction de terme** pour définir les propriétés de l’extraction, telles que la fréquence et la longueur, et indiquer si les mots ou les phrases doivent être extraits.  
  
 Pour en savoir plus sur la transformation d'extraction de terme, consultez [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Indique que la transformation extrait uniquement des noms individuels.  
  
 **Expression nominale**  
 Indique que la transformation extrait uniquement des expressions nominales.  
  
 **Nom et expression nominale**  
 Indique que la transformation extrait des noms et des expressions nominales.  
  
 **Fréquence**  
 Indique que le score correspond à la fréquence du terme.  
  
 **TFIDF**  
 Indique que le score correspond à la valeur TFIDF du terme. Le score TFIDF est le produit de la fréquence des termes (TF, Term Frequency) et de la fréquence inverse de documents (IDF, Inverse Document Frequency), défini comme suit : TFIDF d’un terme T = (fréquence de T) * log((#lignes en entrée) / (#lignes ayant T))  
  
 **Seuil de fréquence**  
 Définissez le nombre d'occurrences d'un mot ou d'une expression avant son extraction. La valeur par défaut est 2.  
  
 **Longueur maximale du terme**  
 Définissez la longueur maximale d'une expression en nombre de mots. Cette option affecte uniquement les expressions nominales. La valeur par défaut est 12.  
  
 **Utiliser l'extraction de terme respectant la casse**  
 Indiquez si l'extraction doit respecter la casse. Par défaut, il s’agit de `False`.  
  
 **Configurer la sortie d’erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../../2014/integration-services/configure-error-output.md) pour spécifier la gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’extraction de terme &#40;onglet extraction de terme&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Éditeur de transformation d’extraction de terme &#40;onglet exclusion&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Transformation de recherche de terme](data-flow/transformations/lookup-transformation.md)  
  
  
