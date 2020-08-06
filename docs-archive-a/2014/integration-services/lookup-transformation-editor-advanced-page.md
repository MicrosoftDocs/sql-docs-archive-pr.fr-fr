---
title: Éditeur de transformation de recherche (page avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23f235ef0506da7ac808d832db6ac36d53cfa604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605555"
---
# <a name="lookup-transformation-editor-advanced-page"></a>Éditeur de transformation de recherche (page Avancé)
  La page **Avancé** de la boîte de dialogue **Éditeur de transformation de recherche** permet de configurer la mise en cache partielle et de modifier l’instruction SQL pour la transformation de recherche.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Taille du cache (32 bits)**  
 Ajustez la taille du cache (en mégaoctets) pour les ordinateurs 32 bits. La valeur par défaut est 5 mégaoctets.  
  
 **Taille du cache (64 bits)**  
 Ajustez la taille du cache (en mégaoctets) pour les ordinateurs 64 bits. La valeur par défaut est 5 mégaoctets.  
  
 **Activer le cache pour les lignes sans entrées correspondantes**  
 Mettez en cache les lignes sans entrées correspondantes dans le dataset de référence.  
  
 **Allocation à partir du cache**  
 Spécifiez le pourcentage de cache à allouer aux lignes sans entrées correspondantes dans le dataset de référence.  
  
 **Modifier l'instruction SQL**  
 Modifiez l'instruction SQL utilisée pour générer le dataset de référence.  
  
> [!NOTE]  
>  L’instruction SQL facultative que vous spécifiez dans cette page substitue et remplace le nom de table que vous avez spécifié dans la page **Connexion** de **l’Éditeur de transformation de recherche**. Pour plus d’informations, consultez [Éditeur de transformation de recherche &#40;page Connexion&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).  
  
 **Définition des paramètres**  
 Mappez les colonnes d’entrée aux paramètres en utilisant la boîte de dialogue **Définition des paramètres de la requête** .  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) sur blogs.msdn.com  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de transformation de recherche &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de transformation de recherche &#40;page connexion&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Éditeur de transformation de recherche &#40;page colonnes&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Éditeur de transformation de recherche &#40;page sortie d’erreur&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [transformation de recherche floue](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
