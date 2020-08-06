---
title: Configurer les paramètres de propriété FailureConditionLevel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605022"
---
# <a name="configure-failureconditionlevel-property-settings"></a>Configurer les paramètres de propriété FailureConditionLevel
  Utilisez la propriété FailureConditionLevel pour définir les conditions de basculement ou de redémarrage de l'instance de cluster de basculement (FCI) AlwaysOn. Les modifications de cette propriété sont appliquées immédiatement sans nécessiter le redémarrage du service WSFC (cluster de basculement Windows Server) ou de la ressource FCI.  
  
-   **Avant de commencer :**  [Paramètres de propriété FailureConditionLevel](#Restrictions), [Sécurité](#Security)  
  
-   **Pour configurer les paramètres de propriété FailureConditionLevel à l’aide de** [PowerShell](#PowerShellProcedure), [Gestionnaire du cluster de basculement](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> Paramètres de propriété FailureConditionLevel  
 Les conditions d'échec sont définies sur une échelle croissante. Pour les niveaux 1-5, chaque niveau inclut toutes les conditions des niveaux précédents en plus de ses propres conditions. Cela signifie qu'à chaque niveau, la probabilité de basculement ou de redémarrage est plus importante.  Pour plus d'informations, consultez la section « Détermination des échecs » de la rubrique [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) .  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Nécessite les autorisations ALTER SETTINGS et VIEW SERVER STATE.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
### <a name="to-configure-failureconditionlevel-settings"></a>Pour configurer les paramètres FailureConditionLevel  
  
1.  Démarrez Windows PowerShell avec élévation de privilèges via **Exécuter en tant qu'administrateur**.  
  
2.  Importez le module `FailoverClusters` pour activer les applets de commande de cluster.  
  
3.  Utilisez l' `Get-ClusterResource` applet de commande pour rechercher la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ressource, puis utilisez l' `Set-ClusterParameter` applet de commande pour définir la propriété **FailureConditionLevel** d’une instance de cluster de basculement.  
  
> [!TIP]  
>  Chaque fois que vous ouvrez une nouvelle fenêtre PowerShell, vous devez importer le module `FailoverClusters`.  

 L'exemple suivant modifie le paramètre FailureConditionLevel sur la ressource [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» par un basculement ou un redémarrage en cas d'erreurs de serveur critiques.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a>Contenu connexe (PowerShell)  
  
-   [Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Clustering et haute disponibilité) (Blog de l’équipe de clustering de basculement et d’équilibrage de la charge réseau)  
  
-   [Mise en route de Windows PowerShell sur un cluster de basculement](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Commandes de ressource de cluster et applets de commande Windows PowerShell équivalentes](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> Utilisation du composant logiciel enfichable Gestionnaire du cluster de basculement  

### <a name="to-configure-failureconditionlevel-property-settings"></a>Pour configurer les paramètres de propriété FailureConditionLevel
  
1.  Ouvrez le composant logiciel enfichable Gestionnaire du cluster de basculement.  
  
2.  Développez **Services et applications** et sélectionnez l'instance FCI.  
  
3.  Cliquez avec le bouton droit sur **Ressource SQL Server** sous **Autres ressources**puis, dans le menu, sélectionnez **Propriétés** . La boîte de dialogue **Propriétés** de la ressource SQL Server s'ouvre.  
  
4.  Sélectionnez l'onglet **Propriétés** , entrez la valeur souhaitée pour la propriété **FaliureConditionLevel** , puis cliquez sur **OK** pour appliquer la modification.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  

### <a name="to-configure-failureconditionlevel-property-settings"></a>Pour configurer les paramètres de propriété FailureConditionLevel
  
 À l’aide de l’instruction [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] , spécifiez la valeur de la propriété FailureConditionLevel.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant affecte à la propriété FailureConditionLevel la valeur 0, ce qui indique qu'aucun basculement ni redémarrage ne sera déclenché automatiquement sur n'importe quelle condition d'échec.  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)   
 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md)  
