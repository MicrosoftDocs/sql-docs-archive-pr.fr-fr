---
title: Créer un pool de ressources | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614483"
---
# <a name="create-a-resource-pool"></a>Créer un pool de ressources
  Vous pouvez créer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour créer un pool de ressources avec :**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Le pourcentage maximal de l'UC doit être supérieur ou égal au pourcentage minimal de l'UC. Le pourcentage maximal de mémoire doit être supérieur ou égal au pourcentage minimal de mémoire.  
  
 La somme des pourcentages d'UC minimal et de mémoire minimal pour tous les pools de ressources ne doit pas dépasser 100.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 La création d'un pool de ressources requiert l'autorisation CONTROL SERVER.  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> Créer un pool de ressources à l'aide de SQL Server Management Studio  
 **Pour créer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'à **Resource Governor**inclus.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor**, puis sélectionnez **Propriétés**.  
  
3.  Dans la grille **Pools de ressources** , cliquez sur la première colonne dans la ligne vide. Cette colonne est marquée d'un astérisque (*).  
  
4.  Double-cliquez sur la cellule vide dans la colonne **Nom** . Tapez le nom de votre choix pour le pool de ressources.  
  
5.  Cliquez ou double-cliquez sur toutes les autres cellules de la ligne que vous souhaitez modifier, puis entrez les nouvelles valeurs.  
  
6.  Cliquez sur **OK**pour enregistrer les modifications.  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a> Créer un pool de ressources à l'aide de Transact-SQL  
 **Pour créer un pool de ressources à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Exécutez l'instruction `CREATE RESOURCE POOL` en spécifiant les valeurs de propriété à définir.  
  
2.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant crée un pool de ressources nommé `poolAdhoc`.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Activer Resource Governor](enable-resource-governor.md)   
 [Pool de ressources de Resource Governor](resource-governor-resource-pool.md)   
 [Modifier les paramètres de pool de ressources](change-resource-pool-settings.md)   
 [Supprimer un pool de ressources](delete-a-resource-pool.md)   
 [Configurer le gouverneur de ressources à l'aide d'un modèle](configure-resource-governor-using-a-template.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
