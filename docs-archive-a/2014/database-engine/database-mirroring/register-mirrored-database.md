---
title: Inscrire la base de données mise en miroir | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 24732f82c971959ed202358613ef98c5ccc714d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701814"
---
# <a name="register-mirrored-database"></a><span data-ttu-id="11ab2-102">Inscrire la base de données mise en miroir</span><span class="sxs-lookup"><span data-stu-id="11ab2-102">Register Mirrored Database</span></span>
  <span data-ttu-id="11ab2-103">Utilisez cette boîte de dialogue pour inscrire une ou plusieurs bases de données mises en miroir sur une instance de serveur donnée en ajoutant la ou les bases de données au moniteur de mise en miroir de bases de données.</span><span class="sxs-lookup"><span data-stu-id="11ab2-103">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="11ab2-104">Lorsqu'une base de données est ajoutée, le moniteur de mise en miroir de bases de données met en cache localement des informations sur la base de données, ses partenaires et la connexion aux partenaires.</span><span class="sxs-lookup"><span data-stu-id="11ab2-104">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="11ab2-105">Si vous êtes membre du rôle de serveur fixe **sysadmin** sur l’instance de serveur principal, mais pas sur l’instance de serveur miroir, vous pouvez uniquement afficher l’état sur l’instance de serveur principal.</span><span class="sxs-lookup"><span data-stu-id="11ab2-105">If you are a member of the **sysadmin** fixed server role on the principal server instance but not on the mirror server instance, you can only see status on the principal server instance.</span></span>  
  
 <span data-ttu-id="11ab2-106">**Pour utiliser SQL Server Management Studio pour contrôler la mise en miroir de base de données**</span><span class="sxs-lookup"><span data-stu-id="11ab2-106">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="11ab2-107">Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="11ab2-107">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="11ab2-108">Options</span><span class="sxs-lookup"><span data-stu-id="11ab2-108">Options</span></span>  
 <span data-ttu-id="11ab2-109">**Instance de serveur**</span><span class="sxs-lookup"><span data-stu-id="11ab2-109">**Server instance**</span></span>  
 <span data-ttu-id="11ab2-110">Sélectionnez une instance de serveur dans la liste d’instances de serveurs sur lesquelles le moniteur de mise en miroir de bases de données a déjà stocké une connexion, ou cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="11ab2-110">Select a server instance from the list, which contains server instances to which Database Mirroring Monitor already has a connection stored, or click **Connect**.</span></span> <span data-ttu-id="11ab2-111">Pour spécifier de nouvelles informations d’identification pour une instance de serveur répertoriée, cliquez sur **Se connecter** et connectez-vous en utilisant ces nouvelles informations.</span><span class="sxs-lookup"><span data-stu-id="11ab2-111">To specify new credentials for a listed server instance, click **Connect** and connect using the new credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11ab2-112">Pour inscrire des bases de données sur plusieurs instances de serveurs, une fois que vous avez sélectionné les bases de données souhaitées pour une instance de serveur, cliquez sur **Appliquer**et sélectionnez une autre instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="11ab2-112">To register databases on multiple server instances, after you finish checking the desired databases for one server instance, click **Apply**, and then select another server instance.</span></span>  
  
 <span data-ttu-id="11ab2-113">**Connexion**</span><span class="sxs-lookup"><span data-stu-id="11ab2-113">**Connect**</span></span>  
 <span data-ttu-id="11ab2-114">Pour spécifier de nouvelles informations d’identification pour l’instance de serveur, cliquez sur **Se connecter** et connectez-vous en utilisant ces nouvelles informations.</span><span class="sxs-lookup"><span data-stu-id="11ab2-114">To specify new credentials for the server instance, click **Connect** and connect using the new credentials.</span></span> <span data-ttu-id="11ab2-115">Lors de la connexion à une instance de serveur, le moniteur de mise en miroir de bases de données affiche le message **Attente de données**.</span><span class="sxs-lookup"><span data-stu-id="11ab2-115">While connecting to a server instance, Database Mirroring Monitor displays **Waiting for data**.</span></span>  
  
 <span data-ttu-id="11ab2-116">**Bases de données mises en miroir**</span><span class="sxs-lookup"><span data-stu-id="11ab2-116">**Mirrored databases**</span></span>  
 <span data-ttu-id="11ab2-117">La grille **Bases de données mises en miroir** affiche les bases de données mises en miroir sur l’instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="11ab2-117">The **Mirrored databases** grid lists the mirrored databases on the server instance.</span></span>  
  
 <span data-ttu-id="11ab2-118">Cette grille comporte les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="11ab2-118">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="11ab2-119">Nom de la colonne</span><span class="sxs-lookup"><span data-stu-id="11ab2-119">Column name</span></span>|<span data-ttu-id="11ab2-120">Description</span><span class="sxs-lookup"><span data-stu-id="11ab2-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="11ab2-121">**S’inscrire**</span><span class="sxs-lookup"><span data-stu-id="11ab2-121">**Register**</span></span>|<span data-ttu-id="11ab2-122">Sélectionnez chaque base de données à inscrire.</span><span class="sxs-lookup"><span data-stu-id="11ab2-122">Check each of the databases that you want to register.</span></span> <span data-ttu-id="11ab2-123">Si une base de données est actuellement surveillée, la case à cocher correspondante est sélectionnée et inactive.</span><span class="sxs-lookup"><span data-stu-id="11ab2-123">If a database is currently monitored, its check box is checked and is disabled.</span></span><br /><br /> <span data-ttu-id="11ab2-124">Remarque : Pour annuler l’inscription d’une base de données, fermez la boîte de dialogue **Inscrire la base de données mise en miroir**, sélectionnez la base de données dans l’arborescence de navigation, puis choisissez **Annuler l’inscription** dans le menu **Action**.</span><span class="sxs-lookup"><span data-stu-id="11ab2-124">Note: To unregister a database, close the **Registered Mirrored Database** dialog box, select the database in the navigation tree, and select **Unregister** from the **Action** menu.</span></span>|  
