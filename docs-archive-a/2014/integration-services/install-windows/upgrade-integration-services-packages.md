---
title: Mettre à niveau les packages Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a6ca4f80b25a8cc4628da4382c1aae971c74bf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605634"
---
# <a name="upgrade-integration-services-packages"></a>Mettre à niveau des packages Integration Services
  Lorsque vous mettez à niveau une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] vers la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vos packages existants ne [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] sont pas automatiquement mis à niveau vers le format de package utilisé par la version actuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Vous devez choisir une méthode de mise à niveau et mettre à niveau vos packages manuellement.  
  
 Lorsque vous mettez à niveau un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migre les scripts dans une tâche de script et un composant script vers [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , les scripts des tâches de script ou des composants de script utilisés [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour les applications (VSA). Pour plus d’informations sur les modifications que vous devrez peut-être effectuer avant la migration et sur l’échec de conversion de scripts, consultez [Migrer des scripts vers VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).  
  
 Pour plus d'informations sur les packages de mise à niveau lorsque vous convertissez un projet en modèle de déploiement de projet, consultez [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).  
  
## <a name="sql-server-2000-data-transformation-services-packages"></a>Packages Data Transformation Services SQL Server 2000  
 La prise en charge de la migration ou de l’exécution des packages DTS (Data Transformation Services) a été supprimée dans la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Les fonctionnalités DTS suivantes ne sont plus disponibles.  
  
-   Runtime DTS ;  
  
-   DTS API ;  
  
-   Assistant Migration de package pour la migration de packages DTS vers la prochaine version de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Prise en charge de la maintenance des packages DTS dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   Tâche d'exécution de package DTS 2000 ;  
  
-   analyse du Conseiller de mise à niveau des packages DTS.  
  
 Les options suivantes sont disponibles pour la migration des packages DTS.  
  
-   Migrez les packages vers [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], puis mettez à niveau les packages vers [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Pour plus d'informations sur la migration des packages DTS vers [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] et [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], consultez [Migration des packages DTS (Data Transformation Services](https://go.microsoft.com/fwlink/?LinkId=251870) (2005) et [Migration des packages DTS (Data Transformation Services)](https://go.microsoft.com/fwlink/?LinkId=251871) (2008).  
  
-   Recréez les packages DTS à l'aide de [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Pour plus d’informations sur les nouvelles fonctionnalités de [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)], consultez [Nouveautés &#40;Integration Services&#41;](../what-s-new-in-integration-services-in-sql-server-2016.md). Pour obtenir une vue d’ensemble de la structure des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Packages Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md).  
  
## <a name="selecting-an-upgrade-method"></a>Choix d'une méthode de mise à niveau  
 Vous pouvez utiliser différentes méthodes pour mettre à niveau des packages [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . Pour certaines d'entre elles, la mise à niveau n'est que temporaire. Pour d'autres, elle est définitive. Le tableau suivant décrit chacune de ces méthodes et indique si la mise à niveau est temporaire ou définitive.  
  
> [!NOTE]  
>  Lousque vous exécutez un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] à l'aide de l'utilitaire **dtexec** (dtexec.exe) qui est installé avec la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the tempouary package upgrade increases the execution time. Le taux d'accroissement de temps d'exécution de package varie selon la taille du package. Pour éviter une augmentation pendant la durée d'exécution, il est recommandé d'effectuer la mise à niveau du package avant de l'exécuter.  
  
|Méthode de mise à niveau|Type de mise à niveau|  
|--------------------|---------------------|  
|Utiliser l'utilitaire **dtexec** (dtexec.exe) qui est installé avec la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .<br /><br /> Pour plus d'informations, consultez [Utilitaire dtexec](../packages/dtexec-utility.md).|La mise à niveau de packages est temporaire. Pour un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , la migration de script est temporaire.<br /><br /> Les modifications ne peuvent pas être enregistrées.|  
|Ouvrir un fichier de package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|La mise à niveau de packages est définitive si vous enregistrez le package, sinon, elle est temporaire.<br /><br /> Pour un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , le script de migration est définitif si vous enregistrez le package ; sinon, il est temporaire.|  
|Ajouter un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] à un projet existant dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|La mise à niveau de packages est permanente. Pour un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , la migration de script est permanente.|  
|Ouvrez un fichier projet [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], puis utilisez l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour mettre à niveau plusieurs packages dans le projet.<br /><br /> Pour plus d’informations, consultez [Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS](upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) et [Aide sur l’Assistant Mise à niveau de packages SSIS via la touche F1](../ssis-package-upgrade-wizard-f1-help.md).|La mise à niveau de packages est permanente. Pour un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , la migration de script est permanente.|  
|Utilisez l’utilitaire <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> pour mettre à niveau un ou plusieurs packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|La mise à niveau de packages est permanente. Pour un package [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , la migration de script est permanente.|  
  
## <a name="custom-applications-and-custom-components"></a>Applications et composants personnalisés  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ne fonctionnent pas avec la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Vous pouvez utiliser la version actuelle des outils [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour exécuter et gérer des packages qui incluent des composants personnalisés [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)]. Nous avons ajouté quatre règles de redirection de liaison aux fichiers suivants pour aider à rediriger des assemblys du runtime de la version 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]) vers la version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 Pour utiliser [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] pour concevoir des packages qui incluent [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] des [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] composants personnalisés et, vous devez modifier le fichier devenv.exe.config qui se trouve dans *\<drive>* : \Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE.  
  
 Pour utiliser ces packages avec les applications clientes générées avec le runtime pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], incluez les règles de redirection dans la section de configuration du fichier *.exe .config de l'exécutable. Les règles redirigent les assemblys du runtime vers la version 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]). Pour plus d’informations sur la redirection des versions d’assemblys, consultez [Élément \<assemblyBinding> pour \<runtime>](https://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### <a name="locating-the-assemblies"></a>Recherche d'assemblys  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les assemblys [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ont été mis à niveau vers le .NET 4.0. Il existe un Global Assembly Cache distinct pour .NET 4, situé dans *\<drive>* :\Windows\Microsoft.NET\assembly. Vous trouverez tous les assemblys [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sous ce chemin d'accès, en général dans le dossier GAC_MSIL.  
  
 Comme dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les principaux fichiers .dll d’extensibilité [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] se trouvent également dans *\<drive>* :\Program files\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>Présentation des résultats de mise à niveau de packages SQL Server  
 Au cours de la mise à niveau de packages, la plupart des composants et fonctionnalités des packages [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sont convertis de façon transparente en leurs équivalents de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il existe toutefois certains composants et fonctionnalités pour lesquels aucune mise à niveau ne sera effectuée ou pour lesquels vous devez connaître les résultats. Le tableau suivant identifie ces composants et fonctionnalités.  
  
> [!NOTE]  
>  Pour identifier les packages concernés par les points répertoriés dans le tableau, exécutez le Conseiller de mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
|Composant ou fonctionnalité|Résultats de la mise à niveau|  
|--------------------------|---------------------|  
|Chaînes de connexion|Pour les packages [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , les noms de certains fournisseurs ont changé et requièrent des valeurs différentes dans les chaînes de connexion. Pour mettre à jour les chaînes de connexion, utilisez l'une des procédures suivantes :<br /><br /> -Utilisez l' [!INCLUDE[ssIS](../../includes/ssis-md.md)] Assistant Mise à niveau de packages pour mettre à niveau le package, puis sélectionnez l’option **mettre à jour les chaînes de connexion pour utiliser les nouveaux noms de fournisseurs** .<br /><br /> -Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , dans la page général de la boîte de dialogue Options, sélectionnez l’option **mettre à jour les chaînes de connexion pour utiliser les nouveaux noms de fournisseurs** . Pour plus d’informations sur cette option, consultez la [page général](../general-page-of-integration-services-designers-options.md).<br /><br /> -Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package et modifiez manuellement le texte de la propriété ConnectionString.<br /><br /> Remarque : vous ne pouvez pas appliquer les procédures ci-dessus pour mettre à jour une chaîne de connexion lorsque celle-ci est stockée dans un fichier de configuration ou dans un fichier de source de données, ou lorsqu’une expression définit la propriété `ConnectionString`. Pour mettre à jour la chaîne de connexion dans ces cas-là, vous devez mettre à jour le fichier ou l'expression manuellement.<br /><br /> Pour plus d’informations sur les sources de données disponibles, consultez [Sources de données](../connection-manager/data-sources.md).|  
|Transformation de recherche|Pour les packages [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], le processus de mise à niveau effectue automatiquement une mise à niveau de la transformation de recherche vers la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Toutefois, la version actuelle de ce composant propose des fonctions supplémentaires dont vous souhaiterez peut-être tirer parti.<br /><br /> Pour plus d’informations, voir [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).|  
|Tâche de script et composant Script|Pour les packages [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , le processus de mise à niveau de packages effectue automatiquement une migration des scripts de la tâche de script et du composant Script de VSA vers VSTA.<br /><br /> Pour plus d’informations sur les modifications que vous devrez peut-être effectuer avant la migration et sur l’échec de conversion de scripts, consultez [Migrer des scripts vers VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>Scripts qui dépendent d'ADODB.dll  
 Les scripts de la tâche de script et du composant Script qui référencent explicitement ADODB.dll risquent de ne pas pouvoir être mis à niveau ou de ne pas pouvoir s'exécuter sur les ordinateurs qui ne disposent pas de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Pour permettre la mise à niveau des scripts de la tâche de script et du composant Script, il est recommandé de supprimer la dépendance sur ADODB.dll.  Ado.Net est l'alternative recommandée pour le code managé, à l'instar des scripts VB et C#.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Article technique, [5 conseils pour une mise à niveau en douceur de SSIS vers SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=235321), sur msdn.microsoft.com.  
  
-   Entrée de blog [Faire fonctionner vos extensions et applications SSIS personnalisées existantes à Denali](https://go.microsoft.com/fwlink/?LinkId=238157), sur blogs.msdn.com.  
  
-   WebCast [Mise à niveau des packages SSIS vers SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=258674), sur channel9.msdn.com.  
  
  
