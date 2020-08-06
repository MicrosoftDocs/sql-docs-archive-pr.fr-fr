---
title: Page nouvelle source de données (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 35563d4c-a3d5-4f95-bf46-605da9dfcbb8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8117174f23ae85cd51c30e5ad0026ab2a01be27e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612197"
---
# <a name="new-data-source-page-report-manager"></a>Page Nouvelle source de données (Gestionnaire de rapports)
  La page Nouvelle source de données vous permet de créer un élément de source de données partagée. Une source de données partagée définit une connexion à une source de données externe. À l'aide d'une source de données partagée, vous pouvez créer et gérer les paramètres de connexion à la source de données séparément des rapports, modèles et abonnements pilotés par les données qui utilisent la source de données.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-new-data-source-page"></a>Pour ouvrir la page Nouvelle source de données  
  
1.  Ouvrez le Gestionnaire de rapports et accédez au dossier dans lequel vous souhaitez créer une source de données.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle source de données**. Vous devez disposer des autorisations de gestionnaire de contenu pour créer une source de données partagée.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la source de données partagée qui est utilisé pour identifier l'élément dans l'arborescence des dossiers du serveur de rapports.  
  
 **Description**  
 Fournit des informations sur la source de données partagée. Cette description apparaît dans la page Contenu.  
  
 **Masquer en mode Liste**  
 Activez cette option pour masquer la source de données partagée pour les utilisateurs qui utilisent le mode de visualisation sous forme de listes dans le Gestionnaire de rapports. Le mode Liste est le format d'affichage par défaut lorsque vous parcourez l'arborescence des dossiers du serveur de rapports. En mode Liste, les noms et les descriptions des éléments sont affichés sur la largeur de la page. Un autre format d'affichage, le mode Détails, est également disponible. En mode Détails, les descriptions ne sont pas affichées, mais cette vue fournit d'autres informations sur l'élément. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Activer cette source de données**  
 Sélectionnez cette option pour activer ou désactiver la source de données partagée. Vous pouvez désactiver la source de données partagée pour empêcher le traitement des rapports et modèles qui font référence à l'élément.  
  
 **Type de source de données**  
 Spécifiez l'extension pour le traitement des données utilisée pour traiter les données de la source de données. Le serveur de rapports comprend des extensions pour le traitement des données pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , Oracle, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , SAP, XML, ODBC et OLE DB. Des extensions supplémentaires peuvent être disponibles auprès d'éditeurs tiers.  
  
 Pour plus d’informations sur la prise en charge des sources de données distantes et non-SQL, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (lien hypertexte « <https://go.microsoft.com/fwlink/?linkid=232473> » <https://go.microsoft.com/fwlink/?linkid=232473> ) et [sources de données prises en charge par Reporting Services &#40;&#41;SSRS ](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 **Chaîne de connexion**  
 Spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. Le type de connexion détermine la syntaxe à utiliser. Par exemple, une chaîne de connexion pour une extension pour le traitement des données XML est une URL vers un document XML. Dans la plupart des cas, une chaîne de connexion type spécifie le serveur de bases de données et un fichier de données.  
  
 L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] base de données :  
  
```  
data source=<a SQL Server instance>;initial catalog=AdventureWorks2012  
```  
  
 Pour obtenir plus d’exemples et d’informations sur les différentes façons de spécifier une chaîne de connexion, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 **Se connecter avec**  
 Spécifiez les options qui déterminent de quelle façon les informations d'identification sont obtenues.  
  
> [!IMPORTANT]  
>  Si les informations d'identification sont fournies dans la chaîne de connexion, les options et les valeurs indiquées dans cette section sont ignorées. Notez que si vous spécifiez les informations d'identification sur la chaîne de connexion, les valeurs sont affichées en texte en clair et sont visibles par tous les utilisateurs qui affichent cette page.  
  
 **Les informations d'identification fournies par l'utilisateur qui exécute le rapport (Se connecter avec)**  
 Chaque utilisateur est invité à taper un nom d'utilisateur et un mot de passe pour accéder à la source de données. Vous pouvez définir le texte de l'invite qui demande les informations d'identification aux utilisateurs. La chaîne de texte par défaut est la suivante : « Entrer un nom d'utilisateur et un mot de passe pour accéder à la source de données ».  
  
 Activez la case à cocher **Utiliser en tant qu’informations d’identification Windows lors de la connexion à la source de données** si les informations d’identification fournies par l’utilisateur sont des informations d’identification de l’authentification Windows. N'activez pas cette case à cocher si vous utilisez une authentification dans la base de données (par exemple, l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
 **Informations d'identification stockées en sécurité dans le serveur de rapports (Se connecter avec)**  
 Stocke un nom d'utilisateur et un mot de passe chiffrés dans la base de données du serveur de rapports. Choisissez cette option pour exécuter un rapport sans assistance (par exemple, des rapports qui sont démarrés par des planifications ou des événements au lieu des actions utilisateur). Si vous utilisez la sécurité par défaut, le nom d'utilisateur doit être un compte de domaine Windows. Spécifiez le compte au format suivant : \<domain> \\<nom d’utilisateur \> . Le compte que vous spécifiez doit disposer d'autorisations d'ouverture d'une session locale sur l'ordinateur qui héberge la source de données utilisée par le rapport.  
  
 Activez la case à cocher **Utiliser en tant qu'informations d'identification Windows lors de la connexion à la source de données** si les informations d'identification sont des informations d'identification de l'authentification Windows. N'activez pas cette case à cocher si vous utilisez une authentification dans la base de données (par exemple, l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
 Si vous utilisez l'authentification dans la base de données, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données** pour autoriser la délégation des informations d'identification de la base de données, mais uniquement si un serveur de base de données prend en charge l'emprunt d'identité. Pour les bases de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , cette option définit la fonction SETUSER.  
  
 **Sécurité intégrée Windows (Se connecter avec)**  
 Utilise les informations d'identification Windows de l'utilisateur actuel pour accéder à la source de données. Choisissez cette option lorsque les informations d'identification utilisées pour accéder à une source de données sont identiques à celles utilisées pour ouvrir une session sur le domaine réseau. Cette option convient mieux lorsque l'authentification Kerberos est activée pour votre domaine ou que la source de données se trouve sur le même ordinateur que le serveur de rapports. Si l'authentification Kerberos n'est pas activée, les informations d'identification Windows peuvent être transmises à un autre ordinateur. Si des connexions supplémentaires à des ordinateurs sont requises, vous obtiendrez une erreur à la place des données attendues.  
  
 Un administrateur du serveur de rapports peut désactiver l'utilisation de la sécurité intégrée de Windows pour accéder aux sources de données de rapports. Si cette valeur est grisée, la fonctionnalité n'est pas disponible.  
  
 N'utilisez pas cette option si vous projetez de planifier ce rapport ou de vous y abonner. Le traitement de rapports sans assistance ou planifié requiert des informations d'identification qui peuvent être obtenues sans entrée d'utilisateur ou le contexte de sécurité d'un utilisateur actuel. Seules les informations d'identification stockées fournissent cette fonction. Pour cette raison, le serveur de rapports vous empêche de planifier le traitement d'un rapport ou d'un abonnement si le rapport est configuré pour le type d'informations d'identification de sécurité intégrée de Windows. Si vous choisissez cette option pour un rapport qui fait déjà l'objet d'un abonnement ou pour lequel des opérations sont planifiées, les abonnements et opérations planifiées s'arrêteront.  
  
 **Informations d'identification non requises (Se connecter avec)**  
 Spécifie que les informations d'identification ne sont pas requises pour accéder à la source de données. Notez que si la source de données nécessite une ouverture de session d'utilisateur, cette option est sans effet. Vous devez choisir cette option uniquement si la connexion de source de données ne nécessite pas d'informations d'identification des utilisateurs.  
  
 Pour utiliser cette option, vous devez avoir configuré précédemment le compte d'exécution sans assistance pour le déploiement du serveur de rapports. Le compte d'exécution sans assistance est utilisé pour se connecter aux sources de données externes lorsque les autres sources d'informations d'identification ne sont pas disponibles. Si vous spécifiez cette option et que le compte n'est pas configuré, la connexion à la source de données de rapports échouera et le traitement de rapports ne se produira pas. Pour plus d’informations sur ce compte, consultez [configurer le compte d’exécution sans assistance &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 **OK**  
 Cliquez pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page contenu &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Créer, modifier et supprimer des sources de données partagées &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Aide (F1) Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapports](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
