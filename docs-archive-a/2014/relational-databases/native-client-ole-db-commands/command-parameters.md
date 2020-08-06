---
title: Paramètres de commande | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615139"
---
# <a name="command-parameters"></a><span data-ttu-id="f9ff3-102">Paramètres de commande</span><span class="sxs-lookup"><span data-stu-id="f9ff3-102">Command Parameters</span></span>
  <span data-ttu-id="f9ff3-103">Les paramètres sont marqués dans le texte de la commande avec le caractère de point d'interrogation.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-103">Parameters are marked in command text with the question mark character.</span></span> <span data-ttu-id="f9ff3-104">Par exemple, l'instruction SQL suivante est marquée pour un paramètre d'entrée unique :</span><span class="sxs-lookup"><span data-stu-id="f9ff3-104">For example, the following SQL statement is marked for a single input parameter:</span></span>  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 <span data-ttu-id="f9ff3-105">Pour améliorer les performances en réduisant le trafic réseau, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne dérive pas automatiquement les informations de paramètres, sauf pour l’appel de **ICommandWithParameters :: GetParameterInfo** ou **ICommandPrepare ::P la reparenthèse** est appelée avant l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-105">To improve performance by reducing network traffic, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically derive parameter information unless **ICommandWithParameters::GetParameterInfo** or **ICommandPrepare::Prepare** is called before executing a command.</span></span> <span data-ttu-id="f9ff3-106">Cela signifie que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne fait pas automatiquement :</span><span class="sxs-lookup"><span data-stu-id="f9ff3-106">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically:</span></span>  
  
