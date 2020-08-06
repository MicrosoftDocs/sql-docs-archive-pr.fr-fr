---
title: Vue d’ensemble de l’installation de SQL Server maintenance | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6a9fd19b-2367-4908-b638-363b1e929e1e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30610b1a1016b3343c2264e885847de6f2c233fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612679"
---
# <a name="overview-of-sql-server-servicing-installation"></a>Vue d'ensemble de l'installation de maintenance de SQL Server
  Vous pouvez appliquer une mise à jour à n'importe quel composant [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installé sur votre ordinateur à une mise à jour de maintenance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Si le niveau de version d'un composant [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] existant est ultérieur à celui de la mise à jour, le programme d'installation exclut ce composant de la mise à jour. Pour plus d’informations sur l’application d’une mise à jour de maintenance, consultez [installer les mises à jour de maintenance de SQL Server 2014](../../database-engine/install-windows/install-sql-server-servicing-updates.md).  
  
 Vous devez tenir compte des points suivants lors de l'installation de mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
-   Toutes les fonctionnalités appartenant à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être mises à jour en même temps. Par exemple, lorsque vous mettez à jour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devez également mettre à jour les composants [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] s'ils sont installés sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les fonctionnalités partagées, telles que les outils d'administration, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], doivent toujours être mises à jour vers le correctif logiciel le plus récent. Si un composant ou une instance n'est pas sélectionné dans l'arborescence de fonctionnalités, le composant ou l'instance ne sera pas mis à jour.  
  
-   Par défaut, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] les fichiers journaux de mise à jour sont enregistrés dans% Program Files% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\ .  
  
-   Le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut à présent intégrer une mise à jour avec le média d'origine pour exécuter simultanément le média d'origine et la mise à jour. Pour plus d’informations, consultez [What’s New in SQL Server installation](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md).  
  
-   Avant d'appliquer une mise à jour de maintenance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , il est recommandé de sauvegarder vos données.  
  
