---
title: 'Procédure : Déboguer des assemblys personnalisés | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b5f9f5a4595d59cce98da4f753422cd07529926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702496"
---
# <a name="how-to-debug-custom-assemblies"></a>Procédure : Déboguer des assemblages personnalisés
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit plusieurs outils de débogage qui peuvent vous aider à analyser votre code d’assembly personnalisé et à localiser les erreurs qu’il contient. Vous devez choisir un outil en fonction de ce que vous essayez d'accomplir. Cet exemple utilise [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].  
  
 La méthode recommandée pour concevoir, développer et tester des assemblys personnalisés pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste à créer une solution contenant à la fois vos rapports de test et votre assembly personnalisé.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Pour déboguer des assemblys à l'aide d'une instance unique de Visual Studio  
  
1.  Créez un projet de rapport à l'aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
     En même temps que vous créez un projet de rapport, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] crée une solution destinée à le contenir.  
  
2.  Ajoutez un nouveau projet Bibliothèque de classes à la solution existante. Assurez-vous que le projet de rapport est défini comme projet de démarrage. Pour plus d'informations sur la procédure à suivre, consultez la documentation de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
3.  Dans l'Explorateur de solutions, sélectionnez la solution de votre choix.  
  
4.  Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.  
  
     La boîte de dialogue **Pages de propriétés de Solution** s’affiche.  
  
5.  Dans le volet gauche, développez **Propriétés communes** si nécessaire, et cliquez sur **Dépendances du projet**. Sélectionnez le projet de rapport dans la liste déroulante **Projet**. Sélectionnez votre projet d’assembly dans la liste **Dépend de**.  
  
6.  Cliquez sur **OK** pour enregistrer les modifications et fermez le dialogue **Pages de propriétés**.  
  
7.  Dans l'Explorateur de solutions, sélectionnez votre projet d'assembly personnalisé.  
  
8.  Dans le menu **Affichage**, cliquez sur **Pages de propriétés**.  
  
     La boîte de dialogue **Pages de propriétés de Projet** s’affiche.  
  
9. Cliquez sur l’onglet **Générer** si vous travaillez sur un projet C# ou sur l’onglet **Compiler** s’il s’agit d’un projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
10. Dans la page **générer**la / **compilation** , entrez le chemin d’accès au dossier concepteur de rapports. Par défaut, il s’agit de C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE dans la zone de texte **Chemin de sortie**. Une version mise à jour de votre assembly personnalisé est alors générée et déployée directement dans le Concepteur de rapports avant exécution de votre rapport.  
  
11. Une fois votre rapport généré et votre assembly personnalisé développé, définissez des points d'arrêt dans le code de votre assembly personnalisé.  
  
12. Exécutez le rapport en mode **DebugLocal** en appuyant sur la touche F5. Lorsque le rapport s'exécute dans la fenêtre d'aperçu contextuelle, le débogueur atteint chacun des points d'arrêt correspondant au code exécutable de votre assembly. Utilisez la touche F11 pour exécuter le code de votre assembly personnalisé en pas à pas.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Pour déboguer des assemblys à l'aide de deux instances de Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et ouvrez votre projet d'assembly personnalisé.  
  
2.  Générez le projet et déployez votre assembly personnalisé de même que le fichier .pdb associé dans le Concepteur de rapports. Pour plus d’informations sur le déploiement, consultez [Déploiement d’un assembly personnalisé](deploying-a-custom-assembly.md).  
  
3.  Ouvrez un projet de rapport utilisant votre assembly personnalisé en laissant votre code d'assembly personnalisé ouvert dans une instance distincte de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
4.  Naviguez vers l'instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] qui contient votre projet d'assembly personnalisé et définissez des points d'arrêt dans votre code.  
  
5.  Alors que le projet d’assembly personnalisé se trouve toujours dans la fenêtre active, cliquez sur **Attacher au processus** dans le menu **Déboguer**.  
  
     La boîte de dialogue **Attacher au processus** s’ouvre.  
  
6.  Dans la liste des processus, sélectionnez le processus devenv.exe qui correspond à votre projet de rapport, puis cliquez sur **Attacher**.  
  
7.  Définissez les expressions qui vous utiliserez dans votre rapport à partir de votre assembly personnalisé et concevez votre rapport.  
  
8.  Une fois la conception de votre rapport terminée, cliquez sur l’onglet **Aperçu**.  
  
     Le rapport s'exécute et le code de l'assembly personnalisé doit s'arrêter aux points d'arrêt prédéfinis.  
  
    > [!NOTE]  
    >  L’utilisation de l’onglet **Aperçu** ne permet pas d’appliquer les autorisations de code de l’assembly. Pour effectuer un test complet, qui inclut toutes les erreurs de sécurité d’accès du code, lancez le projet de rapport avec le paramètre de configuration **DebugLocal**.  
  
9. Exécutez le code pas à pas à l'aide de la touche F11. Pour plus d'informations sur le débogage à l'aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consultez la documentation de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblys personnalisés avec des rapports](using-custom-assemblies-with-reports.md)  
  
  
