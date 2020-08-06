---
title: Instructions relatives aux niveaux d’isolation des transactions avec des tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 834c5950a8f8b0ddf8854d06c6fb1073a264fc22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701567"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a><span data-ttu-id="72cc6-102">Instructions pour les niveaux d'isolement des transactions sur les tables mémoire optimisées</span><span class="sxs-lookup"><span data-stu-id="72cc6-102">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>
  <span data-ttu-id="72cc6-103">Dans de nombreux scénarios, vous devez spécifier le niveau d'isolation de la transaction.</span><span class="sxs-lookup"><span data-stu-id="72cc6-103">In many scenarios, you must specify the transaction isolation level.</span></span> <span data-ttu-id="72cc6-104">L'isolation des transactions pour les tables mémoire optimisées est différente de celle des tables sur disque.</span><span class="sxs-lookup"><span data-stu-id="72cc6-104">Transaction isolation for memory-optimized tables differs from disk-based tables.</span></span>  
  
 <span data-ttu-id="72cc6-105">Conditions requises pour spécifier le niveau d'isolation de la transaction :</span><span class="sxs-lookup"><span data-stu-id="72cc6-105">Requirements for specifying transaction isolation level:</span></span>  
  
-   <span data-ttu-id="72cc6-106">TRANSACTION ISOLATION LEVEL est une option requise pour le bloc ATOMIC contenant le contenu d'une procédure stockée compilée en mode natif.</span><span class="sxs-lookup"><span data-stu-id="72cc6-106">TRANSACTION ISOLATION LEVEL is a required option for the ATOMIC block comprising the content of a natively compiled stored procedure.</span></span>  
  
-   <span data-ttu-id="72cc6-107">En raison des restrictions d'utilisation du niveau d'isolation dans les transactions entre conteneurs, l'utilisation des tables mémoire optimisées en [!INCLUDE[tsql](../includes/tsql-md.md)] interprété doit généralement être accompagnée d'un indicateur de table spécifiant le niveau d'isolation utilisé pour accéder à la table.</span><span class="sxs-lookup"><span data-stu-id="72cc6-107">Because of restrictions on isolation level use in cross-container transactions, uses of memory-optimized tables in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] must often be accompanied by a table hint specifying the isolation level used to access the table.</span></span> <span data-ttu-id="72cc6-108">Pour plus d’informations sur les indicateurs de niveau d’isolation et les transactions entre conteneurs, consultez [niveaux d’isolation des transactions](../../2014/database-engine/transaction-isolation-levels.md).</span><span class="sxs-lookup"><span data-stu-id="72cc6-108">For more information about isolation level hints and cross-container transactions, see [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="72cc6-109">Le niveau d'isolation de la transaction souhaité doit être déclaré explicitement.</span><span class="sxs-lookup"><span data-stu-id="72cc6-109">The desired transaction isolation level must be explicitly declared.</span></span> <span data-ttu-id="72cc6-110">Il n'est pas possible d'utiliser des indicateurs de verrouillage (tels que XLOCK) pour garantir l'isolation de certaines lignes ou tables dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="72cc6-110">It is not possible to use locking hints (such as XLOCK) to guarantee the isolation of certain rows or tables in the transaction.</span></span>  
  
-   <span data-ttu-id="72cc6-111">L'application qui accède à la base de données doit implémenter la logique de nouvelle tentative pour traiter les erreurs résultant de conflits qui condamnent la transaction, les échecs de validation et les échecs de dépendance de validation.</span><span class="sxs-lookup"><span data-stu-id="72cc6-111">The application accessing the database should implement retry logic to deal with errors resulting from transaction-dooming conflicts, validation failures, and commit-dependency failures.</span></span> <span data-ttu-id="72cc6-112">Notez que les échecs de validation de dépendance peuvent se produire même avec les transactions en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="72cc6-112">Note that commit dependency failures can occur even with read-only transactions.</span></span>  
  
