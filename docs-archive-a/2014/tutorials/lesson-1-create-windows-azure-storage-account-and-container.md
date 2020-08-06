---
title: 'Leçon 1 : créer un compte et un conteneur de stockage Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 07167c513d2c6ed3ae0f7b431461ee3915047636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601216"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a><span data-ttu-id="b221b-102">Leçon 1 : Créer un compte et un conteneur Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="b221b-102">Lesson 1: Create Azure Storage Account and Container</span></span>
  <span data-ttu-id="b221b-103">Avant de pouvoir commencer à stocker des SQL Server fichiers de données dans le stockage Azure, vous devez d’abord créer un compte de stockage Azure et un conteneur d’objets BLOB, ainsi qu’une signature d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="b221b-103">Before you can start storing SQL Server data files in Azure Storage, you must first create an Azure Storage account and a blob container, and a shared access signature.</span></span> <span data-ttu-id="b221b-104">La leçon 1 vous guide tout au long des étapes de connexion à Azure Portail de gestion, de création d’un compte de stockage, d’un conteneur d’objets BLOB et d’une signature d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="b221b-104">Lesson 1 walks you through the steps of logging into the Azure Management Portal, creating a storage account, a blob container, and a shared access signature.</span></span>  
  
 <span data-ttu-id="b221b-105">Par défaut, seul le propriétaire du compte de stockage peut accéder aux objets blob, aux tables et aux files d’attente dans ce compte.</span><span class="sxs-lookup"><span data-stu-id="b221b-105">By default, only the owner of the storage account may access blobs, tables, and queues within that account.</span></span> <span data-ttu-id="b221b-106">Pour accéder à ces ressources en utilisant cette nouvelle amélioration SQL Server sans partager la clé d'accès du compte de stockage, effectuez les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="b221b-106">To be able to access these resources using this new SQL Server enhancement without sharing the storage account access key, you are required to do these:</span></span>  
  
-   <span data-ttu-id="b221b-107">Définissez les autorisations du conteneur avec un accès privé.</span><span class="sxs-lookup"><span data-stu-id="b221b-107">Set the container's permissions to private.</span></span>  
  
-   <span data-ttu-id="b221b-108">Créez une signature d'accès partagé.</span><span class="sxs-lookup"><span data-stu-id="b221b-108">Create a shared access signature.</span></span> <span data-ttu-id="b221b-109">Elle vous permet de déléguer l'accès restreint à un conteneur, à un objet blob, à une table ou à une ressource de file d'attente en spécifiant l'intervalle pendant lequel les ressources sont disponibles et les autorisations dont disposera un client.</span><span class="sxs-lookup"><span data-stu-id="b221b-109">It enables you to delegate restricted access to a container, blob, table, or queue resource by specifying the interval for which the resources are available and the permissions that a client will have to it.</span></span>  
  
