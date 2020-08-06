---
title: Chevauchement des autorisations des utilisateurs et des groupes (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7044bf6260170cbc598719ec204ddb6f861f6301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698358"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>Chevauchement des autorisations d'accès (Master Data Services)
  Les autorisations d'un utilisateur sont basées sur les :  
  
-   autorisations de l'appartenance aux groupes ;  
  
-   autorisations affectées explicitement à l'utilisateur.  
  
 Si un utilisateur est un membre de plusieurs groupes, et que ces groupes ont accès à Master Data Manager, les règles suivantes s'appliquent :  
  
-   **Refuser** remplace toutes les autres autorisations.  
  
-   **Met à jour** les remplacements **en lecture seule**.  
  
 Ces règles s'appliquent à la fois à l'onglet **Modèles** et à l'onglet **Membres de hiérarchie** . Les autorisations sont résolues pour chaque onglet, puis combinées. Pour plus d’informations, consultez [Mode de détermination des autorisations &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Vous pouvez afficher la résolution du chevauchement des autorisations d'accès dans l'interface utilisateur. Les onglets **Modèles** et **Membres de hiérarchie** ont tous deux une liste déroulante dans laquelle vous pouvez sélectionner **Effectives** pour afficher les autorisations effectives.  
  
## <a name="example-1"></a>Exemple 1  
 ![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 L'utilisateur appartient au Groupe 1 et au Groupe 2.  
  
 L’utilisateur a l’autorisation **lecture seule** sur l’entité Product.  
  
 Groupe 1 a l'autorisation **Mise à jour** sur l'entité Product.  
  
 Le groupe 2 a l’autorisation **lecture seule** sur l’entité Product.  
  
 Résultat : l'autorisation effective de l'utilisateur est **Mise à jour** sur l'entité Product.  
  
## <a name="example-2"></a>Exemple 2  
 ![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 L'utilisateur appartient au Groupe 1 et au Groupe 2.  
  
 L’utilisateur a l’autorisation **lecture seule** sur l’entité Product.  
  
 Groupe 1 a l'autorisation **Mise à jour** sur l'entité Product.  
  
 Groupe 2 a l'autorisation **Refuser** sur l'entité Product.  
  
 Résultat : l'autorisation effective de l'utilisateur est **Refuser** sur l'entité Product.  
  
## <a name="example-3"></a>Exemple 3  
 ![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 L'utilisateur appartient au Groupe 1 et au Groupe 2.  
  
 L'utilisateur a l'autorisation **Mise à jour** sur un groupe de membres dans un nœud de la hiérarchie.  
  
 Le groupe 1 a l’autorisation **lecture seule** sur un groupe de membres dans un nœud de la hiérarchie.  
  
 Le groupe 2 a l’autorisation **lecture seule** sur un groupe de membres dans un nœud de la hiérarchie.  
  
 Résultat : l'autorisation effective de l'utilisateur est **Mise à jour** sur les membres.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Chevauchement des autorisations de modèle et de membre &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
