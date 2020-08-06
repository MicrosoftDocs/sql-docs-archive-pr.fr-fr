---
title: Bibliothèque de curseurs ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
author: rothja
ms.author: jroth
ms.openlocfilehash: b0f0ad049c6b9e77f9888d582ab0cda2f5a5e0f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603517"
---
# <a name="odbc-cursor-library"></a><span data-ttu-id="4eace-102">Bibliothèque de curseurs ODBC</span><span class="sxs-lookup"><span data-stu-id="4eace-102">ODBC Cursor Library</span></span>
  <span data-ttu-id="4eace-103">Certains pilotes ODBC prennent uniquement en charge les paramètres de curseur par défaut ; Ces pilotes ne prennent pas non plus en charge les opérations de curseur positionnées, telles que **SQLSetPos**.</span><span class="sxs-lookup"><span data-stu-id="4eace-103">Some ODBC drivers only support the default cursor settings; these drivers also do not support positioned cursor operations, such as **SQLSetPos**.</span></span> <span data-ttu-id="4eace-104">La bibliothèque de curseurs ODBC est un composant de MDAC (Microsoft Data Access Components) qui permet d'implémenter des curseurs de bloc ou statiques sur un pilote qui ne les prend normalement pas en charge.</span><span class="sxs-lookup"><span data-stu-id="4eace-104">The ODBC cursor library is a component of the Microsoft Data Access Components (MDAC) used to implement block or static cursors on a driver that normally does not support them.</span></span> <span data-ttu-id="4eace-105">La bibliothèque de curseurs implémente également les instructions UPDATE et DELETE positionnées et **SQLSetPos** pour les curseurs qu’elle crée.</span><span class="sxs-lookup"><span data-stu-id="4eace-105">The cursor library also implements positioned UPDATE and DELETE statements and **SQLSetPos** for the cursors it creates.</span></span>  
  
 <span data-ttu-id="4eace-106">La bibliothèque de curseurs ODBC est implémentée comme une couche entre le gestionnaire de pilotes ODBC et un pilote ODBC.</span><span class="sxs-lookup"><span data-stu-id="4eace-106">The ODBC cursor library is implemented as a layer between the ODBC Driver Manager and an ODBC driver.</span></span> <span data-ttu-id="4eace-107">Si la bibliothèque de curseurs ODBC est chargée, le Gestionnaire de pilote ODBC route toutes les commandes connexes à curseur à la bibliothèque de curseurs au lieu du pilote.</span><span class="sxs-lookup"><span data-stu-id="4eace-107">If the ODBC cursor library is loaded, the ODBC Driver Manager routes all cursor-related commands to the cursor library instead of the driver.</span></span> <span data-ttu-id="4eace-108">La bibliothèque de curseurs implémente un curseur en extrayant l'intégralité du jeu de résultats du pilote sous-jacent et en mettant en cache le jeu de résultats sur le client.</span><span class="sxs-lookup"><span data-stu-id="4eace-108">The cursor library implements a cursor by fetching the entire result set from the underlying driver and caching the result set on the client.</span></span> <span data-ttu-id="4eace-109">Lors de l'utilisation de la bibliothèque de curseurs ODBC, l'application est limitée aux fonctionnalités de curseur de la bibliothèque de curseurs ; toute prise en charge à des fonctionnalités de curseur supplémentaires dans le pilote sous-jacent n'est pas accessible à l'application.</span><span class="sxs-lookup"><span data-stu-id="4eace-109">When using the ODBC cursor library, the application is limited to the cursor functionality of the cursor library; any support for additional cursor functionality in the underlying driver is not available to the application.</span></span>  
  
 <span data-ttu-id="4eace-110">L'utilisation de la bibliothèque de curseurs ODBC conjointement au pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client présente peu d'intérêt car le pilote prend en charge plus de fonctionnalités de curseur que la bibliothèque de curseurs ODBC.</span><span class="sxs-lookup"><span data-stu-id="4eace-110">There is little need to use the ODBC cursor library with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver because the driver itself supports more cursor functionality than the ODBC cursor library.</span></span> <span data-ttu-id="4eace-111">La seule raison d’utiliser la bibliothèque de curseurs ODBC avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client est que le pilote implémente sa prise en charge de curseur par le biais de curseurs côté serveur et que les curseurs côté serveur ne prennent pas en charge toutes les instructions SQL.</span><span class="sxs-lookup"><span data-stu-id="4eace-111">The only reason to use the ODBC cursor library with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver is because the driver implements its cursor support through server cursors, and server cursors do not support all SQL statements.</span></span> <span data-ttu-id="4eace-112">Chaque fois qu'il est nécessaire d'avoir un curseur statique avec des procédures stockées, des lots ou des instructions SQL contenant COMPUTE, COMPUTE BY, FOR BROWSE ou INTO, songez à utiliser la bibliothèque de curseurs ODBC.</span><span class="sxs-lookup"><span data-stu-id="4eace-112">Any time there is a need to have a static cursor with stored procedures, batches, or SQL statements containing COMPUTE, COMPUTE BY, FOR BROWSE, or INTO, consider using the ODBC cursor library.</span></span> <span data-ttu-id="4eace-113">Toutefois, utilisez-la avec précaution car elle met en cache l'intégralité du jeu de résultats sur le client, ce qui peut consommer de grandes quantités de mémoire et ralentir les performances.</span><span class="sxs-lookup"><span data-stu-id="4eace-113">However, care must be used with the cursor library because it caches the entire result set on the client, which can use large amounts of memory and slow performance.</span></span>  
  
 <span data-ttu-id="4eace-114">Une application appelle la bibliothèque de curseurs connexion par connexion à l’aide de la fonction [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) pour définir l’attribut de connexion SQL_ATTR_ODBC_CURSORS avant de se connecter à une source de données.</span><span class="sxs-lookup"><span data-stu-id="4eace-114">An application invokes the cursor library on a connection-by-connection basis by using [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to set the SQL_ATTR_ODBC_CURSORS connection attribute before connecting to a data source.</span></span> <span data-ttu-id="4eace-115">SQL_ATTR_ODBC_CURSORS prend l'une des trois valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="4eace-115">SQL_ATTR_ODBC_CURSORS is set to one of three values:</span></span>  
  
 <span data-ttu-id="4eace-116">SQL_CUR_USE_ODBC</span><span class="sxs-lookup"><span data-stu-id="4eace-116">SQL_CUR_USE_ODBC</span></span>  
 <span data-ttu-id="4eace-117">Lorsque cette option est définie avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client, la bibliothèque de curseurs ODBC remplace la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du curseur natif du pilote ODBC de Native Client.</span><span class="sxs-lookup"><span data-stu-id="4eace-117">When this option is set with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, the ODBC cursor library overrides the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver's native cursor support.</span></span> <span data-ttu-id="4eace-118">Seuls les types de curseurs pris en charge par la bibliothèque de curseurs peuvent être utilisés pour la connexion ; les curseurs côté serveur ne peuvent pas être utilisés.</span><span class="sxs-lookup"><span data-stu-id="4eace-118">Only the cursor types supported by the cursor library can be used for the connection; server cursors cannot be used.</span></span>  
  
 <span data-ttu-id="4eace-119">SQL_CUR_USE_DRIVER</span><span class="sxs-lookup"><span data-stu-id="4eace-119">SQL_CUR_USE_DRIVER</span></span>  
 <span data-ttu-id="4eace-120">Lorsque cette option est définie, toute la prise en charge de curseur native sur le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client peut être utilisée pour la connexion.</span><span class="sxs-lookup"><span data-stu-id="4eace-120">When this option is set, all of the cursor support native to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver can be used for the connection.</span></span> <span data-ttu-id="4eace-121">La bibliothèque de curseurs ODBC ne peut pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="4eace-121">The ODBC cursor library cannot be used.</span></span> <span data-ttu-id="4eace-122">Tous les curseurs sont implémentés en tant que curseurs côté serveur.</span><span class="sxs-lookup"><span data-stu-id="4eace-122">All cursors are implemented as server cursors.</span></span>  
  
 <span data-ttu-id="4eace-123">SQL_CUR_USE_IF_NEEDED</span><span class="sxs-lookup"><span data-stu-id="4eace-123">SQL_CUR_USE_IF_NEEDED</span></span>  
 <span data-ttu-id="4eace-124">Lorsque cette option est définie, l’effet est le même que SQL_CUR_USE_DRIVER lorsqu’il est utilisé avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client.</span><span class="sxs-lookup"><span data-stu-id="4eace-124">When this option is set, the effect is the same as SQL_CUR_USE_DRIVER when used with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="4eace-125">Au moment de la connexion, le gestionnaire de pilotes ODBC effectue un test pour déterminer si le pilote ODBC qui est connecté prend en charge l’option SQL_FETCH_PRIOR de [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span><span class="sxs-lookup"><span data-stu-id="4eace-125">At connect time, the ODBC Driver Manager tests to see if the ODBC driver being connected to supports the SQL_FETCH_PRIOR option of [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="4eace-126">Si le pilote ne prend pas en charge l'option, le gestionnaire de pilotes ODBC charge la bibliothèque de curseurs ODBC.</span><span class="sxs-lookup"><span data-stu-id="4eace-126">If the driver does not support the option, the ODBC Driver Manager loads the ODBC cursor library.</span></span> <span data-ttu-id="4eace-127">Si le pilote prend en charge l'option, le gestionnaire de pilotes ODBC ne charge pas la bibliothèque de curseurs ODBC et l'application utilise la prise en charge native du pilote.</span><span class="sxs-lookup"><span data-stu-id="4eace-127">If the driver does support the option, the ODBC Driver Manager does not load the ODBC cursor library and the application uses the native support of the driver.</span></span> <span data-ttu-id="4eace-128">Étant donné que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge SQL_FETCH_PRIOR, le gestionnaire de pilotes ODBC ne charge pas la bibliothèque de curseurs ODBC.</span><span class="sxs-lookup"><span data-stu-id="4eace-128">Because the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports SQL_FETCH_PRIOR, the ODBC Driver Manager does not load the ODBC cursor library.</span></span>  
  
 <span data-ttu-id="4eace-129">La bibliothèque de curseurs permet aux applications d'utiliser plusieurs instructions actives sur une connexion, ainsi que des curseurs déroulants pouvant être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="4eace-129">The cursor library allows applications to use multiple active statements on a connection, as well as scrollable, updatable cursors.</span></span> <span data-ttu-id="4eace-130">La bibliothèque de curseurs doit être chargée pour prendre en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="4eace-130">The cursor library must be loaded to support this functionality.</span></span> <span data-ttu-id="4eace-131">Utilisez [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) pour spécifier comment la bibliothèque de curseurs doit être utilisée et [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour spécifier le type de curseur, la concurrence et la taille de l’ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="4eace-131">Use [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to specify how the cursor library should be used and [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to specify the cursor type, concurrency, and rowset size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eace-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eace-132">See Also</span></span>  
 [<span data-ttu-id="4eace-133">Comment les curseurs sont implémentés</span><span class="sxs-lookup"><span data-stu-id="4eace-133">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  