---
title: Gestion des transactions (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
author: minewiskan
ms.author: owend
ms.openlocfilehash: bff1c60addd25b222905e33bc33e77dd85e88803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613671"
---
# <a name="managing-transactions-xmla"></a><span data-ttu-id="e6c1d-102">Gestion des transactions (XMLA)</span><span class="sxs-lookup"><span data-stu-id="e6c1d-102">Managing Transactions (XMLA)</span></span>
  <span data-ttu-id="e6c1d-103">Chaque commande XML for Analysis (XMLA) envoyée à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécute dans le contexte d’une transaction sur la session implicite ou explicite actuelle.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-103">Every XML for Analysis (XMLA) command sent to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs within the context of a transaction on the current implicit or explicit session.</span></span> <span data-ttu-id="e6c1d-104">Pour gérer chacune de ces transactions, vous devez utiliser les commandes [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) .</span><span class="sxs-lookup"><span data-stu-id="e6c1d-104">To manage each of these transactions, you use the [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), and [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) commands.</span></span> <span data-ttu-id="e6c1d-105">En utilisant ces commandes, vous pouvez créer des transactions implicites ou explicites, modifier le nombre de références de transaction, ainsi que les transactions de démarrage, de validation ou d'annulation.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-105">By using these commands, you can create implicit or explicit transactions, change the transaction reference count, as well as start, commit, or roll back transactions.</span></span>  
  
## <a name="implicit-and-explicit-transactions"></a><span data-ttu-id="e6c1d-106">Transactions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="e6c1d-106">Implicit and Explicit Transactions</span></span>  
 <span data-ttu-id="e6c1d-107">Une transaction est soit implicite, soit explicite :</span><span class="sxs-lookup"><span data-stu-id="e6c1d-107">A transaction is either implicit or explicit:</span></span>  
  
 <span data-ttu-id="e6c1d-108">**Transaction implicite**</span><span class="sxs-lookup"><span data-stu-id="e6c1d-108">**Implicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="e6c1d-109">crée une transaction *implicite* pour une commande XMLA si la `BeginTransaction` commande ne spécifie pas le début d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-109">creates an *implicit* transaction for an XMLA command if the `BeginTransaction` command does not specify the start of a transaction.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e6c1d-110">valide toujours une transaction implicite si la commande aboutit et l'annule si la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-110">always commits an implicit transaction if the command succeeds, and rolls back an implicit transaction if the command fails.</span></span>  
  
 <span data-ttu-id="e6c1d-111">**Transaction explicite**</span><span class="sxs-lookup"><span data-stu-id="e6c1d-111">**Explicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="e6c1d-112">crée une transaction *explicite* si la `BeginTransaction` commande démarre une transaction.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-112">creates an *explicit* transaction if the `BeginTransaction` command starts of a transaction.</span></span> <span data-ttu-id="e6c1d-113">Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne valide une transaction explicite que si une commande `CommitTransaction` est envoyée et l'annule si une commande `RollbackTransaction` est envoyée.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-113">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] only commits an explicit transaction if a `CommitTransaction` command is sent, and rolls back an explicit transaction if a `RollbackTransaction` command is sent.</span></span>  
  
 <span data-ttu-id="e6c1d-114">De plus, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] annule les transactions implicites et explicites si la session active se termine avant que la transaction active n'ait abouti.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-114">In addition, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back both implicit and explicit transactions if the current session ends before the active transaction completes.</span></span>  
  
## <a name="transactions-and-reference-counts"></a><span data-ttu-id="e6c1d-115">Transactions et nombres de référence</span><span class="sxs-lookup"><span data-stu-id="e6c1d-115">Transactions and Reference Counts</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e6c1d-116">comptabilise le nombre de référence de transactions pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-116">maintains a transaction reference count for each session.</span></span> <span data-ttu-id="e6c1d-117">Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prend pas en charge les transactions imbriquées dans la mesure où une seule transaction active est gérée par session.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-117">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not support nested transactions in that only one active transaction is maintained per session.</span></span> <span data-ttu-id="e6c1d-118">Si aucune transaction n'est active dans la session active, le nombre de références de transaction est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-118">If the current session does not have an active transaction, the transaction reference count is set to zero.</span></span>  
  
 <span data-ttu-id="e6c1d-119">En d'autres termes, chaque commande `BeginTransaction` incrémente le nombre de références d'une unité, et chaque commande `CommitTransaction` décrémente le nombre de références d'une unité.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-119">In other words, each `BeginTransaction` command increments the reference count by one, while each `CommitTransaction` command decrements the reference count by one.</span></span> <span data-ttu-id="e6c1d-120">Si une commande `CommitTransaction` définit le nombre de transactions à zéro, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-120">If a `CommitTransaction` command sets the transaction count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the transaction.</span></span>  
  
 <span data-ttu-id="e6c1d-121">Cependant, la commande `RollbackTransaction` annule la transaction active quelle que soit la valeur actuelle du nombre de références de transaction.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-121">However, the `RollbackTransaction` command rolls back the active transaction regardless of the current value of the transaction reference count.</span></span> <span data-ttu-id="e6c1d-122">Autrement dit, une seule commande `RollbackTransaction` permet d'annuler la transaction active, quel que soit le nombre de commandes `BeginTransaction` ou `CommitTransaction` qui ont été envoyées, et définit le nombre de références de transaction à zéro.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-122">In other words, a single `RollbackTransaction` command rolls back the active transaction, no matter how many `BeginTransaction` commands or `CommitTransaction` commands were sent, and sets the transaction reference count to zero.</span></span>  
  
