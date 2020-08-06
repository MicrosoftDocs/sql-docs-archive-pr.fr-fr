---
title: Changer le délai d’expiration de session pour un réplica de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708672"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a>Modifier le délai d'expiration de session pour un réplica de disponibilité (SQL Server)
  Cette rubrique explique comment configurer la période d'expiration de session d'un réplica de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. La période d'expiration de session est une propriété de réplica qui contrôle le nombre de secondes (en secondes) pendant lequel un réplica de disponibilité attend une réponse ping d'un réplica connecté avant de considérer que la connexion a échoué. Par défaut, un réplica attend une réponse ping pendant 10 secondes. Cette propriété de réplica applique uniquement la connexion entre un réplica secondaire donné et le réplica principal du groupe de disponibilité. Pour plus d’informations sur le délai d’expiration de session, consultez [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Avant de commencer :**  
  
     [Composants requis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier la période d'expiration de session, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
 Le temps d'attente recommandé est de 10 secondes minimum. En définissant une valeur inférieure à 10 secondes, vous créez la possibilité qu'un système surchargé soit à court de PING et qu'il déclare à tort une défaillance.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour modifier la période d'expiration de session pour un réplica de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez sur le groupe de disponibilité dont vous souhaitez configurer le réplica de disponibilité.  
  
4.  Cliquez avec le bouton droit sur le réplica à configurer, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du réplica de disponibilité** , utilisez le champ **Délai d’expiration de session (secondes)** pour modifier le nombre de secondes pour la période d’expiration de session sur ce réplica.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier la période d'expiration de session pour un réplica de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , comme suit :  
  
     ALTER AVAILABILITY GROUP *nom_groupe*  
  
     MODIFY REPLICA ON «*nom_instance*» WITH ( SESSION_TIMEOUT =*secondes* )  
  
     où *nom_groupe* est le nom du groupe de disponibilité, *nom_instance* est le nom de l’instance de serveur qui héberge le réplica de disponibilité à modifier, et *secondes* spécifie le nombre minimal de secondes pendant lesquelles le réplica doit attendre avant d’appliquer un journal aux bases de données lorsqu’il joue le rôle de réplica secondaire. La valeur par défaut est de 0 seconde, ce qui indique qu'il n'existe pas de délai d'application.  
  
     L'exemple suivant, écrit sur le réplica principal du groupe de disponibilité `AccountsAG` modifie la valeur d'expiration de session sur `15` secondes pour le réplica situé sur l'instance de serveur `INSTANCE09` .  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a>Pour modifier la période d'expiration de session pour un réplica de disponibilité
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'applet de commande `Set-SqlAvailabilityReplica` avec le paramètre `SessionTimeout` pour modifier le nombre de secondes pour la période d'expiration de session sur un réplica de disponibilité spécifié.  
  
     Par exemple, la commande suivante définit le délai d'expiration de session sur 15 secondes.  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Pour configurer et utiliser le fournisseur de SQL Server PowerShell, consultez [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
