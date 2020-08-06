---
title: Correspondance de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fe66d098-bec3-4258-b42a-479ae460feb3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42fcb346e46229d28c62b256d328d6af4fc6cfec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602328"
---
# <a name="data-matching"></a><span data-ttu-id="e816f-102">Correspondance de données</span><span class="sxs-lookup"><span data-stu-id="e816f-102">Data Matching</span></span>
  <span data-ttu-id="e816f-103">Le processus de correspondance de données de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) permet de réduire la duplication de données et d'améliorer la précision de données dans une source de données.</span><span class="sxs-lookup"><span data-stu-id="e816f-103">The [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) data matching process enables you to reduce data duplication and improve data accuracy in a data source.</span></span> <span data-ttu-id="e816f-104">La correspondance analyse le degré de duplication dans tous les enregistrements d'une source de données unique, en retournant les probabilités pondérées d'une correspondance entre chaque ensemble d'enregistrements comparé.</span><span class="sxs-lookup"><span data-stu-id="e816f-104">Matching analyzes the degree of duplication in all records of a single data source, returning weighted probabilities of a match between each set of records compared.</span></span> <span data-ttu-id="e816f-105">Vous pouvez alors décider quels enregistrements sont des correspondances et entreprendre l'action appropriée sur les données sources.</span><span class="sxs-lookup"><span data-stu-id="e816f-105">You can then decide which records are matches and take the appropriate action on the source data.</span></span>

 <span data-ttu-id="e816f-106">Le processus de correspondance de DQS présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="e816f-106">The DQS matching process has the following benefits:</span></span>

-   <span data-ttu-id="e816f-107">La correspondance vous permet d'éliminer les différences entre des valeurs de données qui doivent être égales, en déterminant la valeur correcte et en réduisant les erreurs que des différences de données peuvent entraîner.</span><span class="sxs-lookup"><span data-stu-id="e816f-107">Matching enables you to eliminate differences between data values that should be equal, determining the correct value and reducing the errors that data differences can cause.</span></span> <span data-ttu-id="e816f-108">Par exemple, les noms et les adresses sont souvent les informations d'identification d'une source de données, en particulier les données client, mais les données peuvent devenir incorrectes et se détériorer dans le temps.</span><span class="sxs-lookup"><span data-stu-id="e816f-108">For example, names and addresses are often the identifying data for a data source, particularly customer data, but the data can become dirty and deteriorate over time.</span></span> <span data-ttu-id="e816f-109">L'exécution d'une correspondance pour identifier et corriger ces erreurs peut considérablement faciliter l'utilisation et la maintenance des données.</span><span class="sxs-lookup"><span data-stu-id="e816f-109">Performing matching to identify and correct these errors can make data use and maintenance much easier.</span></span>

-   <span data-ttu-id="e816f-110">La correspondance vous permet de garantir l'uniformité de valeurs qui sont équivalentes, mais qui ont été entrées dans un format ou un style différent.</span><span class="sxs-lookup"><span data-stu-id="e816f-110">Matching enables you to ensure that values that are equivalent, but were entered in a different format or style, are rendered uniform.</span></span>

-   <span data-ttu-id="e816f-111">La correspondance identifie les correspondances exactes et approximatives, vous permettant de supprimer les données en double lorsque vous la définissez.</span><span class="sxs-lookup"><span data-stu-id="e816f-111">Matching identifies exact and approximate matches, enabling you to remove duplicate data as you define it.</span></span> <span data-ttu-id="e816f-112">Vous définissez le point auquel une correspondance approximative est en fait une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-112">You define the point at which an approximate match is in fact a match.</span></span> <span data-ttu-id="e816f-113">Vous définissez les champs qui sont évalués pour la correspondance, et ceux qui ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="e816f-113">You define which fields are assessed for matching, and which are not.</span></span>

-   <span data-ttu-id="e816f-114">DQS vous permet de créer une stratégie de correspondance à l'aide d'un processus assisté par ordinateur, de la modifier de manière interactive en fonction des résultats de la correspondance, et de l'ajouter à une base de connaissances réutilisable.</span><span class="sxs-lookup"><span data-stu-id="e816f-114">DQS enables you to create a matching policy using a computer-assisted process, modify it interactively based upon matching results, and add it to a knowledge base that is reusable.</span></span>

