---
title: Mode de détermination des autorisations (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ea3306b772224bc8602659c7e17e8dc1634f0d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611133"
---
# <a name="how-permissions-are-determined-master-data-services"></a>Mode de détermination des autorisations (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], la méthode la plus simple pour configurer la sécurité est d'affecter des autorisations d'objet de modèle à un groupe dont l'utilisateur est membre.

 La sécurité devient plus complexe lorsque :

-   sont attribués à la fois des autorisations d'objet de modèle et des autorisations des membres de la hiérarchie ;

-   l'utilisateur appartient à des groupes et l'autorisation est attribuée à la fois à l'utilisateur et aux groupes ;

-   l'utilisateur appartient à des groupes et l'autorisation est attribuée à plusieurs groupes.

## <a name="permissions-assigned-to-a-single-group-or-user"></a>Autorisations attribuées à un seul groupe ou utilisateur
 Si vous attribuez des autorisations à un seul groupe ou utilisateur, les autorisations sont déterminées selon le flux de travail suivant.

 ![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")

### <a name="step-1-effective-attribute-permissions-are-determined"></a>Étape 1 : les autorisations d'attribut effectives sont déterminées.
 La liste suivante décrit comment sont déterminées les autorisations d'attribut effectives :

-   Les autorisations attribuées aux objets de modèle déterminent les attributs auxquels un utilisateur peut accéder.

-   Tous les objets de modèle héritent automatiquement de l'autorisation de l'objet le plus proche à un niveau supérieur dans la structure du modèle.

-   Tout objet situé au même niveau que l'entité est refusé implicitement.

-   Tout objet situé à un niveau supérieur obtient un accès de navigation. Pour plus d’informations sur l’accès de navigation, consultez [&#40;de l’accès de navigation Master Data Services&#41;](navigational-access-master-data-services.md).

 Dans cet exemple, l’autorisation **en lecture seule** est assignée à une entité et cette autorisation est héritée par son attribut, qui se trouve à un niveau inférieur dans la structure du modèle. Le modèle fournit un accès de navigation à cette entité et à son attribut. L'autre entité dans le modèle ne dispose d'aucune autorisation explicite attribuée et n'hérite d'aucune autorisation, donc elle est refusée implicitement.

 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")

### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a>Étape 2 : si les autorisations des membres de la hiérarchie sont attribuées, les autorisations de membre effectives sont déterminées.
 La liste suivante explique comment les autorisations des membres de la hiérarchie effectives sont déterminées :

-   Les autorisations attribuées aux nœuds de la hiérarchie déterminent les membres auxquels un utilisateur peut accéder.

-   Tous les nœuds dans une hiérarchie héritent automatiquement de l'autorisation de l'objet le plus proche à un niveau supérieur dans la structure de la hiérarchie.

-   Tout nœud situé au même niveau est refusé implicitement.

-   Tout nœud situé aux niveaux supérieurs auquel aucune autorisation n'est attribuée est refusé implicitement.

 Dans cet exemple, l’autorisation **lecture seule** est affectée à un nœud de la hiérarchie et cette autorisation est héritée par un nœud à un niveau inférieur dans la structure de la hiérarchie. La racine n'a aucune autorisation attribuée, donc elle est refusée implicitement. L'autre nœud dans la structure de hiérarchie ne dispose d'aucune autorisation explicite attribuée et n'hérite d'aucune autorisation, donc il est refusé implicitement.

 ![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")

### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a>Étape 3 : l'intersection des autorisations d'attribut et de membre est déterminée.
 Si les autorisations d'attribut effectives sont différentes des autorisations de membre effectives, les autorisations doivent être déterminées pour chaque valeur d'attribut individuelle. Pour plus d’informations, consultez [Chevauchement des autorisations de modèle et de membre &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).

## <a name="permissions-assigned-to-multiple-groups"></a>Autorisations attribuées à plusieurs groupes
 Si un utilisateur appartient à un ou plusieurs groupes et que les autorisations sont attribuées à la fois à l'utilisateur et aux groupes, le flux de travail devient plus complexe.

 ![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")

 Dans ce cas, le chevauchement des autorisations de l'utilisateur et du groupe doit être résolu avant que les autorisations de l'objet de modèle et des membres de la hiérarchie puissent être comparées. Pour plus d’informations, consultez [Chevauchement des autorisations d’accès &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).

## <a name="see-also"></a>Voir aussi
 Le [chevauchement des autorisations d’accès &#40;d’utilisateurs et de groupes Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) le [chevauchement des autorisations de modèle et de membre &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)


