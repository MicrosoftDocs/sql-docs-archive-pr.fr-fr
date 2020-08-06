---
title: Enregistrer des scripts sous forme de projets ou de solutions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fade3900c8859f211bb0c66820dc97792262481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702228"
---
# <a name="save-scripts-as-projects-or-solutions"></a>Enregistrer des scripts sous forme de projets ou de solutions
  Les développeurs familiarisés avec [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio seront heureux de pouvoir utiliser l'Explorateur de solutions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les scripts sur lesquels votre activité est basée peuvent être groupés en projets de scripts et ces projets être gérés ensemble sous la forme d'une solution. Lorsque les scripts sont placés dans des projets de scripts et des solutions, il est possible de les ouvrir en groupe ou de les enregistrer ensemble dans un produit de contrôle du code source tel que Visual SourceSafe. Les projets de scripts contiennent les informations de connexion pour que les scripts puissent s'exécuter correctement et peuvent inclure des fichiers non script tels que des fichiers texte.  
  
 Au cours de l'exercice pratique suivant, vous allez créer un script court qui interroge la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , et qui est placé dans un projet de scripts et une solution.  
  
## <a name="using-script-projects-and-solutions"></a>Utilisation des projets de scripts et des solutions  
  
#### <a name="to-create-a-script-project-and-solution"></a>Pour créer un projet de scripts et une solution  
  
1.  Ouvrez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]et établissez une connexion à un serveur avec l'Explorateur d'objets.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**. La boîte de dialogue **Nouveau projet** s’affiche.  
  
3.  Dans la zone de texte **Nom** , tapez **StatusCheck**, cliquez sur **Scripts SQL Server** dans **Modèles**, puis cliquez sur **OK** pour ouvrir une nouvelle solution et un projet de scripts.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Connexions**et choisissez **Nouvelle connexion**. La boîte de dialogue **Se connecter au serveur** s'ouvre.  
  
5.  Dans la zone de liste **Nom du serveur** , tapez le nom de votre serveur.  
  
6.  Cliquez sur **Options**, puis sur l’onglet **Propriétés de connexions** .  
  
7.  Dans la zone **Se connecter à la base de données** , parcourez le serveur, sélectionnez la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , puis cliquez sur **Se connecter**. Les données de connexion concernant la base de données sont ajoutées au projet.  
  
8.  Si la fenêtre des propriétés ne s'affiche pas, sélectionnez la nouvelle connexion dans l'Explorateur de solutions et appuyez sur F4. Les propriétés de la connexion s’affichent et présentent les informations relatives à la connexion concernant la **Base de données initiale** qui est [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la connexion, puis cliquez sur **Nouvelle requête**. Une nouvelle requête nommée **SQLQuery1.sql** est créée, connectée à la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sur votre serveur et ajoutée à votre projet de scripts.  
  
10. Dans l'Éditeur de requête, tapez la requête suivante pour déterminer le nombre de bons de commande pour lesquels les dates d'échéance sont antérieures aux dates de début. (Vous pouvez copier et coller le code à partir de la fenêtre du didacticiel.)  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  Si vous avez besoin de davantage d'espace pour taper votre requête, appuyez sur Maj+Alt+Entrée pour afficher un plein écran.  
  
11. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **SQLQuery1**et choisissez **Renommer**. Tapez **Check ordres de validation. SQL** comme nouveau nom de la requête, puis appuyez sur entrée.  
  
12. Pour enregistrer votre solution et votre projet de scripts, dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : Solutions et projets de script](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
