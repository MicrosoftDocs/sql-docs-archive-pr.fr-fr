---
title: Informations de référence sur l’API d’instance de base de données locale | SQL Server Express Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5934bc5159998db22d7c560b31457524773e74eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695611"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a><span data-ttu-id="b0a31-102">Guide de référence de l'API d'instance SQL Server Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="b0a31-102">SQL Server Express LocalDB Instance API Reference</span></span>
  <span data-ttu-id="b0a31-103">Dans le monde traditionnel SQL Server basé sur les services, différentes instances de SQL Server installées sur un même ordinateur sont physiquement séparées ; autrement dit, chaque instance doit être installée et supprimée séparément, possède un jeu distinct de binaires, et s'exécute sous un processus de service distinct.</span><span class="sxs-lookup"><span data-stu-id="b0a31-103">In the traditional, service-based SQL Server world, individual SQL Server instances installed on a single computer are physically separated; that is, each instance must be installed and removed separately, has a separate set of binaries, and runs under a separate service process.</span></span> <span data-ttu-id="b0a31-104">Le nom de l'instance SQL Server est utilisé pour spécifier l'instance SQL Server à laquelle l'utilisateur souhaite se connecter.</span><span class="sxs-lookup"><span data-stu-id="b0a31-104">The SQL Server instance name is used to specify which SQL Server instance the user wants to connect to.</span></span>  
  
 <span data-ttu-id="b0a31-105">L’API SQL Server Express de l’instance de base de données locale utilise un modèle d’instance simplifié et « clair ».</span><span class="sxs-lookup"><span data-stu-id="b0a31-105">The SQL Server Express LocalDB instance API uses a simplified, "light" instance model.</span></span> <span data-ttu-id="b0a31-106">Bien que les instances LocalDB individuelles soient séparées sur le disque et dans le Registre, elles utilisent le même jeu de binaires LocalDB partagés.</span><span class="sxs-lookup"><span data-stu-id="b0a31-106">Although individual LocalDB instances are separated on the disk and in the registry, they use the same set of shared LocalDB binaries.</span></span> <span data-ttu-id="b0a31-107">De plus, LocalDB n'utilise pas de services ; les instances de LocalDB sont lancées sur demande par des appels d'API d'instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-107">Moreover, LocalDB does not use services; LocalDB instances are launched on demand through LocalDB instance API calls.</span></span> <span data-ttu-id="b0a31-108">Dans LocalDB, le nom de l'instance est utilisé pour spécifier les instances de LocalDB avec lesquelles l'utilisateur souhaite travailler.</span><span class="sxs-lookup"><span data-stu-id="b0a31-108">In LocalDB, the instance name is used to specify which of the LocalDB instances the user wants to work with.</span></span>  
  
 <span data-ttu-id="b0a31-109">Une instance de base de données locale est toujours la propriété d’un seul utilisateur et est visible et accessible uniquement à partir du contexte de cet utilisateur, sauf si le partage d’instance est activé.</span><span class="sxs-lookup"><span data-stu-id="b0a31-109">A LocalDB instance is always owned by a single user and is visible and accessible only from this user's context, unless instance sharing is enabled.</span></span>  
  
 <span data-ttu-id="b0a31-110">Bien que techniquement les instances de LocalDB ne soient pas les mêmes que les instances SQL Server traditionnelles, leur utilisation est similaire.</span><span class="sxs-lookup"><span data-stu-id="b0a31-110">Although technically LocalDB instances are not the same as traditional SQL Server instances, their intended use is similar.</span></span> <span data-ttu-id="b0a31-111">Elles sont appelées *instances* pour insister sur cette similarité et les rendre plus intuitives pour SQL Server les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="b0a31-111">They are called *instances* to emphasize this similarity and to make them more intuitive to SQL Server users.</span></span>  
  
 <span data-ttu-id="b0a31-112">LocalDB prend en charge deux types d'instances : les instances automatiques (AI) et les instances nommées (NI).</span><span class="sxs-lookup"><span data-stu-id="b0a31-112">LocalDB supports two kinds of instances: automatic instances (AI) and named instances (NI).</span></span> <span data-ttu-id="b0a31-113">L'identificateur d'une instance de LocalDB est le nom de l'instance.</span><span class="sxs-lookup"><span data-stu-id="b0a31-113">The identifier for a LocalDB instance is the instance name.</span></span>  
  
