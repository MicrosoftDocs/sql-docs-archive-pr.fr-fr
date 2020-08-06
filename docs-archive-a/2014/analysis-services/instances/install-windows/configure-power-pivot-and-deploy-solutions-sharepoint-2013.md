---
title: Configurer PowerPivot et déployer des solutions (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697320"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a><span data-ttu-id="a2781-102">Configurer PowerPivot et déployer des solutions (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="a2781-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span></span>
  <span data-ttu-id="a2781-103">Cette rubrique décrit le déploiement et la configuration des améliorations de niveau intermédiaire apportées aux fonctionnalités de PowerPivot dans [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] , dont la Galerie PowerPivot, l'actualisation planifiée des données, le tableau de bord de gestion et les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="a2781-103">This topics describes the deployment and configuration of middle-tier enhancements to the PowerPivot features in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] including PowerPivot Gallery, Schedule data refresh, Management Dashboard, and data providers.</span></span> <span data-ttu-id="a2781-104">Exécutez l'outil **Configuration de PowerPivot pour SharePoint 2013** pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2781-104">Run **PowerPivot for SharePoint 2013 Configuration** tool to complete the following:</span></span>  
  
-   <span data-ttu-id="a2781-105">Déployer les fichiers de solution SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-105">Deploy SharePoint solution files.</span></span>  
  
-   <span data-ttu-id="a2781-106">Créer une application de service PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="a2781-106">Create a PowerPivot service application.</span></span>  
  
-   <span data-ttu-id="a2781-107">Configurer une application Excel Services pour utiliser un serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] en mode SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-107">Configure an Excel Services Application to use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="a2781-108">Pour plus d’informations sur les services principaux et l’installation [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] d’un serveur en mode SharePoint, consultez [PowerPivot pour SharePoint l’installation de 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span><span class="sxs-lookup"><span data-stu-id="a2781-108">For information on backend services and installing a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
 <span data-ttu-id="a2781-109">Pour plus d’informations sur l’installation de l’outil de configuration PowerPivot pour SharePoint 2013, consultez [installer ou désinstaller le complément PowerPivot pour SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span><span class="sxs-lookup"><span data-stu-id="a2781-109">For information on installing the PowerPivot for SharePoint 2013 Configuration tool, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span></span>  
  
 <span data-ttu-id="a2781-110">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2781-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="a2781-111">Exécuter l'outil de configuration de PowerPivot pour SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="a2781-111">Run PowerPivot for SharePoint 2013 configuration</span></span>](#bkmk_run_configuration_tool)  
  
 [<span data-ttu-id="a2781-112">Vérifier la configuration PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-112">Verify PowerPivot Configuration</span></span>](#bkmk_verify_powerpivot)  
  
 [<span data-ttu-id="a2781-113">Résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="a2781-113">Troubleshoot Issues</span></span>](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a><span data-ttu-id="a2781-114">Exécuter PowerPivot pour SharePoint Configuration 2013</span><span class="sxs-lookup"><span data-stu-id="a2781-114">Run PowerPivot for SharePoint 2013 configuration</span></span>  
 <span data-ttu-id="a2781-115">**Remarque :** l'Assistant Installation de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] installe deux outils de configuration différents pour [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2781-115">**Note:** The [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] setup wizard installs two different configuration tools for [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span></span> <span data-ttu-id="a2781-116">Chacun d'eux prend en charge une version différente de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-116">They each support a different version of SharePoint.</span></span>  
  
|<span data-ttu-id="a2781-117">Nom</span><span class="sxs-lookup"><span data-stu-id="a2781-117">Name</span></span>|<span data-ttu-id="a2781-118">Description</span><span class="sxs-lookup"><span data-stu-id="a2781-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a2781-119">Configuration de PowerPivot pour SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="a2781-119">PowerPivot for SharePoint 2013 Configuration</span></span>|<span data-ttu-id="a2781-120">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="a2781-120">SharePoint 2013</span></span>|  
|<span data-ttu-id="a2781-121">Outil de configuration de PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-121">PowerPivot Configuration Tool</span></span>|<span data-ttu-id="a2781-122">SharePoint 2010 avec SharePoint 2010 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="a2781-122">SharePoint 2010 with SharePoint 2010 Service Pack 1 (SP1)</span></span>|  
  
 <span data-ttu-id="a2781-123">**Remarque :** pour effectuer les étapes suivantes, vous devez être administrateur de batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="a2781-123">**Note:** To complete the following steps, you must be a farm administrator.</span></span> <span data-ttu-id="a2781-124">Si un message d'erreur semblable au suivant s'affiche :</span><span class="sxs-lookup"><span data-stu-id="a2781-124">If you see an error message similar to the following:</span></span>  
  
-   <span data-ttu-id="a2781-125">«L’utilisateur n’est pas un administrateur de batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="a2781-125">"The user is not a farm administrator.</span></span> <span data-ttu-id="a2781-126">Traitez les échecs de validation et réessayez. »</span><span class="sxs-lookup"><span data-stu-id="a2781-126">Please address the validation failures and try again."</span></span>  
  
 <span data-ttu-id="a2781-127">Connectez-vous avec le compte qui a installé SharePoint ou configurez le compte d'installation en tant qu'administrateur principal du site Administration centrale de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-127">Either login as the account that installed SharePoint or configure the setup account as the primary administrator of the SharePoint Central Administration Site.</span></span>  
  
1.  <span data-ttu-id="a2781-128">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, puis sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Configuration PowerPivot pour SharePoint 2013**.</span><span class="sxs-lookup"><span data-stu-id="a2781-128">On the **Start** menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click **PowerPivot For SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="a2781-129">L'outil est répertorié uniquement lorsque PowerPivot pour SharePoint est installé sur le serveur local.</span><span class="sxs-lookup"><span data-stu-id="a2781-129">Toold is listed only when PowerPivot for SharePoint is installed on the local server.</span></span>  
  
2.  <span data-ttu-id="a2781-130">Cliquez sur **Configurer ou réparer PowerPivot pour SharePoint** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2781-130">Click **Configure or Repair PowerPivot for SharePoint** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="a2781-131">L'outil exécute la validation pour vérifier l'état actuel de PowerPivot et les étapes nécessaires pour terminer la configuration.</span><span class="sxs-lookup"><span data-stu-id="a2781-131">The tool runs validation to verify the current state of PowerPivot and what steps are required to complete configuration.</span></span> <span data-ttu-id="a2781-132">Affichez la fenêtre en plein écran.</span><span class="sxs-lookup"><span data-stu-id="a2781-132">Expand the window to full size.</span></span> <span data-ttu-id="a2781-133">Vous devez voir une barre d'icônes en bas de la fenêtre qui comprend les commandes **Valider**, **Exécuter**et **Quitter** .</span><span class="sxs-lookup"><span data-stu-id="a2781-133">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="a2781-134">Dans l'onglet **Paramètres** :</span><span class="sxs-lookup"><span data-stu-id="a2781-134">On the **Parameters** tab:</span></span>  
  
    1.  <span data-ttu-id="a2781-135">**Nom d'utilisateur de compte par défaut**: entrez un compte d'utilisateur de domaine pour le compte par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2781-135">**Default Account UserName**: Enter a domain user account for the default account.</span></span> <span data-ttu-id="a2781-136">Ce compte sera utilisé pour configurer des services, notamment le pool d'applications de service PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="a2781-136">This account will be used to provision services, including the PowerPivot service application pool.</span></span> <span data-ttu-id="a2781-137">Ne spécifiez pas un compte intégré tel que Service réseau ou Système local.</span><span class="sxs-lookup"><span data-stu-id="a2781-137">Do not specify a built-in account such as Network Service or Local System.</span></span> <span data-ttu-id="a2781-138">L'outil bloque les configurations qui spécifient des comptes intégrés.</span><span class="sxs-lookup"><span data-stu-id="a2781-138">The tool blocks configurations that specify built-in accounts.</span></span>  
  
    2.  <span data-ttu-id="a2781-139">**Serveur de base de données**: vous pouvez utiliser le moteur de base de données SQL Server pris en charge pour la batterie de serveurs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-139">**Database Server**: You can use SQL Server Database engine that is supported for the SharePoint farm.</span></span>  
  
    3.  <span data-ttu-id="a2781-140">**Phrase secrète**: entrez une phrase secrète.</span><span class="sxs-lookup"><span data-stu-id="a2781-140">**Passphrase**: Enter a passphrase.</span></span> <span data-ttu-id="a2781-141">Si vous créez une batterie de serveurs SharePoint, la phrase secrète est utilisée chaque fois que vous ajoutez un serveur ou une application à la batterie de serveurs SharePoint.</span><span class="sxs-lookup"><span data-stu-id="a2781-141">If you are creating a new SharePoint farm, the passphrase is used whenever you add a server or application to the SharePoint farm.</span></span> <span data-ttu-id="a2781-142">Si la batterie existe déjà, entrez la phrase secrète qui vous permet d'ajouter une application de serveur à la batterie.</span><span class="sxs-lookup"><span data-stu-id="a2781-142">If the farm already exists, enter the passphrase that allows you to add a server application to the farm.</span></span>  
  
    4.  <span data-ttu-id="a2781-143">**Serveur PowerPivot pour Excel Services**: entrez le nom d'un serveur en mode SharePoint pour [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a2781-143">**PowerPivot Server for Excel Services**: Type the name of an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server.</span></span> <span data-ttu-id="a2781-144">Dans un déploiement sur un seul serveur, il est identique à celui du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="a2781-144">In a single-server deployment, it is the same as the database server.</span></span> `[ServerName]\powerpivot`  
  
    5.  <span data-ttu-id="a2781-145">Cliquez sur **Créer une collection de sites** dans la fenêtre de gauche.</span><span class="sxs-lookup"><span data-stu-id="a2781-145">Click **Create Site Collection** in the left window.</span></span> <span data-ttu-id="a2781-146">Notez l' **URL du site** afin de pouvoir y faire référence dans les étapes ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a2781-146">Note **Site URL** so you can reference it in later steps.</span></span> <span data-ttu-id="a2781-147">Si le serveur SharePoint n'est pas déjà configuré, l'Assistant de configuration définit par défaut l'application Web et les URL de collection de sites sur la racine de `http://[ServerName]`.</span><span class="sxs-lookup"><span data-stu-id="a2781-147">If the SharePoint server is not already configured, then the configuration wizard defaults the web application, and site collection URLs to the root of `http://[ServerName]`.</span></span> <span data-ttu-id="a2781-148">Pour modifier les valeurs par défaut, examinez les pages suivantes dans la fenêtre de gauche : **Créer une application Web par défaut** et **Déployer une solution d'application Web**.</span><span class="sxs-lookup"><span data-stu-id="a2781-148">To modify the defaults review the following pages in the left window: **Create Default Web application** and **Deploy Web Application Solution**</span></span>  
  
5.  <span data-ttu-id="a2781-149">Éventuellement, examinez les valeurs d'entrée restantes utilisées pour effectuer chaque action.</span><span class="sxs-lookup"><span data-stu-id="a2781-149">Optionally, review the remaining input values used to complete each action.</span></span> <span data-ttu-id="a2781-150">Cliquez sur chaque action dans la fenêtre à gauche pour afficher et passer en revue les détails de l'action.</span><span class="sxs-lookup"><span data-stu-id="a2781-150">Click each action in the left window to see and review the details of the action.</span></span> <span data-ttu-id="a2781-151">Pour plus d’informations sur chacune d’elles, consultez la section «valeurs d’entrée utilisées pour configurer le serveur dans [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a2781-151">For more information about each one, see the section "Input values used to configure the server in [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in this topic.</span></span>  
  
6.  <span data-ttu-id="a2781-152">Éventuellement, supprimez toutes les actions que vous ne souhaitez pas traiter à ce stade.</span><span class="sxs-lookup"><span data-stu-id="a2781-152">Optionally, remove any actions that you do not want to process at this time.</span></span> <span data-ttu-id="a2781-153">Par exemple, si vous souhaitez configurer le service Banque d'informations sécurisé ultérieurement, cliquez sur **Configurer le service Banque d'informations sécurisé**, puis désactivez la case à cocher **Inclure cette action dans la liste des tâches**.</span><span class="sxs-lookup"><span data-stu-id="a2781-153">For example, if you want to configure Secure Store Service later, click **Configure Secure Store Service**, and then clear the checkbox **Include this action in the task list**.</span></span>  
  
7.  <span data-ttu-id="a2781-154">Cliquez sur **Valider** pour vérifier que l'outil dispose d'informations suffisantes pour traiter les actions de la liste.</span><span class="sxs-lookup"><span data-stu-id="a2781-154">Click **Validate** to check whether the tool has sufficient information to process the actions in the list.</span></span> <span data-ttu-id="a2781-155">Si des erreurs de validation s'affichent, cliquez sur les avertissements dans le volet gauche pour afficher les détails de l'erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="a2781-155">If you see validation errors, click the warnings in the left pane to see details of the validation error.</span></span> <span data-ttu-id="a2781-156">Corrigez toutes les erreurs de validation, puis cliquez de nouveau sur **Valider** .</span><span class="sxs-lookup"><span data-stu-id="a2781-156">Correct any validation errors and then click **Validate** again.</span></span>  
  
8.  <span data-ttu-id="a2781-157">Cliquez sur **Exécuter** pour traiter toutes les actions de la liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="a2781-157">Click **Run** to process all of the actions in the task list.</span></span> <span data-ttu-id="a2781-158">Notez qu' **Exécuter** devient disponible lorsque vous avez validé les actions.</span><span class="sxs-lookup"><span data-stu-id="a2781-158">Note that **Run** becomes available after you validate the actions.</span></span> <span data-ttu-id="a2781-159">Si **Exécuter** n'est pas activé, commencez par cliquer sur **Valider** .</span><span class="sxs-lookup"><span data-stu-id="a2781-159">If **Run** is not enabled, click **Validate** first.</span></span>  
  
 <span data-ttu-id="a2781-160">Pour plus d’informations, consultez [configurer ou réparer PowerPivot pour SharePoint 2010 &#40;outil de configuration de PowerPivot&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="a2781-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span></span>  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a><span data-ttu-id="a2781-161">Vérifier la configuration PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-161">Verify PowerPivot Configuration</span></span>  
 <span data-ttu-id="a2781-162">**Services :**</span><span class="sxs-lookup"><span data-stu-id="a2781-162">**Services:**</span></span>  
  
1.  <span data-ttu-id="a2781-163">Dans l’administration centrale, sous paramètres système, cliquez sur **gérer les services sur le serveur**.</span><span class="sxs-lookup"><span data-stu-id="a2781-163">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="a2781-164">Vérifiez que **SQL Server Analysis Services** et le **service système SQL Server PowerPivot** sont démarrés.</span><span class="sxs-lookup"><span data-stu-id="a2781-164">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
 <span data-ttu-id="a2781-165">**Fonctionnalités de la batterie de serveurs :**</span><span class="sxs-lookup"><span data-stu-id="a2781-165">**Farm Feature:**</span></span>  
  
1.  <span data-ttu-id="a2781-166">Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les fonctionnalités des batteries de serveurs**.</span><span class="sxs-lookup"><span data-stu-id="a2781-166">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
2.  <span data-ttu-id="a2781-167">Vérifiez que l'option **Fonctionnalité d'intégration PowerPivot** a la valeur **Activée**.</span><span class="sxs-lookup"><span data-stu-id="a2781-167">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
 <span data-ttu-id="a2781-168">**Fonctionnalités de la collection de sites :**</span><span class="sxs-lookup"><span data-stu-id="a2781-168">**Site Collection Feature:**</span></span>  
  
1.  <span data-ttu-id="a2781-169">Accédez à l'URL du site créé par l'outil de configuration.</span><span class="sxs-lookup"><span data-stu-id="a2781-169">Browse to your site URL that was created by the Configuration tool.</span></span>  
  
     <span data-ttu-id="a2781-170">Cliquez sur **paramètres**paramètres![SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Paramètres SharePoint"), puis sur **paramètres du site**.</span><span class="sxs-lookup"><span data-stu-id="a2781-170">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings"), and then click **Site Settings**.</span></span>  
  
     <span data-ttu-id="a2781-171">Cliquez sur **Fonctionnalités de la collection de sites**.</span><span class="sxs-lookup"><span data-stu-id="a2781-171">Click **Site Collection Features**.</span></span>  
  
2.  <span data-ttu-id="a2781-172">Vérifiez que **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est **Activée**.</span><span class="sxs-lookup"><span data-stu-id="a2781-172">Verify that **PowerPivot Feature Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="a2781-173">**Application de service PowerPivot :**</span><span class="sxs-lookup"><span data-stu-id="a2781-173">**PowerPivot Service Application:**</span></span>  
  
1.  <span data-ttu-id="a2781-174">Dans l'Administration centrale, sous **Gestion des applications**, cliquez sur **Gérer les applications de service**.</span><span class="sxs-lookup"><span data-stu-id="a2781-174">In Central Administration, in the **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="a2781-175">Vérifiez que l'état de l'application de service est **Démarré**.</span><span class="sxs-lookup"><span data-stu-id="a2781-175">Verify the service application status is **started**.</span></span> <span data-ttu-id="a2781-176">Le nom par défaut est **application de service PowerPivot par défaut**.</span><span class="sxs-lookup"><span data-stu-id="a2781-176">The default name is **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="a2781-177">Cliquez sur le nom de l'application de service pour ouvrir le Tableau de bord de gestion PowerPivot pour cette application de service.</span><span class="sxs-lookup"><span data-stu-id="a2781-177">Click the name of the services application to open the PowerPivot Management Dashboard for the service application opens.</span></span> <span data-ttu-id="a2781-178">À la première utilisation, le tableau de bord prend plusieurs minutes à charger.</span><span class="sxs-lookup"><span data-stu-id="a2781-178">On first use, the dashboard takes several minutes to load.</span></span>  
  
 <span data-ttu-id="a2781-179">Pour plus d’informations, consultez [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span><span class="sxs-lookup"><span data-stu-id="a2781-179">For more information, see [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span></span>  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a><span data-ttu-id="a2781-180">Résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="a2781-180">Troubleshoot Issues</span></span>  
 <span data-ttu-id="a2781-181">Pour aider les problèmes de dépannage, il peut être judicieux de vérifier que la journalisation du diagnostic est activée.</span><span class="sxs-lookup"><span data-stu-id="a2781-181">To assist in troubleshooting issues, it is a good idea to verify the diagnostic logging is enabled.</span></span>  
  
1.  <span data-ttu-id="a2781-182">Dans l'Administration centrale de SharePoint, cliquez sur **Analyse** , puis sur **Configurer la collecte des données d'utilisation et d'intégrité**.</span><span class="sxs-lookup"><span data-stu-id="a2781-182">In SharePoint Central Administration, click **Monitoring** and then click **Configure usage and health data collection**.</span></span>  
  
2.  <span data-ttu-id="a2781-183">Vérifiez que l'option **Activer la collecte des données d'utilisation** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="a2781-183">Verify **Enable usage data collection** is selected.</span></span>  
  
3.  <span data-ttu-id="a2781-184">Vérifiez que les événements suivants sont sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="a2781-184">Verify the following events are selected:</span></span>  
  
    -   <span data-ttu-id="a2781-185">Définition des champs d'utilisation de la télémesure d'éducation</span><span class="sxs-lookup"><span data-stu-id="a2781-185">Definition of usage fields for Education telemetry</span></span>  
  
    -   <span data-ttu-id="a2781-186">Connexions PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-186">PowerPivot Connects</span></span>  
  
    -   <span data-ttu-id="a2781-187">Utilisation des données de chargement PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-187">PowerPivot Load Data Usage</span></span>  
  
    -   <span data-ttu-id="a2781-188">Utilisation des requêtes PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-188">PowerPivot Query Usage</span></span>  
  
    -   <span data-ttu-id="a2781-189">Utilisation des données de déchargement PowerPivot</span><span class="sxs-lookup"><span data-stu-id="a2781-189">PowerPivot Unload Data Usage</span></span>  
  
4.  <span data-ttu-id="a2781-190">Vérifiez que l'option **Activer la collecte des données d'intégrité** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="a2781-190">Verify **Enable health data collection** is selected.</span></span>  
  
5.  <span data-ttu-id="a2781-191">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2781-191">Click **OK**.</span></span>  
  
 <span data-ttu-id="a2781-192">Pour plus d’informations sur le dépannage de l’actualisation des données, consultez [résolution des problèmes d’actualisation des données PowerPivot](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) ( https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) .</span><span class="sxs-lookup"><span data-stu-id="a2781-192">For more information on trouble shooting data refresh, see [Troubleshooting PowerPivot Data Refresh](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).</span></span>  
  
 <span data-ttu-id="a2781-193">Pour plus d'informations sur l'outil de configuration, consultez [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a2781-193">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>  
  
  