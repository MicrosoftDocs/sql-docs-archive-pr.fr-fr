---
title: Assistant modification de base de données (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changedatabase.F1
helpviewer_keywords:
- Change Database Wizard
- report server database, create
ms.assetid: 1a2e8d18-5997-482f-a9c1-87d99f7407b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c1ca83e3e09ffd1aa452c5253db5d7d9347490ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604971"
---
# <a name="change-database-wizard-ssrs-native-mode"></a>Assistant Modification de base de données (SSRS en mode natif)
  Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit l'Assistant Modification de la base de données pour vous guider à travers les différentes étapes de la création d'une base de données du serveur de rapports ou de la sélection d'une base de données existante du serveur de rapports en vue de l'utiliser avec l'instance en cours du serveur de rapports.  
  
 Si vous sélectionnez une base de données du serveur de rapports d'une version antérieure, elle sera mise à niveau pour correspondre à la version de l'instance du serveur de rapports à laquelle elle est connectée. Lorsque le service démarre, il vérifie automatiquement la version de la base de données et la met automatiquement à niveau avec le schéma en cours.  
  
 Pour démarrer l'Assistant, cliquez sur **Modifier la base de données** dans la page Base de données du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour obtenir des instructions sur la façon de démarrer le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultez [Gestionnaire de configuration de Reporting Services &#40;Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.  
  
## <a name="options"></a>Options  
 **Action**  
 Sélectionnez la tâche à exécuter. Vous pouvez créer une base de données en mode natif ou en mode intégré SharePoint. Ou, vous pouvez sélectionner une base de données existante du serveur de rapports afin de l'utiliser avec l'instance en cours du serveur de rapports.  
  
 **Serveur de base de données**  
 Spécifiez le nom de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance qui héberge la base de données du serveur de rapports. Vous pouvez utiliser une instance par défaut ou nommée sur un ordinateur local ou distant. Si vous vous connectez à une instance nommée, entrez le nom du serveur au format suivant : \<*server*> \\ < *instance*>.  
  
 Pour vous connecter à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , vous devez utiliser les informations d’identification qui ont l’autorisation de se connecter au serveur et de mettre à jour les informations de la base de données. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise vos informations d'identification Windows en cours, mais si vous n'avez pas de connexion ou d'autorisations sur la base de données, vous devez spécifier une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous ne pouvez pas spécifier d'autres informations d'identification Windows. Si vous souhaitez vous connecter en tant qu'utilisateur Windows différent, connectez-vous comme cet utilisateur et démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 La connexion à une instance distante nécessite que vous activiez au préalable cette instance pour les connexions distantes. Certaines versions et éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'autorisent pas les connexions distantes par défaut. Pour vérifier si les connexions distantes sont autorisées, utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et confirmez que les protocoles TCP/IP et des canaux nommés sont activés. Si l'instance distante est également une instance nommée, vérifiez que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est activé et en cours d'exécution sur le serveur cible. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser fournit le numéro de port utilisé par l'instance nommée sur le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **Sauvegarde de la base de données**  
 Spécifie le nom de la base de données du serveur de rapports qui stocke les données du serveur. Vous pouvez spécifier une base de données existante ou en créer une.  
  
 Les propriétés utilisées pour créer une base de données apparaissent dans l'Assistant lorsque vous sélectionnez **Créer une nouvelle base de données** sur la page Actions. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crée deux bases de données liées par le nom : une base de données pour contenir les données statiques et une base de données temporaire pour stocker les données de session et les données de travail. Pour plus d’informations, consultez [base de données du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation en ligne de.  
  
 Vous pouvez également choisir une base de données existante du serveur de rapports. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne filtre pas les bases de données non valides. Les bases de données valides sont basées sur le schéma de base de données du serveur de rapports (vous ne pouvez pas sélectionner une base de données où manquent les tables, les vues ou les procédures stockées nécessaires). Si vous choisissez une base de données créée à partir d'une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], la base de données sera mise à niveau au format actuel.  
  
 **Langage**  
 Cette valeur est définie uniquement lorsque vous créez une nouvelle base de données du serveur de rapports.  
  
 Avec cette valeur, vous spécifiez la langue dans laquelle les définitions de rôle et les descriptions sont créées. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit un modèle d'autorisation à base de rôles qui inclut un ensemble de rôles prédéfinis. Ces rôles sont créés une fois dans la langue spécifiée. Les noms des rôles et les descriptions n'apparaissent jamais dans d'autres langues, même si vous vous connectez au serveur de rapports à l'aide d'un navigateur dont les paramètres de culture ou de langue sont pris en charge par le serveur. La langue que vous spécifiez détermine aussi celle utilisée pour créer le nom du dossier Mes rapports et les dossiers Utilisateurs qui font partie de la fonctionnalité Mes rapports.  
  
 **Mode serveur**  
 Une base de données de serveur de rapports prend en charge le mode natif ou le mode intégré SharePoint. Les modes s'excluent mutuellement.  
  
 Si vous créez une base de données du serveur de rapports, vous devez spécifier un mode. Le mode que vous sélectionnez détermine la structure de la base de données du serveur de rapports et attribue à la propriété système `SharePointIntegrated` du serveur de rapports la valeur `true` ou `false`.  
  
 Si vous sélectionnez une autre base de données du serveur de rapports, le mode de la base de données courante s'affiche afin que vous sachiez comment celle-ci est utilisée.  
  
 **Informations d'identification**  
 Spécifie le compte utilisé par le serveur de rapports pour se connecter à la base de données du serveur de rapports. Les valeurs valides incluent le compte de service du service Web Report Server, une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définie sur l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] que vous utilisez pour héberger le serveur de rapports, ou un compte Windows. Si vous utilisez un compte Windows, vous pouvez spécifier un compte local (* \<computername> \\<nom d' \> utilisateur*) si le serveur de rapports et la base de données se trouvent sur le même ordinateur, ou un compte d’utilisateur de domaine (* \<domain> \\<nom d' \> *utilisateur) s’ils se trouvent sur des ordinateurs différents du même domaine.  
  
 Le serveur de rapports crée alors une connexion de base de données et attribue les autorisations de base de données au compte que vous spécifiez.  
  
 Le serveur de rapports ne crée pas le compte lui-même. Le compte que vous spécifiez doit déjà exister et doit être valide pour votre configuration de déploiement. Plus particulièrement, si la base de données se trouve sur un ordinateur distant et que vous souhaitez utiliser un compte Windows, vous devez spécifier un compte qui a les autorisations de connexion sur cet ordinateur.  
  
 Si l'ordinateur se trouve dans un domaine différent ou non approuvé, pensez à utiliser la connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur le choix d’un compte, consultez [configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Résumé**  
 Vérifiez les paramètres avant que le programme d'installation ne configure la connexion.  
  
 **État d'avancement et fin**  
 Surveillez la progression de chaque tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données &#40;en mode natif SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Assistant modification des informations d’identification &#40;en mode natif SSRS&#41;](../../../2014/sql-server/install/change-credentials-wizard-ssrs-native-mode.md)   
 [Créer une base de données du serveur de rapports en mode natif &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