## <a name="automatic-localdb-instances"></a><span data-ttu-id="b0a31-114">Instances automatiques de LocalDB</span><span class="sxs-lookup"><span data-stu-id="b0a31-114">Automatic LocalDB Instances</span></span>  
 <span data-ttu-id="b0a31-115">Les instances de base de données locale automatiques sont « publiques ». elles sont créées et gérées automatiquement pour l’utilisateur et peuvent être utilisées par n’importe quelle application.</span><span class="sxs-lookup"><span data-stu-id="b0a31-115">Automatic LocalDB instances are "public"; they are created and managed automatically for the user and can be used by any application.</span></span> <span data-ttu-id="b0a31-116">Une instance de base de données locale automatique existe pour chaque version de base de données locale installée sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-116">One automatic LocalDB instance exists for every version of LocalDB that is installed on the user's computer.</span></span>  
  
 <span data-ttu-id="b0a31-117">Les instances automatiques de LocalDB fournissent la gestion transparente d'instances.</span><span class="sxs-lookup"><span data-stu-id="b0a31-117">Automatic LocalDB instances provide seamless instance management.</span></span> <span data-ttu-id="b0a31-118">L'utilisateur n'a pas besoin de créer l'instance.</span><span class="sxs-lookup"><span data-stu-id="b0a31-118">The user does not need to create the instance.</span></span> <span data-ttu-id="b0a31-119">Cela permet aux utilisateurs d'installer facilement des applications et de migrer vers d'autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b0a31-119">This enables users to easily install applications and to migrate to different computers.</span></span> <span data-ttu-id="b0a31-120">Si la version spécifiée de LocalDB est installée sur l'ordinateur, l'instance automatique de LocalDB pour cette version est également disponible sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-120">If the target computer has the specified version of LocalDB installed, the automatic LocalDB instance for that version is also available on that computer.</span></span>  
  
### <a name="automatic-instance-management"></a><span data-ttu-id="b0a31-121">Gestion automatique d'instances</span><span class="sxs-lookup"><span data-stu-id="b0a31-121">Automatic Instance Management</span></span>  
 <span data-ttu-id="b0a31-122">Un utilisateur n'a pas besoin de créer une instance automatique de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-122">A user does not need to create an automatic LocalDB instance.</span></span> <span data-ttu-id="b0a31-123">L’instance est créée de manière différée la première fois que l’instance est utilisée, à condition que la version spécifiée de la base de données locale soit disponible sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-123">The instance is lazily created the first time the instance is used, provided that the specified version of LocalDB is available on the user's computer.</span></span> <span data-ttu-id="b0a31-124">Du point de vue de l’utilisateur, l’instance automatique est toujours présente si les binaires de base de données locale sont présents.</span><span class="sxs-lookup"><span data-stu-id="b0a31-124">From the user's point of view, the automatic instance is always present if the LocalDB binaries are present.</span></span>  
  
 <span data-ttu-id="b0a31-125">D'autres opérations de gestion d'instances, telles que la suppression, le partage et l'annulation du partage, s'exécutent également pour les instances automatiques.</span><span class="sxs-lookup"><span data-stu-id="b0a31-125">Other instance management operations, such as Delete, Share, and Unshare, also work for automatic instances.</span></span> <span data-ttu-id="b0a31-126">En particulier, la suppression d'une instance automatique réinitialise efficacement l'instance, qui sera recréée lors de l'opération suivante de démarrage.</span><span class="sxs-lookup"><span data-stu-id="b0a31-126">In particular, deleting an automatic instance effectively resets the instance, which will be re-created on the next Start operation.</span></span> <span data-ttu-id="b0a31-127">La suppression d'une instance automatique peut être requise si les bases de données système sont endommagées.</span><span class="sxs-lookup"><span data-stu-id="b0a31-127">Deleting an automatic instance may be required if the system databases become corrupted.</span></span>  
  
