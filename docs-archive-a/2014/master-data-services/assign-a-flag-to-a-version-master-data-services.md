---
title: Affecter un indicateur à une version (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2de0d0d8d8ea96814e13b9123fe4fcd4782d6bef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614146"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>Affecter un indicateur à une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], affectez un indicateur à une version pour indiquer la version que les utilisateurs ou les systèmes d'abonnement doivent utiliser.  
  
> [!NOTE]  
>  Les indicateurs de version ne peuvent être affectés qu'à une seule version à la fois. Si vous affectez un indicateur qui est déjà affecté à une autre version, l'indicateur est déplacé vers la version que vous avez sélectionnée.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Vous devez créer un indicateur de version avant de l'affecter. Pour plus d’informations, consultez [Créer un indicateur de version &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md).  
  
### <a name="to-assign-a-flag-to-a-version"></a>Pour affecter un indicateur à une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , dans la ligne correspondant à la version à laquelle vous souhaitez affecter un indicateur, double-cliquez sur la cellule dans la colonne **Indicateur** .  
  
3.  Dans la liste, sélectionnez l'indicateur à affecter.  
  
    > [!NOTE]  
    >  Si l’indicateur n’est pas disponible, il se peut qu’il soit uniquement disponible pour les versions dont l’état est **Activé** . Pour le vérifier, allez à la page **Gérer les indicateurs de version** et recherchez l’indicateur dans le champ **Versions activées uniquement** .  
  
4.  Appuyez sur ENTRÉE pour enregistrer la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un indicateur de version &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)   
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
  