-   <span data-ttu-id="e816f-115">Vous pouvez réindexer des données copiées de la source vers la table de mise en lots, ou ne pas les réindexer, en fonction de l'état de la stratégie de correspondance et des données sources.</span><span class="sxs-lookup"><span data-stu-id="e816f-115">You can re-index data copied from the source to the staging table, or not re-index, depending on the state of the matching policy and the source data.</span></span> <span data-ttu-id="e816f-116">Ne pas réindexer les données peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="e816f-116">Not re-indexing can improve performance.</span></span>

 <span data-ttu-id="e816f-117">Vous pouvez exécuter le processus de correspondance en combinaison avec d'autres processus de nettoyage des données pour améliorer la qualité globale des données.</span><span class="sxs-lookup"><span data-stu-id="e816f-117">You can perform the matching process in conjunction with other data cleansing processes to improve overall data quality.</span></span> <span data-ttu-id="e816f-118">Vous pouvez également effectuer une déduplication des données à l'aide de la fonctionnalités DQS intégrée à Master Data Services.</span><span class="sxs-lookup"><span data-stu-id="e816f-118">You can also perform data de-duplication using DQS functionality built into Master Data Services.</span></span> <span data-ttu-id="e816f-119">Pour plus d’informations, consultez [Master Data Services Overview](../master-data-services/master-data-services-overview-mds.md).</span><span class="sxs-lookup"><span data-stu-id="e816f-119">For more information, see [Master Data Services Overview](../master-data-services/master-data-services-overview-mds.md).</span></span>

 <span data-ttu-id="e816f-120">L'illustration suivante montre le processus de correspondance des données dans DQS :</span><span class="sxs-lookup"><span data-stu-id="e816f-120">The following illustration displays how data matching is done in DQS:</span></span>

 <span data-ttu-id="e816f-121">![Processus de mise en correspondance dans DQS](../../2014/data-quality-services/media/dqs-matchingprocess.gif "Processus de mise en correspondance dans DQS")</span><span class="sxs-lookup"><span data-stu-id="e816f-121">![Matching Process in DQS](../../2014/data-quality-services/media/dqs-matchingprocess.gif "Matching Process in DQS")</span></span>

##  <a name="how-to-perform-data-matching"></a><a name="How"></a> <span data-ttu-id="e816f-122">Comment effectuer une correspondance des données</span><span class="sxs-lookup"><span data-stu-id="e816f-122">How to Perform Data Matching</span></span>
 <span data-ttu-id="e816f-123">Comme avec d'autres processus de qualité des données dans DQS, vous effectuez une correspondance en créant une base de connaissances et en exécutant une activité de correspondance dans un projet de qualité des données en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="e816f-123">As with other data quality processes in DQS, you perform matching by building a knowledge base and executing a matching activity in a data quality project in the following steps:</span></span>

1.  <span data-ttu-id="e816f-124">Créez une stratégie de correspondance dans la base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="e816f-124">Create a matching policy in the knowledge base</span></span>

2.  <span data-ttu-id="e816f-125">Exécutez un processus de déduplication dans une activité de correspondance qui fait partie d'un projet de qualité des données.</span><span class="sxs-lookup"><span data-stu-id="e816f-125">Perform a de-duplication process in a matching activity that is part of a data quality project.</span></span>

