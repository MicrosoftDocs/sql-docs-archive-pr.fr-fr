---
title: Exécuter un package dans SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31ca2390ef6bb04b63e4de9978193aed8884da36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696920"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>Exécuter un package dans les outils de données SQL Server
  Les packages sont exécutés le plus souvent dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pendant le développement, le débogage et le test des packages. Quand vous exécutez un package à partir du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , il est exécuté immédiatement.  
  
 Pendant qu’un package s’exécute, le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] affiche la progression de l’exécution sous l’onglet **Progression** . Vous pouvez afficher l'heure de début et de fin du package et de ses tâches et conteneurs, ainsi que des informations sur les tâches et les conteneurs du package ayant échoué. Quand un package a terminé son exécution, les informations sur l’exécution restent disponibles sous l’onglet **Résultats d’exécution** . Pour plus d’informations, consultez la section « Rapport de progression » dans la rubrique [Débogage du flux de contrôle](control-flow/control-flow.md).  
  
 **Déploiement au moment du design**. Lorsqu'un package est exécuté dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], il est créé, puis déployé dans un dossier. Avant d'exécuter le package, vous pouvez spécifier le dossier dans lequel il est déployé. Si vous ne spécifiez aucun dossier, le dossier **bin** est utilisé par défaut. Ce type de déploiement est appelé déploiement au moment de la conception.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>Pour exécuter un package dans les outils de données SQL Server  
  
1.  Dans l’Explorateur de solutions, si votre solution contient plusieurs projets, cliquez avec le bouton droit sur le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package, puis cliquez sur **Définir en tant qu’objet de démarrage** pour définir le projet de démarrage.  
  
2.  Dans l’Explorateur de solutions, si votre projet contient plusieurs packages, cliquez avec le bouton droit sur un package, puis cliquez sur **Définir en tant qu’objet de démarrage** pour définir le package de démarrage.  
  
3.  Pour exécuter un package, utilisez l'une des procédures suivantes :  
  
    -   Ouvrez le package à exécuter, puis cliquez sur **Démarrer le débogage** dans la barre de menus ou appuyez sur F5. Une fois l'exécution du package terminée, appuyez sur Maj+F5 pour revenir au mode Création.  
  
    -   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le package, puis cliquez sur **Exécuter le package**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>Pour spécifier un dossier différent pour le déploiement au moment du design  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier de projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package à exécuter, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **\<project name>Pages de propriétés de** , cliquez sur **Générer**.  
  
3.  Mettez à jour la valeur de la propriété OutputPath pour indiquer le dossier que vous souhaitez utiliser pour le déploiement au moment du design, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md)   
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
