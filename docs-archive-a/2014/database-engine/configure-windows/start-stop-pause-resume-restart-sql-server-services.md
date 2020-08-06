---
title: Démarrer, arrêter, suspendre, reprendre, redémarrer le service Moteur de base de données, SQL Server Agent ou SQL Server Browser | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706707"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a>Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser
  Cette rubrique explique comment démarrer, des commandes arrêter, des commandes interrompre, des commandes reprendre, des commandes ou redémarrer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], des commandes l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , des commandes de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], des commandes **net** à partir d'une invite de commandes, de des commandes [!INCLUDE[tsql](../../includes/tsql-md.md)], des commandes or PowerShell.  
  
-   **Avant de commencer :**  
  
    -   [Quels sont ces services ?](#Services)  
  
    -   [Informations supplémentaires](#MoreInformation)  
  
    -   [Sécurité](#Security)  
  
-   **Instructions pour utiliser :**  
  
    -   [Gestionnaire de configuration SQL Server](#SSCMProcedure)  
  
    -   [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [commandes net à partir d'une fenêtre d'invite de commandes](#CommandPrompt)  
  
    -   [Transact-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a> Qu'est-ce que le service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont des programmes exécutables qui s'exécutent en tant que service Windows. Les programmes qui s'exécutent en tant que service Windows peuvent continuer à fonctionner sans afficher d'activité sur l'écran de l'ordinateur.  
  
 **[!INCLUDE[ssDE](../../includes/ssde-md.md)]services**  
 Processus exécutable qui est le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut être l'instance par défaut (avec une limite d'une par ordinateur), ou peut être l'une des nombreuses instances nommées du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour déterminer quelles instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sont installées sur l'ordinateur. L’instance par défaut (si vous l’installez) est indiquée sous la forme ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**. Les instances nommées (si vous les installez) sont répertoriées sous la forme ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express est installé en tant que ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLExpress)**.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Service agent**  
 Service Windows qui exécute des tâches administratives planifiées, appelées travaux et alertes. Pour plus d’informations, consultez [SQL Server Agent](../../ssms/agent/sql-server-agent.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Service Browser**  
 Service Windows qui écoute les demandes entrantes des ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et fournit aux clients des informations sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur. Une seule instance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est utilisée pour toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a>Informations supplémentaires  
  
-   La suspension du service [!INCLUDE[ssDE](../../includes/ssde-md.md)] empêche les nouveaux utilisateurs de se connecter au [!INCLUDE[ssDE](../../includes/ssde-md.md)], mais les utilisateurs qui sont déjà connectés peuvent continuer à travailler jusqu'à ce que leurs connexions soient interrompues. Utilisez suspendre lorsque vous souhaitez attendre que les utilisateurs aient terminé leur travail avant d'arrêter le service. Cela leur permet d'effectuer les transactions en cours. Reprendre permet au [!INCLUDE[ssDE](../../includes/ssde-md.md)] d'accepter à nouveau de nouvelles connexions. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne peut pas être suspendu ou repris.  
  
-   Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] indiquent l'état actuel des services à l'aide des icônes suivantes.  
  
     **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**  
  
    -   Une flèche verte sur l'icône située à côté du nom du service indique que le service a démarré.  
  
    -   Un carré rouge sur l'icône située à côté du nom du service indique que le service s'est arrêté.  
  
    -   Deux lignes bleues verticales sur l'icône située à côté du nom du service indique que le service est suspendu.  
  
    -   Lors du redémarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)], un carré rouge indique que le service s'est arrêté, puis une flèche verte indique que le service a démarré.  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   Une flèche blanche sur l'icône de cercle vert située à côté du nom du service indique que le service a démarré.  
  
    -   Un carré blanc sur l'icône de cercle rouge située à côté du nom du service indique que le service s'est arrêté.  
  
    -   Deux lignes blanches verticales sur une icône de cercle bleue située à côté du nom du service indiquent que le service est suspendu.  
  
-   Lorsque vous utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], seules les options possibles sont disponibles. Par exemple, si le service a déjà démarré, **Démarrer** n'est pas disponible.  
  
-   Lors de l'exécution sur un cluster, le service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] est mieux géré à l'aide de l'Administrateur de cluster.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Par défaut, seuls les membres du groupe des administrateurs locaux peuvent démarrer, arrêter, interrompre, reprendre ou redémarrer un service. Pour accorder aux non-administrateurs la capacité de gérer des services, consultez [Comment accorder aux utilisateurs des droits de gestion des services dans Windows Server 2003](https://support.microsoft.com/kb/325349). (le processus est semblable sur d'autres versions de Windows).  
  
 L’arrêt du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à l’aide de la [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` commande requiert l’appartenance aux rôles serveur fixes **sysadmin** ou **ServerAdmin** , et n’est pas transférable.  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a>Utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Pour démarrer, arrêter, interrompre, reprendre, ou redémarrer une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Si la boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche, cliquez sur **Oui**.  
  
3.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dans le volet gauche, cliquez sur **Services SQL Server**.  
  
4.  Dans le volet de résultats, cliquez avec le bouton droit sur **SQL Server (MSSQLServer)** ou sur une instance nommée, puis cliquez sur **Démarrer**, **Arrêter**, **Suspendre**, **Reprendre**ou **Redémarrer**.  
  
5.  Cliquez sur **OK** pour fermer le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Pour démarrer une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] avec les options de démarrage, consultez [Configurer les options de démarrage du serveur &#40;Gestionnaire de configuration SQL Server&#41;](scm-services-configure-server-startup-options.md).  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a>Pour démarrer, arrêter, interrompre, reprendre, ou redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ou une instance de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Si la boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche, cliquez sur **Oui**.  
  
3.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dans le volet gauche, cliquez sur **Services SQL Server**.  
  
4.  Dans le volet des résultats, cliquez avec le bouton droit sur ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] navigateur**ou ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent (MSSQLSERVER)** ou sur ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent (<instance_name>)** pour une instance nommée, puis cliquez sur **Démarrer**, **arrêter**, **suspendre**, **reprendre**ou **redémarrer**.  
  
5.  Cliquez sur **OK** pour fermer le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  L’agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas être suspendu.  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>Pour démarrer, arrêter, interrompre, reprendre, ou redémarrer une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  Dans l’Explorateur d’objets, connectez-vous à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)], cliquez avec le bouton droit sur l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à démarrer, puis cliquez **Démarrer**, **Arrêter**, **Suspendre**, **Reprendre**ou **Redémarrer**.  
  
     Ou, dans Serveurs inscrits, cliquez avec le bouton droit sur l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à démarrer, pointez sur **Contrôle du service**, puis cliquez sur **Démarrer**, **Arrêter**, **Suspendre**, **Reprendre**ou **Redémarrer**.  
  
2.  Si la boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche, cliquez sur **Oui**.  
  
3.  Lorsque vous y êtes invité, et si vous souhaitez exécuter l'action, cliquez sur **Oui**.  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a>Pour démarrer, arrêter ou redémarrer une instance de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Dans l’Explorateur d’objets, connectez-vous à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , cliquez avec le bouton droit sur ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent**, puis cliquez sur **Démarrer**, **arrêter**ou **redémarrer**.  
  
2.  Si la boîte de dialogue **Contrôle de compte d'utilisateur** s'affiche, cliquez sur **Oui**.  
  
3.  Lorsque vous y êtes invité, et si vous souhaitez exécuter l'action, cliquez sur **Oui**.  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a> À partir de la fenêtre d'invite de commandes en utilisant les commandes net  
 Les services [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être démarrés, arrêtés ou suspendus à l’aide des commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)]**net** Windows.  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a> Pour démarrer l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   À partir d'une invite de commandes, entrez l'une des commandes suivantes :  
  
     **net start "SQL Server (MSSQLSERVER)"**  
  
     -ou-  
  
     **net start MSSQLSERVER**  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> Pour démarrer une instance nommée du [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   À partir d'une invite de commandes, entrez l'une des commandes suivantes. Remplacez le *\<instancename>* par le nom de l'instance à gérer.  
  
     **net start "SQL Server (** *nom_instance* **)"**  
  
     -ou-  
  
     **net start MSSQL$** *nom_instance*  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> Pour démarrer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] avec des options de démarrage  
  
-   Ajoutez les options de démarrage à la fin de l’instruction **"SQL Server (MSSQLSERVER)"** , en les séparant par un espace. Lors d’un démarrage avec l’instruction **net start**, les options de démarrage utilisent une barre oblique (/) au lieu d’un tiret (-).  
  
     **net start "SQL Server (MSSQLSERVER)" /f /m**  
  
     -ou-  
  
     **net start MSSQLSERVER /f /m**  
  
    > [!NOTE]  
    >  Pour plus d’informations sur les options de démarrage, consultez [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md).  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> Pour démarrer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   À partir d'une invite de commandes, entrez l'une des commandes suivantes :  
  
     **net start "SQL Server Agent (MSSQLSERVER)"**  
  
     -ou-  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a>Pour démarrer l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent sur une instance nommée de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   À partir d'une invite de commandes, entrez l'une des commandes suivantes. Remplacez *nom_instance* par le nom de l’instance à gérer.  
  
     **net start "SQL Server Agent (** *nom_instance* **)"**  
  
     -ou-  
  
     **net start SQLAgent$** *nom_instance*  
  
 Pour obtenir des informations sur la façon d’exécuter l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode détaillé à des fins de résolution des problèmes, consultez [Application sqlagent90](../../tools/sqlagent90-application.md).  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a> Pour démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser  
  
-   À partir d'une invite de commandes, entrez l'une des commandes suivantes :  
  
     **net start "SQL Server Browser"**  
  
     -ou-  
  
     **net start SQLBrowser**  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> Pour suspendre ou arrêter des services à partir de la fenêtre d'invite de commandes  
  
-   Pour suspendre ou arrêter des services, modifiez les commandes des façons suivantes.  
  
    -   Pour suspendre un service, remplacez **net start** par **net pause**.  
  
    -   Pour arrêter un service, remplacez **net start** par **net stop**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut être arrêté à l'aide de l'instruction `SHUTDOWN`.  
  
#### <a name="to-stop-the-ssde-using-tsql"></a>Pour arrêter le [!INCLUDE[ssDE](../../includes/ssde-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Pour attendre la fin des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et des procédures stockées en cours d'exécution, puis arrêter le [!INCLUDE[ssDE](../../includes/ssde-md.md)], exécutez l'instruction suivante.  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   Pour arrêter le [!INCLUDE[ssDE](../../includes/ssde-md.md)] immédiatement, exécutez l'instruction suivante.  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 Pour plus d’informations sur l' `SHUTDOWN` instruction, consultez [Shutdown &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
#### <a name="to-start-and-stop-ssde-services"></a>Pour démarrer et arrêter des services du [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
1.  Dans une fenêtre d'invite de commandes, démarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell en exécutant la commande suivante.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  À l'invite de commandes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, exécutez la commande suivante. Remplacez `computername` par le nom de votre ordinateur.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  Identifiez le service que vous souhaitez arrêter ou démarrer. Choisissez l'une des lignes suivantes. Remplacez `instancename` par le nom de l'instance nommée.  
  
    -   Pour obtenir une référence à l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   Pour obtenir une référence à une instance nommée du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   Pour obtenir une référence au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   Pour obtenir une référence au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur une instance nommée du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   Pour obtenir une référence au service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Terminez l'exemple pour démarrer, puis arrêter le service sélectionné.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer SQL Server avec une configuration minimale](start-sql-server-with-minimal-configuration.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
