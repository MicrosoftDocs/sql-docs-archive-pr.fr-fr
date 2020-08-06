---
title: Débogage des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f5971fe611f06a413ca48b2bc91237a8c87ee8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700433"
---
# <a name="debugging-stored-procedures"></a>Débogage des procédures stockées
  Les procédures stockées [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont en réalité des bibliothèques CLR ou COM (normalement des DLL) écrites en C# (ou dans tout autre langage CLR ou COM). Par conséquent, le débogage d'une procédure stockée n'est pas sans ressembler à celui des autres applications dans l'environnement de débogage de Visual Studio. Pour déboguer les procédures stockées, l'environnement de développement de Visual Studio met à votre disposition ses fonctions de débogage intégrées. Ces fonctions vous permettent d'arrêter l'exécution aux emplacements des procédures, d'inspecter des valeurs en mémoire et dans le Registre, de modifier des variables, d'observer les échanges de messages et de regarder de près comment votre code fonctionne.  
  
### <a name="to-debug-a-stored-procedure"></a>Pour déboguer une procédure stockée  
  
1.  Ouvrez le projet utilisé pour créer la DLL dans Visual Studio.  
  
2.  Créez des points d'arrêt dans la méthode ou la fonction correspondant à la procédure à déboguer.  
  
3.  Utilisez Visual Studio pour créer une version debug d'une DLL de procédure stockée.  
  
4.  Déployez la DLL vers le serveur. Pour plus d’informations sur le déploiement de la DLL sur le serveur, consultez [création de procédures stockées](creating-stored-procedures.md).  
  
5.  Vous avez besoin d'une application qui appelle la procédure stockée que vous voulez tester. Si vous n'avez pas d'application prête à jouer ce rôle, vous pouvez utiliser l'éditeur de requête MDX dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une requête MDX qui appelle la procédure stockée à tester.  
  
6.  Dans Visual Studio, attachez la DLL au processus [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (Msmdsrv.exe).  
  
    1.  Dans le menu **Déboguer** , choisissez **attacher toProcess**.  
  
    2.  Dans la boîte de dialogue **attacher toProcess** , sélectionnez **afficher les processus de tous les utilisateurs**.  
  
    3.  Dans la liste **processus disponibles** , dans la colonne **traiter** , cliquez sur **Msmdsrv.exe**. S'il y a plus d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui s'exécute sur le serveur, vous devez identifier le processus par l'identificateur de l'instance que vous souhaitez utiliser.  
  
    4.  Dans la zone de texte **attacher à** , assurez-vous que le type de programme approprié est sélectionné. Pour une DLL CLR, cliquez sur **Sélectionner**, puis sur **Déboguer ces types de codes**, sur **géré**, puis sur **OK**. Pour une DLL COM, cliquez sur **Sélectionner**, puis sur **Déboguer ces types de codes**, sur **natif**, puis sur **OK**.  
  
    5.  Cliquez sur **Attacher**.  
  
7.  Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], appelez le programme ou le script MDX qui appelle la procédure stockée. Le débogueur s'interrompt lorsqu'il atteint une ligne contenant un point d'arrêt. Vous pouvez évaluer des variables dans la fenêtre Espion, afficher des variables locales et exécuter le code en pas à pas.  
  
 Si le débogage d'une bibliothèque pose des problèmes, vérifiez que le fichier de base de données du programme (fichier PDB) correspondant a été copié vers l'emplacement du déploiement sur le serveur. Si ce fichier n'a pas été copié durant l'inscription ou le déploiement, vous devez le copier manuellement au même endroit que la DLL. Pour le code natif (DLL COM), le fichier PDB réside dans le sous-répertoire \debug. Pour le code managé (DLL CLR), il réside dans le sous-répertoire \WINDEBUG.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Définition de procédures stockées](defining-stored-procedures.md)  
  
  
