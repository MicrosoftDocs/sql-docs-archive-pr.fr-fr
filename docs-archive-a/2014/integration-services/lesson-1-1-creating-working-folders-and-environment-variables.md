---
title: 'Étape 1 : Création des variables d’environnement et des dossiers de travail | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63308d406e230538e5ca8b90dbb55bb802759bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605597"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a>Étape 1 : Création des variables d’environnement et des dossiers de travail
  Dans cette tâche, vous allez créer le dossier de travail (C:\DeploymentTutorial) et les nouvelles variables d'environnement système (`DataTransfer` et `LoadXMLData`) que vous utiliserez dans les tâches de didacticiel ultérieures.  
  
 Le dossier de travail se trouve à la racine du lecteur C. Vous pouvez utiliser un lecteur ou un emplacement différent si vous le souhaitez. Cependant, vous devez prendre note de cet emplacement et vous en servir lorsque le didacticiel vous renvoie à l'emplacement du dossier de travail DeploymentTutorial.  
  
 Dans une prochaine leçon, vous allez déployer dans la table sysssispackages de la base de données msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , des packages enregistrés dans le système de fichiers. Idéalement, vous allez déployer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un autre ordinateur. Si cela n'est pas possible, ce didacticiel peut néanmoins vous apporter beaucoup d'informations si vous déployez les packages vers une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui se trouve sur l'ordinateur local. Les variables d'environnement utilisées sur les ordinateurs locaux et de destination ont les mêmes noms de variables mais contiennent des valeurs différentes. Par exemple, sur l'ordinateur local, la valeur de la variable d'environnement `DataTransfer` référence le dossier C:\DeploymentTutorial, tandis que sur l'ordinateur cible, la variable d'environnement `DataTransfer` référence le dossier C:\DeploymentTutorialInstall.  
  
 Si vous envisagez de déployer sur l'ordinateur local, il vous suffit de créer un seul jeu de variables d'environnement ; cependant, vous devez mettre à jour la valeur des variables d'environnement avec une valeur appropriée avant d'effectuer le déploiement local.  
  
 Si vous envisagez de déployer les packages sur un autre ordinateur, vous devez créer deux jeux de variables d'environnement : un jeu pour l'ordinateur local et un jeu pour l'ordinateur de destination. Vous pouvez désormais créer seulement les variables destinées à l'ordinateur source, et celles destinées à l'ordinateur de destination ultérieurement, mais les variables d'environnement et le dossier doivent figurer sur l'ordinateur de destination avant que vous puissiez installer les packages sur cet ordinateur.  
  
### <a name="to-create-the-local-working-folder"></a>Pour créer le dossier de travail local  
  
1.  Cliquez avec le bouton droit sur le menu Démarrer et cliquez sur Explorer.  
  
2.  Cliquez sur **Disque local (C:)** .  
  
3.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Dossier**.  
  
4.  Renommez le nouveau dossier `DeploymentTutorial` .  
  
### <a name="to-create-local-environment-variables"></a>Pour créer des variables d'environnement locales  
  
1.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, double-cliquez sur **Système**.  
  
3.  Dans la boîte de dialogue **Propriétés système** , cliquez sur l’onglet **Avancé** , puis sur **Variables d’environnement**.  
  
4.  Dans la boîte de dialogue **Variables d’environnement** , dans le cadre **Variables système** , cliquez sur **Nouveau**.  
  
5.  Dans la boîte de dialogue **nouvelle variable système** , tapez `DataTransfer` dans la zone nom de la **variable** , puis `C:\DeploymentTutorial\datatransferconfig.dtsconfig` dans la zone valeur de la **variable** .  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez à nouveau sur **nouveau** , puis tapez `LoadXMLData` dans la zone nom de la **variable** et `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` dans la zone valeur de la **variable** .  
  
8.  Cliquez sur **OK** pour quitter la boîte de dialogue **Variables d’environnement** .  
  
9. Cliquez sur **OK** pour quitter la boîte de dialogue **Propriétés système** .  
  
10. Redémarrez l'ordinateur si nécessaire. Si vous ne redémarrez pas l'ordinateur, le nom de la nouvelle variable ne sera pas affiché dans l'Assistant Configuration de package, mais vous pouvez quand même l'utiliser.  
  
### <a name="to-create-destination-environment-variables"></a>Pour créer des variables d'environnement de destination  
  
1.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, double-cliquez sur **Système**.  
  
3.  Dans la boîte de dialogue **Propriétés système** , cliquez sur l’onglet **Avancé** , puis sur **Variables d’environnement**.  
  
4.  Dans la boîte de dialogue **Variables d’environnement** , dans le cadre **Variables système** , cliquez sur **Nouveau**.  
  
5.  Dans la boîte de dialogue **nouvelles variables système** , tapez `DataTransfer` dans la zone nom de la **variable** et `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` dans la zone valeur de la **variable** .  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez à nouveau sur **nouveau** , puis tapez `LoadXMLData` dans la zone nom de la **variable** et `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` dans la zone valeur de la **variable** .  
  
8.  Cliquez sur **OK** pour quitter la boîte de dialogue **Variables d’environnement** .  
  
9. Cliquez sur **OK** pour quitter la boîte de dialogue **Propriétés système** .  
  
10. Redémarrez l'ordinateur si nécessaire.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Création du projet de déploiement](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
