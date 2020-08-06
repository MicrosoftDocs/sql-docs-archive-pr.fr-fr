---
title: Rôles de base de données fixes de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, roles
- SQLAgentUserRole database role
- SQLAgentReaderRole database role
- multiple roles
- security [SQL Server Agent], fixed database roles
- fixed database roles [SQL Server]
- SQLAgentOperatorRole database role
ms.assetid: 719ce56b-d6b2-414a-88a8-f43b725ebc79
author: stevestein
ms.author: sstein
ms.openlocfilehash: e5e523f720292909ccb9d943524e5d6d7d017b28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613269"
---
# <a name="sql-server-agent-fixed-database-roles"></a>Rôles de base de données fixes de SQL Server Agent
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède les rôles fixes de base de données **msdb** suivants, qui permettent aux administrateurs de contrôler plus précisément l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Les rôles sont classés ci-après selon leurs privilèges d'accès, du moins privilégié au plus privilégié :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Quand les utilisateurs qui ne sont pas membres de l’un de ces rôles sont connectés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], le nœud **SQL Server Agent** dans l’Explorateur d’objets n’est pas visible. Pour utiliser **Agent, un utilisateur doit être membre de l’un de ces rôles de base de données fixes ou du rôle serveur fixe** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions-of-sql-server-agent-fixed-database-roles"></a>Autorisations des rôles de base de données fixes de SQL Server Agent  
 Les autorisations des rôles de base de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont concentriques les unes avec les autres : les rôles les plus privilégiés héritent des autorisations des rôles les moins privilégiés sur les objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (notamment les alertes, les opérateurs, les travaux, les planifications et les proxys). Par exemple, si les membres du rôle **SQLAgentUserRole** le moins privilégié ont l’autorisation d’accéder au proxy_A, les membres des rôles **SQLAgentReaderRole** et **SQLAgentOperatorRole** ont automatiquement accès à ce proxy, même si l’autorisation ne leur a pas été explicitement accordée. Ceci peut avoir des incidences sur la sécurité qui sont décrites dans les sections suivantes par rapport à chaque rôle.  
  
### <a name="sqlagentuserrole-permissions"></a>Autorisations du rôle SQLAgentUserRole  
 **SQLAgentUserRole** est le moins privilégié des rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Il dispose uniquement d'autorisations sur les opérateurs, les travaux locaux et les planifications de travaux. Les membres du rôle **SQLAgentUserRole** disposent uniquement d’autorisations sur les travaux locaux et les planifications des travaux qu’ils possèdent. Ils ne peuvent pas utiliser de travaux multiserveur (travaux de serveur maître et cible) et ne peuvent pas modifier l'appartenance des travaux pour accéder aux travaux qui ne leur appartiennent pas encore. Les membres de**SQLAgentUserRole** peuvent uniquement consulter la liste des proxys disponibles dans la boîte de dialogue **Propriétés de l’étape du travail** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Seul le nœud **Travaux** de l’Explorateur d’objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est visible aux membres de **SQLAgentUserRole**.  
  
> [!IMPORTANT]  
>  Tenez compte des implications en matière de sécurité avant d’accorder l’accès proxy aux **membres du** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Agentdatabaseroles**. Les rôles **SQLAgentReaderRole** et **SQLAgentOperatorRole** sont automatiquement membres du rôle **SQLAgentUserRole**. Ceci signifie que les membres de **SQLAgentReaderRole** et de **SQLAgentOperatorRole** ont accès à tous les proxys de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent auxquels **SQLAgentUserRole** peut accéder et qu’ils peuvent les utiliser.  
  
 Le tableau suivant récapitule les autorisations de **SQLAgentUserRole** sur les objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Action|Opérateurs|Travaux locaux<br /><br /> (travaux lui appartenant uniquement)|Calendriers de travaux<br /><br /> (planifications lui appartenant uniquement)|Proxies|  
|------------|---------------|----------------------------------------|------------------------------------------------|-------------|  
|Créer/modifier/supprimer|Non|Oui <sup>1</sup>|Oui|Non|  
|Afficher la liste (énumérer)|Oui <sup>2</sup>|Oui|Oui|Oui <sup>3</sup>|  
|Activer/désactiver|Non|Oui|Oui|Non applicable|  
|Afficher les propriétés|Non|Oui|Oui|Non|  
|Exécuter/arrêter/démarrer|Non applicable|Oui|Non applicable|Non applicable|  
|Afficher l’historique des travaux|Non applicable|Oui|Non applicable|Non applicable|  
|Supprimer l'historique des travaux|Non applicable|Non <sup>4</sup>|Non applicable|Non applicable|  
|Attacher/détacher|Non applicable|Non applicable|Oui|Non applicable|  
  
 <sup>1</sup> impossible de modifier la propriété du travail.  
  
 <sup>2</sup> peut obtenir la liste des opérateurs disponibles à utiliser dans **sp_notify_operator** et la boîte de dialogue **Propriétés du travail** de Management Studio.  
  
 <sup>3</sup> liste de proxys uniquement disponibles dans la boîte de dialogue Propriétés de l' **étape du travail** de Management Studio.  
  
 <sup>4</sup> les membres de **SQLAgentUserRole** doivent disposer explicitement de l’autorisation EXECUTE sur **sp_purge_jobhistory** pour supprimer l’historique des travaux dont ils sont propriétaires. Ils ne peuvent supprimer l'historique d'aucun autre travail.  
  
