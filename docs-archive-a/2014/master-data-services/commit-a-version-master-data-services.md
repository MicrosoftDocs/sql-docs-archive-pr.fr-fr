---
title: Activer une version (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699977"
---
# <a name="commit-a-version-master-data-services"></a>Activer une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], activez une version d’un modèle pour empêcher que des modifications ne soient apportées aux membres du modèle et à leurs attributs. Les versions activées ne peuvent pas être déverrouillées.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   L’état de la version doit être **Verrouillé**. Pour plus d’informations, consultez [Verrouiller une version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).  
  
-   Tous les membres doivent avoir été validés correctement.  
  
### <a name="to-commit-a-version"></a>Pour activer une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , dans la barre de menus, cliquez sur **Valider la version**.  
  
3.  Dans la page **Valider la version** , sélectionnez le modèle et la version à activer.  
  
4.  Cliquez sur **Valider**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un indicateur de version &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Affecter un indicateur à une version &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Copier une version &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
  
