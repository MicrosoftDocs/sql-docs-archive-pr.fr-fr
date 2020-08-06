---
title: Collecte de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 0cc1f95c-5815-4d78-8868-a900be15e674
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6efa08a0cd9a92690ceac212b005f1f5607d4e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602161"
---
# <a name="data-collection"></a><span data-ttu-id="9fa0a-102">Collecte de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-102">Data Collection</span></span>
  <span data-ttu-id="9fa0a-103">Le collecteur de données est un composant de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] qui recueille différents jeux de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-103">The Data Collector is a component of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that collects different sets of data.</span></span> <span data-ttu-id="9fa0a-104">La collecte de données peut s'exécuter de façon constante ou selon une planification définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-104">Data collection either runs constantly or on a user-defined schedule.</span></span> <span data-ttu-id="9fa0a-105">Le collecteur de données stocke les données recueillies dans une base de données relationnelle appelée entrepôt de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-105">The data collector stores the collected data in a relational database known as the management data warehouse.</span></span>

## <a name="benefits-of-data-collector"></a><span data-ttu-id="9fa0a-106">Avantages du collecteur de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-106">Benefits of Data Collector</span></span>
 <span data-ttu-id="9fa0a-107">Le collecteur de données est un composant majeur de la plateforme de collecte de données pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et les outils fournis par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa0a-107">The data collector is a core component of the data collection platform for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and the tools that are provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9fa0a-108">Le collecteur de données centralise la collecte de données sur vos serveurs et applications de base de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-108">The data collector provides one central point for data collection across your database servers and applications.</span></span> <span data-ttu-id="9fa0a-109">Ce point de collecte peut obtenir des données de diverses sources et n'est pas limité aux données de performance, contrairement à SQL Trace.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-109">This collection point can obtain data from a variety of sources and is not limited to performance data, unlike SQL Trace.</span></span>

 <span data-ttu-id="9fa0a-110">Le collecteur de données vous permet d'ajuster l'étendue de la collecte de données pour l'adapter à vos environnements de test et de production.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-110">The data collector enables you to adjust the scope of data collection to suit your test and production environments.</span></span> <span data-ttu-id="9fa0a-111">Le collecteur de données utilise également un entrepôt de données, une base de données relationnelle qui vous permet de gérer les données que vous collectez en définissant pour elles différentes périodes de rétention.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-111">The data collector also uses a data warehouse, a relational database that enables you to manage the data that you collect by setting different retention periods for your data.</span></span>

 <span data-ttu-id="9fa0a-112">Le collecteur de données prend en charge le paramétrage dynamique de la collecte de données et il est extensible via son API.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-112">The data collector supports dynamic tuning for data collection and is extensible through its API.</span></span> <span data-ttu-id="9fa0a-113">Pour plus d’informations, consultez [Programmation du collecteur de données](../../database-engine/dev-guide/data-collector-programming.md).</span><span class="sxs-lookup"><span data-stu-id="9fa0a-113">For more information, see [Data Collector Programming](../../database-engine/dev-guide/data-collector-programming.md).</span></span>

 <span data-ttu-id="9fa0a-114">L'illustration suivante montre l'intégration du collecteur de données dans la stratégie globale de la collecte et de la gestion de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa0a-114">The following illustration shows how the data collector fits in the overall strategy for data collection and data management in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>

 <span data-ttu-id="9fa0a-115">![Rôle du collecteur de données dans la Gestion des données](../../database-engine/media/datacollectorroleindatastrategy.gif "Rôle du collecteur de données dans la Gestion des données")</span><span class="sxs-lookup"><span data-stu-id="9fa0a-115">![The Data Collector's Role in Data Management](../../database-engine/media/datacollectorroleindatastrategy.gif "The Data Collector's Role in Data Management")</span></span>

## <a name="data-collector-concepts"></a><span data-ttu-id="9fa0a-116">Concepts du collecteur de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-116">Data Collector Concepts</span></span>
 <span data-ttu-id="9fa0a-117">Le collecteur de données est intégré à l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], et il utilise ces deux composants de manière intensive.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-117">The data collector is integrated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and uses both extensively.</span></span> <span data-ttu-id="9fa0a-118">Avant de vous servir du collecteur de données, vous devez donc comprendre certains concepts liés à chacun de ces composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9fa0a-118">Before you work with the data collector, you should therefore understand certain concepts related to each of these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>

 <span data-ttu-id="9fa0a-119">L’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet de planifier et d’exécuter des travaux de collecte.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is used to schedule and run collection jobs.</span></span> <span data-ttu-id="9fa0a-120">Vous devez maîtriser les concepts suivants :</span><span class="sxs-lookup"><span data-stu-id="9fa0a-120">You should understand the following concepts:</span></span>

