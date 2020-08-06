---
title: Règles d’intégrité PowerPivot-configurer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a01e63e6-97dc-43e5-ad12-ae6580afc606
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c16db9ca1ba0e66402f5c157b44a38c45eb0852
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703315"
---
# <a name="powerpivot-health-rules---configure"></a><span data-ttu-id="81725-102">Règles d'intégrité de PowerPivot - Configurer</span><span class="sxs-lookup"><span data-stu-id="81725-102">PowerPivot Health Rules - Configure</span></span>
  <span data-ttu-id="81725-103">PowerPivot pour SharePoint inclut des règles d'intégrité SharePoint qui vous aident à analyser et à résoudre les problèmes de disponibilité et de configuration du serveur.</span><span class="sxs-lookup"><span data-stu-id="81725-103">PowerPivot for SharePoint includes SharePoint health rules that help you monitor and remedy server availability and configuration problems.</span></span> <span data-ttu-id="81725-104">Les règles d'intégrité qui s'appliquent à PowerPivot pour SharePoint apparaissent dans la page Vérifier les définitions de règles.</span><span class="sxs-lookup"><span data-stu-id="81725-104">Health rules that apply to PowerPivot for SharePoint appear in the Review rule definitions page.</span></span>  
  
 <span data-ttu-id="81725-105">Les règles d'intégrité permettent la détection anticipée des problèmes de serveur susceptibles de provoquer des interruptions de service.</span><span class="sxs-lookup"><span data-stu-id="81725-105">Health rules provide early detection of server problems that could eventually result in service disruptions.</span></span> <span data-ttu-id="81725-106">PowerPivot pour SharePoint fournit plusieurs règles pour vous aider à identifier et résoudre les problèmes avant qu'ils ne touchent vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="81725-106">PowerPivot for SharePoint provides a number of rules to help you identify and fix problems before they impact your users.</span></span> <span data-ttu-id="81725-107">Vous pouvez personnaliser beaucoup de ces règles pour les adapter aux besoins uniques de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="81725-107">You can customize many of these rules to fit the unique characteristics of your deployment.</span></span> <span data-ttu-id="81725-108">Par exemple, si vous souhaitez disposer de plus de temps pour traiter les avertissements relatifs à l'espace disque, vous pouvez augmenter le pourcentage d'espace disque disponible de 5 % à 10 % afin de recevoir l'avertissement plus tôt.</span><span class="sxs-lookup"><span data-stu-id="81725-108">For example, if you want more time to address warnings about disk space, you could raise the available disk space percentage from 5% to 10% so that you get the warning earlier.</span></span>  
  
 <span data-ttu-id="81725-109">Les règles qui peuvent être personnalisées sont celles qui surveillent la consommation des ressources ou la disponibilité du serveur.</span><span class="sxs-lookup"><span data-stu-id="81725-109">Rules that can be customized are those that report on resource consumption or server availability.</span></span> <span data-ttu-id="81725-110">La personnalisation est utile dans ce cas parce que la capacité du système sous-jacent varie fortement selon les topologies de serveur et de déploiement.</span><span class="sxs-lookup"><span data-stu-id="81725-110">Customization is helpful in these areas because underlying system capacity varies widely across different servers and deployment topologies.</span></span> <span data-ttu-id="81725-111">Par opposition, aucune personnalisation n'est possible pour les règles qui identifient la configuration du serveur ou les problèmes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="81725-111">In contrast, no customization is available for rules that identify server configuration or security issues.</span></span> <span data-ttu-id="81725-112">Ces règles doivent être appliquée uniformément sur toutes les installations.</span><span class="sxs-lookup"><span data-stu-id="81725-112">Those rules are intended to be applied uniformly across all installations.</span></span>  
  
