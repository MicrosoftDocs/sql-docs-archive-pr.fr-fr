---
title: Migrer une installation Reporting Services (mode natif) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.custom: ''
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.date: 08/10/2017
ms.openlocfilehash: 7b809028e0996bfd3849fe2e1011f8633817662c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710328"
---
# <a name="migrate-a-reporting-services-installation-native-mode"></a>Migrer une installation Reporting Services (mode natif)

  Cette rubrique fournit des instructions pas à pas pour la migration de l’une des versions prises en charge suivantes d’un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] déploiement en mode natif vers une nouvelle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance de :  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)](Pour plus d’informations, consultez [vous ne pouvez pas utiliser SQL Server 2005 pour héberger des bases de données 2014 du serveur de rapports](https://support.microsoft.com/kb/2796721).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.|  
  
 Pour plus d’informations sur la migration d’un déploiement en mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [Migrer une installation Reporting Services &#40;mode SharePoint&#41;](migrate-a-reporting-services-installation-sharepoint-mode.md).  
  
 La migration s'entend ici comme étant le déplacement de fichiers de données d'application vers une nouvelle instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Voici quelques raisons courantes pour lesquelles vous devez migrer votre installation :  
  
-   Vous disposez d'un déploiement à grande échelle ou d'un temps d'exécution spécifique.  
  
-   Vous modifiez le matériel ou la topologie de votre installation.  
  
-   Vous rencontrez un problème qui empêche la mise à niveau.  
  
##  <a name="native-mode-migration-overview"></a><a name="bkmk_nativemode_migration_overview"></a> Présentation de la migration en mode natif  
 Le processus de migration pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend des étapes manuelles et des étapes automatiques. Les tâches suivantes sont inhérentes au processus de migration d'un serveur de rapports :  
  
-   Sauvegardez les fichiers de base de données, de configuration et d'application.  
  
-   Sauvegardez la clé de chiffrement.  
  
-   Installez une nouvelle instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Si vous utilisez le même matériel, installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] côte à côte avec votre installation existante, si elle est d'une des versions prises en charge.  
  
    > [!TIP]  
    >  Une installation côte à côte peut nécessiter l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] comme instance nommée.  
  
-   Déplacez la base de données du serveur de rapports et les autres fichiers d'application de votre installation existante vers votre nouvelle installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
-   Déplacez tous les fichiers d'application personnalisés vers la nouvelle installation.  
  
-   Configurez le serveur de rapports.  
  
-   Modifiez **RSReportServer.config** pour y inclure tous les paramètres personnalisés de votre installation précédente.  
  
-   Le cas échéant, configurez des listes de contrôle d’accès (ACL, Access Control List) personnalisées pour le nouveau groupe du service Windows [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Supprimez les applications et outils inutiles après avoir vérifié que la nouvelle instance est complètement opérationnelle.  
  
 Des restrictions s'appliquent pour les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui hébergent la base de données du serveur de rapports. Consultez la rubrique suivante si vous réutilisez une base de données du serveur de rapports créée dans une installation précédente.  
  
-   [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
##  <a name="fixed-database-name"></a><a name="bkmk_fixed_database_name"></a> Nom de base de données fixe  
 Vous ne pouvez pas renommer la base de données du serveur de rapports. L'identité de la base de données est enregistrée dans des procédures stockées du serveur de rapports lors de la création de la base de données. Renommer les bases de données primaires ou temporaires du serveur de rapports provoque des erreurs lors de l'exécution des procédures, invalidant alors votre installation du serveur de rapports.  
  
 Si le nom de la base de données de l'installation existante ne convient pas pour la nouvelle installation, vous devez envisager de créer une base de données portant le nom souhaité, puis de charger les données d'application existantes à l'aide des techniques énumérées ci-dessous :  
  
-   Écrivez un script [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] qui appelle des méthodes SOAP du service Web Report Server pour copier des données entre des bases de données. Vous pouvez utiliser l'utilitaire RS.exe pour exécuter le script. Pour plus d’informations sur cette approche, consultez [Scripts et PowerShell avec Reporting Services](../tools/scripting-and-powershell-with-reporting-services.md).  
  
-   Écrivez du code qui appelle le fournisseur WMI pour copier des données entre des bases de données. Pour plus d’informations sur cette approche, consultez [Accès au fournisseur WMI de Reporting Services](../tools/access-the-reporting-services-wmi-provider.md).  
  
-   Si vous avez seulement quelques éléments, vous pouvez publier de nouveau les rapports, les modèles de rapport et les sources de données partagées du Concepteur de rapports, du Générateur de modèles et du Générateur de rapports sur le nouveau serveur de rapports. Vous devez recréer les attributions de rôles, les abonnements, les planifications partagées, les planifications d'instantanés de rapports, les propriétés personnalisées que vous définissez sur les rapports ou d'autres éléments, la sécurité des éléments de modèle et les propriétés que vous définissez sur le serveur de rapports. L'historique de rapport et les données du journal des exécutions des rapports seront perdus.  
  
##  <a name="before-you-start"></a><a name="bkmk_before_you_start"></a> Avant de commencer  
 Même si vous effectuez une migration et non une mise à niveau de l'installation, pensez à exécuter le Conseiller de mise à niveau sur votre installation existante ; cela vous permettra d'identifier les problèmes susceptibles d'affecter la migration. Cette étape est particulièrement utile si vous migrez un serveur de rapports que vous n'avez pas installé ou configuré vous-même. En exécutant le Conseiller de mise à niveau, vous pouvez trouver des informations sur des paramètres personnalisés qui peuvent ne pas être pris en charge dans une nouvelle installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Vous devez en outre prendre connaissance de plusieurs modifications importantes introduites dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et décrites ci-dessous, qui affecteront la manière dont vous migrerez votre installation.  
  
-   Depuis [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], IIS n'est plus indispensable. Si vous effectuez une migration d'une installation du serveur de rapports vers un nouvel ordinateur, il n'est pas nécessaire d'ajouter le rôle de serveur Web. De plus, la procédure de configuration des URL et de l'authentification diffère par rapport à la précédente version, de même que les techniques et outils de diagnostic et de résolution des problèmes.  
  
-   Le service Web Report Server, le Gestionnaire de rapports et le service Windows Report Server ont été regroupés en un seul service Report Server. Ces trois applications s'exécutent sous le même compte. Toutes les trois lisent les paramètres de configuration du fichier RSReportServer.config, ce qui rend obsolète le fichier RSWebApplication.config.  
  
-   Le Gestionnaire de rapports et SQL Server Management Studio ont été repensés de manière à supprimer les fonctionnalités à double emploi. Chaque outil prend en charge un ensemble de tâches distinct ; les outils ne sont plus interchangeables.  
  
-   Les filtres ISAPI ne sont pas pris en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et versions ultérieures. Si vous utilisez des filtres ISAPI, vous devez reconcevoir votre solution de création de rapports avant la migration.  
  
-   Les restrictions d’adresse IP ne sont pas prises en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et versions ultérieures. Si vous utilisez des restrictions d'adresse IP, vous devez revoir votre solution de création de rapports avant la migration ou utiliser une technologie telle qu'un pare-feu, un routeur ou un traducteur d'adresses réseau (NAT, Network Address Translation) pour configurer des adresses restreintes pouvant accéder au serveur de rapports.  
  
-   Les certificats de protocole SSL client (SSL) ne sont pas pris en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et versions ultérieures. Si vous utilisez des certificats SSL clients, vous devez reconcevoir votre solution de création de rapports avant la migration.  
  
-   Si vous utilisez un type d’authentification autre que l’authentification intégrée de Windows, vous devez mettre à jour l’élément `<AuthenticationTypes>` dans le fichier **RSReportServer.config** avec un type d’authentification pris en charge. Les types d'authentification pris en charge sont NTLM, Kerberos, Negotiate et Basic. Les authentifications Digest, .NET Passport et anonyme ne sont pas prises en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et versions ultérieures.  
  
-   Si vous utilisez des feuilles de style en cascade personnalisées dans votre environnement de création de rapports, elles ne seront pas migrées. Vous devez les déplacer manuellement après la migration.  
  
 Pour plus d’informations sur les modifications apportées à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez la documentation relative au conseiller de mise à niveau et [nouveautés &#40;Reporting Services&#41;](../what-s-new-reporting-services.md).  
  
##  <a name="backup-files-and-data"></a><a name="bkmk_backup"></a> Sauvegarde des fichiers et des données  
 Avant d'installer une nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], assurez-vous de sauvegarder tous les fichiers de votre installation actuelle.  
  
1.  Sauvegardez la clé de chiffrement de la base de données du serveur de rapports. Cette étape est cruciale pour le succès de la migration. En effet, à un stade plus avancé du processus de migration, vous devrez la restaurer pour rendre au serveur de rapports l'accès aux données chiffrées. Pour sauvegarder la clé, utilisez le Gestionnaire de configuration de Reporting Services.  
  
2.  Sauvegardez la base de données du serveur de rapports en utilisant l'une des méthodes prises en charge pour la sauvegarde d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez les instructions relatives à la sauvegarde de la base de données du serveur de rapports dans [Déplacement des bases de données du serveur de rapports vers un autre ordinateur &#40;SSRS en mode natif&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
3.  Sauvegardez les fichiers de configuration du serveur de rapports. Les fichiers à sauvegarder sont les suivants :  
  
    1.  RSReportServer.config  
  
    2.  Rswebapplication.config  
  
    3.  Rssvrpolicy.config  
  
    4.  Rsmgrpolicy.config  
  
    5.  Reportingservicesservice.exe.config  
  
    6.  Web.config pour les applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] Report Server et Gestionnaire de rapports.  
  
    7.  Machine.config pour [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] si vous l'avez modifié pour les opérations du serveur de rapports.  
  
##  <a name="install-sql-server-reporting-services"></a><a name="bkmk_install_ssrs"></a> Installation de SQL Server Reporting Services  
 Installez une nouvelle instance du serveur de rapports en mode fichiers uniquement ; vous pourrez ainsi la configurer pour une utilisation de valeurs autres que celles définies par défaut. Pour une installation via la ligne de commande, utilisez l'argument `FilesOnly`. Dans l’Assistant Installation, sélectionnez l’option **Installer, mais ne pas configurer le serveur de rapports**.  
  
 Cliquez sur l'un des liens suivants pour obtenir des instructions sur l'installation d'une nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:  
  
-   [Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)  
  
-   [Installer SQL Server 2014 à partir de l'invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
##  <a name="move-the-report-server-database"></a><a name="bkmk_move_database"></a> Déplacement de la base de données du serveur de rapports  
 La base de données du serveur de rapports contient des rapports publiés, des modèles, des sources de données partagées, des planifications, des ressources, des abonnements et des dossiers. Elle contient également des propriétés système et d'élément, ainsi que les autorisations d'accès au contenu du serveur de rapports.  
  
 Si votre migration comprend l'utilisation d'une autre instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , vous devez déplacer la base de données du serveur de rapports vers la nouvelle instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Si vous utilisez la même instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] , passez à la section [Déplacement des assemblys ou extensions personnalisés](#bkmk_move_custom).  
  
 Pour déplacer la base de données du serveur de rapports, procédez comme suit :  
  
1.  Choisissez l'instance [!INCLUDE[ssDE](../../includes/ssde-md.md)] à utiliser. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]requiert l’utilisation de l’une des versions suivantes pour héberger la base de données du serveur de rapports :  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
    -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
    -   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
    -   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
2.  Démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
3.  Créez le `RSExecRole` dans les bases de données système si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'a jamais hébergé une base de données du serveur de rapports. Pour plus d’informations, consultez [Créer le rôle RSExecRole](../security/create-the-rsexecrole.md).  
  
4.  Suivez les instructions fournies dans [Déplacement des bases de données du serveur de rapports vers un autre ordinateur &#40;SSRS en mode natif&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
 N'oubliez pas que la base de données du serveur de rapports et la base de données temporaire dépendent l'une de l'autre et doivent être déplacées simultanément. Ne copiez pas les bases de données ; la copie ne transfère pas tous les paramètres de sécurité vers la nouvelle installation. Ne déplacez pas de travaux de l'Agent SQL Server pour les opérations planifiées du serveur de rapports. Le serveur de rapports recrée automatiquement ces travaux.  
  
##  <a name="move-custom-assemblies-or-extensions"></a><a name="bkmk_move_custom"></a> Déplacement des assemblys ou extensions personnalisés  
 Si votre installation comprend des éléments de rapport, des assemblys ou des extensions personnalisés, vous devez redéployer les composants personnalisés. Si vous n’utilisez pas des composants personnalisés, passez à la section [Configuration du serveur de rapports](#bkmk_configure_reportserver).  
  
 Pour redéployer les composants personnalisés, procédez comme suit :  
  
1.  Déterminez si les assemblys sont pris en charge ou doivent être recompilés :  
  
    -   Les extensions d'authentification personnalisées créées pour la version [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] doivent être recompilées.  
  
    -   Les extensions de rendu personnalisées pour [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] doivent être réécrites à l’aide du modèle objet de rendu.  
  
    -   Les convertisseurs HTML 3.2 et HTML OWC ne sont pas pris en charge dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et versions ultérieures.  
  
    -   Les autres assemblys personnalisés ne devraient pas nécessiter de recompilation.  
  
2.  Déplacez les assemblys vers le nouveau serveur de rapports et les dossiers \bin du Gestionnaire de rapports. Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , les fichiers binaires du serveur de rapports se trouvent à l’emplacement suivant pour l’instance par défaut [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
     `\Program files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\bin`  
  
3.  Modifiez les fichiers de configuration de façon à y ajouter des entrées pour votre composant personnalisé. Les entrées à ajouter dépendent du type d'assembly que vous utilisez. Pour obtenir des instructions sur l'endroit où placer des fichiers et ajouter des entrées de configuration, consultez les rubriques suivantes :  
  
    1.  [Déploiement d'un assembly personnalisé](../custom-assemblies/deploying-a-custom-assembly.md)  
  
    2.  [Procédure : déployer un élément de rapport personnalisé](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
    3.  [Déploiement d'une extension pour le traitement des données](../extensions/data-processing/deploying-a-data-processing-extension.md)  
  
    4.  [Déploiement d'une extension de remise](../extensions/delivery-extension/deploying-a-delivery-extension.md)  
  
    5.  [Déploiement d'une extension de rendu](../extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
    6.  [Implémentation d'une extension de sécurité](../extensions/security-extension/implementing-a-security-extension.md)  
  
##  <a name="configure-the-report-server"></a><a name="bkmk_configure_reportserver"></a> Configuration du serveur de rapports  
 Configurez les URL du service Web Report Server et du Gestionnaire de rapports, ainsi que la connexion à la base de données du serveur de rapports.  
  
 Si vous migrez un déploiement avec montée en puissance parallèle, mettez tous les nœuds du serveur de rapports hors connexion et migrez les serveurs un par un. Une fois que le premier serveur de rapports est migré et qu'il se connecte avec succès à la base de données du serveur de rapports, la version de la base de données du serveur de rapports est automatiquement mise à niveau vers la version de la base de donnée [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
> [!IMPORTANT]  
>  Si l'un des serveurs de rapports dans le déploiement avec montée en puissance parallèle est en ligne et n'a pas été migré, il peut rencontrer une exception rsInvalidReportServerDatabase parce qu'il utilise un schéma plus ancien lorsqu'il est connecté aux éléments mis à niveau.  
  
> [!NOTE]  
>  Si le serveur de rapports que vous avez migré a été configuré comme base de données partagée pour un déploiement avec montée en puissance parallèle, vous devez supprimer toutes les anciennes clés de chiffrement de la table **Keys** dans la base de données **ReportServer** avant de configurer le service de serveur de rapports. Si les clés ne sont pas supprimées, le serveur de rapports migré essaiera de s'initialiser en mode de déploiement avec montée en puissance parallèle. Pour plus d’informations, consultez [Ajouter et supprimer des clés de chiffrement pour un déploiement évolutif &#40;Gestionnaire de configuration de SSRS&#41;](add-and-remove-encryption-keys-for-scale-out-deployment.md) et [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-encryption-keys-manage-encryption-keys.md).  
>   
>  Les clés de montée en puissance parallèle ne peuvent pas être supprimées à l'aide du Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les anciennes clés doivent être supprimées de la table **Keys** dans la base de données **ReportServer** à l’aide de SQL Server Management Studio. Supprimez toutes les lignes dans la table Keys. Cela effacera la table et la préparera en vue de la restauration de la clé symétrique uniquement, comme documenté dans les étapes suivantes.  
>   
>  Avant de supprimer les clés, il est recommandé de d'abord sauvegarder la clé de chiffrement symétrique. Vous pouvez utiliser le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour sauvegarder la clé. Ouvrez la Configuration Manager ouvrir, cliquez sur l’onglet **clés de chiffrement** , puis sur le bouton **sauvegarder** . Vous pouvez également écrire un script de commandes WMI afin de sauvegarder la clé de chiffrement. Pour plus d’informations sur WMI, consultez [Méthode BackupEncryptionKey &#40;WMI MSReportServer_ConfigurationSetting&#41;](../wmi-provider-library-reference/configurationsetting-method-backupencryptionkey.md).  
  
1.  Démarrez le Gestionnaire de configuration de Reporting Services et connectez-vous à l'instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous venez d'installer. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Configurez les URL du serveur de rapports et du Gestionnaire de rapports. Pour plus d’informations, consultez [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md).  
  
3.  Configurez la base de données du serveur de rapports, en sélectionnant la base de données du serveur de rapports de votre installation précédente. Une fois la configuration réussie, les services du serveur de rapports redémarreront et, une fois la connexion établie à la base de données du serveur de rapports, la base de données sera automatiquement mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations sur l’exécution de l’Assistant Modification de base de données que vous utilisez pour créer ou sélectionner une base de données du serveur de rapports, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
4.  Restaurez les clés de chiffrement. Cette étape est indispensable pour activer le chiffrement réversible sur les chaînes de connexion préexistantes et les informations d'identification déjà présentes dans la base de données du serveur de rapports. Pour plus d’informations, consultez [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
5.  Si vous avez installé le serveur de rapports sur un nouvel ordinateur et que vous utilisez le Pare-feu Windows, assurez-vous que le port TCP sur lequel le serveur de rapports est à l'écoute est ouvert. Par défaut, il s'agit du port 80. Pour plus d’informations, consultez [Configurer un pare-feu pour accéder au serveur de rapports](../report-server/configure-a-firewall-for-report-server-access.md).  
  
6.  Si vous souhaitez administrer votre serveur de rapports en mode natif localement, vous devez configurer le système d'exploitation pour permettre l'administration locale à l'aide du Gestionnaire de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="copy-custom-configuration-settings-to-rsreportserverconfig-file"></a><a name="bkmk_copy_custom_config"></a> Copie des paramètres de configuration personnalisés dans le fichier RSReportServer.config  
 Si vous avez modifié le fichier RSReportServer.config ou RSWebApplication.config dans l'installation précédente, vous devez apporter les mêmes modifications au nouveau fichier RSReportServer.config. La liste suivante résume certaines des raisons pour lesquelles vous avez pu modifier le fichier de configuration précédent et fournit des liens vers des informations supplémentaires sur la manière de configurer les mêmes paramètres dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Personnalisation|Information|  
|-------------------|-----------------|  
|Remise du courrier électronique du serveur de rapports avec des paramètres personnalisés|[Configurer un serveur de rapports pour la remise par messagerie &#40;ssrs Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) et [paramètres de messagerie-Configuration Manager &#40;le Mode natif SSRS&#41;](e-mail-settings-reporting-services-native-mode-configuration-manager.md).|  
|Paramètres d'informations de périphérique|[Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md)|  
|Gestionnaire de rapports sur une instance distante|[Configurer le Gestionnaire de rapports &#40;mode natif&#41;](../report-server/configure-web-portal.md)|  
  
##  <a name="windows-service-group-and-security-acls"></a><a name="bkmk_windowsservice_group"></a> Groupe de service Windows et ACL de sécurité  
 Dans [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] , il existe un groupe de service, le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] groupe de service Windows, qui est utilisé pour créer des listes de contrôle d’accès (ACL) de sécurité pour toutes les clés de Registre, les fichiers et les dossiers installés avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Ce nom de groupe Windows apparaît au format SQLServerReportServerUser $ \<*computer_name*> $ \<*instance_name*> . Ce groupe remplace les deux groupes de services Windows dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous avez des listes de contrôle d’accès personnalisées associées à l’un des [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] groupes Windows, vous devrez appliquer ces listes de contrôle d’accès au nouveau groupe pour votre nouvelle instance de serveur de rapports dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="verify-your-deployment"></a><a name="bkmk_verify"></a> Vérification de votre déploiement  
  
1.  Testez les répertoires virtuels du serveur de rapports et du Gestionnaire de rapports en ouvrant un navigateur et en tapant une adresse URL dans le champ approprié. Pour plus d’informations, consultez [Vérifier une installation de Reporting Services](verify-a-reporting-services-installation.md).  
  
2.  Testez les rapports et assurez-vous qu'ils contiennent les données attendues. Passez en revue les informations de la source de données pour vérifier si ses informations de connexion sont toujours spécifiées. Le serveur de rapports utilise le modèle objet des rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] lors du traitement et du rendu des rapports, mais il ne remplace pas les constructions [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] par de nouveaux éléments RDL (Report Definition Language). Pour en savoir plus sur l’exécution de rapports existants sur un serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , consultez [Rapports de mise à niveau](upgrade-reports.md).  
  
##  <a name="remove-unused-programs-and-files"></a><a name="bkmk_remove_unused"></a> Suppression des programmes et fichiers inutiles  
 Une fois que vous avez effectué la migration de votre serveur de rapports vers une [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance, vous pouvez effectuer les étapes suivantes pour supprimer des programmes et des fichiers qui ne sont plus nécessaires.  
  
1.  Désinstallez la version précédente de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] si elle n'est plus nécessaire. Cette étape ne supprime pas les éléments suivants, mais vous pouvez les supprimer manuellement si vous n'en avez plus besoin :  
  
    -   Ancienne base de données du serveur de rapports  
  
    -   Rôle RsExec  
  
    -   Comptes de service du serveur de rapports  
  
    -   Pool d'applications du service Web Report Server  
  
    -   Répertoires virtuels pour le serveur de rapports et le Gestionnaire de rapports  
  
    -   Fichiers journaux du serveur de rapports  
  
2.  Supprimez IIS si vous n'en avez plus besoin sur cet ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Migrer une installation Reporting Services &#40;le mode SharePoint&#41;](migrate-a-reporting-services-installation-sharepoint-mode.md)   
 [Base de données du serveur de rapports &#40;le mode natif SSRS&#41;](../report-server/report-server-database-ssrs-native-mode.md)   
 [Mettre à niveau et migrer Reporting Services](upgrade-and-migrate-reporting-services.md)   
 [Compatibilité descendante Reporting Services](../reporting-services-backward-compatibility.md)   
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
