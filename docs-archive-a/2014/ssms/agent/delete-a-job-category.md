---
title: Supprimer une catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e96dd0461f3dace138b7822cdbaaa2fa242e2cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696368"
---
# <a name="delete-a-job-category"></a>Supprimer une catégorie de travaux
  Cette rubrique explique comment supprimer une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catégorie de travaux de l’agent dans à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , [!INCLUDE[tsql](../../includes/tsql-md.md)] ou SQL Server Management Objects.  
  
 Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données.  

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
 Lorsque vous supprimez une catégorie de travaux définie par l'utilisateur, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous invite à réaffecter les travaux qui en dépendent à une autre catégorie de travaux. Seules les catégories de travaux définies par l'utilisateur peuvent être supprimées.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  

##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
### <a name="to-delete-a-job-category"></a>Pour supprimer une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez supprimer une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Gérer les catégories de travaux**.  
  
4.  Dans la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ , sélectionnez la catégorie de travaux à supprimer.  
  
5.  Cliquez sur **Supprimer**.  
  
6.  Dans la boîte de dialogue **Catégories de travaux** , cliquez sur **Oui**.  
  
7.  Fermez la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ .  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Utilisation de Transact-SQL  
  
### <a name="to-delete-a-job-category"></a>Pour supprimer une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).  

  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Utilisation de SQL Server Management Objects  

### <a name="to-delete-a-job-category"></a>Pour supprimer une catégorie de travaux
  
 Appelez la classe `JobCategory` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell.  
