---
title: 'Leçon 3 : installation de packages | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8b58cee7bd8e16cd0ca2e726dc8e5eff2cfec5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604628"
---
# <a name="lesson-3-installing-packages"></a>Leçon 3 : Installation des packages
  Dans [la leçon 2 : création de l’ensemble de déploiement](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md), vous avez créé un utilitaire de déploiement et créé l’ensemble de déploiement qui contient les éléments que vous devez installer sur un autre ordinateur. Vous avez vérifié également la liste de fichiers dans l'application de déploiement et examiné le contenu du fichier de manifeste créé lorsque vous avez créé l'utilitaire de déploiement.  
  
 Dans cette leçon, vous allez copier l'application de déploiement dans l'ordinateur de destination et exécuter l'Assistant Installation de package pour installer les packages, les dépendances de package et les fichiers annexes sur cet ordinateur. Les packages seront installés dans la **msdb** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données msdb et les autres éléments seront installés dans le système de fichiers. Une fois le package installé, vous allez tester le déploiement en exécutant les packages à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à l'aide de l'utilitaire d'exécution de package.  
  
 **Durée estimée pour effectuer cette leçon :** 30 minutes  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copier le bundle de déploiement](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Étape 2 : Exécution de l’Assistant Installation de package](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Étape 3 : Test des packages déployés](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Copier le bundle de déploiement](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