### <a name="sqlagentreaderrole-permissions"></a>Autorisations du rôle SQLAgentReaderRole  
 **SQLAgentReaderRole** inclut toutes les autorisations de **SQLAgentUserRole** , ainsi que les autorisations permettant d’afficher la liste des travaux multiserveur disponibles, leurs propriétés et leur historique. Les membres de ce rôle peuvent également afficher la liste de tous les travaux et planifications de travaux disponibles et de leurs propriétés, pas uniquement la liste des travaux et des planifications de travaux dont ils sont propriétaires. Les membres de**SQLAgentReaderRole** ne peuvent pas modifier l’appartenance des travaux pour obtenir l’accès aux travaux qui ne leur appartiennent pas encore. Seul le nœud **Travaux** de l’Explorateur d’objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est visible aux membres de **SQLAgentReaderRole**.  
  
> [!IMPORTANT]  
>  Tenez compte des implications en matière de sécurité avant d’accorder l’accès proxy aux **membres du** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Agentdatabaseroles**. Les membres de **SQLAgentReaderRole** sont automatiquement membres de **SQLAgentUserRole**. Ceci signifie que les membres de **SQLAgentReaderRole** ont accès à tous les proxys de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent auxquels **SQLAgentUserRole** peut accéder et qu’ils peuvent les utiliser.  
  
 Le tableau suivant récapitule les autorisations de **SQLAgentReaderRole** sur les objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Action|Opérateurs|Travaux locaux|Travaux multiserveur|Calendriers de travaux|Proxies|  
|------------|---------------|----------------|----------------------|-------------------|-------------|  
|Créer/modifier/supprimer|Non|Oui <sup>1</sup> (travaux détenus uniquement)|Non|Oui (planifications lui appartenant uniquement)|Non|  
|Afficher la liste (énumérer)|Oui <sup>2</sup>|Oui|Oui|Oui|Oui <sup>3</sup>|  
|Activer/désactiver|Non|Oui (travaux lui appartenant uniquement)|Non|Oui (planifications lui appartenant uniquement)|Non applicable|  
|Afficher les propriétés|Non|Oui|Oui|Oui|Non|  
|Modifier les propriétés|Non|Oui (travaux lui appartenant uniquement)|Non|Oui (planifications lui appartenant uniquement)|Non|  
|Exécuter/arrêter/démarrer|Non applicable|Oui (travaux lui appartenant uniquement)|Non|Non applicable|Non applicable|  
|Afficher l’historique des travaux|Non applicable|Oui|Oui|Non applicable|Non applicable|  
|Supprimer l'historique des travaux|Non applicable|Non <sup>4</sup>|Non|Non applicable|Non applicable|  
|Attacher/détacher|Non applicable|Non applicable|Non applicable|Oui (planifications lui appartenant uniquement)|Non applicable|  
  
 <sup>1</sup> impossible de modifier la propriété du travail.  
  
 <sup>2</sup> peut obtenir la liste des opérateurs disponibles à utiliser dans **sp_notify_operator** et la boîte de dialogue **Propriétés du travail** de Management Studio.  
  
 <sup>3</sup> liste de proxys uniquement disponibles dans la boîte de dialogue Propriétés de l' **étape du travail** de Management Studio.  
  
 <sup>4</sup> les membres de **SQLAgentReaderRole** doivent disposer explicitement de l’autorisation EXECUTE sur **sp_purge_jobhistory** pour supprimer l’historique des travaux dont ils sont propriétaires. Ils ne peuvent supprimer l'historique d'aucun autre travail.  
  