-   Les mises à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont disponibles via [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update. Il est recommandé de vérifier régulièrement l'existence de mises à jour pour garantir l'actualisation et la sécurisation de votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 est fourni sous la forme d'une installation complète de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Alors qu'habituellement, le Service Pack est disponible dans le package correctif exécutable standard devant être appliqué aux instances de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RTM, pour cette version, un package d'installation (composé de 2 fichiers) est fourni. Une fois exécuté, il installe une nouvelle instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle le SP1 est préinstallé.  
  
## <a name="requirements-and-known-issues"></a>Configuration requise et problèmes connus  
 L'espace disque nécessaire représente environ 2,5 fois la taille du package pour permettre l'installation, le téléchargement et l'extraction de ce dernier. Après l'installation d'un Service Pack, vous pouvez supprimer le package téléchargé. Les fichiers temporaires sont supprimés automatiquement.  
  
 **Passer en revue les problèmes connus :** pour plus d’informations sur les problèmes connus relatifs à la version actuelle, consultez la rubrique correspondante consacrée aux notes de publication ici : [Notes de publication de SQL Server](https://msdn.microsoft.com/f617a0af-92dd-47aa-82c3-f51b1346bcd8).  
  
## <a name="installation-overview"></a>Vue d'ensemble de l'installation  
 Cette section traite de l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour les mises à jour cumulatives et les Service Packs. Elle explique notamment comment effectuer les opérations suivantes :  
  
-   Préparer l'installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   Installer les mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   Redémarrer les services et les applications  
  
### <a name="prepare-for-a-sscurrent-update-installation"></a>Préparer l'installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Il est vivement conseillé d'effectuer les opérations suivantes avant d'installer les mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
-   **Sauvegardez vos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données système** -avant d’installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] les mises à jour, sauvegardez les `master` `msdb` `model` bases de données, et. L'installation d'une mise à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] modifie ces bases de données et les rend incompatibles avec les versions antérieures de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. La sauvegarde de ces bases de données est nécessaire si vous décidez de réinstaller [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sans ces mises à jour.  
  
     Il est également prudent de sauvegarder vos bases de données utilisateur.  
  
    > [!IMPORTANT]  
    >  Lorsque vous appliquez des mises à jour à des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui participent à une topologie de réplication, vous devez sauvegarder vos bases de données répliquées en même temps que vos bases de données système avant d'appliquer les mises à jour.  
  
-   **Sauvegarder vos [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bases de données, votre fichier de configuration et votre référentiel** : avant de mettre à jour une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous devez sauvegarder les éléments suivants :  
  
    -   Bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Par défaut, ceux-ci sont installés dans C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSAS12. \<InstanceID> \OLAP\Data \\ . Pour l’installation de WOW, le chemin d’accès par défaut est C:\ProgramFiles (x86) \ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSAS12. \<InstanceID> \OLAP\Data \\ .  
  
    -   Paramètre de configuration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans le fichier de configuration msmdsrv.ini. Par défaut, il se trouve dans le dossier C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSAS12. \<InstanceID> Répertoire \OLAP\Config\.  
  
    -   (Facultatif) Base de données qui contient le référentiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Cette étape est requise uniquement si [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a été configuré pour fonctionner avec la bibliothèque DSO (Decision Support Objects).  
  
    > [!NOTE]  
    >  Si vous ne sauvegardez pas vos bases de données, votre fichier de configuration et votre base de données de référentiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , il ne vous sera pas possible de rétrograder une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mise à jour vers la version antérieure.  
  
-   **Vérifiez que les bases de données système disposent d’un espace libre suffisant** . si l’option de croissance automatique n’est pas sélectionnée pour les `master` `msdb` bases de données système et, ces bases de données doivent avoir au moins 500 Ko d’espace libre. Pour vérifier que les bases de données disposent d'un espace suffisant, exécutez la procédure stockée système `sp_spaceused` sur les bases de données `master` et `msdb`. Si l'espace non alloué dans l'une ou l'autre base de données est inférieur à 500 Ko, augmentez la taille de la base de données.  
  
-   **Arrêter les services et les applications** : pour éviter un éventuel redémarrage du système, arrêtez toutes les applications et tous les services qui se connectent aux instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont en cours de mise à niveau avant d’installer les [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mises à jour. Ceux-ci comprennent notamment [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d'informations, consultez [Démarrer, arrêter, suspendre, reprendre, redémarrer les services SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
    > [!NOTE]  
    >  Vous ne pouvez pas arrêter les services dans un environnement de cluster de basculement. Pour plus d'informations, consultez la section relative à l'installation sur un cluster de basculement plus loin dans cette rubrique.  
  
-   Pour vous éviter d'avoir à redémarrer votre ordinateur après l'installation des mises à jour, le programme d'installation affichera la liste des processus qui verrouillent des fichiers. Si le programme d'installation des mises à jour doit arrêter un service au cours de l'installation, il redémarrera ce dernier une fois l'installation terminée.  
  
-   Si le programme d'installation détermine que des fichiers sont verrouillés au cours de l'installation, vous devrez peut-être redémarrer votre ordinateur au terme de l'installation. Si c'est le cas, le programme d'installation vous invite à le faire.  
  
### <a name="install-sscurrent-updates"></a>Installer les mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Cette section décrit le processus d'installation.  
  
> [!IMPORTANT]  
>  Les mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] doivent être installées à l'aide d'un compte disposant de privilèges administratifs sur l'ordinateur sur lequel elles seront installées. Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.  
  
#### <a name="starting-a-sscurrent-update"></a>Démarrage d'une mise à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Pour installer une mise à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , exécutez le fichier de package à extraction automatique.  
  
 Package de mise à jour cumulative (CU) : \<SQLServer2014> -KBXXXXXX-*PPP*. exe  
  
 Package Service Pack (PCU) : \<SQLServer2014> \<SPx> -KBxxxxxx-PPP-LLL.exe  
  
-   x indique le numéro de Service Pack  
  
-   PPP indique la plateforme spécifique.  
  
-   LLL correspond à l'abréviation de la langue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par exemple, pour l'anglais, LLL correspond à ENU.  
  
 Pour appliquer des mises à jour à des composants [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] qui font partie d'un cluster de basculement, consultez la section relative à l'installation d'un cluster de basculement. Pour plus d’informations sur l’exécution d’une installation de mise à jour en mode sans assistance, consultez [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
####  <a name="product-updates-in-sscurrent-installation"></a><a name="Slipstream"></a>Mises à jour du produit dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’installation  
 La Mise à jour de produit est une fonctionnalité du programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Elle intègre les dernières mises à jour du produit avec l'installation principale du produit de sorte que le produit principal et ses mises à jour applicables sont installés en même temps. La fonctionnalité de mise à jour du produit peut rechercher les mises à jour applicables dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, Windows Server Update Services (WSUS), un dossier local ou un partage réseau.  Une fois que le programme d'installation a détecté les versions les plus récentes des mises à jour applicables, il les télécharge et les intègre dans le processus d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours. La fonctionnalité de mise à jour du produit peut extraire une mise à jour, un Service Pack, ou un Service Pack et la mise à jour cumulative. La fonctionnalité de mise à jour de produit est une extension de la fonctionnalité Slipstream qui était disponible dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="updating-a-prepared-image-of-ssnoversion"></a>Mise à jour d'une image préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Vous pouvez appliquer une mise à jour à une instance préparée non configurée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans terminer la configuration de l'instance préparée. Les différentes méthodes pour appliquer une mise à une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont expliquées ci-dessous :  
  
-   Mise à jour d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] préparée précédemment  
  
     Il est possible d'appliquer des mises à jour à une instance préparée avant la configuration. Le package de mise à jour détecte que l'instance est en état préparé et applique le correctif logiciel à l'instance préparée, sans terminer la configuration.  
  
-   Mise à jour d'une instance préparée à l'aide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update :  
  
     Vous pouvez appliquer des mises à jour à une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update. Le package [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update détecte que l'instance est en état préparé et applique le correctif logiciel à l'instance préparée, sans terminer la configuration.  
  
 Si vous mettez à jour une image préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez spécifier le paramètre InstanceID. Pour obtenir plus d'informations et un exemple de syntaxe, consultez [Installing Updates from the Command Prompt](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md).  
  
## <a name="updating-a-completed-image-of-ssnoversion"></a>Mise à jour d'une image finalisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 La mise à jour d'une instance finalisée et configurée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suit les mêmes processus que toute autre instance installée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="rebuilding-a-sscurrent-failover-cluster-node"></a>Reconstruction d'un nœud de cluster de basculement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Si vous devez reconstruire un nœud dans le cluster de basculement après l'application de mises à jour, procédez comme suit :  
  
1.  Reconstruisez le nœud dans le cluster de basculement. Pour plus d'informations sur la reconstruction d'un nœud, consultez [Recover from Failover Cluster Instance Failure](../failover-clusters/windows/recover-from-failover-cluster-instance-failure.md).  
  
2.  Exécutez le programme d'installation d'origine de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur le nœud de cluster de basculement.  
  
3.  Exécutez le programme d'installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur le nœud que vous avez ajouté.  
  
## <a name="restart-services-and-applications"></a>Redémarrer les services et les applications  
 Une fois l'exécution du programme d'installation terminée, vous devrez peut-être redémarrer l'ordinateur. Après le redémarrage du système ou après l'exécution du programme d'installation sans redémarrage, utilisez le nœud **Services** dans le Panneau de configuration pour redémarrer les services que vous avez arrêtés avant d'appliquer les mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Cela inclut des services tels que Distributed Transaction Coordinator et les services [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search ou des services équivalents spécifiques à une instance.  
  
 Redémarrez les applications que vous avez fermées avant d'exécuter le programme d'installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Vous pouvez également effectuer une autre sauvegarde des bases de données `master`, `msdb` et `model` mises à niveau, immédiatement après l'installation réussie.  
  
## <a name="uninstalling-updates-from-sscurrent"></a>Désinstallation des mises à jour à partir de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Vous pouvez désinstaller les mises à jour cumulatives ou les Service Packs de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à partir de l'élément **Programmes et fonctionnalités** du Panneau de configuration. Pour consulter la liste des mises à jour installées, ouvrez Mises à jour installées en cliquant sur **Démarrer** , **Panneau de configuration**et **Programmes**. Ensuite, sous **Programmes et fonctionnalités**, cliquez sur **Afficher les mises à jour installées**. Chaque mise à jour cumulative est répertoriée séparément. Toutefois, lorsqu'un Service Pack est installé et que sa version est supérieure à celle des mises à jour cumulatives, les entrées des mises à jour cumulatives sont masquées et deviennent accessibles uniquement si vous désinstallez le Service Pack.  
  
 Pour désinstaller les Service Packs et les mises à jour, vous devez commencer par la mise à jour ou le Service Pack appliqué en dernier à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et progresser à rebours. Dans chacun des exemples suivants, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne dispose plus que de Cumulative Update 1 une fois que la désinstallation des autres Service Packs ou mises à jour a été effectuée :  
  
-   Pour une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] où sont installés Cumulative Update 1 et le SP1, désinstallez le SP1.  
  
-   Pour une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] où sont installés Cumulative Update 1, le SP1 et Cumulative Update 2, désinstallez Cumulative Update 2 en premier, puis désinstallez le SP1.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Installer les mises à jour de maintenance de SQL Server 2014](../../database-engine/install-windows/install-sql-server-servicing-updates.md)   
 [Valider une installation SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
