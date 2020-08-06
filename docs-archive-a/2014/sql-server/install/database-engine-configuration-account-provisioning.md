---
title: Configuration de Moteur de base de données-approvisionnement de comptes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7885bdda72668ac96e90b0900772a4f56575d5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600498"
---
# <a name="database-engine-configuration---account-provisioning"></a><span data-ttu-id="feecb-102">Configuration du moteur de base de données – Mise en service de compte</span><span class="sxs-lookup"><span data-stu-id="feecb-102">Database Engine Configuration - Account Provisioning</span></span>
  <span data-ttu-id="feecb-103">Utilisez cette page pour définir le mode de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ajouter des utilisateurs Windows ou des groupes comme administrateurs du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-103">Use this page to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="considerations-for-running-sscurrent"></a><span data-ttu-id="feecb-104">Éléments à prendre en considération pour l'exécution de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feecb-104">Considerations for Running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="feecb-105">Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le groupe **BUILTIN\Administrators** était fourni en tant que compte de connexion du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et les membres du groupe Administrateurs local pouvaient se connecter en utilisant leurs informations d’identification d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="feecb-105">On previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BUILTIN\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and members of the local Administrators group could login using their Administrator credentials.</span></span> <span data-ttu-id="feecb-106">L'utilisation d'autorisations élevées n'est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="feecb-106">Using elevated permissions is not a best practice.</span></span> <span data-ttu-id="feecb-107">Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , le groupe **BUILTIN\Administrators** n’est pas fourni en tant que compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="feecb-107">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] the **BUILTIN\Administrators** group is not provisioned as a login.</span></span> <span data-ttu-id="feecb-108">Par conséquent, vous devez créer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque utilisateur administrateur et ajouter ce nom de connexion au rôle serveur fixe sysadmin lors de l'installation d'une nouvelle instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-108">As a result, you should create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="feecb-109">Vous devez procéder de même pour les comptes Windows utilisés pour exécuter les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="feecb-109">You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent jobs.</span></span> <span data-ttu-id="feecb-110">Ceux-ci incluent les travaux de l'agent de réplication.</span><span class="sxs-lookup"><span data-stu-id="feecb-110">These include replication agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="feecb-111">Options</span><span class="sxs-lookup"><span data-stu-id="feecb-111">Options</span></span>  
 <span data-ttu-id="feecb-112">**Mode de sécurité** - Sélectionnez l’authentification Windows ou l’authentification en mode mixte pour votre installation.</span><span class="sxs-lookup"><span data-stu-id="feecb-112">**Security Mode** - Select Windows Authentication or Mixed Mode Authentication for your installation.</span></span>  
  
 <span data-ttu-id="feecb-113">**Configuration du principal Windows** - Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le groupe local de Windows Builtin\Administrator a été placé dans le rôle serveur sysadmin de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en accordant aux administrateurs Windows l’accès à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-113">**Windows Principal Provisioning** - In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Windows Builtin\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="feecb-114">Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le groupe Builtin\Administrator n'est pas configuré dans le rôle serveur sysadmin.</span><span class="sxs-lookup"><span data-stu-id="feecb-114">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the Builtin\Administrator group is not provisioned in the sysadmin server role.</span></span> <span data-ttu-id="feecb-115">Au lieu de cela, vous devez configurer de manière explicite des administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les nouvelles installations lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="feecb-115">Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="feecb-116">Vous devez configurer de manière explicite des administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les nouvelles installations lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="feecb-116">You must explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span> <span data-ttu-id="feecb-117">L'installation ne vous permet pas de continuer tant que cette étape n'a pas été effectuée.</span><span class="sxs-lookup"><span data-stu-id="feecb-117">Setup will not allow you to continue until you complete this step.</span></span>  
  
 <span data-ttu-id="feecb-118">**Spécifier les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]administrateurs** - Vous devez spécifier au moins un principal Windows pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-118">**Specify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators** - You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="feecb-119">Pour ajouter le compte sous lequel le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute, cliquez sur le bouton **Utilisateur actuel**.</span><span class="sxs-lookup"><span data-stu-id="feecb-119">To add the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running, click the **Current User** button.</span></span> <span data-ttu-id="feecb-120">Pour ajouter ou supprimer des comptes dans la liste des administrateurs système, cliquez sur **Ajouter** ou sur **Supprimer**, puis modifiez la liste des utilisateurs, groupes ou ordinateurs qui disposeront des privilèges d'administrateur pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-120">To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="feecb-121">Lorsque vous avez terminé de modifier la liste, cliquez sur **OK**, puis vérifiez la liste des administrateurs dans la boîte de dialogue de configuration.</span><span class="sxs-lookup"><span data-stu-id="feecb-121">When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog.</span></span> <span data-ttu-id="feecb-122">Une fois la liste complète, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="feecb-122">When the list is complete, click **Next**.</span></span>  
  
 <span data-ttu-id="feecb-123">Si vous sélectionnez l'authentification de mode mixte, vous devez fournir les informations d'identification de session pour le compte de l'administrateur système (SA) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré.</span><span class="sxs-lookup"><span data-stu-id="feecb-123">If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (SA) account.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="feecb-124">**Mode d’authentification Windows**</span><span class="sxs-lookup"><span data-stu-id="feecb-124">**Windows Authentication Mode**</span></span>  
 <span data-ttu-id="feecb-125">Quand un utilisateur se connecte par le biais d'un compte d'utilisateur Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide le nom et le mot de passe du compte à l'aide du jeton du principal Windows du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="feecb-125">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="feecb-126">Il s'agit du mode d'authentification par défaut et il est plus fiable que le mode mixte.</span><span class="sxs-lookup"><span data-stu-id="feecb-126">This is the default authentication mode, and is much more secure than Mixed Mode.</span></span> <span data-ttu-id="feecb-127">L'authentification Windows utilise le protocole de sécurité Kerberos, met en œuvre les stratégies de mot de passe en termes de validation de la complexité des mots de passe forts et prend en charge le verrouillage des comptes et l'expiration des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="feecb-127">Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="feecb-128">Ne définissez jamais un mot de passe d'administrateur système (SA) vide ou faible.</span><span class="sxs-lookup"><span data-stu-id="feecb-128">Never set a blank or weak sa password.</span></span>  
  
 <span data-ttu-id="feecb-129">**Mode mixte (authentification Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification)**</span><span class="sxs-lookup"><span data-stu-id="feecb-129">**Mixed Mode (Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication)**</span></span>  
 <span data-ttu-id="feecb-130">Permet aux utilisateurs de se connecter en utilisant l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="feecb-130">Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="feecb-131">Les utilisateurs qui se connectent via un compte d'utilisateur Windows peuvent utiliser des connexions approuvées qui sont validées par Windows.</span><span class="sxs-lookup"><span data-stu-id="feecb-131">Users who connect through a Windows user account can use trusted connections that are validated by Windows.</span></span>  
  
 <span data-ttu-id="feecb-132">Si vous devez choisir l'authentification en mode mixte et utiliser des connexions SQL pour vous adapter à des applications héritées, définissez des mots de passe forts pour tous les comptes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-132">If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="feecb-133">L'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fournie uniquement dans un souci de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="feecb-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is provided for backward compatibility only.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="feecb-134">**Entrer le mot de passe**</span><span class="sxs-lookup"><span data-stu-id="feecb-134">**Enter Password**</span></span>  
 <span data-ttu-id="feecb-135">Entrez et confirmez la connexion d'administrateur système (sa).</span><span class="sxs-lookup"><span data-stu-id="feecb-135">Enter and confirm the system administrator (sa) login.</span></span> <span data-ttu-id="feecb-136">Les mots de passe constituant la première ligne de défense contre les intrus, le choix de mots de passe forts est essentiel à la sécurité de votre système.</span><span class="sxs-lookup"><span data-stu-id="feecb-136">Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="feecb-137">Ne définissez jamais un mot de passe sa vide ou faible.</span><span class="sxs-lookup"><span data-stu-id="feecb-137">Never set a blank or weak sa password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="feecb-138">Les mots de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent contenir de 1 à 128 caractères, constitués d’une combinaison quelconque de lettres, de symboles et de chiffres.</span><span class="sxs-lookup"><span data-stu-id="feecb-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers.</span></span> <span data-ttu-id="feecb-139">Si vous choisissez l'authentification en mode mixte, vous devez d'abord entrer un mot de passe sa fort avant de passer à la page suivante de l'Assistant Installation.</span><span class="sxs-lookup"><span data-stu-id="feecb-139">If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.</span></span>  
  
 <span data-ttu-id="feecb-140">**Instructions sur les mots de passe forts**</span><span class="sxs-lookup"><span data-stu-id="feecb-140">**Strong Password Guidelines**</span></span>  
 <span data-ttu-id="feecb-141">Les mots de passe forts ne peuvent pas être aisément devinés par une personne et ils ne sont pas aisément piratés par un programme informatique.</span><span class="sxs-lookup"><span data-stu-id="feecb-141">Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program.</span></span> <span data-ttu-id="feecb-142">Les mots de passe forts ne peuvent pas utiliser des conditions ou des termes interdits, notamment :</span><span class="sxs-lookup"><span data-stu-id="feecb-142">Strong passwords cannot use prohibited conditions or terms, including:</span></span>  
  