### <a name="automatic-instance-naming-rules"></a><span data-ttu-id="b0a31-128">Règles de dénomination d'instance automatique</span><span class="sxs-lookup"><span data-stu-id="b0a31-128">Automatic Instance Naming Rules</span></span>  
 <span data-ttu-id="b0a31-129">Les instances automatiques de LocalDB ont un modèle particulier pour le nom de l'instance qui appartient à un espace de noms réservé.</span><span class="sxs-lookup"><span data-stu-id="b0a31-129">Automatic LocalDB instances have a special pattern for the instance name that belongs to a reserved namespace.</span></span> <span data-ttu-id="b0a31-130">Cela est nécessaire pour éviter des conflits de noms avec les instances nommées de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-130">This is necessary to prevent name conflicts with named LocalDB instances.</span></span>  
  
 <span data-ttu-id="b0a31-131">Le nom d’instance automatique est le numéro de version de la ligne de base de la base de données locale précédé d’un seul caractère « v ».</span><span class="sxs-lookup"><span data-stu-id="b0a31-131">The automatic instance name is the LocalDB baseline release version number preceded by a single "v" character.</span></span> <span data-ttu-id="b0a31-132">Cela ressemble à « v » plus deux nombres avec un point entre eux ; par exemple, v 11.0 ou V 12,00.</span><span class="sxs-lookup"><span data-stu-id="b0a31-132">This looks like "v" plus two numbers with a period between them; for example, v11.0 or V12.00.</span></span>  
  
 <span data-ttu-id="b0a31-133">Voici des exemples de noms d'instance automatique non conformes :</span><span class="sxs-lookup"><span data-stu-id="b0a31-133">Examples of illegal automatic instance names are:</span></span>  
  
-   <span data-ttu-id="b0a31-134">11,0 (absence du caractère « v » au début)</span><span class="sxs-lookup"><span data-stu-id="b0a31-134">11.0 (missing the "v" character at the beginning)</span></span>  
  
-   <span data-ttu-id="b0a31-135">v11 (il manque un point et le second numéro de version)</span><span class="sxs-lookup"><span data-stu-id="b0a31-135">v11 (missing a period and the second number of the version)</span></span>  
  
-   <span data-ttu-id="b0a31-136">v11.</span><span class="sxs-lookup"><span data-stu-id="b0a31-136">v11.</span></span> <span data-ttu-id="b0a31-137">(il manque le deuxième numéro de version)</span><span class="sxs-lookup"><span data-stu-id="b0a31-137">(missing the second number of the version)</span></span>  
  
-   <span data-ttu-id="b0a31-138">v 11.0.1.2 (le numéro de version a plus de deux parties)</span><span class="sxs-lookup"><span data-stu-id="b0a31-138">v11.0.1.2 (version number has more than two parts)</span></span>  
  
## <a name="named-localdb-instances"></a><span data-ttu-id="b0a31-139">Instances nommées de LocalDB</span><span class="sxs-lookup"><span data-stu-id="b0a31-139">Named LocalDB Instances</span></span>  
 <span data-ttu-id="b0a31-140">Les instances de base de données locale nommées sont « privées ». une instance appartient à une seule application chargée de créer et de gérer l’instance.</span><span class="sxs-lookup"><span data-stu-id="b0a31-140">Named LocalDB instances are "private"; an instance is owned by a single application that is responsible for creating and managing the instance.</span></span> <span data-ttu-id="b0a31-141">Les instances nommées de LocalDB fournissent l'isolement et améliorent les performances.</span><span class="sxs-lookup"><span data-stu-id="b0a31-141">Named LocalDB instances provide isolation and improve performance.</span></span>  
  
