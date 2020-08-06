---
title: Éditeur de transformation de recherche (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696983"
---
# <a name="lookup-transformation-editor-general-page"></a>Éditeur de transformation de recherche (page Général)
  Utilisez la page **Général** de la boîte de dialogue Éditeur de transformation de recherche pour sélectionner le mode de cache ainsi que le type de connexion et pour spécifier comment gérer les lignes sans entrées correspondantes.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Cache complet**  
 Générez et chargez le dataset de référence dans le cache avant l'exécution de la transformation de recherche.  
  
 **Cache partiel**  
 Générez le dataset de référence pendant l'exécution de la transformation de recherche. Chargez dans le cache les lignes avec des entrées correspondantes dans le dataset de référence et celles sans entrées correspondantes dans le dataset.  
  
 **Aucun cache**  
 Générez le dataset de référence pendant l'exécution de la transformation de recherche. Aucune donnée n'est chargée dans le cache.  
  
 **Gestionnaire de connexions du cache**  
 Configurez la transformation de recherche pour utiliser un gestionnaire de connexions du cache. Cette option n'est disponible que si l'option Cache complet est sélectionnée.  
  
 **Gestionnaire de connexions OLE DB**  
 Configurez la transformation de recherche pour utiliser un gestionnaire de connexions OLE DB.  
  
 **Spécifier comment gérer les lignes sans entrées correspondantes**  
 Sélectionnez une option pour gérer les lignes qui ne correspondent pas au moins à une entrée dans le dataset de référence.  
  
 Lorsque vous sélectionnez **Rediriger les lignes vers la sortie sans correspondance**, les lignes sont redirigées vers une sortie sans correspondance et ne sont pas gérées comme des erreurs. L'option **Erreur** figurant dans la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de transformation de recherche** n'est pas disponible.  
  
 Lorsque vous sélectionnez une autre option dans la zone de liste **Spécifier comment gérer les lignes sans entrées correspondantes** , les lignes sont gérées comme des erreurs. L'option **Erreur** de la page **Sortie d'erreur** est disponible.  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) sur blogs.msdn.com  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions du cache](connection-manager/cache-connection-manager.md)   
 [Éditeur de transformation de recherche &#40;page connexion&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Éditeur de transformation de recherche &#40;page colonnes&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Éditeur de transformation de recherche &#40;&#41;de page avancé](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Éditeur de transformation de recherche &#40;page Sortie d’erreur&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
