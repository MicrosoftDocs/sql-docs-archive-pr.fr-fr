---
title: Démarrer un travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705852"
---
# <a name="start-a-job"></a>Démarrer un travail
  Cette rubrique explique comment démarrer l’exécution d’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travail de l’agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] ou SQL Server Management Objects.  
  
 Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peuvent être exécutés sur un serveur local ou sur plusieurs serveurs distants.  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour démarrer un travail, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
### <a name="to-start-a-job"></a>Pour démarrer un travail  
  
1.  Dans l' **Explorateur d’objets,** Connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , puis développez cette instance.  
  
2.  Développez **Agent SQL Server** et développez **Travaux**. Selon la façon dont vous voulez démarrer le travail, procédez de l'une des manières suivantes :  
  
    -   Si vous travaillez sur un seul serveur, si vous travaillez sur un serveur cible ou si vous exécutez un travail de serveur local sur un serveur maître, cliquez avec le bouton droit sur le travail à démarrer et cliquez sur **Démarrer le travail**.  
  
    -   Pour démarrer plusieurs travaux, cliquez avec le bouton droit sur **Moniteur d'activité des travaux**, puis cliquez sur **Afficher l'activité du travail**. Dans le Moniteur d'activité des travaux, vous pouvez sélectionner plusieurs travaux. Pour cela, cliquez avec le bouton droit sur votre sélection et cliquez sur **Démarrer les travaux**.  
  
    -   Si vous travaillez sur un serveur maître et souhaitez que tous les serveurs cibles exécutent le travail simultanément, cliquez avec le bouton droit sur le travail à démarrer, cliquez sur **Démarrer le travail**, puis sur **Démarrer sur tous les serveurs cibles**.  
  
    -   Si vous travaillez sur un serveur maître et souhaitez spécifier les serveurs cibles pour le travail, cliquez avec le bouton droit sur le travail à démarrer, cliquez sur **Démarrer le travail**, puis sur **Démarrer sur les serveurs cibles spécifiques**. Dans la boîte de dialogue **Publier les instructions à télécharger** , activez la case à cocher **Serveurs cibles sélectionnés** , puis sélectionnez chacun des serveurs cibles sur lesquels ce travail doit s'exécuter.  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Utilisation de Transact-SQL  
  
### <a name="to-start-a-job"></a>Pour démarrer un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Utilisation de SQL Server Management Objects  

### <a name="to-start-a-job"></a>Pour démarrer un travail
  
 Appelez la méthode `Start` de la classe `Job` à l'aide d'un langage de programmation tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