-   <span data-ttu-id="9fa0a-121">Travail</span><span class="sxs-lookup"><span data-stu-id="9fa0a-121">Job</span></span>

-   <span data-ttu-id="9fa0a-122">Étape de travail</span><span class="sxs-lookup"><span data-stu-id="9fa0a-122">Job step</span></span>

-   <span data-ttu-id="9fa0a-123">Planification du travail</span><span class="sxs-lookup"><span data-stu-id="9fa0a-123">Job schedule</span></span>

-   <span data-ttu-id="9fa0a-124">Subsystem</span><span class="sxs-lookup"><span data-stu-id="9fa0a-124">Subsystem</span></span>

-   <span data-ttu-id="9fa0a-125">Comptes proxy</span><span class="sxs-lookup"><span data-stu-id="9fa0a-125">Proxy accounts</span></span>

 <span data-ttu-id="9fa0a-126">Pour plus d’informations, consultez [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md).</span><span class="sxs-lookup"><span data-stu-id="9fa0a-126">For more information, see [Automated Administration Tasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md).</span></span>

 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9fa0a-127">([!INCLUDE[ssIS](../../includes/ssis-md.md)]) permet d’exécuter des packages qui collectent des données provenant de fournisseurs de données individuels.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-127">([!INCLUDE[ssIS](../../includes/ssis-md.md)]) is used to execute packages that collect data from individual data providers.</span></span> <span data-ttu-id="9fa0a-128">Vous devez maîtriser les outils et les concepts [!INCLUDE[ssIS](../../includes/ssis-md.md)] suivants :</span><span class="sxs-lookup"><span data-stu-id="9fa0a-128">You should be familiar with the following [!INCLUDE[ssIS](../../includes/ssis-md.md)] tools and concepts:</span></span>