||  
|-|  
|<span data-ttu-id="81725-113">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="81725-113">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|  
  
 <span data-ttu-id="81725-114">**Remarque :** les paramètres des règles d'intégrité sont configurés séparément pour l'instance de SQL Server Analysis Services et l'application de service PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="81725-114">**Note:** Health rule settings are configured separately for the SQL Server Analysis Services instance and the PowerPivot service application.</span></span> <span data-ttu-id="81725-115">Suivez les instructions de cette rubrique pour configurer des règles d'intégrité pour chaque service.</span><span class="sxs-lookup"><span data-stu-id="81725-115">Use the instructions in this topic to configure health rules for each service.</span></span> <span data-ttu-id="81725-116">Pour un déploiement SharePoint 2013, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] utilise uniquement l'application de service.</span><span class="sxs-lookup"><span data-stu-id="81725-116">For a SharePoint 2013 deployment, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] only uses the service application.</span></span> <span data-ttu-id="81725-117">Par conséquent, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installe différents jeux de règles d'intégrité pour différentes versions de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="81725-117">Therefore [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installs different sets of health rules for different versions of SharePoint.</span></span> <span data-ttu-id="81725-118">Consultez la colonne « version » dans la rubrique [référence des règles d’intégrité &#40;PowerPivot pour SharePoint&#41;](health-rules-reference-power-pivot-for-sharepoint.md), ou exécutez la commande Windows PowerShell suivante pour voir les règles installées.</span><span class="sxs-lookup"><span data-stu-id="81725-118">See the "version" column in the topic [Health Rules Reference &#40;PowerPivot for SharePoint&#41;](health-rules-reference-power-pivot-for-sharepoint.md), or you can run the following Windows PowerShell command to see the installed rules.</span></span>  
  
```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default  
```  
  
 <span data-ttu-id="81725-119">**Dans cette rubrique :**</span><span class="sxs-lookup"><span data-stu-id="81725-119">**In this topic:**</span></span>  
  
 [<span data-ttu-id="81725-120">Afficher les règles d'intégrité PowerPivot</span><span class="sxs-lookup"><span data-stu-id="81725-120">View PowerPivot health rules</span></span>](#bkmk_view)  
  
 [<span data-ttu-id="81725-121">Configurer les règles d'intégrité utilisées pour évaluer la stabilité du serveur (SQL Server Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="81725-121">Configure health rules used to evaluate server stability (SQL Server Analysis Services)</span></span>](#bkmk_HR_SSAS)  
  
 [<span data-ttu-id="81725-122">Configurer les règles d'intégrité utilisées pour évaluer la stabilité de l'application (Application de service PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="81725-122">Configure health rules used to evaluate application stability (PowerPivot Service Application)</span></span>](#bkmk_evaluate_application_stability)  
  
## <a name="prerequisites"></a><span data-ttu-id="81725-123">Prérequis</span><span class="sxs-lookup"><span data-stu-id="81725-123">Prerequisites</span></span>  
 <span data-ttu-id="81725-124">Vous devez être administrateur de l'application de service pour modifier les propriétés de configuration de l'instance d'Analysis Services et de l'application de service PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="81725-124">You must be a service application administrator to change configuration properties of the Analysis Services instance and of the PowerPivot service application.</span></span>  
  
##  <a name="view-powerpivot-health-rules"></a><a name="bkmk_view"></a><span data-ttu-id="81725-125">Afficher les règles d’intégrité PowerPivot</span><span class="sxs-lookup"><span data-stu-id="81725-125">View PowerPivot health rules</span></span>  
  
1.  <span data-ttu-id="81725-126">Dans l'Administration centrale de SharePoint, cliquez sur **Analyse**, puis dans la section **Analyseur d’intégrité** , cliquez sur **Vérifier les définitions de règles**.</span><span class="sxs-lookup"><span data-stu-id="81725-126">In SharePoint Central Administration, click **Monitoring**, and in the **Health Analyzer** section, click **Review rule definitions**.</span></span>  
  
2.  <span data-ttu-id="81725-127">Dans la section de configuration, recherchez les règles qui ont le préfixe **PowerPivot :** .</span><span class="sxs-lookup"><span data-stu-id="81725-127">In the Configuration section, find the rules that have the **PowerPivot:** prefix.</span></span> <span data-ttu-id="81725-128">Toutes les règles d'intégrité connexes à PowerPivot ont ce préfixe pour vous aider à les distinguer des règles SharePoint intégrées.</span><span class="sxs-lookup"><span data-stu-id="81725-128">All PowerPivot-related health rules have this prefix to help you distinguish them from the built-in SharePoint rules.</span></span>  
  
 <span data-ttu-id="81725-129">Ces règles s'afficheront dans la page **Examiner les problèmes et solutions** lorsque des problèmes sont détectés.</span><span class="sxs-lookup"><span data-stu-id="81725-129">These rules will appear in the **Review problems and solutions** page when problems are detected.</span></span>  
  
 <span data-ttu-id="81725-130">Si vous soupçonnez un problème et souhaitez vérifier cela immédiatement, vous pouvez exécuter manuellement une vérification de la règle pour déterminer si un problème existe.</span><span class="sxs-lookup"><span data-stu-id="81725-130">If you suspect a problem that you want to investigate immediately, you can run a rule check manually to find out if there is an issue.</span></span>  
  
 <span data-ttu-id="81725-131">Pour ce faire, cliquez sur la règle pour ouvrir sa définition, puis cliquez sur **Exécuter maintenant** dans le ruban.</span><span class="sxs-lookup"><span data-stu-id="81725-131">To do this, click the rule to open its rule definition, and then click **Run Now** in the ribbon.</span></span> <span data-ttu-id="81725-132">Cliquez sur **Fermer** pour revenir à la page **Examiner les problèmes et solutions** et afficher le rapport.</span><span class="sxs-lookup"><span data-stu-id="81725-132">Click **Close** to go back to the **Review problems and solutions** page to view the report.</span></span> <span data-ttu-id="81725-133">Si la règle a détecté un problème, un avertissement ou une erreur sera signalé sur la page.</span><span class="sxs-lookup"><span data-stu-id="81725-133">If the rule detected a problem, a warning or error will be reported on the page.</span></span> <span data-ttu-id="81725-134">Dans certains cas, l'affichage de l'erreur ou de l'avertissement peut prendre quelques minutes.</span><span class="sxs-lookup"><span data-stu-id="81725-134">In some cases, it can take a few minutes before the error or warning will appear.</span></span>  
  
##  <a name="configure-health-rules-used-to-evaluate-server-stability-sql-server-analysis-services"></a><a name="bkmk_HR_SSAS"></a><span data-ttu-id="81725-135">Configurer les règles d’intégrité utilisées pour évaluer la stabilité du serveur (SQL Server Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="81725-135">Configure health rules used to evaluate server stability (SQL Server Analysis Services)</span></span>  
 <span data-ttu-id="81725-136">L'instance d'Analysis Services inclut des règles d'intégrité qui détectent des problèmes au niveau du système (UC, mémoire et espace disque utilisé pour la mise en cache).</span><span class="sxs-lookup"><span data-stu-id="81725-136">The Analysis Services instance includes health rules that detect problems at the system level (CPU, memory, and disk space used for caching purposes).</span></span> <span data-ttu-id="81725-137">Utilisez les instructions suivantes pour modifier les seuils qui déclenchent des règles d'intégrité spécifiques.</span><span class="sxs-lookup"><span data-stu-id="81725-137">Use the following instructions to modify thresholds that trigger specific health rules.</span></span>  
  
1.  <span data-ttu-id="81725-138">Dans l'Administration centrale de SharePoint, cliquez sur **Gérer les services sur le serveur** dans la section **Paramètres système**.</span><span class="sxs-lookup"><span data-stu-id="81725-138">In SharePoint Central Administration, in the **System Settings** section, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="81725-139">En haut de la page, sélectionnez le serveur dans votre batterie de serveurs SharePoint dotée d'une instance d'Analysis Services (dans l'illustration suivante, le nom du serveur est AW-SRV033).</span><span class="sxs-lookup"><span data-stu-id="81725-139">At the top of the page, select the server in your SharePoint farm that has an instance of Analysis Services (in the following illustration, the server name is AW-SRV033).</span></span> <span data-ttu-id="81725-140">**SQL Server Analysis Services** apparaît dans la liste des services.</span><span class="sxs-lookup"><span data-stu-id="81725-140">**SQL Server Analysis Services** will appear in the list of services.</span></span>  
  
     <span data-ttu-id="81725-141">![Capture d'écran de la page Gérer les services sur le serveur](../media/ssas-centraladmin-servicesonserver.gif "Capture d'écran de la page Gérer les services sur le serveur")</span><span class="sxs-lookup"><span data-stu-id="81725-141">![Screenshot of Manage Services on Server page](../media/ssas-centraladmin-servicesonserver.gif "Screenshot of Manage Services on Server page")</span></span>  
  
3.  <span data-ttu-id="81725-142">Cliquez sur **SQL Server Analysis Services**.</span><span class="sxs-lookup"><span data-stu-id="81725-142">Click **SQL Server Analysis Services**.</span></span>  
  
4.  <span data-ttu-id="81725-143">Dans les pages de propriétés du service, dans Paramètres de règle d'intégrité, modifiez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="81725-143">In the service property pages, in Health Rule Settings, modify the following settings:</span></span>  
  
     <span data-ttu-id="81725-144">Allocation de ressources processeur insuffisante (la valeur par défaut est 80 %)</span><span class="sxs-lookup"><span data-stu-id="81725-144">Insufficient CPU Resource Allocation (default is 80%)</span></span>  
     <span data-ttu-id="81725-145">Cette règle d'intégrité est déclenchée si les ressources processeur utilisées par le processus serveur d'Analysis Services (msmdsrv.exe) sont supérieures ou égales à 80 % pendant une période de 4 heures (comme spécifié par le paramètre Intervalle de collecte des données).</span><span class="sxs-lookup"><span data-stu-id="81725-145">This health rule is triggered if the CPU resources used by Analysis Services server process (msmdsrv.exe) remains at or above 80% over a 4 hour period (as specified through the Data Collection Interval setting).</span></span>  
  
     <span data-ttu-id="81725-146">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : Analysis Services ne dispose pas de suffisamment de ressources processeur pour effectuer les opérations demandées.**</span><span class="sxs-lookup"><span data-stu-id="81725-146">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: Analysis Services does not have sufficient CPU resources to perform requested operations.**</span></span>  
  
     <span data-ttu-id="81725-147">Ressources processeur insuffisantes sur le système (la valeur par défaut est 90 %)</span><span class="sxs-lookup"><span data-stu-id="81725-147">Insufficient CPU Resources on the System (default is 90%)</span></span>  
     <span data-ttu-id="81725-148">Cette règle d'intégrité est déclenchée si les ressources processeur pour le serveur sont inférieures ou égales à 90 % pendant une période de 4 heures (comme spécifié via le paramètre Intervalle de collecte des données).</span><span class="sxs-lookup"><span data-stu-id="81725-148">This health rule is triggered if CPU resources for the server remain at or above 90% over a 4 hour period (as specified through the Data Collection Interval setting).</span></span> <span data-ttu-id="81725-149">L'utilisation générale de l'UC est mesurée dans le cadre de l'algorithme d'équilibrage de charge basé sur l'intégrité qui surveille l'utilisation de l'UC pour mesurer l'intégrité du serveur.</span><span class="sxs-lookup"><span data-stu-id="81725-149">Overall CPU utilization is measured as part of the health-based load balancing algorithm that monitors CPU usage as a measure of server health.</span></span>  
  
     <span data-ttu-id="81725-150">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : l'utilisation globale du processeur est trop élevée.**</span><span class="sxs-lookup"><span data-stu-id="81725-150">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: Overall CPU usage is too high.**</span></span>  
  
     <span data-ttu-id="81725-151">Seuil de mémoire insuffisante (la valeur par défaut est 5 %)</span><span class="sxs-lookup"><span data-stu-id="81725-151">Insufficient Memory Threshold (default is 5%)</span></span>  
     <span data-ttu-id="81725-152">Sur un serveur d'applications SharePoint, une instance de SQL Server Analysis Services doit toujours avoir une quantité minimale de mémoire en réserve, toujours inutilisée.</span><span class="sxs-lookup"><span data-stu-id="81725-152">On a SharePoint application server, a SQL Server Analysis Services instance should always have a small amount of memory in reserve that is always unused.</span></span> <span data-ttu-id="81725-153">Étant donné que le fonctionnement du serveur est lié à la mémoire pour la plupart de ses opérations, celui-ci s'exécute mieux s'il n'atteint pas complètement la limite supérieure.</span><span class="sxs-lookup"><span data-stu-id="81725-153">Because the server is memory-bound for the majority of its operations, the server runs best if it does not run all the way to the upper limit.</span></span> <span data-ttu-id="81725-154">Les 5 % de mémoire inutilisée sont calculés sous forme de pourcentage de la mémoire allouée à Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="81725-154">The 5% of unused memory is calculated as a percentage of memory allocated to Analysis Services.</span></span> <span data-ttu-id="81725-155">Par exemple, si vous avez 200 Go de mémoire totale et qu'Analysis Services en utilise 80 % (soit 160 Go), les 5 % de mémoire inutilisée correspondent à 5 % de 160 Go (soit 8 Go).</span><span class="sxs-lookup"><span data-stu-id="81725-155">For example, if you have 200 GB of total memory, and Analysis Services is allocated 80% of that (or 160 GB), then the 5% of unused memory is 5% of 160 GB (or 8 GB).</span></span>  
  
     <span data-ttu-id="81725-156">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : Analysis Services ne dispose pas de suffisamment de mémoire pour effectuer les opérations demandées.**</span><span class="sxs-lookup"><span data-stu-id="81725-156">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: Analysis Services does not have sufficient memory to perform requested operations.**</span></span>  
  
     <span data-ttu-id="81725-157">Nombre maximal de connexions (la valeur par défaut est 100)</span><span class="sxs-lookup"><span data-stu-id="81725-157">Maximum Number of Connections (default is 100)</span></span>  
     <span data-ttu-id="81725-158">Cette règle d'intégrité est déclenchée si le nombre de connexions à l'instance d'Analysis Services est supérieur ou égal à 100 connexions pendant une période de 4 heures (comme spécifié via le paramètre Intervalle de collecte des données).</span><span class="sxs-lookup"><span data-stu-id="81725-158">This health rule is triggered if the number of connections to the Analysis Services instance remains at or above 100 connections over a 4 hour period (as specified through the Data Collection Interval setting).</span></span> <span data-ttu-id="81725-159">Cette valeur par défaut est arbitraire (elle n'est pas basée sur les spécifications matérielles de votre serveur ou sur l'activité des utilisateurs), vous pouvez donc augmenter ou diminuer la valeur en fonction de la capacité du serveur et de l'activité des utilisateurs dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="81725-159">This default value is arbitrary (it is not based on the hardware specifications of your server or on user activity) so you might raise or lower the value depending on the server capacity and user activity in your environment.</span></span>  
  
     <span data-ttu-id="81725-160">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : le nombre élevé de connexions indique que davantage de serveurs devraient être déployés afin de pouvoir gérer la charge actuelle.**</span><span class="sxs-lookup"><span data-stu-id="81725-160">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: The high number of connections indicates that more servers should be deployed to handle the current load.**</span></span>  
  
     <span data-ttu-id="81725-161">Espace disque insuffisant (la valeur par défaut est 5 %)</span><span class="sxs-lookup"><span data-stu-id="81725-161">Insufficient Disk Space (default is 5%)</span></span>  
     <span data-ttu-id="81725-162">L'espace disque est utilisé pour mettre en cache les données PowerPivot chaque fois qu'une base de données est demandée.</span><span class="sxs-lookup"><span data-stu-id="81725-162">Disk space is used to cache PowerPivot data each time a database is requested.</span></span> <span data-ttu-id="81725-163">Cette règle vous permet de savoir quand l'espace disque est trop faible.</span><span class="sxs-lookup"><span data-stu-id="81725-163">This rule lets you know when disk space is running low.</span></span> <span data-ttu-id="81725-164">Par défaut, cette règle d'intégrité est déclenchée lorsque l'espace disque est inférieur à 5 % sur le lecteur de disque où se trouve le dossier de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="81725-164">By default, this health rule is triggered when disk space is less than 5% on the disk drive where the backup folder is located.</span></span> <span data-ttu-id="81725-165">Pour plus d’informations sur l’utilisation des disques, consultez [configurer l’utilisation de l’espace disque &#40;PowerPivot pour SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md).</span><span class="sxs-lookup"><span data-stu-id="81725-165">For more information about disk usage, see [Configure Disk Space Usage &#40;PowerPivot for SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md).</span></span>  
  
     <span data-ttu-id="81725-166">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : il n'y a presque plus d'espace disponible sur le lecteur sur lequel se trouvent les données PowerPivot mises en cache.**</span><span class="sxs-lookup"><span data-stu-id="81725-166">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: Disk space is running low on the drive where PowerPivot data is cached.**</span></span>  
  
     <span data-ttu-id="81725-167">Intervalle de collecte des données (en heures)</span><span class="sxs-lookup"><span data-stu-id="81725-167">Data Collection Interval (in hours)</span></span>  
     <span data-ttu-id="81725-168">Vous pouvez spécifier la période de collecte de données prise en compte pour calculer les valeurs utilisées pour déclencher des règles d'intégrité.</span><span class="sxs-lookup"><span data-stu-id="81725-168">You can specify the data collection period used for calculating the numbers used for triggering health rules.</span></span> <span data-ttu-id="81725-169">Bien que le système soit surveillé en permanence, les seuils utilisés pour déclencher des avertissements de règle d'intégrité sont calculés à l'aide de données qui ont été générées pendant un intervalle prédéfini.</span><span class="sxs-lookup"><span data-stu-id="81725-169">Although the system is monitored constantly, the thresholds used to trigger health rule warnings are calculated using data that was generated over a predefined interval.</span></span> <span data-ttu-id="81725-170">L'intervalle par défaut est de 4 heures.</span><span class="sxs-lookup"><span data-stu-id="81725-170">The default interval is 4 hours.</span></span> <span data-ttu-id="81725-171">Le serveur récupère les données système et d'utilisation collectées au cours des 4 heures précédentes pour évaluer le nombre de connexions utilisateur, l'utilisation de l'espace disque et les taux d'utilisation de l'UC et de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="81725-171">The server retrieves system and usage data collected over the previous 4 hours to evaluate the number of user connections, disk space usage, and CPU and memory utilization rates.</span></span>  
  
##  <a name="configure-health-rules-used-to-evaluate-application-stability-powerpivot-service-application"></a><a name="bkmk_evaluate_application_stability"></a><span data-ttu-id="81725-172">Configurer les règles d’intégrité utilisées pour évaluer la stabilité de l’application (application de service PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="81725-172">Configure health rules used to evaluate application stability (PowerPivot Service Application)</span></span>  
  
1.  <span data-ttu-id="81725-173">Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.</span><span class="sxs-lookup"><span data-stu-id="81725-173">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="81725-174">Dans la page Applications de service, cliquez sur **Application de service PowerPivot par défaut**.</span><span class="sxs-lookup"><span data-stu-id="81725-174">In the Service Applications page, click **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="81725-175">![Capture d'écran de la page Gérer l'application de service](../media/ssas-centraladmin-app.gif "Capture d'écran de la page Gérer l'application de service")</span><span class="sxs-lookup"><span data-stu-id="81725-175">![Screenshot of ManageService Application page](../media/ssas-centraladmin-app.gif "Screenshot of ManageService Application page")</span></span>  
  
3.  <span data-ttu-id="81725-176">Le Tableau de bord de gestion PowerPivot apparaît.</span><span class="sxs-lookup"><span data-stu-id="81725-176">The PowerPivot Management Dashboard appears.</span></span> <span data-ttu-id="81725-177">Cliquez sur **Configurer les paramètres d'application de service** dans la liste **Actions** pour ouvrir la page des paramètres d'application de service.</span><span class="sxs-lookup"><span data-stu-id="81725-177">Click the **Configure service application settings** in the **Actions** list to open the service application settings page.</span></span>  
  
     <span data-ttu-id="81725-178">![Capture d'écran du tableau de bord, et plus particulièrement de la liste Actions](../media/ssas-centraladmin-actionslist.gif "Capture d'écran du tableau de bord, et plus particulièrement de la liste Actions")</span><span class="sxs-lookup"><span data-stu-id="81725-178">![Screenshot of dashboard, focus on Actions list](../media/ssas-centraladmin-actionslist.gif "Screenshot of dashboard, focus on Actions list")</span></span>  
  
4.  <span data-ttu-id="81725-179">Dans les paramètres de la règle d'intégrité modifiez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="81725-179">In Health Rule Settings, modify the following settings:</span></span>  
  
     <span data-ttu-id="81725-180">Rapport chargements/connexions (la valeur par défaut est 20 %)</span><span class="sxs-lookup"><span data-stu-id="81725-180">Load to Connection Ratio (default is 20%)</span></span>  
     <span data-ttu-id="81725-181">Cette règle d'intégrité est déclenchée si le nombre d'événements de chargement est élevé par rapport au nombre d'événements de connexion, et signale que le serveur est peut-être en train de décharger trop rapidement des bases de données, ou que les paramètres de réduction du cache sont trop stricts.</span><span class="sxs-lookup"><span data-stu-id="81725-181">This health rule is triggered if the number of load events is high relative to the number of connection events, signaling that the server might be unloading databases too quickly, or that cache reduction settings are too aggressive.</span></span>  
  
     <span data-ttu-id="81725-182">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : le taux d'événements de chargement par rapport aux connexions est trop élevé.**</span><span class="sxs-lookup"><span data-stu-id="81725-182">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: The ratio of load events to connections is too high.**</span></span>  
  
     <span data-ttu-id="81725-183">Intervalle de collecte des données (la valeur par défaut est 4 heures)</span><span class="sxs-lookup"><span data-stu-id="81725-183">Data Collection Interval (default is 4 hours)</span></span>  
     <span data-ttu-id="81725-184">Vous pouvez spécifier la période de collecte de données prise en compte pour calculer les valeurs utilisées pour déclencher des règles d'intégrité.</span><span class="sxs-lookup"><span data-stu-id="81725-184">You can specify the data collection period used for calculating the numbers used for triggering health rules.</span></span> <span data-ttu-id="81725-185">Bien que le système soit surveillé en permanence, les seuils utilisés pour déclencher des avertissements de règle d'intégrité sont calculés à l'aide de données qui ont été générées pendant un intervalle prédéfini.</span><span class="sxs-lookup"><span data-stu-id="81725-185">Although the system is monitored constantly, the thresholds used to trigger health rule warnings are calculated using data that was generated over a predefined interval.</span></span> <span data-ttu-id="81725-186">L'intervalle par défaut est de 4 heures.</span><span class="sxs-lookup"><span data-stu-id="81725-186">The default interval is 4 hours.</span></span> <span data-ttu-id="81725-187">Le serveur récupère les données système et d'utilisation collectées au cours des 4 heures précédentes pour évaluer le rapport chargement/connexion.</span><span class="sxs-lookup"><span data-stu-id="81725-187">The server retrieves system and usage data collected over the previous 4 hours to evaluate the load to collection ratio.</span></span>  
  
     <span data-ttu-id="81725-188">Recherche les mises à jour du fichier de gestion Dashboard.xlsx PowerPivot (la valeur par défaut est 5 jours)</span><span class="sxs-lookup"><span data-stu-id="81725-188">Check for Updates to PowerPivot Management Dashboard.xlsx (default is 5 days)</span></span>  
     <span data-ttu-id="81725-189">Le fichier de la gestion Dashboard.xlsx PowerPivot est une source de données utilisée par les rapports du Tableau de bord de gestion PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="81725-189">The PowerPivot Management Dashboard.xlsx file is a data source used by reports in PowerPivot Management Dashboard.</span></span> <span data-ttu-id="81725-190">Dans une configuration de serveur par défaut, le fichier .xlsx est actualisé quotidiennement, à l'aide des données d'utilisation collectées par SharePoint et le service système PowerPivot.</span><span class="sxs-lookup"><span data-stu-id="81725-190">In a default server configuration, the .xlsx file is refreshed daily, using usage data collected by SharePoint and the PowerPivot System Service.</span></span> <span data-ttu-id="81725-191">Si le fichier n'est pas mis à jour, une règle d'intégrité le signale comme un problème.</span><span class="sxs-lookup"><span data-stu-id="81725-191">In event the file is not updated, a health rule reports it as a problem.</span></span> <span data-ttu-id="81725-192">Par défaut, la règle est déclenchée si l'horodateur du fichier n'a pas changé pendant 5 jours.</span><span class="sxs-lookup"><span data-stu-id="81725-192">By default, the rule is triggered if the timestamp of the file has not changed for 5 days.</span></span>  
  
     <span data-ttu-id="81725-193">Pour plus d’informations sur la collecte des données d’utilisation, consultez [configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span><span class="sxs-lookup"><span data-stu-id="81725-193">For more information about usage data collection, see [Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).</span></span>  
  
     <span data-ttu-id="81725-194">Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : les données d'utilisation ne sont pas mises à jour à la fréquence prévue.**</span><span class="sxs-lookup"><span data-stu-id="81725-194">This configuration setting corresponds to the following rule definition on the **Review problems and solutions** page: **PowerPivot: Usage data is not getting updated at the expected frequency.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81725-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81725-195">See Also</span></span>  
 <span data-ttu-id="81725-196">[Configurer l’utilisation de l’espace disque &#40;PowerPivot pour SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="81725-196">[Configure Disk Space Usage &#40;PowerPivot for SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="81725-197">Tableau de bord de gestion PowerPivot et données d’utilisation</span><span class="sxs-lookup"><span data-stu-id="81725-197">PowerPivot Management Dashboard and Usage Data</span></span>](power-pivot-management-dashboard-and-usage-data.md)  