###  <a name="building-a-matching-policy"></a><a name="Policy"></a> <span data-ttu-id="e816f-126">Création d'une stratégie de correspondance</span><span class="sxs-lookup"><span data-stu-id="e816f-126">Building a Matching Policy</span></span>
 <span data-ttu-id="e816f-127">Pour préparer la base de connaissances afin d'effectuer une correspondance, vous devez créer une stratégie de correspondance dans la base de connaissances pour définir la façon dont DQS affecte la probabilité de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-127">You prepare the knowledge base for performing matching by creating a matching policy in the knowledge base to define how DQS assigns matching probability.</span></span> <span data-ttu-id="e816f-128">Une stratégie de correspondance se compose d'une ou de plusieurs règles de correspondance qui identifient les domaines qui sont utilisés quand DQS évalue le degré de correspondance d'un enregistrement avec un autre, et spécifient le poids de chaque valeur de domaine dans l'estimation de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-128">A matching policy consists of one or more matching rules that identify which domains will be used when DQS assesses how well one record matches to another, and specify the weight that each domain value carries in the matching assessment.</span></span> <span data-ttu-id="e816f-129">Vous spécifiez dans la règle si des valeurs de domaine doivent être une correspondance exacte ou si elles peuvent juste être semblables, et avec quel degré de similarité.</span><span class="sxs-lookup"><span data-stu-id="e816f-129">You specify in the rule whether domain values have to be an exact match or can just be similar, and to what degree of similarity.</span></span> <span data-ttu-id="e816f-130">Vous pouvez également spécifier si une correspondance de domaine est requise.</span><span class="sxs-lookup"><span data-stu-id="e816f-130">You also specify whether a domain match is a prerequisite.</span></span>

 <span data-ttu-id="e816f-131">Dans l'Assistant de gestion des bases de connaissances, l'activité de stratégie de correspondance analyse des exemples de données en appliquant chaque règle de correspondance pour comparer deux enregistrements à la fois dans la plage des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e816f-131">The matching policy activity in the Knowledge Base Management wizard analyzes sample data by applying each matching rule to compare two records at a time throughout the range of records.</span></span> <span data-ttu-id="e816f-132">Les enregistrements dont les scores de correspondance sont supérieurs à un minimum spécifié sont regroupés dans des clusters dans les résultats de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-132">Records whose matching scores are greater than a specified minimum are grouped in clusters in the matching results.</span></span> <span data-ttu-id="e816f-133">Ces résultats de correspondance ne sont pas ajoutés à la base de connaissances ; vous les utilisez pour affiner les règles de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-133">These matching results are not added to the knowledge base; you use them to tune the matching rules.</span></span> <span data-ttu-id="e816f-134">La création d'une stratégie de correspondance peut être un processus itératif dans lequel vous modifiez des règles de correspondance basées sur les résultats de correspondance ou les statistiques de profilage.</span><span class="sxs-lookup"><span data-stu-id="e816f-134">Creating a matching policy can be an iterative process in which you modify matching rules based on the matching results or profiling statistics.</span></span>

 <span data-ttu-id="e816f-135">Vous pouvez spécifier, pour un domaine, que les chaînes de données seront normalisées lors du chargement de données de la source de données vers le domaine.</span><span class="sxs-lookup"><span data-stu-id="e816f-135">You can specify for a domain that data strings will be normalized when you load data from the data source into the domain.</span></span> <span data-ttu-id="e816f-136">Ce processus consiste à remplacer les caractères spéciaux par une valeur Null ou un espace, ce qui supprime souvent la différence entre deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="e816f-136">This process consists of replacing special characters with a null or a space, which often removes the difference between two strings.</span></span> <span data-ttu-id="e816f-137">Cela peut augmenter la précision de la correspondance, et peut souvent permettre à un résultat de correspondance de dépasser le seuil de correspondance minimal, alors qu'il ne passerait pas sans normalisation.</span><span class="sxs-lookup"><span data-stu-id="e816f-137">This can increase matching accuracy, and can often enable a matching result to surpass the minimum matching threshold, when without normalization it would not pass.</span></span>

> [!NOTE]
>  <span data-ttu-id="e816f-138">Des valeurs Null dans les champs de correspondance de deux enregistrements sont considérées comme une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-138">Null values in the corresponding fields of two records will be considered a match.</span></span>

 <span data-ttu-id="e816f-139">La stratégie de correspondance est exécutée sur les domaines mappés aux exemples de données.</span><span class="sxs-lookup"><span data-stu-id="e816f-139">The matching policy is run on domains mapped to the sample data.</span></span> <span data-ttu-id="e816f-140">Vous pouvez spécifier si les données sont, ou non, copiées de la source de données vers la table de mise en lots et réindexées lorsque vous exécutez la stratégie de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-140">You can specify whether data is copied from the data source into the staging table and re-indexed when you run the matching policy, or not.</span></span> <span data-ttu-id="e816f-141">Vous pouvez effectuer cette opération aussi bien lors de la création de la base de connaissances que lors de l'exécution du projet de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-141">You can do so both when building the knowledge base and when running the matching project.</span></span> <span data-ttu-id="e816f-142">Ne pas réindexer les données peut entraîner une amélioration des performances.</span><span class="sxs-lookup"><span data-stu-id="e816f-142">Not re-indexing could result in improved performance.</span></span> <span data-ttu-id="e816f-143">La réindexation n'est pas nécessaire si la condition suivante est remplie : la stratégie de correspondance n'a pas changé, et vous n'avez pas mis à jour la source de données, remappé la stratégie, sélectionné une nouvelle source de données ou mappé un ou plusieurs nouveaux domaines.</span><span class="sxs-lookup"><span data-stu-id="e816f-143">Re-indexing is not necessary if the following is true: the matching policy has not changed, and you have not updated the data source, remapped the policy, selected a new data source, or mapped one or more new domains.</span></span>

 <span data-ttu-id="e816f-144">Chaque règle de correspondance est enregistrée dans la base de connaissances lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="e816f-144">Each matching rule is saved in the knowledge base when it is created.</span></span> <span data-ttu-id="e816f-145">Toutefois, une base de connaissances peut être utilisée dans un projet de qualité des données uniquement lorsqu'elle est publiée.</span><span class="sxs-lookup"><span data-stu-id="e816f-145">However, a knowledge base is available for use in a data quality project only when it is published.</span></span> <span data-ttu-id="e816f-146">En outre, tant que la base de connaissances n'est pas publiée, les règles de correspondance qu'elle contient ne peuvent pas être modifiées par un utilisateur autre que celui qui l'a créée.</span><span class="sxs-lookup"><span data-stu-id="e816f-146">In addition, until the knowledge base is published, the matching rules in it cannot be changed by a user other than the person who created it.</span></span>

