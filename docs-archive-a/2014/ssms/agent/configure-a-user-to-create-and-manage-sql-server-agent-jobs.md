---
title: Configurer un utilisateur de manière à créer et à gérer des travaux de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614328"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
  Cette rubrique explique comment configurer un utilisateur pour créer ou exécuter des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travaux de l’agent.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour configurer un utilisateur afin qu'il puisse créer et gérer des travaux de SQL Server Agent à l'aide de :**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Pour configurer un utilisateur pour créer ou exécuter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des travaux de l’agent, vous devez d’abord ajouter un rôle de connexion SQL Server ou msdb existant à l’un des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôles de base de données fixes de l’agent suivants dans la base de données msdb : SQLAgentUserRole, SQLAgentReaderRole ou SQLAgentOperatorRole.  
  
 Par défaut, les membres de ces rôles de base de données peuvent créer leurs propres étapes de travail qui s'exécutent de façon autonome. Si ces utilisateurs non-administrateurs souhaitent exécuter des travaux qui lancent d'autres types d'étapes de travail (par exemple, des packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] ), ils doivent disposer d'un accès à un compte proxy. Tous les membres du rôle de serveur fixe sysadmin sont habilités à créer, à modifier et à supprimer des comptes proxy. Pour plus d’informations sur les autorisations associées à ces rôles de base de données fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Rôles de base de données fixes de SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilisation de SQL Server Management Studio  
 **Pour ajouter une connexion SQL ou un rôle msdb à un rôle de base de données fixe de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Sécurité**puis **Connexions**.  
  
3.  Cliquez avec le bouton droit sur la connexion à ajouter au rôle de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, puis sélectionnez **Propriétés**.  
  
4.  Dans la page mappage de l' **utilisateur** de la boîte de dialogue Propriétés de la **connexion** , sélectionnez la ligne contenant `msdb` .  
  
5.  Sous **Appartenance au rôle de base de données : msdb**, cochez le rôle de base de données fixe de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approprié.  
  
 **Pour configurer un compte proxy de manière à créer et à gérer des étapes de travail de SQL Server Agent**  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur.  
  
2.  Développez **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit de la souris sur **Proxies** , puis sélectionnez **Nouveau proxy**.  
  
4.  Dans la page **Général** de la boîte de dialogue **Nouveau compte de proxy** , indiquez le nom de proxy, le nom d'identification et la description du nouveau proxy. Notez que vous devez créer une information d'identification avant de créer un proxy de SQL Server Agent. Pour plus d’informations sur la création d’informations d’identification, consultez [créer des informations d'](../../relational-databases/security/authentication-access/create-a-credential.md) identification et [créer des informations d’identification &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-credential-transact-sql).  
  
5.  Activez les sous-systèmes appropriés pour ce proxy.  
  
6.  Sur la page **Principaux** , ajoutez ou supprimez des connexions ou des rôles pour accorder ou refuser un accès au compte proxy.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité de l'Agent SQL Server](implement-sql-server-agent-security.md)  
  
  
