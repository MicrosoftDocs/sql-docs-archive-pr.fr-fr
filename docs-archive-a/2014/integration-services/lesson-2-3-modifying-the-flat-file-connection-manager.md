---
title: 'Étape 3 : Modification du gestionnaire de connexions de fichiers plats | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601564"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a>Étape 3 : Modification du Gestionnaire de connexions de fichiers plats
  Dans cette tâche, vous allez modifier le gestionnaire de connexions de fichiers plats que vous avez créé et configuré dans la leçon 1. Le gestionnaire de connexions de fichiers plats a été configuré au départ pour charger statiquement un seul fichier. Pour faire en sorte que le Gestionnaire de connexions de fichiers plats charge les fichiers interactivement, vous devez modifier la propriété ConnectionString du Gestionnaire de connexions afin que la variable `User:varFileName`définie par l’utilisateur soit acceptée. Cette variable contient le chemin du fichier qui doit être chargé au moment de l’exécution.  
  
 La modification du Gestionnaire de connexions pour qu’il utilise la variable `User::varFileName`définie par l’utilisateur et qui remplit la propriété ConnectionString du Gestionnaire de connexions, permettra à ce dernier de se connecter à plusieurs fichiers plats. Au moment de l'exécution, chaque itération du conteneur de boucles Foreach mettra à jour la variable `User::varFileName` dynamiquement. Si la variable est à son tour mise à jour, le Gestionnaire de connexions se connecte à un autre fichier plat et la tâche de flux de données traite un autre jeu de données.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>Pour configurer le Gestionnaire de connexions de fichiers plats afin qu'il utilise une variable pour la chaîne de connexion  
  
1.  Dans le volet **Gestionnaires de connexions** , cliquez avec le bouton droit sur **Sample Flat File Source Data**, puis sélectionnez **Propriétés**.  
  
2.  Dans la Fenêtre Propriétés, pour **expressions**, cliquez dans la cellule vide, puis cliquez sur le bouton de sélection **(...)**.  
  
3.  Dans la boîte de dialogue **éditeur d’expressions** de la propriété, dans la colonne **propriété** , tapez ou sélectionnez `ConnectionString` .  
  
4.  Dans la colonne **expression** , cliquez sur le bouton de sélection **(...)** pour ouvrir la boîte de dialogue **Générateur d’expressions** .  
  
5.  Dans la boîte de dialogue **Générateur d’expression** , développez le nœud **Variables** .  
  
6.  Faites glisser la variable **User :: varFileName**vers la zone **expression** .  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Générateur d’expression** .  
  
8.  Recliquez sur **OK** pour fermer la boîte de dialogue **Éditeur d’expressions de la propriété** .  
  
## <a name="next-lesson-task"></a>Tâche suivante de la leçon  
 [Étape 4 : Test du package du tutoriel de la leçon 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
