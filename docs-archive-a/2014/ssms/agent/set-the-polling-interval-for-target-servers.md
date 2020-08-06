---
title: Définir la fréquence d’interrogation pour les serveurs cibles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710092"
---
# <a name="set-the-polling-interval-for-target-servers"></a>Set the Polling Interval for Target Servers
  Cette rubrique explique comment définir la fréquence à laquelle l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent actualise les informations du serveur maître sur les serveurs cibles. Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un travail multiserveur est un travail exécuté par un serveur maître sur un ou plusieurs serveurs cibles.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour définir l’intervalle d’interrogation pour les serveurs cibles, avec :**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
 Chaque serveur cible peut exécuter une instance du même travail au même moment. Chaque serveur cible interroge régulièrement le serveur maître, télécharge une copie des nouveaux travaux affectés au serveur cible, puis se déconnecte. Le serveur cible exécute localement le travail, puis se reconnecte au serveur maître pour charger l'état de la sortie du travail.  
  
> [!NOTE]  
>  Si le serveur maître est accessible lorsque le serveur cible tente de charger l'état du travail, ce dernier est mis en attente dans le spouleur jusqu'à ce que le serveur maître soit accessible.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) et [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilisation de SQL Server Management Studio  
 **Pour définir l'intervalle d'interrogation pour les serveurs cibles**  
  
1.  Dans l' **Explorateur d’objets,** Connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , puis développez cette instance.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Sous l'onglet **État du serveur cible** , cliquez sur **Publier les instructions**.  
  
4.  Dans la liste **Type d'instruction** , sélectionnez **Définir la fréquence d'interrogation**.  
  
5.  Dans la zone **Fréquence d'interrogation** , entrez le nombre de secondes, entre 10 et 28800, qui doivent s'écouler avant que le serveur cible n'interroge le serveur maître.  
  
6.  Sous **Destinataires**, activez l'une des options suivantes :  
  
    1.  Cliquez sur **Tous les serveurs cibles** si tous les serveurs cibles partagent la même fréquence d'interrogation.  
  
    2.  Cliquez sur **Serveurs cibles sélectionnés** si les serveurs cibles ne partagent pas tous la même fréquence d'interrogation, puis sélectionnez chacun des serveurs cibles qui utilisera cette fréquence d'interrogation.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Utilisation de Transact-SQL  
 **Pour définir l'intervalle d'interrogation pour les serveurs cibles**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, utilisez la procédure stockée système [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) pour définir la fréquence d’interrogation pour les serveurs cibles.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysdownloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
