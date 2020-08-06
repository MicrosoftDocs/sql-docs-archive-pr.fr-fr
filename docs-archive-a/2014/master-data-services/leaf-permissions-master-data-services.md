---
title: Autorisations de feuille (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706551"
---
# <a name="leaf-permissions-master-data-services"></a>Autorisations de feuille (services de données de référence)
  Les autorisations de feuille s'appliquent aux valeurs d'attribut pour tous les membres feuille d'une entité.  
  
 Pour les entités sans hiérarchies explicites activées, l'affectation d'une autorisation **Feuille** revient à affecter l'autorisation à l'entité.  
  
 **Remarques :**  
  
-   Les autorisations de feuille s'appliquent à la zone fonctionnelle **Explorateur** de l'interface utilisateur uniquement.  
  
-   Les autorisations attribuées à **Nom** et **Code** ne sont pas appliquées.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|Les membres feuille sont affichés, mais l'utilisateur ne peut ni les ajouter, ni les supprimer ni les modifier.<br /><br /> Si des membres consolidés existent, les noms et codes sont affichés, mais l'utilisateur ne peut pas les ajouter, les supprimer ni les modifier.|  
|**Mettre à jour**|Les membres feuille sont affichés et l'utilisateur peut les ajouter, les supprimer et les modifier.<br /><br /> Si des membres consolidés existent, les noms et codes sont affichés, mais l'utilisateur ne peut pas les ajouter, les supprimer ni les modifier.|  
|**Deny**|Les membres feuille pour l'entité ne sont pas affichés.|  
  
## <a name="attribute-permissions"></a>Autorisations d'attribut  
 Les autorisations d’attribut s’appliquent aux valeurs de l’attribut pour l’entité spécifique. Les utilisateurs avec des autorisations d'attribut uniquement ne peuvent pas ajouter ni supprimer des membres.  
  
|Autorisation|Description|  
|----------------|-----------------|  
|**Lecture seule**|L'attribut est affiché, mais l'utilisateur ne peut pas modifier les valeurs d'attribut.|  
|**Mettre à jour**|L'attribut est affiché et l'utilisateur peut modifier les valeurs d'attribut.|  
|**Deny**|L'attribut n'est pas affiché.<br /><br /> Remarque : vous ne pouvez pas refuser explicitement l’accès aux attributs Name et Code.|  
  
### <a name="example"></a>Exemple  
 Pour l'entité Product, affectez l'autorisation **Mise à jour** à l'attribut Subcategory. Autorisation refuser à tous les autres attributs.  
  
|Nom|Code|Subcategory (Mise à jour)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5}VTT|  
|Mountain-100|BK-M201|{5}VTT|  
  
 Dans l' **Explorateur**, vous pouvez mettre à jour toute valeur d'attribut de la colonne Subcategory. Si vous n'avez pas d'autorisation sur un attribut, l'attribut n'est pas affiché.  
  
> [!NOTE]  
>  Dans cet exemple, Subcategory est un attribut basé sur un domaine, basé sur l'entité SubcategoryList. Vous pouvez sélectionner une sous-catégorie différente pour Mountain-100, mais vous ne pouvez pas ajouter ni supprimer des membres dans l'entité SubcategoryList.  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md)   
 [Autorisations consolidées &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