### <a name="sqlagentoperatorrole-permissions"></a>Autorisations du rôle SQLAgentOperatorRole  
 **SQLAgentOperatorRole** est le plus privilégié des rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Il inclut toutes les autorisations des rôles **SQLAgentUserRole** et **SQLAgentReaderRole**. Les membres de ce rôle peuvent également afficher les propriétés pour les opérateurs et les proxys, ainsi que dresser la liste des proxys disponibles et des alertes sur le serveur.  
  
 Les membres de**SQLAgentOperatorRole** disposent d’autorisations supplémentaires sur les travaux locaux et les planifications. Ils peuvent exécuter, arrêter ou démarrer tous les travaux locaux, ainsi que supprimer l'historique de n'importe quel travail local sur le serveur. Ils peuvent également activer ou désactiver tous les travaux locaux et les planifications sur le serveur. Pour ce faire, les membres de ce rôle doivent utiliser les procédures stockées **sp_update_job** et **sp_update_schedule**. Seuls les paramètres qui spécifient le nom ou l’identificateur du travail ou de la planification et le paramètre ** \@ activé** peuvent être spécifiés par les membres de **SQLAgentOperatorRole**. S'ils spécifient d'autres paramètres, l'exécution de ces procédures stockées échoue. Les membres de**SQLAgentOperatorRole** ne peuvent pas modifier l’appartenance des travaux pour obtenir l’accès aux travaux qui ne leur appartiennent pas encore.  
  
 Les nœuds **Travaux**, **Alertes**, **Opérateurs**et **Proxies** dans l’Explorateur d’objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sont visibles aux membres de **SQLAgentOperatorRole**. Seul le nœud **Journaux d’erreur** n’est pas visible aux membres de ce rôle.  
  
> [!IMPORTANT]  
>  Tenez compte des implications en matière de sécurité avant d’accorder l’accès proxy aux **membres du** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Agentdatabaseroles**. Les membres de **SQLAgentOperatorRole** sont automatiquement membres de **SQLAgentUserRole** et **SQLAgentReaderRole**. Ceci signifie que les membres de **SQLAgentOperatorRole** ont accès à tous les proxys de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent auxquels **SQLAgentUserRole** ou **SQLAgentReaderRole** peut accéder et qu’ils peuvent les utiliser.  
  
 Le tableau suivant récapitule les autorisations de **SQLAgentOperatorRole** sur les objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Action|Alertes|Opérateurs|Travaux locaux|Travaux multiserveur|Calendriers de travaux|Proxies|  
|------------|------------|---------------|----------------|----------------------|-------------------|-------------|  
|Créer/modifier/supprimer|Non|Non|Oui <sup>2</sup> (travaux détenus uniquement)|Non|Oui (planifications lui appartenant uniquement)|Non|  
|Afficher la liste (énumérer)|Oui|Oui <sup>1</sup>|Oui|Oui|Oui|Oui|  
|Activer/désactiver|Non|Non|Oui <sup>3</sup>|Non|Oui<sup>4</sup>|Non applicable|  
|Afficher les propriétés|Oui|Oui|Oui|Oui|Oui|Oui|  
|Modifier les propriétés|Non|Non|Oui (travaux lui appartenant uniquement)|Non|Oui (planifications lui appartenant uniquement)|Non|  
|Exécuter/arrêter/démarrer|Non applicable|Non applicable|Oui|Non|Non applicable|Non applicable|  
|Afficher l’historique des travaux|Non applicable|Non applicable|Oui|Oui|Non applicable|Non applicable|  
|Supprimer l'historique des travaux|Non applicable|Non applicable|Oui|Non|Non applicable|Non applicable|  
|Attacher/détacher|Non applicable|Non applicable|Non applicable|Non applicable|Oui (planifications lui appartenant uniquement)|Non applicable|  
  
 <sup>1</sup> peut obtenir la liste des opérateurs disponibles à utiliser dans **sp_notify_operator** et la boîte de dialogue **Propriétés du travail** de Management Studio.  
  
 <sup>2</sup> impossible de modifier la propriété du travail.  
  
 <sup>3</sup> les membres **SQLAgentOperatorRole** peuvent activer ou désactiver les travaux locaux qu’ils n’appartiennent pas en utilisant la procédure stockée **sp_update_job** et en spécifiant des valeurs pour les paramètres ** \@ Enabled** et ** \@ job_id** (ou ** \@ job_name**). Si un membre de ce rôle spécifie d'autres paramètres pour cette procédure stockée, l'exécution de cette dernière échoue.  
  
 <sup>4</sup> les membres **SQLAgentOperatorRole** peuvent activer ou désactiver les planifications qui ne sont pas propriétaires en utilisant la procédure stockée **sp_update_schedule** et en spécifiant des valeurs pour les paramètres ** \@ Enabled** et ** \@ schedule_id** (ou ** \@ Name**). Si un membre de ce rôle spécifie d'autres paramètres pour cette procédure stockée, l'exécution de cette dernière échoue.  
  
## <a name="assigning-users-multiple-roles"></a>Assignation de plusieurs rôles aux utilisateurs  
 Les membres du rôle serveur fixe **sysadmin** ont accès à toutes les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Si un utilisateur n’est pas membre du rôle **sysadmin** , mais qu’il est membre de plusieurs rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, il est important de prendre en compte le modèle concentrique des autorisations de ces rôles. Étant donné que les rôles plus privilégiés contiennent toujours toutes les autorisations des rôles moins privilégiés, un utilisateur qui est membre de plusieurs rôles a automatiquement les autorisations associées au rôle le plus privilégié dont il est membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité SQL Server Agent](implement-sql-server-agent-security.md)   
 [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)   
 [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)   
 [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)   
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)  
  
  
