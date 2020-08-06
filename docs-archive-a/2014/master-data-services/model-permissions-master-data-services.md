---
title: Autorisations de modèle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605528"
---
# <a name="model-permissions-master-data-services"></a>Autorisations de modèle (Master Data Services)
  Les autorisations de modèle s'appliquent à l'ensemble des entités, attributs, groupes d'attributs, hiérarchies dérivées, hiérarchies explicites et collections qui existent dans le modèle. Les autorisations affectées au modèle peuvent être remplacées pour tout objet individuel.  
  
> [!NOTE]  
>  Si l'utilisateur est administrateur de modèle, le modèle est affiché dans toutes les zones fonctionnelles de l'interface utilisateur. Sinon, le modèle est affiché uniquement dans la zone fonctionnelle **Explorateur** . Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|Dans l' **Explorateur**, le modèle est affiché, mais l’utilisateur ne peut pas ajouter ou supprimer des membres et ne peut pas mettre à jour les valeurs d’attribut, les appartenances de hiérarchie ou les appartenances de collection.|  
|**Mettre à jour**|Dans l' **Explorateur**, le modèle est affiché et l’utilisateur peut ajouter et supprimer des membres, peut mettre à jour les valeurs d’attribut, les appartenances de hiérarchie et les appartenances de collection.|  
|**Deny**|Le modèle n’est pas affiché.|  
  
 Lorsque vous affectez l'autorisation à un modèle, l'utilisateur obtient l'accès à toutes les versions du modèle. Vous ne pouvez pas affecter d'autorisation à une version individuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Autorisations d’entité &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md)   
 [Autorisations de collection &#40;Master Data Services&#41;](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
