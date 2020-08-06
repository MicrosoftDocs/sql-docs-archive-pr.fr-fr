---
title: Déploiement d’un projet de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5d98bab3-3577-4143-b737-5196444a36ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 031c25b8a7e777cacb3be215b733119ff783db3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600272"
---
# <a name="deploying-an-analysis-services-project"></a>Déploiement d'un projet Analysis Services
  Pour afficher les données du cube et de dimension pour les objets du cube Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans le projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous devez déployer le projet sur une instance spécifiée d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis traiter le cube et ses dimensions. Le *déploiement* d’un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet crée les objets définis dans une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Le*traitement* des objets dans une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] copie les données à partir des sources de données sous-jacentes dans les objets du cube. Pour plus d’informations, consultez [Déployer des projets Analysis Services &#40;SSDT&#41;](multidimensional-models/deploy-analysis-services-projects-ssdt.md) et [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
 À ce stade du processus de développement, vous déployez généralement le cube sur une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur un serveur de développement. À la fin du développement de votre projet Business Intelligence, vous utiliserez généralement l'Assistant Déploiement d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour le déployer à partir du serveur de développement sur un serveur de production. Pour plus d’informations, consultez [Déploiement d’une solution de modèle multidimensionnel](multidimensional-models/multidimensional-model-solution-deployment.md) et [Déployer des solutions de modèles à l’aide de l’assistant Déploiement](multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md).  
  
 Au cours de la tâche suivante, vous allez vérifier les propriétés de déploiement du projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis déployer le projet sur votre instance locale d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
### <a name="to-deploy-the-analysis-services-project"></a>Pour déployer le projet Analysis Services  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet **Didacticiel Analysis Services** , puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Pages de propriétés de Didacticiel Analysis Services** s’affiche et présente les propriétés de la configuration (développement) active. Vous pouvez définir plusieurs configurations, chacune avec des propriétés différentes. Par exemple, un développeur peut souhaiter configurer un même projet pour qu'il soit déployé sur des ordinateurs de développement différents et avec des propriétés de déploiement différentes, telles que des noms de bases de données différents ou des propriétés de traitement différentes. Notez la valeur de la propriété **Output Path** . Cette propriété spécifie l'emplacement dans lequel sont enregistrés les scripts de déploiement XMLA du projet lorsqu'un projet est créé. Ces scripts sont ceux qui sont utilisés pour déployer les objets dans le projet sur une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
2.  Dans le nœud **Propriétés de configuration** dans le volet gauche, cliquez sur **Déploiement**.  
  
     Vérifiez les propriétés de déploiement du projet. Par défaut, le modèle de projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] configure un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour déployer de façon incrémentielle tous les projets sur l'instance par défaut d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur l'ordinateur local, pour créer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avec le même nom que le projet, et pour traiter les objets après le déploiement en utilisant l'option de traitement par défaut. Pour plus d’informations, consultez [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
    > [!NOTE]  
    >  Si vous souhaitez déployer le projet sur une instance nommée de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur l’ordinateur local ou sur un serveur distant, remplacez la propriété de **serveur** par le nom d’instance approprié, par exemple \<*ServerName**> \\ < **InstanceName**> *.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet **Analysis Services Tutorial** , puis cliquez sur **Déployer**. Cela peut prendre un certain temps.  
  
    > [!NOTE]  
    >  Si vous obtenez des erreurs pendant le déploiement, utilisez SQL Server Management Studio pour vérifier les autorisations relatives à la base de données. Le compte que vous avez spécifié pour la connexion à la source de données doit avoir une connexion sur l'instance SQL Server. Double-cliquez sur la connexion pour consulter les propriétés de mappage des utilisateurs. Le compte doit avoir les autorisations db_datareader sur la base de données **AdventureWorksDW2012** .  
  
     [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] génère et déploie le projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur l’instance spécifiée de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à l’aide d’un script de déploiement. La progression du déploiement s’affiche dans deux fenêtres : la fenêtre **sortie** et la fenêtre **progression du déploiement-Analysis Services didacticiel** .  
  
     Ouvrez la fenêtre de sortie, si nécessaire, en cliquant sur **Sortie** dans le menu **Affichage** . La fenêtre **Sortie** affiche la progression globale du déploiement. La fenêtre **progression du déploiement-didacticiel Analysis Services** affiche les détails de chaque étape effectuée pendant le déploiement. Pour plus d’informations, consultez [Générer des projets Analysis Services &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) et [Déployer des projets Analysis Services &#40;SSDT&#41;](multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
5.  Examinez le contenu de la fenêtre **sortie** et la fenêtre **progression du déploiement-Analysis Services didacticiel** pour vérifier que le cube a été généré, déployé et traité sans erreurs.  
  
6.  Pour masquer la fenêtre **État d’avancement du déploiement - Analysis Services Tutorial** , cliquez sur l’icône **Masquer automatiquement** (en forme de punaise) dans la barre d’outils de la fenêtre.  
  
7.  Pour masquer la fenêtre **Sortie** , cliquez sur l’icône **Masquer automatiquement** dans la barre d’outils de la fenêtre.  
  
 Vous avez correctement déployé le cube Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur votre instance locale d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], puis traité le cube déployé.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du cube](lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des projets Analysis Services &#40;SSDT&#41;](multidimensional-models/deploy-analysis-services-projects-ssdt.md)   
 [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  
