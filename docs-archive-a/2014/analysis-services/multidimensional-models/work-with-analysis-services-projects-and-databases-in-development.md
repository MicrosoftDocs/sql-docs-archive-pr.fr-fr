---
title: Utilisation des projets et des bases de données Analysis Services pendant la phase de développement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605799"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a>Utilisation de projets et de bases de données Analysis Services en phase de développement
  Vous pouvez développer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode projet ou en mode en ligne.  
  
## <a name="single-developer"></a>Développeur unique  
 Si un seul développeur est chargé du développement de l'intégralité de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et des objets qui la constituent, celui-ci peut utiliser [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode projet ou en mode en ligne à tout moment pendant le cycle de vie de la solution Business Intelligence. Dans ce cas, le choix du mode n'est pas vraiment essentiel. La maintenance d'un fichier de projet hors connexion intégré à un système de contrôle de la source présente de nombreux avantages, tels que l'archivage et la restauration. Cependant, avec un seul et unique développeur vous n'aurez aucun problème lié à la communication des modifications entre les développeurs.  
  
## <a name="multiple-developers"></a>Plusieurs développeurs  
 Si plusieurs développeurs collaborent sur une solution Business Intelligence, des problèmes surviendront s'ils ne travaillent pas en mode projet avec contrôle de la source dans la plupart des cas, si ce n'est tous. Le contrôle de la source permet à deux développeurs de ne pas modifier simultanément le même objet.  
  
 Par exemple, supposons qu'un développeur travaille en mode projet et apporte des modifications à des objets sélectionnés. Pendant qu'il effectue ces modifications, supposons qu'un autre développeur modifie la base de données déployée en mode en ligne. Un problème surviendra lorsque le premier développeur tentera de déployer son projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifié. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] détectera que des objets ont été modifiés dans la base de données déployée et invitera le développeur à remplacer l'intégralité de la base de données. Cela entraînera le remplacement des modifications apportées par le deuxième développeur. Étant donné que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ne dispose d'aucun moyen de résoudre les modifications entre l'instance de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et les objets contenus dans le projet qui seront remplacés, la seule solution pour le premier développeur consiste à ignorer toutes ses modifications et à créer un nouveau projet sur la base de la version actuelle de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
  
