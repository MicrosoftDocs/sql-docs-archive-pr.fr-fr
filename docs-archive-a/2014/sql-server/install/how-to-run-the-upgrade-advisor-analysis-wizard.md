---
title: 'Procédure : exécuter l’Assistant analyse du conseiller de mise à niveau | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613797"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>Procédure : exécuter l’Assistant Analyse du Conseiller de mise à niveau
  Vous démarrez l'Assistant Analyse du Conseiller de mise à niveau à partir de la page de démarrage du Conseiller de mise à niveau. Cette rubrique décrit comment exécuter l'Assistant Analyse du Conseiller de mise à niveau.  
  
> [!IMPORTANT]
>  Lorsque vous exécutez l'Assistant Analyse du Conseiller de mise à niveau, le Conseiller de mise à niveau enregistre les rapports dans le dossier des rapports par défaut. Toutefois, la visionneuse de rapports affiche uniquement les cinq derniers rapports enregistrés. L’emplacement par défaut des rapports est My documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>Pour exécuter l’Assistant analyse du conseiller de mise à niveau  
  
1.  Sur la page de démarrage du conseiller de mise à niveau, cliquez sur **lancer l’Assistant analyse du conseiller de mise à niveau**.  
  
2.  Dans la page ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants** , entrez le nom du serveur à analyser dans la zone **nom du serveur** , puis cliquez sur **détecter**. Utilisez les indications suivantes pour le nom du serveur :  
  
    -   Pour analyser les instances non cluster, entrez le nom de l’ordinateur.  
  
    -   Pour analyser les instances cluster, entrez le nom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] virtuel.  
  
    -   Pour analyser les composants non-cluster installés sur un nœud d’un cluster, entrez le nom du nœud.  
  
    > [!WARNING]  
    >  Le Conseiller de mise à niveau ne prend pas en charge la connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui n'est pas définie pour utiliser le port standard (1433) pour les connexions clientes. Si vous voulez vous connecter à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui n'utilise pas le port standard (1433), créez un alias à l'aide de l'adresse IP et du port. Pour plus d’informations sur la configuration des protocoles clients et la création d’un alias pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances, consultez [configurer des protocoles clients](../../database-engine/configure-windows/configure-client-protocols.md).  
    >   
    >  Si vous n’avez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installé sur l’ordinateur sur lequel vous exécutez le conseiller de mise à niveau, cliquez sur **Démarrer**, puis sur exécuter `cliconfg` . La boîte de dialogue ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilitaire réseau client** s’ouvre. Utilisez l’onglet **alias** pour créer l’alias.  
  
3.  Passez en revue la liste des composants détectés, modifiez les sélections si nécessaire, puis cliquez sur **suivant**.  
  
4.  Sur la page **paramètres de connexion** , sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous souhaitez analyser, sélectionnez la méthode d’authentification et, si nécessaire, entrez les informations de nom d’utilisateur et de mot de passe, puis cliquez sur **suivant**.  
  
     MSSQLSERVER est le nom de l'instance par défaut.  
  
5.  Pour les composants sélectionnés, entrez les informations demandées. Pour plus d’informations sur les boîtes de dialogue individuelles, consultez Référence de l' [interface utilisateur du conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
6.  Sur la page **confirmer le paramètre du conseiller de mise à niveau** , passez en revue les informations que vous avez entrées. Vous pouvez sélectionner **Envoyer des rapports [!INCLUDE[msCoName](../../includes/msconame-md.md)] à** si vous souhaitez envoyer votre rapport de mise à niveau. Vous pouvez également examiner la politique de confidentialité.  
  
7.  Cliquez sur **exécuter** pour analyser l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
8.  Une fois l’analyse terminée, cliquez sur **lancer le rapport** pour afficher les problèmes de mise à niveau détectés.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : lancer le conseiller de mise à niveau](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Exécution du conseiller de mise à niveau &#40;de l’interface utilisateur&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