|<span data-ttu-id="11ab2-125">**Sauvegarde de la base de données**</span><span class="sxs-lookup"><span data-stu-id="11ab2-125">**Database**</span></span>|<span data-ttu-id="11ab2-126">Nom d'une base de données mise en miroir sur l'instance de serveur sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="11ab2-126">The name of a mirrored database on the selected server instance.</span></span>|  
|<span data-ttu-id="11ab2-127">**Rôle actuel**</span><span class="sxs-lookup"><span data-stu-id="11ab2-127">**Current Role**</span></span>|<span data-ttu-id="11ab2-128">Rôle actuel de mise en miroir de la base de données (Principal ou Miroir) sur l'instance de serveur sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="11ab2-128">The current mirroring role of the database, either Principal or Mirror, on the selected server instance.</span></span>|  
|<span data-ttu-id="11ab2-129">**Partenaire (Se connecter en tant que)**</span><span class="sxs-lookup"><span data-stu-id="11ab2-129">**Partner (Connect as)**</span></span>|<span data-ttu-id="11ab2-130">Nom du partenaire de basculement pour la base de données.</span><span class="sxs-lookup"><span data-stu-id="11ab2-130">The name of the failover partner for the database.</span></span> <span data-ttu-id="11ab2-131">**Authentification Windows de l’utilisateur de la console** ou **Authentification SQL Server de la connexion « \*\*\*\<login name>**\*  »\*\* s’affiche entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="11ab2-131">Either **Windows Authentication of console user** or **SQL Server Authentication of login '***\<login name>***'** is displayed within the parentheses.</span></span> <span data-ttu-id="11ab2-132">Il s'agit des informations d'authentification actuellement utilisées si l'instance a été ajoutée auparavant ou qui seront utilisées si l'instance n'a pas encore été ajoutée au moniteur.</span><span class="sxs-lookup"><span data-stu-id="11ab2-132">This is the authentication information currently used, if the instance has been added before, or that will be used, if this instance has not been added to the monitor.</span></span>|  
  
 <span data-ttu-id="11ab2-133">**Afficher la boîte de dialogue Gérer les connexions serveur lorsque je clique sur OK.**</span><span class="sxs-lookup"><span data-stu-id="11ab2-133">**Show the Manage Server Connections dialog box when I click OK.**</span></span>  
 <span data-ttu-id="11ab2-134">Par défaut, le moniteur de mise en miroir de bases de données utilise les informations d'authentification Windows pour les instances de serveurs partenaires pour lesquelles aucune information d'identification n'a été précédemment fournie.</span><span class="sxs-lookup"><span data-stu-id="11ab2-134">By default, Database Mirroring Monitor uses Windows Authentication credentials for partner server instances for which credentials have not been previously given.</span></span> <span data-ttu-id="11ab2-135">Activez cette option si vous souhaitez modifier les informations d'identification sur une ou plusieurs instances de serveurs, une fois que vous avez inscrit des bases de données.</span><span class="sxs-lookup"><span data-stu-id="11ab2-135">Enable this option to change the credentials for one or more server instances when you finish registering databases.</span></span>  
  
 <span data-ttu-id="11ab2-136">Si cette option est activée, lorsque vous cliquez sur **OK**, la boîte de dialogue **Gérer les connexions serveur** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="11ab2-136">If this option is enabled, when you click **OK**, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="11ab2-137">Vous pouvez alors choisir une instance de serveur pour laquelle vous souhaitez spécifier des informations d'identification qui seront utilisées par le moniteur lors de la connexion à un partenaire de basculement donné.</span><span class="sxs-lookup"><span data-stu-id="11ab2-137">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given failover partner.</span></span>  
  
 <span data-ttu-id="11ab2-138">Pour modifier les informations d’identification pour un partenaire, recherchez l’entrée correspondante dans la grille **Instances de serveur** et cliquez sur **Modifier** dans cette ligne.</span><span class="sxs-lookup"><span data-stu-id="11ab2-138">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="11ab2-139">La boîte de dialogue **Se connecter au serveur** s’ouvre pour ce nom d’instance de serveur, avec les contrôles d’informations d’identification initialisés sur la valeur actuelle mise en cache.</span><span class="sxs-lookup"><span data-stu-id="11ab2-139">This opens the **Connect to Server** dialog box for that server instance name, with the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="11ab2-140">Modifiez les informations d’identification comme souhaité et cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="11ab2-140">Change the credentials as necessary and click **Connect**.</span></span> <span data-ttu-id="11ab2-141">Si les informations d’identification disposent des privilèges suffisants, la colonne **Se connecter avec** est mise à jour avec les nouvelles informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="11ab2-141">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>  
  
 <span data-ttu-id="11ab2-142">**Appliquer**</span><span class="sxs-lookup"><span data-stu-id="11ab2-142">**Apply**</span></span>  
 <span data-ttu-id="11ab2-143">Cliquez sur ce bouton pour inscrire les bases de données sélectionnées (et enregistrer les informations d'identification pour les instances de serveurs partenaires) tout en laissant la boîte de dialogue ouverte.</span><span class="sxs-lookup"><span data-stu-id="11ab2-143">Click this button to register the selected databases (and save credentials for the partner server instances) while keeping the dialog box open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ab2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11ab2-144">See Also</span></span>  
 <span data-ttu-id="11ab2-145">[Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="11ab2-145">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="11ab2-146">[Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="11ab2-146">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="11ab2-147">Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="11ab2-147">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  