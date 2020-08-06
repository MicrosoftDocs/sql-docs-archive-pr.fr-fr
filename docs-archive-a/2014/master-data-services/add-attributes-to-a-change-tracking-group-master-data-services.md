---
title: Ajouter des attributs à un groupe de suivi des modifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c8a13dad3ca886668c96c1886f8cd238d9adad9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614151"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Ajouter des attributs à un groupe de suivi des modifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ajoutez des attributs à un groupe de suivi des modifications lorsque vous souhaitez effectuer le suivi des modifications apportées aux valeurs d'attribut.  
  
> [!NOTE]  
>  Lorsque qu'un attribut est ajouté à un groupe de suivi des modifications et que ses valeurs changent, l'attribut est alors signalé comme modifié dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Créez une règle d'entreprise pour entreprendre une action basée sur la modification.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Les attributs doivent exister pour pouvoir être ajoutés au groupe de suivi des modifications. Pour plus d’informations, consultez [Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Pour ajouter des attributs à un groupe de suivi des modifications  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Explorateur de modèles** , dans la barre de menus, pointez sur **gérer** , puis cliquez sur **entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez effectuer le suivi des valeurs d'attribut.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Dans la page **Modifier l'entité** :  
  
    -   Si l’attribut concerne les membres feuille, dans le volet **attributs feuille** , sélectionnez l’attribut et cliquez sur **modifier l’attribut feuille**.  
  
    -   Si l’attribut est destiné à des membres consolidés, dans le volet **attributs consolidés** , sélectionnez l’attribut, puis cliquez sur **modifier l’attribut consolidé**.  
  
    -   Si l’attribut est destiné à des collections, dans le volet **attributs de collection** , sélectionnez l’attribut, puis cliquez sur modifier l' **attribut de collection**.  
  
7.  Activez la case à cocher **Activer le suivi des modifications** .  
  
8.  Dans la zone **Groupe de suivi des modifications** , tapez un numéro pour le groupe.  
  
9. Cliquez sur **Enregistrer l'attribut**.  
  
10. Dans la page **Maintenance de l'entité** , cliquez sur **Enregistrer l'entité**.  
  
11. Répétez cette procédure pour tous les attributs que vous souhaitez inclure dans le groupe. Utilisez le même numéro de groupe de suivi des modifications pour chaque attribut dans le groupe.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Initier des actions en fonction de modifications de valeurs d’attribut &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créez un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
