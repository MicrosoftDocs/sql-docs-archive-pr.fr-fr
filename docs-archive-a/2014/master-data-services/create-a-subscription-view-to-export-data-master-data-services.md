---
title: Créer une vue d’abonnement (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611846"
---
# <a name="create-a-subscription-view-master-data-services"></a>Créer une vue d'abonnement (Master Data Services)
  Créez une vue d’abonnement lorsque vous souhaitez créer une vue de vos données dans la [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données afin qu’elles soient utilisées par les systèmes d’abonnement.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Gestion de l'intégration** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Pour créer une vue d'abonnement  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion de l'intégration**.  
  
2.  Dans la barre de menus, cliquez sur **Créer des vues**.  
  
3.  Sur la page **vues d’abonnement** , cliquez sur Ajouter une vue d' **abonnement**.  
  
4.  Dans le volet **créer une vue d’abonnement** , dans la zone nom de la vue d' **abonnement** , tapez un nom pour la vue.  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Sélectionnez l’option **version** ou **indicateur de version** , puis sélectionnez dans la liste correspondante.  
  
    > [!TIP]  
    >  Créez une vue d'abonnement selon un indicateur de version. Lorsque vous verrouillez une version, vous pouvez réaffecter l'indicateur à une version ouverte sans mettre à jour la vue d'abonnement.  
  
7.  Sélectionnez l’option **entité** ou **hiérarchie dérivée** , puis sélectionnez dans la liste correspondante.  
  
8.  Dans la liste **Format** , sélectionnez un format de vue d'abonnement.  
  
9. Si vous avez sélectionné **Niveaux explicites** ou **Niveaux dérivés** dans la liste **Format** , tapez le nombre de niveaux dans la hiérarchie à inclure dans la vue.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de données &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Supprimer une vue d’abonnement &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md)   
 [Créer un indicateur de version &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