-   <span data-ttu-id="feecb-143">Une condition vide ou NULL</span><span class="sxs-lookup"><span data-stu-id="feecb-143">A blank or NULL condition</span></span>  
  
-   <span data-ttu-id="feecb-144">« Mot de passe »</span><span class="sxs-lookup"><span data-stu-id="feecb-144">"Password"</span></span>  
  
-   <span data-ttu-id="feecb-145">"Admin"</span><span class="sxs-lookup"><span data-stu-id="feecb-145">"Admin"</span></span>  
  
-   <span data-ttu-id="feecb-146">"Administrator"</span><span class="sxs-lookup"><span data-stu-id="feecb-146">"Administrator"</span></span>  
  
-   <span data-ttu-id="feecb-147">"sa"</span><span class="sxs-lookup"><span data-stu-id="feecb-147">"sa"</span></span>  
  
-   <span data-ttu-id="feecb-148">"sysadmin"</span><span class="sxs-lookup"><span data-stu-id="feecb-148">"sysadmin"</span></span>  
  
 <span data-ttu-id="feecb-149">Un mot de passe fort ne peut pas se composer des termes suivants associés à l'ordinateur d'installation :</span><span class="sxs-lookup"><span data-stu-id="feecb-149">A strong password cannot be the following terms associated with the installation computer:</span></span>  
  