-   <span data-ttu-id="72cc6-113">Les transactions longues doivent être évitées avec les tables mémoire optimisées.</span><span class="sxs-lookup"><span data-stu-id="72cc6-113">Long-running transactions should be avoided with memory-optimized tables.</span></span> <span data-ttu-id="72cc6-114">De telles transactions augmentent la probabilité des conflits et l'arrêt des transactions suivantes.</span><span class="sxs-lookup"><span data-stu-id="72cc6-114">Such transactions increase the likelihood of conflicts and subsequent transaction terminations.</span></span> <span data-ttu-id="72cc6-115">Une transaction longue diffère également l'opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="72cc6-115">A long-running transaction also defers garbage collection.</span></span> <span data-ttu-id="72cc6-116">Plus une transaction est longue, plus l’OLTP en mémoire est lent et les versions de ligne sont supprimées récemment, ce qui peut réduire les performances de recherche pour les nouvelles transactions.</span><span class="sxs-lookup"><span data-stu-id="72cc6-116">The longer a transaction runs, the longer In-Memory OLTP keeps recently deleted row versions, which can decrease lookup performance for new transactions.</span></span>  
  
 <span data-ttu-id="72cc6-117">Les tables sur disque reposent généralement sur le verrouillage et le blocage de l'isolation des transactions.</span><span class="sxs-lookup"><span data-stu-id="72cc6-117">Disk-based tables typically rely on locking and blocking for transaction isolation.</span></span> <span data-ttu-id="72cc6-118">Les tables mémoire optimisées reposent sur plusieurs contrôles de version et la détection de conflit pour garantir l'isolation.</span><span class="sxs-lookup"><span data-stu-id="72cc6-118">Memory-optimized tables rely on multi-versioning and conflict detection to guarantee isolation.</span></span> <span data-ttu-id="72cc6-119">Pour plus d’informations, consultez la section sur la détection de conflit, la validation et les vérifications de dépendance de validation dans les [transactions dans les tables mémoire optimisées](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span><span class="sxs-lookup"><span data-stu-id="72cc6-119">For details, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="72cc6-120">Les tables sur disque permettent plusieurs contrôles de version avec les niveaux d'isolation SNAPSHOT et READ_COMMITTED_SNAPSHOT.</span><span class="sxs-lookup"><span data-stu-id="72cc6-120">Disk-based tables do allow multi-versioning with the isolation levels SNAPSHOT and READ_COMMITTED_SNAPSHOT.</span></span> <span data-ttu-id="72cc6-121">Pour les tables mémoire optimisées, tous les niveaux d'isolation sont basés sur plusieurs contrôles de version, y compris REPEATABLE READ et SERIALIZABLE.</span><span class="sxs-lookup"><span data-stu-id="72cc6-121">For memory-optimized tables all isolation levels are multi-version based, including REPEATABLE READ and SERIALIZABLE.</span></span>  
  
## <a name="types-of-transactions"></a><span data-ttu-id="72cc6-122">Types de transactions</span><span class="sxs-lookup"><span data-stu-id="72cc6-122">Types of Transactions</span></span>  
 <span data-ttu-id="72cc6-123">Chaque requête dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute dans le contexte d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="72cc6-123">Every query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] runs in the context of a transaction.</span></span>  
  
 <span data-ttu-id="72cc6-124">Il existe trois types de transactions dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="72cc6-124">There are three types of transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="72cc6-125">Transactions en mode de validation automatique.</span><span class="sxs-lookup"><span data-stu-id="72cc6-125">Autocommit transactions.</span></span> <span data-ttu-id="72cc6-126">S'il n'y a pas de contexte de transaction active et les transactions implicites ne sont pas activées (ON) dans une session, chaque requête a son propre contexte de transaction.</span><span class="sxs-lookup"><span data-stu-id="72cc6-126">If there is no active transaction context and implicit transactions are not set to ON in the session, each query has its own transaction context.</span></span> <span data-ttu-id="72cc6-127">La transaction démarre lorsque l'instruction démarre l'exécution, et se termine lorsque l'instruction est terminée.</span><span class="sxs-lookup"><span data-stu-id="72cc6-127">The transaction starts when the statement starts execution, and completes when the statement finishes.</span></span>  
  
-   <span data-ttu-id="72cc6-128">Transactions explicites.</span><span class="sxs-lookup"><span data-stu-id="72cc6-128">Explicit transactions.</span></span> <span data-ttu-id="72cc6-129">L'utilisateur démarre la transaction via un BEGIN TRAN ou BEGIN ATOMIC explicite.</span><span class="sxs-lookup"><span data-stu-id="72cc6-129">The user starts the transaction through an explicit BEGIN TRAN or BEGIN ATOMIC.</span></span> <span data-ttu-id="72cc6-130">La transaction est terminée après le COMMIT et ROLLBACK ou END correspondant (dans le cas d'un bloc Atomic).</span><span class="sxs-lookup"><span data-stu-id="72cc6-130">The transaction is completed following the corresponding COMMIT and ROLLBACK or END (in the case of an atomic block).</span></span>  
  
