---
title: Aide (F1) de l’Assistant Optimisation de l’utilisation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704376"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>Aide F1 sur l'Assistant Optimisation de l'utilisation
  Le résultat de l'Assistant Optimisation de l'utilisation est similaire à celui de l'Assistant Conception d'agrégation : il s'utilise pour concevoir les agrégations d'une partition. Cependant, l'Assistant Optimisation de l'utilisation conçoit les agrégations en fonction des habitudes d'utilisation des requêtes enregistrées dans le journal des requêtes d'une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Les agrégations améliorent les performances en permettant [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à d’extraire des totaux précalculés directement à partir du stockage du cube au lieu de recalculer les données à partir d’une source de données sous-jacente pour chaque requête.  
  
 Pour ouvrir l’Assistant Optimisation de l’utilisation à partir de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , ouvrez le concepteur de cube pour un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet, puis cliquez sur l’onglet **agrégations** . cliquez sur le bouton **optimisation basée** sur l’utilisation dans la barre d’outils.  
  
 Pour ouvrir l’Assistant Optimisation de l’utilisation à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connectez-vous à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] puis ouvrez le dossier **Cubes** . Sélectionnez un cube puis ouvrez le dossier **Groupes de mesures** et développez le groupe de mesures que vous souhaitez modifier. Cliquez avec le bouton droit sur le dossier **Partitions** puis sélectionnez **Optimisation basée sur l’utilisation**.  
  
 Vous pouvez utiliser l'Assistant Conception d'agrégation pour concevoir ces agrégations. Cet Assistant vous guide dans les étapes suivantes :  
  
-   sélection des paramètres standard ou personnalisés pour les options de stockage et de mise en cache d'une partition, d'un groupe de mesures ou d'un cube ;  
  
-   calcul des nombres estimés ou réels d'objets référencés par la partition, le groupe de mesures ou le cube ;  
  
-   spécification des options et des limites d'agrégation de façon à optimiser les performances du stockage et des requêtes des agrégations conçues ;  
  
-   enregistrement et traitement facultatif de la partition, du groupe de mesures ou du cube pour générer les agrégations définies.  
  
 L'Assistant Conception d'agrégation [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est destiné à concevoir des agrégations en fonction de l'analyse statistique de la partition. Il permet d'obtenir un modèle d'agrégation qui peut être à nouveau limité par la capacité de stockage ou les performances estimées. Vous l'utilisez pour améliorer les performances globales d'une partition ; cependant, le modèle d'agrégation n'est pas destiné aux besoins particuliers de vos utilisateurs. L’Assistant Optimisation de l’utilisation fournit un modèle d’agrégation destiné à ces besoins particuliers ; cependant, il ne peut le faire que si le journal des requêtes de l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] contient suffisamment d’informations pour construire de telles requêtes.  
  
 Généralement, les deux assistants s'utilisent ensemble pour améliorer les performances lors du déploiement et par la suite. L'Assistant Conception d'agrégation doit être utilisé en premier lors du déploiement initial de la partition (ou du cube ou du groupe de mesures la contenant) pour améliorer globalement les performances. Après quelque temps passé à enregistrer dans le journal des requêtes les requêtes des utilisateurs de la partition, vous pouvez utiliser l'Assistant Optimisation de l'utilisation pour affiner le modèle d'agrégation et répondre plus précisément aux besoins de performances et aux exigences des requêtes de vos utilisateurs.  
  
> [!NOTE]  
>  Pour des informations sur la configuration du journal des requêtes, consultez [Configuring the Analysis Services Query Log](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)(Configuration du journal des requêtes Analysis Services).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sélectionnez les partitions à modifier &#40;Assistant Optimisation de l’utilisation&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [Spécifiez les critères de requête &#40;Assistant Optimisation de l’utilisation&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [Passez en revue les requêtes qui seront optimisées &#40;Assistant Optimisation de l’utilisation&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [Passez en revue utilisation de l’agrégation &#40;Assistant Optimisation basé sur l’utilisation&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [Spécifier le nombre d’objets &#40;Assistant Optimisation de l’utilisation&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [Définir les options d’agrégation &#40;Assistant Optimisation de l’utilisation&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [Fin de l’Assistant &#40;l’Assistant Optimisation de l’utilisation&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégations et conceptions d’agrégation](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Cubes dans les modèles multidimensionnels](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Aide (F1) de l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Analysis Services assistants &#40;&#41;de données multidimensionnelles](analysis-services-wizards-multidimensional-data.md)  
  
  