### <a name="named-instance-creation"></a><span data-ttu-id="b0a31-142">Création d'instance nommée</span><span class="sxs-lookup"><span data-stu-id="b0a31-142">Named Instance Creation</span></span>  
 <span data-ttu-id="b0a31-143">L'utilisateur doit créer des instances nommées explicitement via l'API de gestion de LocalDB, ou implicitement à l'aide du fichier app.config pour une application managée.</span><span class="sxs-lookup"><span data-stu-id="b0a31-143">The user must create named instances explicitly through the LocalDB management API, or implicitly through the app.config file for a managed application.</span></span> <span data-ttu-id="b0a31-144">Une application managée peut également utiliser l'API.</span><span class="sxs-lookup"><span data-stu-id="b0a31-144">A managed application may also use the API.</span></span>  
  
 <span data-ttu-id="b0a31-145">Chaque instance nommée possède une version associée de LocalDB ; autrement dit, elle indique un jeu de binaires de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-145">Each named instance has an associated LocalDB version; that is, it points to a specified set of LocalDB binaries.</span></span> <span data-ttu-id="b0a31-146">La version de l'instance nommée est définie pendant le processus de création de l'instance.</span><span class="sxs-lookup"><span data-stu-id="b0a31-146">The version for the named instance is set during the instance creation process.</span></span>  
  
### <a name="named-instance-naming-rules"></a><span data-ttu-id="b0a31-147">Règles de dénomination d'instance nommée</span><span class="sxs-lookup"><span data-stu-id="b0a31-147">Named Instance Naming Rules</span></span>  
 <span data-ttu-id="b0a31-148">Un nom d'instance de LocalDB peut comporter au plus 128 caractères (la limite est imposée par le type de données `sysname`).</span><span class="sxs-lookup"><span data-stu-id="b0a31-148">A LocalDB instance name can have up to a total of 128 characters (the limit is imposed by the `sysname` data type).</span></span> <span data-ttu-id="b0a31-149">Il s'agit d'une différence importante comparée aux noms d'instances SQL Server traditionnelles, qui sont limités aux noms NetBIOS de 16 caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="b0a31-149">This is a significant difference compared to traditional SQL Server instance names, which are limited to NetBIOS names of 16 ASCII characters.</span></span> <span data-ttu-id="b0a31-150">La raison de cette différence est que la base de données locale traite les bases de données en tant que fichiers et implique donc la sémantique basée sur les fichiers. il est donc intuitif pour les utilisateurs d’avoir plus de liberté dans le choix des noms d’instance.</span><span class="sxs-lookup"><span data-stu-id="b0a31-150">The reason for this difference is that LocalDB treats databases as files, and therefore implies file-based semantics, so it's intuitive for users to have more freedom in choosing instance names.</span></span>  
  
 <span data-ttu-id="b0a31-151">Un nom d'instance de LocalDB peut contenir tous les caractères Unicode qui sont valides dans le composant nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="b0a31-151">A LocalDB instance name can contain any Unicode characters that are legal within the filename component.</span></span> <span data-ttu-id="b0a31-152">Les caractères non conformes dans un composant filename sont généralement les suivants : caractères ASCII/Unicode 1 à 31, guillemets ("), inférieur à ( \<), greater than (> ), canal (|), retour arrière (\b), tabulation (\t), deux-points ( :), astérisque (\*), point d’interrogation ( ?), barre oblique inverse ( \\ ) et barre oblique (/).</span><span class="sxs-lookup"><span data-stu-id="b0a31-152">Illegal characters in a filename component generally include the following characters: ASCII/Unicode characters 1 through 31, as well as quote ("), less than (\<), greater than (>), pipe (|), backspace (\b), tab (\t), colon (:), asterisk (\*), question mark (?), backslash (\\), and forward slash (/).</span></span> <span data-ttu-id="b0a31-153">Notez que le caractère Null (\0) est autorisé, car il est utilisé pour la fin de chaîne ; tout caractère qui se trouve après le premier caractère NULL est ignoré.</span><span class="sxs-lookup"><span data-stu-id="b0a31-153">Note that the null character (\0) is allowed because it is used for string termination; everything after the first null character will be ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0a31-154">La liste de caractères non conformes peut dépendre du système d'exploitation et peut changer dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b0a31-154">The list of illegal characters may depend on the operating system and may change in future releases.</span></span>  
  
 <span data-ttu-id="b0a31-155">Les espaces de début et de fin dans les noms d'instances sont ignorés et seront supprimés.</span><span class="sxs-lookup"><span data-stu-id="b0a31-155">Leading and trailing white spaces in instance names are ignored and will be trimmed.</span></span>  
  
 <span data-ttu-id="b0a31-156">Pour éviter les conflits de noms, les instances de base de données locale nommées ne peuvent pas avoir un nom qui suit le modèle d’affectation de noms pour les instances automatiques, comme décrit précédemment dans « règles d’affectation automatique des noms d’instance ».</span><span class="sxs-lookup"><span data-stu-id="b0a31-156">To avoid naming conflicts, named LocalDB instances cannot have a name that follows the naming pattern for automatic instances, as described earlier in "Automatic Instance Naming Rules."</span></span> <span data-ttu-id="b0a31-157">Une tentative de création d’une instance nommée avec un nom qui suit le modèle d’affectation de noms d’instance automatique crée effectivement une instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="b0a31-157">An attempt to create a named instance with a name that follows the automatic instance naming pattern effectively creates a default instance.</span></span>  
  
