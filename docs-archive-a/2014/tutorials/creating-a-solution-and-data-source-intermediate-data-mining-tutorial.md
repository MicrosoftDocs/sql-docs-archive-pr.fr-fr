---
title: Création d’une solution et d’une source de données (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 48009fae653c4c1a231380e8d286363168ae28d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602700"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>Création d'une solution et d'une source de données (Didacticiel sur l'exploration de données intermédiaire)
  Pour utiliser l'exploration de données, vous devez d'abord créer un projet dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] à l'aide du modèle **Projet multidimensionnel et d'exploration de données Analysis Services**. Lorsque vous ouvrez le modèle, il charge dans le concepteur tous les schémas dont vous pourriez avoir besoin pour l'exploration de données : sources de données, structures et modèles d'exploration de données, et même cubes si votre structure d'exploration de données utilise des données multidimensionnelles.  
  
 Lorsque vous créez le projet, votre solution est stockée sous forme de fichier local jusqu'à ce que la solution soit déployée. Lorsque vous déployez la solution, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] recherche le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] spécifié dans les propriétés du projet, et crée une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avec le même nom que le projet. Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise l'instance **localhost** pour les nouveaux projets. Si vous utilisez une instance nommée ou spécifiez un autre nom pour l'instance par défaut, vous devez déplacer la propriété de la base de données de déploiement du projet vers l'emplacement auquel vous souhaitez créer vos objets d'exploration de données.  
  
 Pour plus d’informations sur les [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projets, consultez [créer un projet Analysis Services &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt).  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>Pour créer un projet Analysis Services pour ce didacticiel  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Sélectionnez **Projet multidimensionnel et d'exploration de données Analysis Services** dans le volet **Modèles installés** .  
  
4.  Dans la zone **Nom** , nommez le nouveau projet **DM Intermediate**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>Pour modifier l'instance de stockage des objets d'exploration de données (facultatif)  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Sur le côté gauche du volet **Pages de propriétés** , cliquez sur **Déploiement**.  
  
3.  Vérifiez que le nom **Serveur** est **localhost**. Si vous utilisez une instance différente, tapez le nom de l'instance. Si vous utilisez une instance nommée différente de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], tapez le nom de l'ordinateur et le nom de l'instance. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>Pour modifier les propriétés de déploiement d'un projet (facultatif)  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.  
  
     - ou -  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le menu **Projet** , sélectionnez **Propriétés**.  
  
2.  Sur le côté gauche du volet **Pages de propriétés** , cliquez sur **Déploiement**.  
  
     Dans le volet **Options** , sélectionnez **Mode de déploiement**et définissez les options sur **Déployer tout** pour remplacer les objets ou sur **Déployer uniquement ce qui a changé** pour les mettre à jour ou en ajouter.  
  
## <a name="creating-a-data-source"></a>Création d'une source de données  
 Dans le didacticiel sur l'exploration de données de base, vous avez créé une *source de données* qui stocke des informations de connexion pour la base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] . Suivez les mêmes étapes pour créer la source de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] dans cette solution.  
  
#### <a name="to-create-a-data-source"></a>Pour créer une source de données  
  
-   [Création d’une source de données &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 Une source de données unique peut prendre en charge plusieurs vues de sources de données, lesquelles peuvent comporter plusieurs tables. Toutefois, étant donné que la source de données et la vue de source de données sont déployées sur votre [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données avec les modèles d’exploration de données que vous créez, il est recommandé d’inclure dans chaque vue de source de données uniquement les tables requises pour chaque modèle d’exploration de données ou groupe de modèles.  
  
 Dans les leçons suivantes, vous allez ajouter des vues de source de données afin de prendre en charge les nouveaux scénarios. Seules les leçons relatives au panier d'achat et à Sequence Clustering utilisent la même vue de source de données, sinon chaque scénario utilise une vue de source de données différente. Les leçons sont donc indépendantes les unes des autres et peuvent être accomplies séparément.  
  
|Scénario|Données incluses dans la vue de source de données|  
|--------------|-------------------------------------------|  
|[Leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|États des ventes mensuels pour les versions de vélos dans les différentes régions, collectés comme une seule vue.|  
|[Leçon 3 : Génération d’un scénario de panier d’achat &#40;Didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|Une table contenant la liste des commandes clients, et une table imbriquée affichant les achats individuels pour chaque client.|  
|[Leçon 4 : génération d’un scénario Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|Les mêmes données que celles utilisées pour l'analyse du panier d'achat, avec en plus un identificateur qui affiche l'ordre dans lequel les éléments ont été achetés.|  
|[Leçon 5 : Génération de modèles de réseau neuronal et de régression logistique &#40;Didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|Une seule table contenant des données de suivi des performances préliminaires provenant d'un centre d'appels.|  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Projets d’exploration de données](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [Vues de sources de données dans les modèles multidimensionnels](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
