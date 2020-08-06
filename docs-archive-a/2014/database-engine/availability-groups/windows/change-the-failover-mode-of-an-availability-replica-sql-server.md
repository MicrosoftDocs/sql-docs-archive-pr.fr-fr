---
title: Changer le mode de basculement d’un réplica de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708679"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a>Modifier le mode de basculement d'un réplica de disponibilité (SQL Server)
  Cette rubrique explique comment modifier le mode de basculement d'un réplica de disponibilité dans un groupe de disponibilité AlwaysOn dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell. Le mode de basculement est une propriété de réplica qui détermine le mode de basculement pour les réplicas qui s'exécutent en mode de disponibilité avec validation synchrone. Pour plus d’informations, consultez [Basculement et modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md) et [Modes de disponibilité &#40;groupes de disponibilité AlwaysOn&#41;](availability-modes-always-on-availability-groups.md).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> Conditions préalables requises et restrictions  
  
-   Cette tâche est prise en charge uniquement sur les réplicas principaux. Vous devez être connecté à l'instance de serveur qui héberge le réplica principal.  
  
-   Les instances de cluster de basculement (FCI) SQL Server ne prennent pas en charge le basculement automatique par les groupes de disponibilité. Par conséquent, tout réplica de disponibilité hébergé par une instance de cluster de basculement ne peut être configuré que pour un basculement manuel.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour modifier le mode de basculement d'un réplica de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Cliquez sur le groupe de disponibilité dont vous souhaitez modifier le réplica.  
  
4.  Cliquez avec le bouton droit sur le réplica, puis cliquez sur **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du réplica de disponibilité** , utilisez la liste déroulante **Mode de basculement** pour modifier le mode de basculement de ce réplica.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour modifier le mode de basculement d'un réplica de disponibilité**  
  
1.  Connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'instruction [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , comme suit :  
  
     ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     }  )  
  
     where  
  
    -   *nom_groupe* correspond au nom du groupe de disponibilité.  
  
    -   { '*nom_système*[\\*nom_instance*]' | '*nom_réseau_FCI*[\\*nom_instance*]' }  
  
         Spécifie l'adresse de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica de disponibilité à modifier. Les composants de cette adresse sont les suivants :  
  
         *nom_système*  
         Nom NetBIOS du système informatique sur lequel réside une instance de serveur autonome.  
  
         *nom_réseau_FCI*  
         Nom réseau utilisé pour accéder à un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans lequel une instance de serveur cible est un serveur partenaire de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (FCI).  
  
         *instance_name*  
         Nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica de disponibilité cible. Pour une instance de serveur par défaut, *nom_instance* est facultatif.  
  
     Pour plus d’informations sur ces paramètres, consultez [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
     L’exemple suivant, entré sur le réplica principal du groupe de disponibilité *MyAG* , remplace le mode de basculement par le basculement automatique sur le réplica de disponibilité situé sur l’instance de serveur par défaut sur un ordinateur nommé *COMPUTER01*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a>Pour modifier le mode de basculement d'un réplica de disponibilité
  
1.  Accédez au répertoire (`cd`) de l'instance de serveur qui héberge le réplica principal.  
  
2.  Utilisez l'applet de commande `Set-SqlAvailabilityReplica` avec le paramètre `FailoverMode`. En définissant un réplica en mode de basculement automatique, vous devrez peut-être utiliser le paramètre `AvailabilityMode` pour modifier le réplica en mode de disponibilité avec validation synchrone.  
  
     Par exemple, la commande suivante modifie le réplica `MyReplica` dans le groupe de disponibilité `MyAg` afin qu'il utilise le mode de disponibilité avec validation synchrone et prenne en charge le basculement automatique.  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Pour afficher la syntaxe d'une applet de commande, utilisez l'applet de commande `Get-Help` dans l'environnement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Pour configurer et utiliser le fournisseur de SQL Server PowerShell, consultez [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
 [Modes de disponibilité &#40;groupes de disponibilité AlwaysOn&#41;](availability-modes-always-on-availability-groups.md)   
 [Basculement et modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md) 
