---
title: Définir un alias de SQL Server pour le service SQL Server Agent (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b178d91a47d907b182ef7962b98c7f22d4454094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601068"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Définir un alias SQL Server pour le service SQL Server Agent (SQL Server Management Studio)
  Cette rubrique explique comment définir un [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alias [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que l’agent doit utiliser pour se connecter au à l' [!INCLUDE[ssDE](../includes/ssde-md.md)] aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Par défaut, le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent se connecte à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par l'intermédiaire de canaux de communication nommés qui utilisent des noms de serveur dynamiques ne nécessitant aucune configuration supplémentaire du client. Vous devez configurer un alias de connexion serveur uniquement si vous n'utilisez pas le transport réseau par défaut ou si vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] via un autre canal nommé.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour définir un alias SQL Server pour le service SQL Server Agent à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne fonctionnera correctement que si vous sélectionnez un alias qui se réfère à l'instance locale de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
 Pour plus d’informations sur les autorisations Windows requises pour le compte de service de l' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et configurer les [comptes de service Windows et les autorisations](configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>Pour définir un alias SQL Server pour le service SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets,** connectez-vous à une instance de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , puis développez cette instance.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue Propriétés de la **SQL Server Agent**_Server_name_ , sous **Sélectionner une page**, sélectionnez **connexion**, puis  
  
4.  Dans la zone **Alias du serveur hôte local** , tapez l'alias du serveur auquel l'agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit se connecter.  
  
5.  Cliquez sur **OK**.  
  
  