-   <span data-ttu-id="f9ff3-107">La vérification de ce que le type de données spécifié avec **ICommandWithParameters::SetParameterInfo** est correct.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-107">Verify the correctness of the data type specified with **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="f9ff3-108">Mappage du DBTYPE spécifié dans les informations de liaison d'accesseur au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correct pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-108">Map from the DBTYPE specified in the accessor binding information to the correct [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter.</span></span>  
  
 <span data-ttu-id="f9ff3-109">Les applications recevront des erreurs ou présenteront une perte de précision avec l'une ou l'autre de ces méthodes si elles spécifient des types de données qui ne sont pas compatibles avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-109">Applications will receive possible errors or loss of precision with either of these methods if they specify data types that are not compatible with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the parameter.</span></span>  
  
 <span data-ttu-id="f9ff3-110">Pour éviter cela, l'application doit :</span><span class="sxs-lookup"><span data-stu-id="f9ff3-110">To ensure this does not happen, the application should:</span></span>  
  
-   <span data-ttu-id="f9ff3-111">vérifier que *pwszDataSourceType* correspond au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage en dur de **ICommandWithParameters::SetParameterInfo**.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-111">Ensure that *pwszDataSourceType* matches the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="f9ff3-112">s'assurer que la valeur DBTYPE qui est liée au paramètre est du même type que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage effectué de manière irréversible d'un accesseur ;</span><span class="sxs-lookup"><span data-stu-id="f9ff3-112">Ensure that the DBTYPE value being bound to the parameter is of the same type as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding an accessor.</span></span>  
  
-   <span data-ttu-id="f9ff3-113">coder l’application de façon à appeler **ICommandWithParameters::GetParameterInfo** afin que le fournisseur puisse obtenir dynamiquement les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des paramètres.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-113">Code the application to call **ICommandWithParameters::GetParameterInfo** so that the provider can obtain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types of the parameters dynamically.</span></span> <span data-ttu-id="f9ff3-114">Notez que cela provoque une boucle réseau supplémentaire au serveur.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-114">Note that this causes an extra network round trip to the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9ff3-115">Le fournisseur ne prend pas en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les instructions UPDATE ou DELETE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant une clause FROM ; pour les instructions SQL qui dépendent d’une sous-requête contenant des paramètres ; pour les instructions SQL contenant des marqueurs de paramètre dans les deux expressions d’un prédicat de comparaison, like ou quantifié ; ou les requêtes dans lesquelles un des paramètres est un paramètre d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-115">The provider does not support calling **ICommandWithParameters::GetParameterInfo** for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE or DELETE statement containing a FROM clause; for any SQL statement depending on a subquery containing parameters; for SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate; or queries where one of the parameters is a parameter to a function.</span></span> <span data-ttu-id="f9ff3-116">Lors du traitement d’un lot d’instructions SQL, le fournisseur ne prend pas non plus en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les marqueurs de paramètre dans les instructions après la première instruction du lot.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-116">When processing a batch of SQL statements, the provider also does not support calling **ICommandWithParameters::GetParameterInfo** for parameter markers in statements after the first statement in the batch.</span></span> <span data-ttu-id="f9ff3-117">Les commentaires (/\* \*/) ne sont pas autorisés dans la commande [!INCLUDE[tsql](../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9ff3-117">Comments (/\* \*/) are not allowed in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="f9ff3-118">Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge les paramètres d’entrée dans les commandes d’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input parameters in SQL statement commands.</span></span> <span data-ttu-id="f9ff3-119">Sur les commandes d’appel de procédure, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge les paramètres d’entrée, de sortie et d’entrée/sortie.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-119">On procedure-call commands, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input, output, and input/output parameters.</span></span> <span data-ttu-id="f9ff3-120">Les valeurs de paramètre de sortie sont retournées à l'application lors de l'exécution (uniquement si aucun ensemble de lignes n'est retourné) ou lorsque tous les ensembles de lignes retournés sont épuisés par l'application.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-120">Output parameter values are returned to the application either on execution (only if there are no rowsets returned) or when all returned rowsets are exhausted by the application.</span></span> <span data-ttu-id="f9ff3-121">Pour garantir que les valeurs retournées sont valides, utilisez **IMultipleResults** pour forcer la consommation de l’ensemble de lignes.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-121">To ensure that returned values are valid, use **IMultipleResults** to force rowset consumption.</span></span>  
  
 <span data-ttu-id="f9ff3-122">Les noms des paramètres de procédure stockée n'ont pas besoin d'être spécifiés dans une structure DBPARAMBINDINFO.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-122">The names of stored procedure parameters need not be specified in a DBPARAMBINDINFO structure.</span></span> <span data-ttu-id="f9ff3-123">Utilisez NULL pour la valeur du membre *pwszName* pour indiquer que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client doit ignorer le nom du paramètre et utiliser uniquement l’ordinal spécifié dans le membre *rgParamOrdinals* de **ICommandWithParameters :: SetParameterInfo**.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-123">Use NULL for the value of the *pwszName* member to indicate that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider should ignore the parameter name and use only the ordinal specified in the *rgParamOrdinals* member of **ICommandWithParameters::SetParameterInfo**.</span></span> <span data-ttu-id="f9ff3-124">Si le texte de la commande contient à la fois des paramètres nommés et sans nom, tous les paramètres sans nom doivent être spécifiés avant les paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-124">If the command text contains both named and unnamed parameters, all of the unnamed parameters must be specified before any named parameters.</span></span>  
  
 <span data-ttu-id="f9ff3-125">Si le nom d’un paramètre de procédure stockée est spécifié, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client vérifie le nom pour s’assurer qu’il est valide.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-125">If the name of a stored procedure parameter is specified, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks the name to ensure that it is valid.</span></span> <span data-ttu-id="f9ff3-126">Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne une erreur lorsqu’il reçoit un nom de paramètre erroné du consommateur.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error when it receives an erroneous parameter name from the consumer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9ff3-127">Pour exposer la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML et des types définis par l’utilisateur (UDT), le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client implémente une nouvelle interface [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) .</span><span class="sxs-lookup"><span data-stu-id="f9ff3-127">To expose support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements a new [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ff3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9ff3-128">See Also</span></span>  
 [<span data-ttu-id="f9ff3-129">Commandes</span><span class="sxs-lookup"><span data-stu-id="f9ff3-129">Commands</span></span>](commands.md)  
  
  