-   <span data-ttu-id="9fa0a-129">Package [!INCLUDE[ssIS](../../includes/ssis-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa0a-129">[!INCLUDE[ssIS](../../includes/ssis-md.md)] package</span></span>

-   <span data-ttu-id="9fa0a-130">Configuration de package [!INCLUDE[ssIS](../../includes/ssis-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa0a-130">[!INCLUDE[ssIS](../../includes/ssis-md.md)] package configuration</span></span>

 <span data-ttu-id="9fa0a-131">Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41;, packages](../../integration-services/integration-services-ssis-packages.md).</span><span class="sxs-lookup"><span data-stu-id="9fa0a-131">For more information, see [Integration Services &#40;SSIS&#41; Packages](../../integration-services/integration-services-ssis-packages.md).</span></span>

## <a name="data-collector-terminology"></a><span data-ttu-id="9fa0a-132">Terminologie relative au collecteur de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-132">Data Collector Terminology</span></span>
 <span data-ttu-id="9fa0a-133">Ciblez une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prend en charge la collecte de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-133">target An instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports Data Collection.</span></span> <span data-ttu-id="9fa0a-134">Pour plus d’informations sur les éditions prises en charge, consultez la section « simplicité de gestion » des [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span><span class="sxs-lookup"><span data-stu-id="9fa0a-134">For more information about supported editions, see the "Manageability" section of [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>

 <span data-ttu-id="9fa0a-135">Une *racine cible* définit une sous-arborescence dans la hiérarchie cible.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-135">A *target root* defines a subtree in the target hierarchy.</span></span> <span data-ttu-id="9fa0a-136">Un *jeu de cibles* désigne le groupe de cibles obtenu après l’application d’un filtre à une sous-arborescence définie par une racine cible.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-136">A *target set* is the group of targets that results from applying a filter to a subtree defined by a target root.</span></span> <span data-ttu-id="9fa0a-137">Une racine cible peut être une base de données, une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou une instance d'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-137">A target root can be a database, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or a computer instance.</span></span>

 <span data-ttu-id="9fa0a-138">type de cible : type de cible, qui a certaines caractéristiques et le comportement.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-138">target type The type of target, which has certain characteristics and behavior.</span></span> <span data-ttu-id="9fa0a-139">Par exemple, une cible d'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède des caractéristiques différentes d'une cible de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9fa0a-139">For example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance target has different characteristics than a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database target.</span></span>

 <span data-ttu-id="9fa0a-140">fournisseur de données : source de données connue, spécifique à un type de cible, qui fournit des données à un type de collecteur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-140">data provider A known data source, specific to a target type, that provides data to a collector type.</span></span>

 <span data-ttu-id="9fa0a-141">type de collecteur logique autour des [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages qui fournissent le mécanisme réel pour la collecte des données et leur téléchargement dans l’entrepôt de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-141">collector type A logical wrapper around the [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages that provide the actual mechanism for collecting data and uploading it to the management data warehouse.</span></span>

 <span data-ttu-id="9fa0a-142">élément de collecte instance d’un type de collecteur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-142">collection item An instance of a collector type.</span></span> <span data-ttu-id="9fa0a-143">Un élément de collecte est créé avec un jeu de propriétés d'entrée et une fréquence de collecte spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-143">A collection item is created with a specific set of input properties and a collection frequency.</span></span>

 <span data-ttu-id="9fa0a-144">jeu d’éléments de collecte groupe d’éléments de collecte.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-144">collection set A group of collection items.</span></span> <span data-ttu-id="9fa0a-145">Un jeu d'éléments de collection est une unité de collecte de données avec laquelle un utilisateur peut interagir par le biais de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-145">A collection set is a unit of data collection that a user can interact with through the user interface.</span></span>

 <span data-ttu-id="9fa0a-146">mode de collecte la manière dont les données sont collectées et stockées.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-146">collection mode The manner in which the data is collected and stored.</span></span> <span data-ttu-id="9fa0a-147">Le mode de collecte peut être avec mise en cache ou sans mise en cache.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-147">Collection mode can be cached or non-cached.</span></span> <span data-ttu-id="9fa0a-148">Le mode avec mise en cache prend en charge la collecte continue, alors que le mode sans mise en cache est destiné à une collecte à la demande ou à un instantané de collecte.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-148">Cached mode supports continuous collection, whereas non-cached mode is intended for on-demand collection or a collection snapshot.</span></span>

 <span data-ttu-id="9fa0a-149">entrepôt de données de gestion base de données relationnelle utilisée pour stocker les données collectées.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-149">management data warehouse A relational database used to store collected data.</span></span>

 <span data-ttu-id="9fa0a-150">L'illustration suivante montre les dépendances et les relations entre les différents composants du collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-150">The following illustration shows the dependencies and relationships between data collector components.</span></span>

 <span data-ttu-id="9fa0a-151">![Dépendances fonctionnelles du collecteur de données](../../database-engine/media/dc-functional-dependencies.gif "Dépendances fonctionnelles du collecteur de données")</span><span class="sxs-lookup"><span data-stu-id="9fa0a-151">![Data collector functional dependencies](../../database-engine/media/dc-functional-dependencies.gif "Data collector functional dependencies")</span></span>

 <span data-ttu-id="9fa0a-152">Tel qu'indiqué dans l'illustration, le fournisseur de données est externe au collecteur de données et, par définition, entretient une relation implicite avec la cible.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-152">As shown in the illustration, the data provider is external to the data collector and by definition has an implicit relationship with the target.</span></span> <span data-ttu-id="9fa0a-153">Le fournisseur de données est spécifique à une cible particulière (par exemple, un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tel que le moteur relationnel) et fournit des données telles que les vues système dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les compteurs de l'analyseur de performances et les fournisseurs WMI, qui peuvent être consommées par le collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-153">The data provider is specific to a particular target (for example, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service such as the relational engine) and provides data such as system views in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Performance Monitor counters, and WMI providers, that can be consumed by the data collector.</span></span>

 <span data-ttu-id="9fa0a-154">Le type de collecteur est spécifique à un type de cible, en fonction de l'association logique entre un fournisseur de données et un type de cible.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-154">The collector type is specific to a target type, based on the logical association of a data provider to a target type.</span></span> <span data-ttu-id="9fa0a-155">Le type de collecteur définit la manière dont les données sont collectées à partir d'un fournisseur de données spécifique (en utilisant des paramètres schématisés) et spécifie le schéma de stockage des données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-155">The collector type defines how data is collected from a specific data provider (by using schematized parameters) and specifies the data storage schema.</span></span> <span data-ttu-id="9fa0a-156">Le schéma de fournisseur de données et le schéma de stockage sont requis pour stocker les données collectées.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-156">The data provider schema and storage schema are required in order to store the data that is collected.</span></span> <span data-ttu-id="9fa0a-157">Le type de collecteur fournit également l'emplacement de l'entrepôt de données de gestion, qui peut résider sur l'ordinateur exécutant la collecte de données ou sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-157">The collector type also provides the location of the management data warehouse, which can reside on the computer running data collection or on a different computer.</span></span>

 <span data-ttu-id="9fa0a-158">Un élément de collecte, tel qu'indiqué dans l'illustration, est une instance d'un type de collecteur spécifique, paramétrable avec des paramètres d'entrée, tels que le schéma XML pour le type de collecteur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-158">A collection item, shown in the illustration, is an instance of a specific collector type, parameterized with input parameters, such as the XML schema for the collector type.</span></span> <span data-ttu-id="9fa0a-159">Tous les éléments de collecte doivent fonctionner sur la même racine cible ou sur une racine cible vide.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-159">All collection items must operate on the same target root or on an empty target root.</span></span> <span data-ttu-id="9fa0a-160">Cela permet au collecteur de données de combiner différents types de collecteurs à partir du système d'exploitation ou d'une racine cible spécifique, mais pas à partir d'autres racines cibles.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-160">This enables the data collector to combine collector types from the operating system or from a specific target root, but not from different target roots.</span></span>

 <span data-ttu-id="9fa0a-161">Un élément de collection possède une fréquence de collecte définie qui détermine la fréquence d'instantanés de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-161">A collection item has a collection frequency defined that determines how often snapshots of values are taken.</span></span> <span data-ttu-id="9fa0a-162">Bien qu'il s'agisse d'un bloc de construction pour un jeu d'éléments de collecte, un élément de collecte ne peut pas exister de manière autonome.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-162">Although it is a building block for a collection set, a collection item cannot exist on its own.</span></span>

 <span data-ttu-id="9fa0a-163">Les jeux d'éléments de collection sont définis et déployés sur une instance de serveur et peuvent être exécutés indépendamment les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-163">Collection sets are defined and deployed on a server instance and can be run independently of each other.</span></span> <span data-ttu-id="9fa0a-164">Chaque jeu d'éléments de collection peut être appliqué à une cible correspondant aux types de cibles de tous les types de collecteurs appartenant à un jeu d'éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-164">Each collection set can be applied to a target that matches the target types of all the collector types that are part of a collection set.</span></span> <span data-ttu-id="9fa0a-165">Le jeu d'éléments de collection est exécuté par un ou plusieurs travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et les données sont téléchargées dans l'entrepôt de données de gestion selon une planification prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-165">The collection set is run by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job or jobs, and data is uploaded to the management data warehouse on a predefined schedule.</span></span>

 <span data-ttu-id="9fa0a-166">Toutes les données recueillies par les différentes instances du jeu d'éléments de collection sont téléchargées dans l'entrepôt de données de gestion selon la même planification.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-166">All the data collected by different instances within the collection set is uploaded to the management data warehouse on the same schedule.</span></span> <span data-ttu-id="9fa0a-167">Cette planification est définie comme une planification partagée de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et peut être utilisée par plusieurs jeux d'éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-167">This schedule is defined as a shared [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule and can be used by more than one collection set.</span></span> <span data-ttu-id="9fa0a-168">Les jeux d'éléments de collection sont activés ou désactivés comme des entités uniques alors que les éléments de collection ne peuvent pas être activés ou désactivés individuellement.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-168">A collection set is turned on or turned off as a single entity; collection items cannot be turned on or turned off individually.</span></span>

 <span data-ttu-id="9fa0a-169">Lorsque vous créez ou mettez à jour un jeu d'éléments de collection, vous pouvez configurer le mode de collecte pour collecter des données et les télécharger vers l'entrepôt de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-169">When you create or update a collection set, you can configure the collection mode for collecting data and uploading it to the management data warehouse.</span></span> <span data-ttu-id="9fa0a-170">Le type de planification est déterminé par le type de collecte : avec mise en cache ou sans mise en cache.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-170">The type of scheduling is determined by the type of collection: cached or non-cached.</span></span> <span data-ttu-id="9fa0a-171">Si la collecte s'effectue avec mise en cache, la collecte et le téléchargement des données s'exécutent sur deux travaux distincts.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-171">If the collection is cached, data collection and upload each run on a separate job.</span></span> <span data-ttu-id="9fa0a-172">La collecte s'exécute selon une planification qui commence au démarrage de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et selon la fréquence spécifiée dans l'élément de collecte.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-172">Collection runs on a schedule that starts when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts and it runs on the frequency specified in the collection item.</span></span> <span data-ttu-id="9fa0a-173">Le téléchargement s'exécute en fonction de la planification spécifiée par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-173">Upload runs according to the schedule specified by the user.</span></span>

 <span data-ttu-id="9fa0a-174">Dans le cadre d'une collecte sans mise en cache, la collecte et le téléchargement des données s'exécutent sur un même travail, mais en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-174">Under non-cached collection, data collection and upload both run on a single job, but in two steps.</span></span> <span data-ttu-id="9fa0a-175">La collecte s'effectue au cours de la première étape et le téléchargement au cours de la deuxième.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-175">Step one is collection, step two is upload.</span></span> <span data-ttu-id="9fa0a-176">Une collecte à la demande ne requiert aucune planification.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-176">No schedule is required for on-demand collection.</span></span>

 <span data-ttu-id="9fa0a-177">Après l'activation d'un jeu d'éléments de collecte, la collecte de données peut démarrer, selon une planification ou à la demande.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-177">After a collection set is enabled, data collection can start, either according to a schedule or on demand.</span></span> <span data-ttu-id="9fa0a-178">Lorsque la collecte de données démarre, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un processus pour le collecteur de données, qui à son tour charge les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour le jeu d'éléments de collection.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-178">When data collection starts, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent spawns a process for the data collector, which in turn loads the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages for the collection set.</span></span> <span data-ttu-id="9fa0a-179">Les éléments de collection, qui représentent des types de collections, rassemblent des données à partir des fournisseurs de données appropriés sur les cibles spécifiées.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-179">The collection items, which represent collection types, gather data from the appropriate data providers on the specified targets.</span></span> <span data-ttu-id="9fa0a-180">Au terme du cycle de collecte, ces données sont téléchargées dans l'entrepôt de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-180">When the collection cycle ends, this data is uploaded to the management data warehouse.</span></span>

## <a name="data-collector-tasks"></a><span data-ttu-id="9fa0a-181">Tâches du collecteur de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-181">Data Collector Tasks</span></span>

|<span data-ttu-id="9fa0a-182">Description de la tâche</span><span class="sxs-lookup"><span data-stu-id="9fa0a-182">Task Description</span></span>|<span data-ttu-id="9fa0a-183">Rubrique</span><span class="sxs-lookup"><span data-stu-id="9fa0a-183">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="9fa0a-184">Explique comment gérer différents aspects de la collecte de données, tels que l'activation ou la désactivation de la collecte de données, la modification de la configuration d'un jeu d'éléments de collecte ou la consultation des données dans l'entrepôt de données de gestion.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-184">Describes how to manage different aspects of data collection, such as enabling or disabling data collection, changing a collection set configuration, or viewing data in the management data warehouse.</span></span>|[<span data-ttu-id="9fa0a-185">Gérer la collecte de données</span><span class="sxs-lookup"><span data-stu-id="9fa0a-185">Manage Data Collection</span></span>](manage-data-collection.md)|
|<span data-ttu-id="9fa0a-186">Explique comment utiliser ces rapports pour obtenir des informations afin de contrôler la capacité système et de résoudre les problèmes de performances système.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-186">Describes how to use reports to obtain information for monitoring system capacity and troubleshooting system performance.</span></span>|[<span data-ttu-id="9fa0a-187">Rapports de jeux d’éléments de collecte de données système</span><span class="sxs-lookup"><span data-stu-id="9fa0a-187">System Data Collection Set Reports</span></span>](system-data-collection-set-reports.md)|
|<span data-ttu-id="9fa0a-188">Explique comment utiliser l'entrepôt de données de gestion pour collecter des données d'un serveur qui est une cible de collecte de données.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-188">Describes how to use the Management Data Warehouse to collect data from a server that is a data collection target.</span></span>|[<span data-ttu-id="9fa0a-189">Entrepôt de données de gestion</span><span class="sxs-lookup"><span data-stu-id="9fa0a-189">Management Data Warehouse</span></span>](management-data-warehouse.md)|