## <a name="beginning-a-transaction"></a><span data-ttu-id="e6c1d-123">Lancement d'une transaction</span><span class="sxs-lookup"><span data-stu-id="e6c1d-123">Beginning a Transaction</span></span>  
 <span data-ttu-id="e6c1d-124">La commande `BeginTransaction` lance une transaction explicite sur la session active et incrémente le nombre de référence de transactions correspondant d'une unité.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-124">The `BeginTransaction` command begins an explicit transaction on the current session and increments the transaction reference count for the current session by one.</span></span> <span data-ttu-id="e6c1d-125">Toutes les commandes suivantes sont considérées comme faisant partie de la transaction active, jusqu'à ce qu'un nombre suffisant de commandes `CommitTransaction` soit envoyé pour valider la transaction active ou qu'une commande unique `RollbackTransaction` soit envoyée pour annuler la transaction active.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-125">All subsequent commands are considered to be within the active transaction, until either enough `CommitTransaction` commands are sent to commit the active transaction or a single `RollbackTransaction` command is sent to roll back the active transaction.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="e6c1d-126">Validation d'une transaction</span><span class="sxs-lookup"><span data-stu-id="e6c1d-126">Committing a Transaction</span></span>  
 <span data-ttu-id="e6c1d-127">La commande `CommitTransaction` valide les résultats des commandes exécutées après que la commande `BeginTransaction` a été exécutée sur la session active.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-127">The `CommitTransaction` command commits the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="e6c1d-128">Chaque commande `CommitTransaction` décrémente le nombre de référence pour les transactions actives d'une session.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-128">Each `CommitTransaction` command decrements the reference count for active transactions on a session.</span></span> <span data-ttu-id="e6c1d-129">Si une commande `CommitTransaction` définit le nombre de références à zéro, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction active.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-129">If a `CommitTransaction` command sets the reference count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the active transaction.</span></span> <span data-ttu-id="e6c1d-130">En l'absence de toute transaction active (en d'autres termes, le nombre de référence de transactions pour la session active est déjà défini à zéro), une commande `CommitTransaction` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-130">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `CommitTransaction` command results in an error.</span></span>  
  
## <a name="rolling-back-a-transaction"></a><span data-ttu-id="e6c1d-131">Annulation d'une transaction</span><span class="sxs-lookup"><span data-stu-id="e6c1d-131">Rolling Back a Transaction</span></span>  
 <span data-ttu-id="e6c1d-132">La commande `RollbackTransaction` annule les résultats des commandes exécutées après que la commande `BeginTransaction` a été exécutée sur la session active.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-132">The `RollbackTransaction` command rolls back the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="e6c1d-133">La commande `RollbackTransaction` annule la transaction active, quel que soit le nombre de références de transaction actuel, et définit le nombre de références de transaction à zéro.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-133">The `RollbackTransaction` command rolls back the active transaction, regardless of the current transaction reference count, and sets the transaction reference count to zero.</span></span> <span data-ttu-id="e6c1d-134">En l'absence de toute transaction active (en d'autres termes, le nombre de référence de transactions pour la session active est déjà défini à zéro), une commande `RollbackTransaction` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="e6c1d-134">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `RollbackTransaction` command results in an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c1d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6c1d-135">See Also</span></span>  
 [<span data-ttu-id="e6c1d-136">Développement avec XMLA dans Analysis Services</span><span class="sxs-lookup"><span data-stu-id="e6c1d-136">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  