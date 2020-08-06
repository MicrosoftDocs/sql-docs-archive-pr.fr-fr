---
title: Traitement par lots (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c777339f41f5f9029e4d03d47cc7f682e00032b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601151"
---
# <a name="batch-processing-analysis-services"></a>Traitement par lots (Analysis Services)
  Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser la commande batch pour envoyer plusieurs commandes de traitement au serveur dans une demande unique. Le traitement par lots vous offre une méthode pour contrôler les objets qui doivent être traités, et dans quel ordre. De plus, un traitement par lots peut s'exécuter en tant que série de travaux autonomes ou en tant que transaction dans laquelle l'échec d'un processus entraîne une annulation de l'ensemble du traitement par lots.  
  
 Le traitement par lots optimise la disponibilité des données en consolidant et en réduisant la durée nécessaire à la validation des modifications. Lorsque vous traitez entièrement une dimension, toute partition qui utilise cette dimension est marquée comme non traitée. En conséquence, les cubes qui contiennent les partitions non traitées sont indisponibles pour l'exploration. Vous pouvez résoudre ce problème à l'aide d'un travail de traitement par lots en traitant les dimensions avec les partitions affectées. L'exécution du travail de traitement par lots en tant que transaction permet de s'assurer que tous les objets inclus dans la transaction demeurent disponibles pour les requêtes jusqu'à ce que tout le traitement soit terminé. Lorsque la transaction valide les modifications, des verrous sont placés sur les objets affectés, ce qui les rend temporairement indisponibles, mais globalement, la durée nécessaire pour valider les modifications est moindre que si vous traitiez des objets individuellement.  
  
 Les procédures de cette rubrique décrivent les étapes de traitement complet de dimensions et de partitions. Le traitement par lots peut également inclure d'autres options de traitement, telles que le traitement incrémentiel. Pour que ces procédures fonctionnent correctement, vous devez utiliser une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante qui contient au moins deux dimensions et une partition.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Traitement par lots dans SQL Server Data Tools](#bkmk_ssdt)  
  
 [Traitement par lots à l'aide de XMLA dans Management Studio](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a> Traitement par lots dans SQL Server Data Tools  
 Pour que des objets puissent être traités dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], le projet contenant les objets doit être déployé. Pour plus d’informations, consultez [Déployer des projets Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
2.  Ouvrez un projet qui a été déployé.  
  
3.  Dans l'Explorateur de solutions, sous le projet déployé, développez le dossier **Dimensions** .  
  
4.  En maintenant la touche Ctrl enfoncée, cliquez sur chaque dimension répertoriée dans le dossier **Dimensions** .  
  
5.  Cliquez avec le bouton droit sur les dimensions sélectionnées, puis cliquez sur **Traiter**.  
  
6.  En maintenant la touche Ctrl enfoncée, cliquez sur chaque dimension répertoriée dans **Liste d'objets**.  
  
7.  Cliquez avec le bouton droit sur les dimensions sélectionnées et cliquez sur **Traiter entièrement**.  
  
8.  Pour personnaliser le travail de traitement par lots, cliquez sur **Modifier les paramètres**.  
  
9. Sous **Options de traitement**, marquez les paramètres suivants :  
  
    -   **Ordre de traitement** a la valeur **Séquentiel**et **Mode de transaction** a la valeur **Une seule transaction**.  
  
    -   **Option de la table d'écriture différée** a la valeur **Utiliser l'existante**.  
  
    -   Sous **Objets affectés**, activez la case à cocher **Traiter les objets affectés** .  
  
10. Cliquez sur l’onglet **Erreurs de clé de dimension** . Vérifiez que l’option utiliser la configuration d' **erreur par défaut** est sélectionnée.  
  
11. Cliquez sur **OK** pour fermer l'écran **Modifier les paramètres** .  
  
12. Cliquez sur **Exécuter** sur l'écran **Traiter les objets** pour démarrer le travail de traitement.  
  
13. Lorsque la zone **État** indique **Traitement réussi**, cliquez sur **Fermer**.  
  
14. Cliquez sur **Fermer** sur l'écran **Traiter les objets** .  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a>Traitement par lots à l’aide de XMLA dans Management Studio  
 Vous pouvez créer un script XMLA qui exécute le traitement par lots. Commencez en générant un script XMLA dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour chaque objet, puis associez-les dans une seule requête XMLA que vous exécutez de façon interactive ou dans une tâche planifiée.  
  
 Pour obtenir des instructions pas à pas, consultez l' **exemple 2** dans [planifier des tâches d’administration SSAS avec SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des objets de modèles multidimensionnels](processing-a-multidimensional-model-analysis-services.md)  
  
  
