---
title: Configuration requise pour la base de données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b17c04db6805ea412b70644d2ee2c0b7da93b2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613499"
---
# <a name="database-requirements-master-data-services"></a><span data-ttu-id="26fd2-102">Configuration requise pour la base de données (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="26fd2-102">Database Requirements (Master Data Services)</span></span>
  <span data-ttu-id="26fd2-103">Toutes les données de référence sont stockées dans une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26fd2-103">All master data is stored in a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="26fd2-104">L’ordinateur qui héberge cette base de données doit exécuter une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26fd2-104">The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="26fd2-105">Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer et configurer la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="26fd2-105">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database on either a local or a remote computer.</span></span> <span data-ttu-id="26fd2-106">Si vous déplacez la base de données d'un environnement à un autre, vous pouvez maintenir ces informations dans un nouvel environnement en associant le service Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à la base de données dans son nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="26fd2-106">If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service and [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to the database in its new location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26fd2-107">Tout ordinateur sur lequel vous installez les composants de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] doit disposer d'une licence.</span><span class="sxs-lookup"><span data-stu-id="26fd2-107">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="26fd2-108">Pour plus d'informations, reportez-vous au Contrat de Licence Utilisateur Final (CLUF).</span><span class="sxs-lookup"><span data-stu-id="26fd2-108">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26fd2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="26fd2-109">Requirements</span></span>  
 <span data-ttu-id="26fd2-110">Avant de créer une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , assurez -vous que les conditions suivantes sont remplies.</span><span class="sxs-lookup"><span data-stu-id="26fd2-110">Before you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, ensure the following requirements are met.</span></span>  
  
### <a name="sql-server-edition"></a><span data-ttu-id="26fd2-111">Édition SQL Server</span><span class="sxs-lookup"><span data-stu-id="26fd2-111">SQL Server Edition</span></span>  
 <span data-ttu-id="26fd2-112">La base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] peut être hébergée sur les éditions suivantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="26fd2-112">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="26fd2-113">Business Intelligence (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-113">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="26fd2-114">Entreprise (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-114">Enterprise (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="26fd2-115">Developer (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-115">Developer (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="26fd2-116">Business Intelligence (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-116">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="26fd2-117">Entreprise (64 bits) x64 - Mise à niveau de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Entreprise uniquement</span><span class="sxs-lookup"><span data-stu-id="26fd2-117">Enterprise (64-bit) x64 - Upgrade from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise only</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="26fd2-118">Developer (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-118">Developer (64-bit) x64</span></span>  
  
-   <span data-ttu-id="26fd2-119">Microsoft SQL Server 2008 R2 Enterprise (64 bits) x64</span><span class="sxs-lookup"><span data-stu-id="26fd2-119">Microsoft SQL Server 2008 R2 Enterprise (64-bit) x64</span></span>  
  
-   <span data-ttu-id="26fd2-120">Microsoft SQL Server 2008 R2 Developer x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="26fd2-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span></span>  
  
 <span data-ttu-id="26fd2-121">Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="26fd2-121">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="26fd2-122">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="26fd2-122">Operating System</span></span>  
 <span data-ttu-id="26fd2-123">Pour plus d’informations sur les systèmes d’exploitation Windows pris en charge et les autres conditions requises pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , consultez [configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="26fd2-123">For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="26fd2-124">Comptes et autorisations</span><span class="sxs-lookup"><span data-stu-id="26fd2-124">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="26fd2-125">Type</span><span class="sxs-lookup"><span data-stu-id="26fd2-125">Type</span></span>|<span data-ttu-id="26fd2-126">Description</span><span class="sxs-lookup"><span data-stu-id="26fd2-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="26fd2-127">Compte d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="26fd2-127">User account</span></span>|<span data-ttu-id="26fd2-128">Dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], vous pouvez utiliser un compte Windows ou un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vous connecter à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’héberger la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26fd2-128">In [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="26fd2-129">Le compte d’utilisateur doit appartenir au rôle serveur **sysadmin** sur l’instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26fd2-129">The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="26fd2-130">Pour plus d’informations sur le rôle **sysadmin** , consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md).</span><span class="sxs-lookup"><span data-stu-id="26fd2-130">For more information about the **sysadmin** role, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="26fd2-131">Compte administrateur</span><span class="sxs-lookup"><span data-stu-id="26fd2-131">administrator account</span></span>|<span data-ttu-id="26fd2-132">Lorsque vous créez une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , vous devez spécifier un compte d'utilisateur de domaine pour être l'administrateur système [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="26fd2-132">When you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="26fd2-133">Pour toutes les applications Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] associées à cette base de données, cet utilisateur peut mettre à jour tous les modèles et toutes les données dans toutes les zones fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="26fd2-133">For all [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications associated with this database, this user can update all models and all data in all functional areas.</span></span> <span data-ttu-id="26fd2-134">Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="26fd2-134">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>|  
  
### <a name="database-backup"></a><span data-ttu-id="26fd2-135">Sauvegarde de la base de données</span><span class="sxs-lookup"><span data-stu-id="26fd2-135">Database Backup</span></span>  
 <span data-ttu-id="26fd2-136">À titre de recommandation, sauvegardez la base de données complète quotidiennement en période de faible activité et sauvegardez les journaux des transactions plus fréquemment selon les besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="26fd2-136">As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment.</span></span> <span data-ttu-id="26fd2-137">Pour plus d’informations sur les sauvegardes de bases de données, consultez [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="26fd2-137">For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26fd2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26fd2-138">See Also</span></span>  
 <span data-ttu-id="26fd2-139">[Installer Master Data Services](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26fd2-139">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="26fd2-140">[Créer une base de données Master Data Services](create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="26fd2-140">[Create a Master Data Services Database](create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="26fd2-141">[Base de données Master Data Services](../master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="26fd2-141">[Master Data Services Database](../master-data-services-database.md) </span></span>  
 <span data-ttu-id="26fd2-142">[Boîte de dialogue se connecter à une base de données Master Data Services](../connect-to-a-master-data-services-database-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="26fd2-142">[Connect to a Master Data Services Database Dialog Box](../connect-to-a-master-data-services-database-dialog-box.md) </span></span>  
 [<span data-ttu-id="26fd2-143">Assistant Création d’une base de données &#40;Gestionnaire de configuration Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="26fd2-143">Create Database Wizard &#40;Master Data Services Configuration Manager&#41;</span></span>](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  