-   <span data-ttu-id="b221b-110">Utilisez une stratégie d'accès stockée pour gérer les signatures d'accès partagé d'un conteneur ou de ses objets blob.</span><span class="sxs-lookup"><span data-stu-id="b221b-110">Use a stored access policy to manage shared access signatures for a container or its blobs.</span></span> <span data-ttu-id="b221b-111">La stratégie d'accès stockée vous donne une mesure supplémentaire de contrôle de vos signatures d'accès partagé et fournit également un moyen simple de les révoquer.</span><span class="sxs-lookup"><span data-stu-id="b221b-111">The stored access policy gives you an additional measure of control over your shared access signatures and also provides a straightforward means to revoke them.</span></span>  
  
 <span data-ttu-id="b221b-112">Pour plus d’informations, consultez [gérer l’accès aux ressources de stockage Azure](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span><span class="sxs-lookup"><span data-stu-id="b221b-112">For more information, see [Manage Access to Azure Storage Resources](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span></span>  
  
## <a name="create-storage-account"></a><span data-ttu-id="b221b-113">Créer un compte de stockage</span><span class="sxs-lookup"><span data-stu-id="b221b-113">Create Storage Account</span></span>  
 <span data-ttu-id="b221b-114">Pour créer un compte de stockage sur le Portail de gestion Azure, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b221b-114">To create a storage account on the Azure Management Portal, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b221b-115">Connectez-vous au [portail de gestion Azure](https://manage.windowsazure.com) à l’aide de votre compte.</span><span class="sxs-lookup"><span data-stu-id="b221b-115">Log in to the [Azure Management Portal](https://manage.windowsazure.com) using your account.</span></span> <span data-ttu-id="b221b-116">Si vous n'avez pas de compte Azure, visitez la page [Version d'évaluation gratuite d'Azure](https://www.windowsazure.com/pricing/free-trial/).</span><span class="sxs-lookup"><span data-stu-id="b221b-116">If you do not have an Azure account, visit [Azure free trial](https://www.windowsazure.com/pricing/free-trial/).</span></span>  
  
     <span data-ttu-id="b221b-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="b221b-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span></span>  
  
2.  <span data-ttu-id="b221b-118">Suivez les instructions détaillées pour [créer un compte de stockage](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span><span class="sxs-lookup"><span data-stu-id="b221b-118">Use the step by step instructions to [create a storage account](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span> <span data-ttu-id="b221b-119">Notez que lorsque vous créez un compte de stockage à utiliser pour la fonctionnalité fichiers de données SQL Server dans Azure, vous devez désélectionner ou désactiver la géo-réplication.</span><span class="sxs-lookup"><span data-stu-id="b221b-119">Note that when creating a storage account to be used for the SQL Server Data Files in Azure feature, you should unselect or disable the geo-replication.</span></span> <span data-ttu-id="b221b-120">Cela est dû au fait que l'ordre d'écriture n'est pas garanti pour plusieurs objets blob participant à la géoréplication.</span><span class="sxs-lookup"><span data-stu-id="b221b-120">This is because write order is not guaranteed for multiple blobs participating in geo-replication.</span></span> <span data-ttu-id="b221b-121">Si un compte de stockage est géorépliqué et la récupération est requise, une altération se produit.</span><span class="sxs-lookup"><span data-stu-id="b221b-121">If a storage account is geo-replicated and recovery is required, a corruption occurs.</span></span>  
  
     <span data-ttu-id="b221b-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="b221b-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span></span>  
  
## <a name="create-a-blob-container"></a><span data-ttu-id="b221b-123">Créer un conteneur d’objets blob</span><span class="sxs-lookup"><span data-stu-id="b221b-123">Create a Blob container</span></span>  
 <span data-ttu-id="b221b-124">Dans Azure, un conteneur permet de regrouper un ensemble d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="b221b-124">In Azure, a container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="b221b-125">Tous les objets blob doivent figurer dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="b221b-125">All blobs must be in a container.</span></span> <span data-ttu-id="b221b-126">Un compte de stockage peut contenir un nombre illimité de conteneurs, mais doit comporter au moins un conteneur.</span><span class="sxs-lookup"><span data-stu-id="b221b-126">A storage account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="b221b-127">Un conteneur peut stocker un nombre illimité d’objets blob.</span><span class="sxs-lookup"><span data-stu-id="b221b-127">A container can store an unlimited number of blobs.</span></span> <span data-ttu-id="b221b-128">Pour obtenir les informations les plus récentes sur les limites de taille de stockage, consultez la page [utilisation du service de stockage d’objets BLOB Azure dans .net](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span><span class="sxs-lookup"><span data-stu-id="b221b-128">For most up-to-date information on storage size limits, see [How to use the Azure Blob Storage Service in .NET](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span></span>  
  
 <span data-ttu-id="b221b-129">Pour créer un conteneur dans Azure, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b221b-129">To create a container in Azure, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b221b-130">Connectez-vous au [Portail de gestion Azure](https://manage.windowsazure.com).</span><span class="sxs-lookup"><span data-stu-id="b221b-130">Log in to the [Azure Management Portal](https://manage.windowsazure.com).</span></span>  
  
2.  <span data-ttu-id="b221b-131">Sélectionnez le compte de stockage, cliquez sur l'onglet **Conteneurs** , puis cliquez sur **Ajouter un conteneur** en bas de l'écran pour ouvrir une nouvelle boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b221b-131">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen, which opens a new dialog box.</span></span>  
  
3.  <span data-ttu-id="b221b-132">Entrez le nom du conteneur.</span><span class="sxs-lookup"><span data-stu-id="b221b-132">Enter a name for the container.</span></span>  
  
4.  <span data-ttu-id="b221b-133">Sélectionnez **Privé** pour le **Type d'accès**.</span><span class="sxs-lookup"><span data-stu-id="b221b-133">Select **Private** for **Access Type**.</span></span> <span data-ttu-id="b221b-134">Lorsque vous définissez l’accès privé, le conteneur et les données BLOB ne peuvent être lus que par le propriétaire du compte Azure.</span><span class="sxs-lookup"><span data-stu-id="b221b-134">When you set the access to private, the container and blob data can be read by the Azure account owner only.</span></span>  
  
     <span data-ttu-id="b221b-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="b221b-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b221b-136">Pour créer un conteneur par programme, utilisez également des API REST.</span><span class="sxs-lookup"><span data-stu-id="b221b-136">To create a container programmatically, you can also use REST APIs.</span></span> <span data-ttu-id="b221b-137">Pour plus d’informations, consultez [créer un conteneur](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) et également référence de l' [API REST des services de stockage Azure](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span><span class="sxs-lookup"><span data-stu-id="b221b-137">For more information, see [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) and also [Azure Storage Services REST API Reference](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span></span>  
  
 <span data-ttu-id="b221b-138">**Leçon suivante :**</span><span class="sxs-lookup"><span data-stu-id="b221b-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="b221b-139">Leçon 2. Créer une stratégie sur un conteneur et générer une signature d’accès partagé &#40;clé de&#41; SAS</span><span class="sxs-lookup"><span data-stu-id="b221b-139">Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key</span></span>](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  