###  <a name="running-a-matching-project"></a><a name="Project"></a> <span data-ttu-id="e816f-147">Exécution d'un projet de correspondance</span><span class="sxs-lookup"><span data-stu-id="e816f-147">Running a Matching Project</span></span>
 <span data-ttu-id="e816f-148">DQS effectue la déduplication des données en comparant chaque ligne des données sources à chaque autre ligne, en utilisant la stratégie de correspondance définie dans la base de connaissances, et en générant une probabilité de correspondance des lignes.</span><span class="sxs-lookup"><span data-stu-id="e816f-148">DQS performs data de-duplication by comparing each row in the source data to every other row, using the matching policy defined in the knowledge base, and producing a probability that the rows are a match.</span></span> <span data-ttu-id="e816f-149">Cette opération s'effectue dans un projet de qualité des données avec le type Correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-149">This is done in a data quality project with a type of Matching.</span></span> <span data-ttu-id="e816f-150">La correspondance est l'une des principales étapes dans un projet de qualité des données.</span><span class="sxs-lookup"><span data-stu-id="e816f-150">Matching is one of the major steps in a data quality project.</span></span> <span data-ttu-id="e816f-151">Elle s'effectue mieux après un nettoyage des données, car les données à mettre en correspondance sont alors exemptes d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e816f-151">It is best performed after data cleansing, so that the data to be matched is free from error.</span></span> <span data-ttu-id="e816f-152">Avant d'exécuter un processus de correspondance, vous pouvez exporter les résultats du projet de nettoyage vers une table de données ou un fichier .csv, puis créer un projet de correspondance dans lequel vous mappez les résultats du nettoyage aux domaines qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="e816f-152">Before running a matching process, you can export the results of the cleansing project into a data table or .csv file, and then create a matching project in which you map the cleansing results to domains in the matching project.</span></span>

 <span data-ttu-id="e816f-153">Un projet de correspondance des données se compose d'un processus assisté par ordinateur et d'un processus interactif.</span><span class="sxs-lookup"><span data-stu-id="e816f-153">A data matching project consists of a computer-assisted process and an interactive process.</span></span> <span data-ttu-id="e816f-154">Le projet de correspondance applique les règles de correspondance de la stratégie de correspondance à la source de données à évaluer.</span><span class="sxs-lookup"><span data-stu-id="e816f-154">The matching project applies the matching rules in the matching policy to the data source to be assessed.</span></span> <span data-ttu-id="e816f-155">Ce processus évalue la probabilité que deux lignes soient des correspondances dans un score de correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-155">This process assesses the likelihood that any two rows are matches in a matching score.</span></span> <span data-ttu-id="e816f-156">Seuls les enregistrements ayant une probabilité de correspondance supérieure à une valeur définie par le gestionnaire de données dans la stratégie de correspondance sont considérés comme une correspondance.</span><span class="sxs-lookup"><span data-stu-id="e816f-156">Only those records with a probability of a match greater than a value set by the data steward in the matching policy will be considered a match.</span></span>

 <span data-ttu-id="e816f-157">Lorsque DQS exécute l'analyse de correspondance, il crée des clusters des enregistrements qu'il considère comme des correspondances.</span><span class="sxs-lookup"><span data-stu-id="e816f-157">When DQS performs the matching analysis, it creates clusters of records that DQS considers matches.</span></span> <span data-ttu-id="e816f-158">DQS identifie de façon aléatoire un des enregistrements de chaque cluster comme l'enregistrement pivot, ou principal.</span><span class="sxs-lookup"><span data-stu-id="e816f-158">DQS randomly identifies one of the records in each cluster as the pivot, or leading, record.</span></span> <span data-ttu-id="e816f-159">Le gestionnaire de données vérifie les résultats de correspondance, puis refuse tout enregistrement qui n'est pas une correspondance appropriée pour un cluster.</span><span class="sxs-lookup"><span data-stu-id="e816f-159">The data steward verifies the matching results, and rejects any record that is not an appropriate match for a cluster.</span></span> <span data-ttu-id="e816f-160">Le gestionnaire de données sélectionne ensuite une règle de survivance que DQS utilise pour déterminer l'enregistrement qui survivra au processus de correspondance et remplacer les enregistrements correspondants.</span><span class="sxs-lookup"><span data-stu-id="e816f-160">The data steward then selects a survivorship rule that DQS will use to determine the record that will survive the matching process and replace the matching records.</span></span> <span data-ttu-id="e816f-161">La règle de survivance peut être « Enregistrement pivot » (par défaut), « Enregistrement le plus complet et le plus long », « Enregistrement le plus complet » ou « Enregistrement le plus long ».</span><span class="sxs-lookup"><span data-stu-id="e816f-161">The survivorship rule can be "Pivot record" (the default), "most complete and longest record", "most complete record", or "longest record".</span></span> <span data-ttu-id="e816f-162">DQS détermine l'enregistrement survivant (principal) de chaque cluster en fonction de l'enregistrement se rapprochant le plus du ou des critères dans la règle de survivance.</span><span class="sxs-lookup"><span data-stu-id="e816f-162">DQS determines the survivor (leading) record in each cluster based upon which record most closely matches the criteria or criterion in the survivorship rule.</span></span> <span data-ttu-id="e816f-163">Si plusieurs enregistrements d'un cluster donné respectent à la règle de survivance, DQS sélectionne l'un de ces enregistrements de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="e816f-163">If multiple records in a given cluster comply with the survivorship rule, DQS selects one of those records randomly.</span></span> <span data-ttu-id="e816f-164">DQS vous donne la possibilité d’afficher les clusters qui ont des enregistrements en commun sous la forme d’un seul cluster en sélectionnant « Afficher les clusters qui ne se chevauchent pas ».</span><span class="sxs-lookup"><span data-stu-id="e816f-164">DQS gives you the choice of displaying clusters that have records in common as a single cluster by selecting "show non-overlapping clusters".</span></span> <span data-ttu-id="e816f-165">Vous devez exécuter le processus de correspondance pour afficher les résultats en fonction de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="e816f-165">You must execute the matching process in order to display the results according to this setting.</span></span>

 <span data-ttu-id="e816f-166">Vous pouvez exporter les résultats du processus de correspondance vers une table SQL Server ou vers un fichier .csv.</span><span class="sxs-lookup"><span data-stu-id="e816f-166">You can export the results of the matching process either to a SQL Server table or a .csv file.</span></span> <span data-ttu-id="e816f-167">Vous pouvez exporter les résultats de correspondance sous deux formes : soit les enregistrements à correspondance et les enregistrements sans correspondance, soit les enregistrements survivants qui incluent uniquement l'enregistrement survivant d'un cluster et les résultats sans correspondances.</span><span class="sxs-lookup"><span data-stu-id="e816f-167">You can export matching results in two forms: first, the matched records and the unmatched records, or second, survivorship records that include only the survivor record for a cluster and the unmatched results.</span></span> <span data-ttu-id="e816f-168">Dans les enregistrements survivants, si le même enregistrement est identifié en tant que survivant pour plusieurs clusters, cet enregistrement ne sera exporté qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="e816f-168">In the survivorship records, if the same record is identified as the survivor for multiple clusters, that record will only be exported once.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e816f-169">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e816f-169">In This Section</span></span>
 <span data-ttu-id="e816f-170">Vous pouvez effectuer les tâches suivantes liées à la correspondance dans DQS :</span><span class="sxs-lookup"><span data-stu-id="e816f-170">You can perform the following tasks related to matching in DQS:</span></span>

|||
|-|-|
|<span data-ttu-id="e816f-171">Créer et tester les règles de correspondance dans une stratégie de correspondance</span><span class="sxs-lookup"><span data-stu-id="e816f-171">Create and test matching rules in a matching policy</span></span>|[<span data-ttu-id="e816f-172">Créer une stratégie de correspondance</span><span class="sxs-lookup"><span data-stu-id="e816f-172">Create a Matching Policy</span></span>](../../2014/data-quality-services/create-a-matching-policy.md)|
|<span data-ttu-id="e816f-173">Exécuter une correspondance dans un projet de qualité des données</span><span class="sxs-lookup"><span data-stu-id="e816f-173">Run matching in a data quality project</span></span>|[<span data-ttu-id="e816f-174">Exécuter un projet de correspondance</span><span class="sxs-lookup"><span data-stu-id="e816f-174">Run a Matching Project</span></span>](../../2014/data-quality-services/run-a-matching-project.md)|

