---
title: Utilitaire Ssms | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cfc9469e49e6ce3839d02a61477b8957fbc13e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613767"
---
# <a name="ssms-utility"></a>Utilitaire Ssms
  L’utilitaire **Ssms**ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Si cela est spécifié, **Ssms** établit également une connexion à un serveur et ouvre des requêtes, des scripts, des fichiers, des projets et des solutions.  
  
 Vous pouvez spécifier des fichiers contenant des requêtes, des projets ou des solutions. Les fichiers qui contiennent des requêtes sont automatiquement connectés à un serveur si des informations de connexion sont fournies et si le type de fichier est associé à ce type de serveur. Par exemple, les fichiers .sql ouvrent une fenêtre Éditeur de requête SQL dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], tandis que des fichiers .mdx ouvrent une fenêtre Éditeur de requête MDX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Les**solutions et projets SQL Server** s’ouvrent dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  L’utilitaire **Ssms** n’exécute pas de requêtes. Pour exécuter des requêtes depuis la ligne de commande, employez l’utilitaire **sqlcmd** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a>Arguments  
 *scriptfile*  
 Spécifie un ou plusieurs fichiers de script à ouvrir. Le paramètre doit contenir le chemin complet d'accès aux fichiers.  
  
 *projectfile*  
 Spécifie un projet de script à ouvrir. Le paramètre doit contenir le chemin d'accès complet au fichier de projet de script.  
  
 *solutionfile*  
 Spécifie une solution à ouvrir. Le paramètre doit contenir le chemin d'accès complet au fichier de solution.  
  
 [**-S** _nom_serveur_]  
 Nom du serveur  
  
 [**-d** _DatabaseName_]  
 Nom de la base de données  
  
 [**-U** _nom_d_utilisateur_]  
 Nom d'utilisateur lors d'une connexion avec l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 [**-P** _mot de passe_]  
 Mot de passe lors d'une connexion avec l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 [**-E**]  
 Connexion avec l'authentification Windows  
  
 [**-nosplash**]  
 Empêche [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] d'afficher le graphique de l'écran de démarrage lors de l'ouverture. Utilisez cette option lors d'une connexion à l'ordinateur exécutant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] au moyen des services Terminal Server sur une connexion dotée d'une bande passante limitée. Cet argument ne respecte pas la casse et peut apparaître avant ou après d'autres arguments  
  
 [**-log**_[nom de fichier] ?_]  
 Consigne l'activité de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] dans le fichier spécifié à des fins de dépannage  
  
 [**-?**]  
 Affiche l'aide de la ligne de commande.  
  
## <a name="remarks"></a>Notes  
 Tous les commutateurs sont facultatifs et séparés par un espace à l'exception des fichiers qui sont séparés par des virgules. Si vous ne spécifiez pas de commutateur, **Ssms** ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] tel que spécifié dans les paramètres **Options** du menu **Outils** . Par exemple, si l’option **Au démarrage** de la page **Environnement/Général** spécifie **Ouvrir la fenêtre de nouvelle requête**, **Ssms** s’ouvre avec un éditeur de requête vide.  
  
 Le commutateur **-log** doit apparaître à la fin de la ligne de commande, après tous les autres commutateurs. L'argument de nom de fichier (filename) est facultatif. Si un nom de fichier est spécifié et que le fichier n'existe pas, il est créé. Si le fichier ne peut pas être créé (par exemple, en raison d’un accès en écriture insuffisant), le journal est écrit à la place à l’emplacement APPDATA non localisé (voir ci-dessous). Si l'argument du nom de fichier (filename) n'est pas spécifié, deux fichiers sont écrits dans le dossier des données d'application non localisé de l'utilisateur actuel. Le dossier de données d'application non localisé de SQL Server peut se trouver dans la variable d'environnement APPDATA. Par exemple, pour SQL Server 2012, le dossier est \<system drive> : \utilisateurs \\<nom d’utilisateur \> \AppData\Roaming\Microsoft\AppEnv\10.0 \\ . Les deux fichiers sont nommés, par défaut, ActivityLog.xml et ActivityLog.xsl. Le premier contient les données du journal des activités et le deuxième est une feuille de style XML qui offre un moyen plus pratique d'afficher le fichier XML. Suivez les étapes ci-dessous pour afficher le fichier journal dans votre visionneuse XML par défaut, comme Internet Explorer : cliquez sur Démarrer, puis sur Exécuter...», tapez « \<system drive> : \utilisateurs \\<nom d’utilisateur \>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml » dans le champ fourni, puis appuyez sur entrée.  
  
 Les fichiers qui contiennent des requêtes demandent une confirmation pour la connexion à un serveur si des informations de connexion sont fournies et si le type de fichier est associé à ce type de serveur. Par exemple, les fichiers .sql ouvrent une fenêtre Éditeur de requête SQL dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], tandis que des fichiers .mdx ouvrent une fenêtre Éditeur de requête MDX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Les**solutions et projets SQL Server** s’ouvrent dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Le tableau suivant mappe des types de serveur à des extensions de fichier.  
  
|Type de serveur|Extension|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|.sql|  
|SQL Server Analysis Services|.mdx<br /><br /> .xmla|  
  
## <a name="examples"></a>Exemples  
 Le script suivant ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes avec les paramètres par défaut :  
  
```  
Ssms  
  
```  
  
 Le script suivant ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes, avec l'authentification Windows, avec l'Éditeur de code réglé sur le serveur `ACCTG and the database AdventureWorks2012,` , sans affichage de l'écran de démarrage :  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 Le script suivant ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes et ouvre le script MonthEndQuery.  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 Le script suivant ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes et ouvre le projet NewReportsProject sur l'ordinateur nommé `developer`:  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 Le script suivant ouvre [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] à partir d'une invite de commandes et ouvre la solution MonthlyReports.  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  