-   <span data-ttu-id="feecb-150">Le nom de l'utilisateur qui a ouvert la session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="feecb-150">The name of the user currently logged onto the machine.</span></span>  
  
-   <span data-ttu-id="feecb-151">Nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="feecb-151">The computer name.</span></span>  
  
 <span data-ttu-id="feecb-152">Un mot de passe fort doit contenir plus de 8 caractères et satisfaire au moins trois des quatre critères suivants :</span><span class="sxs-lookup"><span data-stu-id="feecb-152">A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:</span></span>  
  
-   <span data-ttu-id="feecb-153">Il doit contenir des lettres majuscules.</span><span class="sxs-lookup"><span data-stu-id="feecb-153">It must contain uppercase letters.</span></span>  
  
-   <span data-ttu-id="feecb-154">Il doit contenir des lettres minuscules.</span><span class="sxs-lookup"><span data-stu-id="feecb-154">It must contain lowercase letters.</span></span>  
  
-   <span data-ttu-id="feecb-155">Il doit contenir des chiffres.</span><span class="sxs-lookup"><span data-stu-id="feecb-155">It must contain numbers.</span></span>  
  
-   <span data-ttu-id="feecb-156">Il doit contenir des caractères non alphanumériques, comme #, % ou ^.</span><span class="sxs-lookup"><span data-stu-id="feecb-156">It must contain non-alphanumeric characters; for example, #, %, or ^.</span></span>  
  
 <span data-ttu-id="feecb-157">Les mots de passe entrés sur cette page doivent répondre aux exigences des stratégies de mots de passe forts.</span><span class="sxs-lookup"><span data-stu-id="feecb-157">Passwords entered on this page must meet strong password policy requirements.</span></span> <span data-ttu-id="feecb-158">Si vous avez un processus automatisé qui utilise l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , assurez-vous que le mot de passe répond aux exigences des stratégies de mots de passe forts.</span><span class="sxs-lookup"><span data-stu-id="feecb-158">If you have any automation that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, ensure that the password meets strong password policy requirements.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="feecb-159">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="feecb-159">Related Content</span></span>  
 <span data-ttu-id="feecb-160">Pour plus d'informations sur le choix de l'authentification Windows ou de l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez la rubrique **Choisir un mode d’authentification** dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="feecb-160">For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="feecb-161">Pour plus d’informations sur le choix d’un compte pour l’exécution de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], consultez la rubrique **Configurer les comptes de service Windows et les autorisations** dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feecb-161">For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feecb-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feecb-162">See Also</span></span>  
 [<span data-ttu-id="feecb-163">Configurer les comptes de service Windows et les autorisations</span><span class="sxs-lookup"><span data-stu-id="feecb-163">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  