-   <span data-ttu-id="72cc6-131">Transactions implicites.</span><span class="sxs-lookup"><span data-stu-id="72cc6-131">Implicit transactions.</span></span> <span data-ttu-id="72cc6-132">Lorsque l'option IMPLICIT_TRANSACTIONS est activée (ON), une transaction est démarrée implicitement lorsque l'utilisateur exécute une instruction et il n'y a aucun contexte de transaction active.</span><span class="sxs-lookup"><span data-stu-id="72cc6-132">When the option IMPLICIT_TRANSACTIONS is set to ON, a transaction is started implicitly whenever the user executes a statement and there is no active transaction context.</span></span> <span data-ttu-id="72cc6-133">La transaction est terminée via un COMMIT ou ROLLBACK explicite.</span><span class="sxs-lookup"><span data-stu-id="72cc6-133">The transaction is completed through an explicit COMMIT and ROLLBACK.</span></span>  
  
## <a name="baseline-read-committed-isolation"></a><span data-ttu-id="72cc6-134">Isolation READ COMMITTED de base</span><span class="sxs-lookup"><span data-stu-id="72cc6-134">Baseline READ COMMITTED Isolation</span></span>  
 <span data-ttu-id="72cc6-135">READ COMMITTED est le niveau d'isolement par défaut dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72cc6-135">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="72cc6-136">Le niveau d'isolement READ COMMITTED garantit que les transactions ne voient aucune donnée non validée par rapport aux modifications effectuées en dehors de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="72cc6-136">The isolation level READ COMMITTED guarantees that transactions do not see any uncommitted data from changes outside the current transaction.</span></span> <span data-ttu-id="72cc6-137">En d'autres termes, la transaction lit uniquement les données qui ont été validées dans la base de données, ou modifiées par la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="72cc6-137">In other words, the transaction only reads data which has either been committed to the database, or has been changed by the current transaction.</span></span>  
  
 <span data-ttu-id="72cc6-138">Tous les niveaux d'isolement pris en charge pour les tables mémoire optimisées garantissent la lecture validée.</span><span class="sxs-lookup"><span data-stu-id="72cc6-138">All isolation levels supported for memory-optimized tables provide the read committed guarantee.</span></span> <span data-ttu-id="72cc6-139">Par conséquent, si la transaction ne requiert pas de garanties plus fortes, vous pouvez utiliser n'importe quel niveau d'isolation pris en charge pour les tables mémoire optimisées.</span><span class="sxs-lookup"><span data-stu-id="72cc6-139">Therefore, if the transaction does not require stronger guarantees, you can use any of the isolation levels supported for memory-optimized tables.</span></span> <span data-ttu-id="72cc6-140">SNAPSHOT utilise moins de ressources système, par rapport à d'autres niveaux d'isolation.</span><span class="sxs-lookup"><span data-stu-id="72cc6-140">SNAPSHOT uses the fewest system resources, compared to other isolation levels.</span></span>  
  
 <span data-ttu-id="72cc6-141">La garantie fournie par le niveau d'isolation SNAPSHOT (le plus bas niveau d'isolation pris en charge pour les tables mémoire optimisées) inclut les garanties de READ COMMITTED.</span><span class="sxs-lookup"><span data-stu-id="72cc6-141">The guarantee provided by the SNAPSHOT isolation level (the lowest level of isolation supported for memory-optimized tables) includes the guarantees of READ COMMITTED.</span></span> <span data-ttu-id="72cc6-142">Chaque instruction dans la transaction lit la même version cohérente de la base de données.</span><span class="sxs-lookup"><span data-stu-id="72cc6-142">Every statement in the transaction reads the same, consistent version of the database.</span></span> <span data-ttu-id="72cc6-143">Non seulement les lignes sont lues par la transaction validée dans la base de données, mais toutes les opérations de lecture voient l'ensemble des modifications effectuées par le même jeu de transactions.</span><span class="sxs-lookup"><span data-stu-id="72cc6-143">Not only are all the rows read by the transaction committed to the database, also all the read operations see the set of changes made by the same set of transactions.</span></span>  
  
 <span data-ttu-id="72cc6-144">**Recommandation**: si seule la garantie d’isolation Read Committed est requise, utilisez l’isolement d’instantané avec les procédures stockées compilées en mode natif et pour accéder aux tables optimisées en mémoire par le biais de l’interpréteur [!INCLUDE[tsql](../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72cc6-144">**Guideline**: If only the READ COMMITTED isolation guarantee is required, use SNAPSHOT isolation with natively compiled stored procedures and for accessing memory-optimized tables through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="72cc6-145">Pour les transactions avec validation automatique, le niveau d'isolation READ COMMITTED est mappé implicitement pour les tables mémoire optimisées.</span><span class="sxs-lookup"><span data-stu-id="72cc6-145">For autocommit transactions, the isolation level READ COMMITTED is implicitly mapped to SNAPSHOT for memory-optimized tables.</span></span> <span data-ttu-id="72cc6-146">Par conséquent, si le paramètre de session TRANSACTION ISOLATION LEVEL est défini sur READ COMMITTED, il n'est pas nécessaire de spécifier le niveau d'isolation par un indicateur de table lors de l'accès aux tables mémoire optimisées.</span><span class="sxs-lookup"><span data-stu-id="72cc6-146">Therefore, if the TRANSACTION ISOLATION LEVEL session setting is set to READ COMMITTED, it is not necessary to specify the isolation level through a table hint when accessing memory-optimized tables.</span></span>  
  
 <span data-ttu-id="72cc6-147">L'exemple de transaction avec validation automatique suivant montre une jointure entre la table mémoire optimisée Customers et une table standard [Order History], dans le cadre d'un traitement ad hoc :</span><span class="sxs-lookup"><span data-stu-id="72cc6-147">The following autocommit transaction example shows a join between a memory-optimized table Customers and a regular table [Order History], as part of an ad hoc batch:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 <span data-ttu-id="72cc6-148">L'exemple de transactions, explicites ou implicites, suivant utilise la même jointure, mais cette fois, dans une transaction utilisateur explicite.</span><span class="sxs-lookup"><span data-stu-id="72cc6-148">The following explicit or implicit transactions example shows the same join, but this time in an explicit user transaction.</span></span> <span data-ttu-id="72cc6-149">La table mémoire optimisée Customers est accessible avec l'isolation d'instantané, comme défini par l'indicateur de table WITH (SNAPSHOT), et la table normale [Order History] est accessible avec l'isolation READ COMMITTED :</span><span class="sxs-lookup"><span data-stu-id="72cc6-149">The memory-optimized table Customers is accessed under snapshot isolation, as indicated through the table hint WITH (SNAPSHOT), and the regular table [Order History] is accessed under read committed isolation:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a><span data-ttu-id="72cc6-150">Différences de fonctionnement</span><span class="sxs-lookup"><span data-stu-id="72cc6-150">Operational Differences</span></span>  
 <span data-ttu-id="72cc6-151">Outre la garantie de lecture validée, il existe deux autres points clés dont il faut tenir compte lors de l'implémentation d'applications qui utilisent des tables sur disque.</span><span class="sxs-lookup"><span data-stu-id="72cc6-151">Besides the read committed guarantee, there are also two key implementation details that applications using disk-based tables may rely on.</span></span> <span data-ttu-id="72cc6-152">Tenez compte des points suivants lors de la conversion d'une table sur disque accessible avec l'isolation READ COMMITTED vers une table mémoire optimisée accessible avec l'isolation SNAPSHOT :</span><span class="sxs-lookup"><span data-stu-id="72cc6-152">Be aware of the following when converting a disk-based table that is accessed using READ COMMITTED isolation to a memory-optimized table that is accessed using SNAPSHOT isolation:</span></span>  
  
-   <span data-ttu-id="72cc6-153">L'implémentation du niveau d'isolation READ COMMITTED pour les tables sur disque (en supposant que READ_COMMITTED_SNAPSHOT est désactivé (OFF)) utilise des verrous pour éviter les conflits entre les lecteurs et les enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="72cc6-153">The implementation of the READ COMMITTED isolation level for disk-based tables (assuming READ_COMMITTED_SNAPSHOT is OFF) uses locks to prevent conflicts between readers and writers.</span></span> <span data-ttu-id="72cc6-154">Lorsqu'un enregistreur commence à mettre à jour une ligne, il prend un verrou et ne le libère pas tant que la transaction n'est pas validée.</span><span class="sxs-lookup"><span data-stu-id="72cc6-154">When a writer starts updating a row, it takes a lock and does not release the lock until the transaction is committed.</span></span> <span data-ttu-id="72cc6-155">Toutes les opérations de lecture sont bloquées et attendent la validation de la transaction d'écriture.</span><span class="sxs-lookup"><span data-stu-id="72cc6-155">Any read operations are blocked and will wait for the write transaction to commit.</span></span>  
  
     <span data-ttu-id="72cc6-156">Certaines applications peuvent supposer que les lecteurs attendent toujours la validation des enregistreurs, notamment s'il y a une synchronisation entre les deux transactions dans la couche Application.</span><span class="sxs-lookup"><span data-stu-id="72cc6-156">Some applications may assume readers always wait for writers to commit, particularly if there is any synchronization between the two transactions in the application tier.</span></span>  
  
     <span data-ttu-id="72cc6-157">**Recommandations :** Les applications ne peuvent pas reposer sur le comportement de blocage.</span><span class="sxs-lookup"><span data-stu-id="72cc6-157">**Guideline:** Applications cannot rely on blocking behavior.</span></span> <span data-ttu-id="72cc6-158">Si une application a besoin d’une synchronisation entre des transactions simultanées, une telle logique peut être implémentée dans la couche application ou dans la couche base de données, via [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="72cc6-158">If an application needs synchronization between concurrent transactions, such logic can be implemented in the application tier or in the database tier, through [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span></span>  
  
-   <span data-ttu-id="72cc6-159">Dans les transactions qui utilisent l'isolation READ COMMITTED, chaque instruction voit la dernière version des lignes dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="72cc6-159">In transactions that use READ COMMITTED isolation, each statement sees the most recent version of the rows in the database.</span></span> <span data-ttu-id="72cc6-160">Par conséquent, les instructions suivantes voient les modifications de l'état de la base de données.</span><span class="sxs-lookup"><span data-stu-id="72cc6-160">Therefore, subsequent statements see changes in the state of the database.</span></span>  
  
     <span data-ttu-id="72cc6-161">Interroger une table avec une boucle WHILE jusqu'à ce qu'une nouvelle ligne soit détectée est un exemple de modèle d'application qui utilise cette hypothèse.</span><span class="sxs-lookup"><span data-stu-id="72cc6-161">Polling a table using a WHILE loop until a new row has been found is an example of an application pattern that uses this assumption.</span></span> <span data-ttu-id="72cc6-162">Avec chaque itération de la boucle, la requête verra les dernières mises à jour dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="72cc6-162">With each iteration of the loop, the query will see the latest updates in the database.</span></span>  
  
     <span data-ttu-id="72cc6-163">**Recommandations :** Si une application doit interroger une table optimisée en mémoire pour obtenir les lignes les plus récentes écrites dans la table, déplacez la boucle d’interrogation en dehors de l’étendue de la transaction.</span><span class="sxs-lookup"><span data-stu-id="72cc6-163">**Guideline:** If an application needs to poll a memory-optimized table to obtain the most recent rows written to the table, move the polling loop outside the scope of the transaction.</span></span>  
  
     <span data-ttu-id="72cc6-164">Voici un exemple de modèle d'application qui utilise cette hypothèse.</span><span class="sxs-lookup"><span data-stu-id="72cc6-164">The following is an example application pattern that uses this assumption.</span></span> <span data-ttu-id="72cc6-165">Interroger une table avec une boucle WHILE jusqu'à ce qu'une nouvelle ligne soit détectée.</span><span class="sxs-lookup"><span data-stu-id="72cc6-165">Polling a table using a WHILE loop until a new row is found.</span></span> <span data-ttu-id="72cc6-166">Dans chaque itération de la boucle, la requête accède aux dernières mises à jour dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="72cc6-166">In each loop iteration, the query will access the latest updates in the database.</span></span>  
  
 <span data-ttu-id="72cc6-167">L'exemple de script suivant interroge une table t1 jusqu'à ce qu'il obtienne une ligne.</span><span class="sxs-lookup"><span data-stu-id="72cc6-167">The following example script polls a table t1 until it has a row.</span></span> <span data-ttu-id="72cc6-168">Une seule ligne de la table est ensuite supprimée pour un traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="72cc6-168">It then removes a single row from the table for further processing.</span></span>  
  
 <span data-ttu-id="72cc6-169">Notez que la logique d'interrogation doit être en dehors de l'étendue de la transaction, car elle utilise l'isolation d'instantané pour accéder à la table t1.</span><span class="sxs-lookup"><span data-stu-id="72cc6-169">Notice that the polling logic needs to be outside the scope of the transaction, as it is using snapshot isolation to access table t1.</span></span> <span data-ttu-id="72cc6-170">L'utilisation de la logique d'interrogation au sein de l'étendue d'une transaction créerait une transaction longue, ce qui est une mauvaise pratique.</span><span class="sxs-lookup"><span data-stu-id="72cc6-170">Using polling logic inside the scope of a transaction would create a long-running transaction, which is a bad practice.</span></span>  
  
```sql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a><span data-ttu-id="72cc6-171">Indicateurs de table de verrouillage</span><span class="sxs-lookup"><span data-stu-id="72cc6-171">Locking Table Hints</span></span>  
 <span data-ttu-id="72cc6-172">Les indicateurs de verrouillage ([indicateurs de Table &#40;&#41;Transact-SQL ](/sql/t-sql/queries/hints-transact-sql-table)) tels que HOLDLOCK et XLOCK peuvent être utilisés avec des tables sur disque pour avoir [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] plus de verrous que nécessaire pour le niveau d’isolation spécifié.</span><span class="sxs-lookup"><span data-stu-id="72cc6-172">Locking hints ([Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) such as HOLDLOCK and XLOCK can be used with disk-based tables to have [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] take more locks than are required for the specified isolation level.</span></span>  
  
 <span data-ttu-id="72cc6-173">Les tables mémoire optimisées n'utilisent pas de verrous.</span><span class="sxs-lookup"><span data-stu-id="72cc6-173">Memory-optimized tables do not use locks.</span></span> <span data-ttu-id="72cc6-174">Des niveaux d'isolation plus élevés comme REPEATABLE READ et SERIALIZABLE peuvent être utilisés pour déclarer les garanties de votre choix.</span><span class="sxs-lookup"><span data-stu-id="72cc6-174">Higher isolation levels such as REPEATABLE READ and SERIALIZABLE can be used to declare the desired guarantees.</span></span>  
  
 <span data-ttu-id="72cc6-175">Les indicateurs de verrouillage ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="72cc6-175">Locking hints are not supported.</span></span> <span data-ttu-id="72cc6-176">En revanche, déclarez les garanties requises via les niveaux d'isolation des transactions.</span><span class="sxs-lookup"><span data-stu-id="72cc6-176">Instead, declare the required guarantees through the transaction isolation levels.</span></span> <span data-ttu-id="72cc6-177">(NOLOCK est pris en charge, car [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'utilise pas de verrous sur les tables mémoire optimisées.</span><span class="sxs-lookup"><span data-stu-id="72cc6-177">(NOLOCK is supported because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not take locks on memory-optimized tables.</span></span> <span data-ttu-id="72cc6-178">Notez que contrairement, aux tables sur disque, NOLOCK n'implique pas le comportement UNCOMMITTED READ pour les tables mémoire optimisées.)</span><span class="sxs-lookup"><span data-stu-id="72cc6-178">Note that, in contrast to disk-based tables, NOLOCK does not imply READ UNCOMMITTED behavior for memory-optimized tables.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cc6-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72cc6-179">See Also</span></span>  
 <span data-ttu-id="72cc6-180">[Fonctionnement des transactions sur les tables optimisées en mémoire](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="72cc6-180">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="72cc6-181">[Instructions relatives à la logique de nouvelle tentative pour les transactions sur les tables optimisées en mémoire](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="72cc6-181">[Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="72cc6-182">Niveaux d'isolement des transactions</span><span class="sxs-lookup"><span data-stu-id="72cc6-182">Transaction Isolation Levels</span></span>](../../2014/database-engine/transaction-isolation-levels.md)  
  
  