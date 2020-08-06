---
title: Créer une hiérarchie dérivée (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 20469ad30222e43a3104503cc32187c2e6512743
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701256"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Créer une hiérarchie dérivée (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie dérivée lorsque vous avez besoin d'une hiérarchie basée sur le niveau qui vérifie que les membres existent au niveau correct. Les hiérarchies dérivées sont basées sur les relations d'attribut basé sur un domaine qui existent dans un modèle.  
  
> [!NOTE]  
>  S'il n'existe pas de valeur d'attribut basé sur un domaine pour un membre, le membre n'est pas inclus dans la hiérarchie dérivée. Pour demander une valeur d’attribut basé sur un domaine pour tous les membres, consultez [Requérir des valeurs d’attribut &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Pour créer une hiérarchie dérivée  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **vue du modèle** , dans la barre de menus, pointez sur **gérer** , puis cliquez sur **hiérarchies dérivées**.  
  
3.  Dans la page **Maintenance de la hiérarchie dérivée** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Cliquez sur **Ajouter une hiérarchie dérivée**.  
  
5.  Dans la page **Ajouter une hiérarchie dérivée** , renseignez la zone **Nom de la hiérarchie dérivée** .  
  
    > [!TIP]  
    >   Utilisez un nom qui décrit les niveaux dans la hiérarchie, par exemple **Product to Subcategory to Category**.  
  
6.  Cliquez sur **Enregistrer la hiérarchie dérivée**.  
  
7.  Dans la page **modifier la hiérarchie dérivée** , dans le volet **entités et hiérarchies disponibles** , cliquez sur une entité ou une hiérarchie et faites-la glisser vers le volet **niveaux actuels** .  
  
8.  Continuez à faire glisser des entités ou des hiérarchies jusqu'à ce que votre hiérarchie soit terminée.  
  
9. Cliquez sur **Précédent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec des majuscules &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