## <a name="sql-server-express-localdb-reference-topics"></a><span data-ttu-id="b0a31-158">Rubriques de référence SQL Server Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="b0a31-158">SQL Server Express LocalDB Reference Topics</span></span>  
 [<span data-ttu-id="b0a31-159">En-tête et informations de version SQL Server Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="b0a31-159">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
 <span data-ttu-id="b0a31-160">Fournit des informations sur le fichier d'en-tête et les clés de Registre pour rechercher l'API d'instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-160">Provides header file information and registry keys for finding the LocalDB instance API.</span></span>  
  
 [<span data-ttu-id="b0a31-161">Outil de gestion en ligne de commande : SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="b0a31-161">Command-Line Management Tool: SqlLocalDB.exe</span></span>](command-line-management-tool-sqllocaldb-exe.md)  
 <span data-ttu-id="b0a31-162">Décrit SqlLocalDB.exe, un outil de gestion des instances de LocalDB à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b0a31-162">Describes SqlLocalDB.exe, a tool for managing LocalDB instances from the command line.</span></span>  
  
 [<span data-ttu-id="b0a31-163">Fonction LocalDBCreateInstance</span><span class="sxs-lookup"><span data-stu-id="b0a31-163">LocalDBCreateInstance Function</span></span>](localdbcreateinstance-function.md)  
 <span data-ttu-id="b0a31-164">Décrit la fonction pour créer une nouvelle instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-164">Describes the function to create a new LocalDB instance.</span></span>  
  
 [<span data-ttu-id="b0a31-165">Fonction LocalDBDeleteInstance</span><span class="sxs-lookup"><span data-stu-id="b0a31-165">LocalDBDeleteInstance Function</span></span>](localdbdeleteinstance-function.md)  
 <span data-ttu-id="b0a31-166">Décrit la fonction pour supprimer une instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-166">Describes the function to remove a LocalDB instance.</span></span>  
  
 [<span data-ttu-id="b0a31-167">Fonction LocalDBFormatMessage</span><span class="sxs-lookup"><span data-stu-id="b0a31-167">LocalDBFormatMessage Function</span></span>](localdbformatmessage-function.md)  
 <span data-ttu-id="b0a31-168">Décrit la fonction pour retourner la description localisée d'une erreur de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-168">Describes the function to return the localized description for a LocalDB error.</span></span>  
  
 [<span data-ttu-id="b0a31-169">Fonction LocalDBGetInstanceInfo</span><span class="sxs-lookup"><span data-stu-id="b0a31-169">LocalDBGetInstanceInfo Function</span></span>](localdbgetinstanceinfo-function.md)  
 <span data-ttu-id="b0a31-170">Décrit la fonction pour obtenir des informations sur une instance de LocalDB, entre autres si elle existe, les informations de version, si elle s'exécute, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b0a31-170">Describes the function to get information for a LocalDB instance, such as whether it exists, version information, whether it is running, and so on.</span></span>  
  
 [<span data-ttu-id="b0a31-171">Fonction LocalDBGetInstances</span><span class="sxs-lookup"><span data-stu-id="b0a31-171">LocalDBGetInstances Function</span></span>](localdbgetinstances-function.md)  
 <span data-ttu-id="b0a31-172">Décrit la fonction pour retourner toutes les instances de LocalDB avec une version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b0a31-172">Describes the function to return all the LocalDB instances with a specified version.</span></span>  
  
 [<span data-ttu-id="b0a31-173">Fonction LocalDBGetVersionInfo</span><span class="sxs-lookup"><span data-stu-id="b0a31-173">LocalDBGetVersionInfo Function</span></span>](localdbgetversioninfo-function.md)  
 <span data-ttu-id="b0a31-174">Décrit la fonction pour retourner des informations sur une version spécifiée de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-174">Describes the function to return information for a specified LocalDB version.</span></span>  
  
 [<span data-ttu-id="b0a31-175">Fonction LocalDBGetVersions</span><span class="sxs-lookup"><span data-stu-id="b0a31-175">LocalDBGetVersions Function</span></span>](localdbgetversions-function.md)  
 <span data-ttu-id="b0a31-176">Décrit la fonction pour retourner toutes les versions de LocalDB disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-176">Describes the function to return all LocalDB versions available on a computer.</span></span>  
  
 [<span data-ttu-id="b0a31-177">Fonction LocalDBShareInstance</span><span class="sxs-lookup"><span data-stu-id="b0a31-177">LocalDBShareInstance Function</span></span>](localdbshareinstance-function.md)  
 <span data-ttu-id="b0a31-178">Décrit la fonction pour partager une instance spécifiée de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-178">Describes the function to share a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="b0a31-179">Fonction LocalDBStartInstance</span><span class="sxs-lookup"><span data-stu-id="b0a31-179">LocalDBStartInstance Function</span></span>](localdbstartinstance-function.md)  
 <span data-ttu-id="b0a31-180">Décrit la fonction pour démarrer une instance spécifiée de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-180">Describes the function to start a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="b0a31-181">Fonction LocalDBStartTracing</span><span class="sxs-lookup"><span data-stu-id="b0a31-181">LocalDBStartTracing Function</span></span>](localdbstarttracing-function.md)  
 <span data-ttu-id="b0a31-182">Décrit la fonction pour activer le suivi d'API pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-182">Describes the function to enable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="b0a31-183">Fonction LocalDBStopInstance</span><span class="sxs-lookup"><span data-stu-id="b0a31-183">LocalDBStopInstance Function</span></span>](localdbstopinstance-function.md)  
 <span data-ttu-id="b0a31-184">Décrit la fonction pour cesser l'exécution d'une instance spécifiée de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-184">Describes the function to stop a specified LocalDB instance from running.</span></span>  
  
 [<span data-ttu-id="b0a31-185">Fonction LocalDBStopTracing</span><span class="sxs-lookup"><span data-stu-id="b0a31-185">LocalDBStopTracing Function</span></span>](localdbstoptracing-function.md)  
 <span data-ttu-id="b0a31-186">Décrit la fonction pour désactiver le suivi d'API pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0a31-186">Describes the function to disable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="b0a31-187">LocalDBUnshareInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="b0a31-187">LocalDBUnshareInstance Function</span></span>](localdbunshareinstance-function.md)  
 <span data-ttu-id="b0a31-188">Décrit la fonction pour cesser le partage d'une instance spécifiée de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b0a31-188">Describes the function to stop sharing a specified LocalDB instance.</span></span>  
  
  