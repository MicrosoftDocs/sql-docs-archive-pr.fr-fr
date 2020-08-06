---
title: Assistant modification des informations d’identification (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f2e84ec59f1241a10ce52e597920827f3afbc06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604976"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistant Modification des informations d'identification (SSRS en mode natif)
  Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit l'Assistant Modification des informations d'identification pour vous guider à travers les étapes de reconfiguration du compte que le serveur de rapports utilise pour se connecter à la base de données du serveur de rapports. Lorsque vous modifiez les informations d'identification, le Gestionnaire de configuration met à jour toutes les autorisations et informations de connexion de base de données sur le serveur de base de données pour la base de données du serveur de rapports en cours d'utilisation par le serveur de rapports.  
  
 Pour démarrer l'Assistant, cliquez sur **Modifier les informations d'identification** dans la page Base de données du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour obtenir des instructions sur la façon de démarrer le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultez [Gestionnaire de configuration de Reporting Services &#40;Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.  
  
## <a name="options"></a>Options  
 **Serveur de base de données**  
 Spécifie le nom de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance qui exécute la base de données du serveur de rapports.  
  
 Pour vous connecter à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , vous devez utiliser les informations d’identification qui ont l’autorisation de se connecter au serveur et de mettre à jour les informations de la base de données. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise vos informations d'identification Windows en cours, mais si vous n'avez pas de connexion ou d'autorisations sur la base de données, vous pouvez spécifier une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Vous ne pouvez pas spécifier d'autres informations d'identification Windows. Si vous souhaitez vous connecter en tant qu'utilisateur Windows différent, connectez-vous comme cet utilisateur et démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Informations d'identification**  
 Spécifie le compte utilisé par le serveur de rapports pour se connecter à la base de données du serveur de rapports. Les valeurs valides incluent le compte de service du service Web Report Server, une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définie sur l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] que vous utilisez pour héberger le serveur de rapports, ou un compte Windows. Si vous utilisez un compte Windows, vous pouvez spécifier un compte local (* \<computername> \\<nom d' \> utilisateur*) si le serveur de rapports et la base de données se trouvent sur le même ordinateur, ou un compte d’utilisateur de domaine (* \<domain> \\<nom d' \> *utilisateur) s’ils se trouvent sur des ordinateurs différents du même domaine.  
  
 Le serveur de rapports crée alors une connexion de base de données et attribue les autorisations de base de données au compte que vous spécifiez.  
  
 Le serveur de rapports ne crée pas le compte lui-même. Le compte que vous spécifiez doit déjà exister et doit être valide pour votre configuration de déploiement. Plus particulièrement, si la base de données se trouve sur un ordinateur distant et que vous souhaitez utiliser un compte Windows, vous devez spécifier un compte qui a les autorisations de connexion sur cet ordinateur.  
  
 Si l'ordinateur se trouve dans un domaine différent ou non approuvé, pensez à utiliser la connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur le choix d’un compte, consultez [configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Résumé**  
 Vérifiez les paramètres avant l'Assistant ne s'exécute.  
  
 **État d'avancement et fin**  
 Surveillez la progression de chaque tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données &#40;en mode natif SSRS&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Assistant modification de base de données &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Créer une base de données du serveur de rapports en mode natif &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
