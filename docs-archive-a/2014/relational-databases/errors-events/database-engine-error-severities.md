---
title: Niveaux de gravité des erreurs du moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- user-defined error messages [SQL Server]
- severity levels [SQL Server]
- retrieving error severity
- errors [SQL Server], severity
- TRY...CATCH [SQL Server]
ms.assetid: 3e7f5925-6edd-42e1-bf17-f7deb03993a7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: acd8ec235d357853266b0419024ae406fa62fb90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704135"
---
# <a name="database-engine-error-severities"></a><span data-ttu-id="785cf-102">Niveaux de gravité des erreurs du moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="785cf-102">Database Engine Error Severities</span></span>
  <span data-ttu-id="785cf-103">Lorsqu'une erreur est déclenchée par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], la gravité de l'erreur indique le type de problème rencontré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="785cf-103">When an error is raised by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the severity of the error indicates the type of problem encountered by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="levels-of-severity"></a><span data-ttu-id="785cf-104">Niveaux de gravité</span><span class="sxs-lookup"><span data-stu-id="785cf-104">Levels of Severity</span></span>  
 <span data-ttu-id="785cf-105">Le tableau suivant répertorie et décrit les niveaux de gravité des erreurs déclenchées par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="785cf-105">The following table lists and describes the severity levels of the errors raised by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
|<span data-ttu-id="785cf-106">Niveau de gravité</span><span class="sxs-lookup"><span data-stu-id="785cf-106">Severity level</span></span>|<span data-ttu-id="785cf-107">Description</span><span class="sxs-lookup"><span data-stu-id="785cf-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="785cf-108">0-9</span><span class="sxs-lookup"><span data-stu-id="785cf-108">0-9</span></span>|<span data-ttu-id="785cf-109">Messages qui retournent des informations d'état ou qui signalent des erreurs sans gravité.</span><span class="sxs-lookup"><span data-stu-id="785cf-109">Informational messages that return status information or report errors that are not severe.</span></span> <span data-ttu-id="785cf-110">Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne déclenche pas d'erreurs système dont les niveaux de gravité sont compris entre 0 et 9.</span><span class="sxs-lookup"><span data-stu-id="785cf-110">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not raise system errors with severities of 0 through 9.</span></span>|  
|<span data-ttu-id="785cf-111">10</span><span class="sxs-lookup"><span data-stu-id="785cf-111">10</span></span>|<span data-ttu-id="785cf-112">Messages qui retournent des informations d'état ou qui signalent des erreurs sans gravité.</span><span class="sxs-lookup"><span data-stu-id="785cf-112">Informational messages that return status information or report errors that are not severe.</span></span> <span data-ttu-id="785cf-113">Pour des raisons de compatibilité, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] convertit le niveau de gravité 10 en 0 avant de retourner les informations d'erreur à l'application appelante.</span><span class="sxs-lookup"><span data-stu-id="785cf-113">For compatibility reasons, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] converts severity 10 to severity 0 before returning the error information to the calling application.</span></span>|  
|<span data-ttu-id="785cf-114">11-16</span><span class="sxs-lookup"><span data-stu-id="785cf-114">11-16</span></span>|<span data-ttu-id="785cf-115">Indique les erreurs pouvant être corrigées par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="785cf-115">Indicate errors that can be corrected by the user.</span></span>|  
|<span data-ttu-id="785cf-116">11</span><span class="sxs-lookup"><span data-stu-id="785cf-116">11</span></span>|<span data-ttu-id="785cf-117">Indique que l'objet ou l'entité spécifique n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="785cf-117">Indicates that the given object or entity does not exist.</span></span>|  
|<span data-ttu-id="785cf-118">12</span><span class="sxs-lookup"><span data-stu-id="785cf-118">12</span></span>|<span data-ttu-id="785cf-119">Niveau de gravité particulier pour les requêtes qui n'utilisent pas de verrouillage en raison d'indicateurs de requête spéciaux.</span><span class="sxs-lookup"><span data-stu-id="785cf-119">A special severity for queries that do not use locking because of special query hints.</span></span> <span data-ttu-id="785cf-120">Dans certains cas, les opérations de lecture effectuées par ces instructions peuvent produire des données incohérentes, car les verrouillages ne sont pas effectués pour garantir la cohérence.</span><span class="sxs-lookup"><span data-stu-id="785cf-120">In some cases, read operations performed by these statements could result in inconsistent data, since locks are not taken to guarantee consistency.</span></span>|  
|<span data-ttu-id="785cf-121">13</span><span class="sxs-lookup"><span data-stu-id="785cf-121">13</span></span>|<span data-ttu-id="785cf-122">Indique des erreurs de blocage de transaction.</span><span class="sxs-lookup"><span data-stu-id="785cf-122">Indicates transaction deadlock errors.</span></span>|  
|<span data-ttu-id="785cf-123">14</span><span class="sxs-lookup"><span data-stu-id="785cf-123">14</span></span>|<span data-ttu-id="785cf-124">Indique des erreurs liées à la sécurité, par exemple le refus d'une autorisation.</span><span class="sxs-lookup"><span data-stu-id="785cf-124">Indicates security-related errors, such as permission denied.</span></span>|  
|<span data-ttu-id="785cf-125">15</span><span class="sxs-lookup"><span data-stu-id="785cf-125">15</span></span>|<span data-ttu-id="785cf-126">Indique des erreurs de syntaxe dans la commande [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="785cf-126">Indicates syntax errors in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>|  
|<span data-ttu-id="785cf-127">16</span><span class="sxs-lookup"><span data-stu-id="785cf-127">16</span></span>|<span data-ttu-id="785cf-128">Indique des erreurs générales qui peuvent être corrigées par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="785cf-128">Indicates general errors that can be corrected by the user.</span></span>|  
|<span data-ttu-id="785cf-129">17-19</span><span class="sxs-lookup"><span data-stu-id="785cf-129">17-19</span></span>|<span data-ttu-id="785cf-130">Indique des erreurs logicielles qui ne peuvent pas être corrigées par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="785cf-130">Indicate software errors that cannot be corrected by the user.</span></span> <span data-ttu-id="785cf-131">Informez votre administrateur système de l'existence du problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-131">Inform your system administrator of the problem.</span></span>|  
|<span data-ttu-id="785cf-132">17</span><span class="sxs-lookup"><span data-stu-id="785cf-132">17</span></span>|<span data-ttu-id="785cf-133">Indique que l'instruction a obligé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à s'exécuter avec des ressources insuffisantes (mémoire, verrous ou espace disque de la base de données) ou à dépasser une limite fixée par l'administrateur système.</span><span class="sxs-lookup"><span data-stu-id="785cf-133">Indicates that the statement caused [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run out of resources (such as memory, locks, or disk space for the database) or to exceed some limit set by the system administrator.</span></span>|  
|<span data-ttu-id="785cf-134">18</span><span class="sxs-lookup"><span data-stu-id="785cf-134">18</span></span>|<span data-ttu-id="785cf-135">Indique l'existence d'un problème logiciel avec le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ; toutefois, l'instruction s'exécute intégralement et la connexion à l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est conservée.</span><span class="sxs-lookup"><span data-stu-id="785cf-135">Indicates a problem in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] software, but the statement completes execution, and the connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is maintained.</span></span> <span data-ttu-id="785cf-136">L'administrateur système doit être informé chaque fois qu'un message s'affiche avec le niveau de gravité 18.</span><span class="sxs-lookup"><span data-stu-id="785cf-136">The system administrator should be informed every time a message with a severity level of 18 occurs.</span></span>|  
|<span data-ttu-id="785cf-137">19</span><span class="sxs-lookup"><span data-stu-id="785cf-137">19</span></span>|<span data-ttu-id="785cf-138">Indique qu'une limite non configurable du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est dépassée et que le traitement est terminé.</span><span class="sxs-lookup"><span data-stu-id="785cf-138">Indicates that a nonconfigurable [!INCLUDE[ssDE](../../includes/ssde-md.md)] limit has been exceeded and the current batch process has been terminated.</span></span> <span data-ttu-id="785cf-139">Les messages d'erreur dont le niveau de gravité est supérieur ou égal à 19 arrêtent l'exécution du traitement actuel.</span><span class="sxs-lookup"><span data-stu-id="785cf-139">Error messages with a severity level of 19 or higher stop the execution of the current batch.</span></span> <span data-ttu-id="785cf-140">Les erreurs dont le niveau de gravité est 19 se produisent rarement ; elles doivent être résolues par l'administrateur système ou votre support technique.</span><span class="sxs-lookup"><span data-stu-id="785cf-140">Severity level 19 errors are rare and must be corrected by the system administrator or your primary support provider.</span></span> <span data-ttu-id="785cf-141">Contactez votre administrateur système en cas de déclenchement d'un message dont le niveau de gravité est 19.</span><span class="sxs-lookup"><span data-stu-id="785cf-141">Contact your system administrator when a message with a severity level 19 is raised.</span></span> <span data-ttu-id="785cf-142">Les messages d’erreur dont le niveau de gravité est compris entre 19 et 25 sont inscrits dans le journal des erreurs.</span><span class="sxs-lookup"><span data-stu-id="785cf-142">Error messages with a severity level from 19 through 25 are written to the error log.</span></span>|  
|<span data-ttu-id="785cf-143">20-24</span><span class="sxs-lookup"><span data-stu-id="785cf-143">20-24</span></span>|<span data-ttu-id="785cf-144">Indique l'existence de problèmes système et d'erreurs irrécupérables, ce qui signifie que la tâche du [!INCLUDE[ssDE](../../includes/ssde-md.md)] exécutant une instruction ou un traitement n'est plus en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="785cf-144">Indicate system problems and are fatal errors, which means that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] task that is executing a statement or batch is no longer running.</span></span> <span data-ttu-id="785cf-145">La tâche enregistre des informations sur ce qui s'est produit, puis se termine.</span><span class="sxs-lookup"><span data-stu-id="785cf-145">The task records information about what occurred and then terminates.</span></span> <span data-ttu-id="785cf-146">Dans la plupart des cas, la connexion de l'application à l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] se termine également.</span><span class="sxs-lookup"><span data-stu-id="785cf-146">In most cases, the application connection to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] may also terminate.</span></span> <span data-ttu-id="785cf-147">Si cela se produit, selon la nature du problème, l'application risque de ne pas pouvoir se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="785cf-147">If this happens, depending on the problem, the application might not be able to reconnect.</span></span><br /><br /> <span data-ttu-id="785cf-148">Les messages d'erreur de ce niveau peuvent affecter tous les processus qui accèdent aux données de la même base de données et indiquer la détérioration d'une base de données ou d'un objet.</span><span class="sxs-lookup"><span data-stu-id="785cf-148">Error messages in this range can affect all of the processes accessing data in the same database and may indicate that a database or object is damaged.</span></span> <span data-ttu-id="785cf-149">Les messages d'erreur dont le niveau de gravité est compris entre 19 et 24 sont inscrits dans le journal des erreurs.</span><span class="sxs-lookup"><span data-stu-id="785cf-149">Error messages with a severity level from 19 through 24 are written to the error log.</span></span>|  
|<span data-ttu-id="785cf-150">20</span><span class="sxs-lookup"><span data-stu-id="785cf-150">20</span></span>|<span data-ttu-id="785cf-151">Indique qu'une instruction a rencontré un problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-151">Indicates that a statement has encountered a problem.</span></span> <span data-ttu-id="785cf-152">Dans la mesure où le problème affecte uniquement la tâche actuelle, il est improbable que la base de données elle-même soit endommagée.</span><span class="sxs-lookup"><span data-stu-id="785cf-152">Because the problem has affected only the current task, it is unlikely that the database itself has been damaged.</span></span>|  
|<span data-ttu-id="785cf-153">21</span><span class="sxs-lookup"><span data-stu-id="785cf-153">21</span></span>|<span data-ttu-id="785cf-154">Indique qu'un problème a été rencontré et qu'il affecte toutes les tâches de la base de données actuelle ; toutefois, il est improbable que la base de données elle-même soit endommagée.</span><span class="sxs-lookup"><span data-stu-id="785cf-154">Indicates that a problem has been encountered that affects all tasks in the current database, but it is unlikely that the database itself has been damaged.</span></span>|  
|<span data-ttu-id="785cf-155">22</span><span class="sxs-lookup"><span data-stu-id="785cf-155">22</span></span>|<span data-ttu-id="785cf-156">Indique que la table ou l'index spécifié dans le message a été endommagé à la suite d'un problème logiciel ou matériel.</span><span class="sxs-lookup"><span data-stu-id="785cf-156">Indicates that the table or index specified in the message has been damaged by a software or hardware problem.</span></span><br /><br /> <span data-ttu-id="785cf-157">Les erreurs dont le niveau de gravité est 22 se produisent rarement.</span><span class="sxs-lookup"><span data-stu-id="785cf-157">Severity level 22 errors occur rarely.</span></span> <span data-ttu-id="785cf-158">Si ce type d'erreur se produit, exécutez DBCC CHECKDB pour déterminer si d'autres objets de la base de données sont également endommagés.</span><span class="sxs-lookup"><span data-stu-id="785cf-158">If one occurs, run DBCC CHECKDB to determine whether other objects in the database are also damaged.</span></span> <span data-ttu-id="785cf-159">Il est possible que le problème provienne uniquement du cache des tampons et non du disque lui-même.</span><span class="sxs-lookup"><span data-stu-id="785cf-159">The problem might be in the buffer cache only and not on the disk itself.</span></span> <span data-ttu-id="785cf-160">Dans ce cas, le redémarrage de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] permet de corriger le problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-160">If so, restarting the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] corrects the problem.</span></span> <span data-ttu-id="785cf-161">Pour pouvoir continuer à travailler, vous devez vous reconnecter à l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]; dans le cas contraire, utilisez DBCC pour corriger le problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-161">To continue working, you must reconnect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]; otherwise, use DBCC to repair the problem.</span></span> <span data-ttu-id="785cf-162">Dans certains cas, vous pouvez être amené à restaurer la base de données.</span><span class="sxs-lookup"><span data-stu-id="785cf-162">In some cases, you may have to restore the database.</span></span><br /><br /> <span data-ttu-id="785cf-163">Si le redémarrage de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne permet pas de corriger le problème, cela signifie que ce dernier provient du disque.</span><span class="sxs-lookup"><span data-stu-id="785cf-163">If restarting the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not correct the problem, then the problem is on the disk.</span></span> <span data-ttu-id="785cf-164">Dans certains cas, il peut être résolu en détruisant l'objet spécifié dans le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="785cf-164">Sometimes destroying the object specified in the error message can solve the problem.</span></span> <span data-ttu-id="785cf-165">Par exemple, si le message indique que l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] a trouvé une ligne de longueur 0 dans un index non-cluster, supprimez l'index et reconstruisez-le.</span><span class="sxs-lookup"><span data-stu-id="785cf-165">For example, if the message reports that the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] has found a row with a length of 0 in a nonclustered index, delete the index and rebuild it.</span></span>|  
|<span data-ttu-id="785cf-166">23</span><span class="sxs-lookup"><span data-stu-id="785cf-166">23</span></span>|<span data-ttu-id="785cf-167">Indique que l'intégrité de la totalité de la base de données est douteuse en raison d'un problème matériel ou logiciel.</span><span class="sxs-lookup"><span data-stu-id="785cf-167">Indicates that the integrity of the entire database is in question because of a hardware or software problem.</span></span><br /><br /> <span data-ttu-id="785cf-168">Les erreurs dont le niveau de gravité est 23 se produisent rarement.</span><span class="sxs-lookup"><span data-stu-id="785cf-168">Severity level 23 errors occur rarely.</span></span> <span data-ttu-id="785cf-169">Si ce type d'erreur se produit, exécutez DBCC CHECKDB pour déterminer l'étendue des dommages.</span><span class="sxs-lookup"><span data-stu-id="785cf-169">If one occurs, run DBCC CHECKDB to determine the extent of the damage.</span></span> <span data-ttu-id="785cf-170">Il est possible que le problème provienne uniquement du cache et non du disque lui-même.</span><span class="sxs-lookup"><span data-stu-id="785cf-170">The problem might be in the cache only and not on the disk itself.</span></span> <span data-ttu-id="785cf-171">Dans ce cas, le redémarrage de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] permet de corriger le problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-171">If so, restarting the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] corrects the problem.</span></span> <span data-ttu-id="785cf-172">Pour pouvoir continuer à travailler, vous devez vous reconnecter à l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]; dans le cas contraire, utilisez DBCC pour corriger le problème.</span><span class="sxs-lookup"><span data-stu-id="785cf-172">To continue working, you must reconnect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]; otherwise, use DBCC to repair the problem.</span></span> <span data-ttu-id="785cf-173">Dans certains cas, vous pouvez être amené à restaurer la base de données.</span><span class="sxs-lookup"><span data-stu-id="785cf-173">In some cases, you may have to restore the database.</span></span>|  
|<span data-ttu-id="785cf-174">24</span><span class="sxs-lookup"><span data-stu-id="785cf-174">24</span></span>|<span data-ttu-id="785cf-175">Indique une défaillance du support.</span><span class="sxs-lookup"><span data-stu-id="785cf-175">Indicates a media failure.</span></span> <span data-ttu-id="785cf-176">L'administrateur système peut être obligé de restaurer la base de données.</span><span class="sxs-lookup"><span data-stu-id="785cf-176">The system administrator may have to restore the database.</span></span> <span data-ttu-id="785cf-177">Vous pouvez également être amené à contacter le fournisseur de votre matériel.</span><span class="sxs-lookup"><span data-stu-id="785cf-177">You may also have to call your hardware vendor.</span></span>|  
  
## <a name="user-defined-error-message-severity"></a><span data-ttu-id="785cf-178">Niveau de gravité des messages d'erreur définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="785cf-178">User-Defined Error Message Severity</span></span>  
 <span data-ttu-id="785cf-179">**sp_addmessage** permet d’ajouter à l’affichage catalogue **sys.messages** des messages d’erreur définis par l’utilisateur et dont les niveaux de gravité vont de 1 à 25.</span><span class="sxs-lookup"><span data-stu-id="785cf-179">**sp_addmessage** can be used to add user-defined error messages with severities from 1 through 25 to the **sys.messages** catalog view.</span></span> <span data-ttu-id="785cf-180">Ces messages d'erreur définis par l'utilisateur peuvent être utilisés par RAISERROR.</span><span class="sxs-lookup"><span data-stu-id="785cf-180">These user-defined error messages can be used by RAISERROR.</span></span> <span data-ttu-id="785cf-181">Pour plus d’informations, consultez [sp_addmessage &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="785cf-181">For more information, see [sp_addmessage &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span></span>  
  
 <span data-ttu-id="785cf-182">RAISERROR permet de générer des messages d'erreur définis par l'utilisateur et dont les niveaux de gravité vont de 1 à 25.</span><span class="sxs-lookup"><span data-stu-id="785cf-182">RAISERROR can be used to generate user-defined error messages with severities from 1 through 25.</span></span> <span data-ttu-id="785cf-183">RAISERROR peut faire référence à un message d’erreur défini par l’utilisateur et stocké dans l’affichage catalogue **sys.messages** ou générer un message de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="785cf-183">RAISERROR can reference a user-defined error message stored in the **sys.messages** catalog view or build a message dynamically.</span></span> <span data-ttu-id="785cf-184">Lors de l’utilisation du message d’erreur défini par l’utilisateur dans **sys.messages** au cours de la génération d’une erreur, le niveau de gravité spécifié par RAISERROR remplace celui spécifié dans **sys.messages**.</span><span class="sxs-lookup"><span data-stu-id="785cf-184">When using the user-defined error message in **sys.messages** while generating an error, the severity specified by RAISERROR overrides the severity specified in **sys.messages**.</span></span> <span data-ttu-id="785cf-185">Pour plus d’informations, consultez [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="785cf-185">For more information, see [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql).</span></span>  
  
## <a name="error-severity-and-trycatch"></a><span data-ttu-id="785cf-186">Gravité d’erreur et TRY...CATCH</span><span class="sxs-lookup"><span data-stu-id="785cf-186">Error Severity and TRY...CATCH</span></span>  
 <span data-ttu-id="785cf-187">Une construction TRY...CATCH intercepte toutes les erreurs d’exécution dont le niveau de gravité est supérieur à 10 et qui ne mettent pas fin à la connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="785cf-187">A TRY...CATCH construct catches all execution errors with severity greater than 10 that do not terminate the database connection.</span></span>  
  
 <span data-ttu-id="785cf-188">Les erreurs dont le niveau de gravité est compris entre 0 et 10 sont des messages d’information. Elles ne provoquent pas de saut d’exécution du bloc CATCH d’une construction TRY...CATCH.</span><span class="sxs-lookup"><span data-stu-id="785cf-188">Errors with severity from 0 through 10 are informational messages and do not cause execution to jump from the CATCH block of a TRY...CATCH construct.</span></span>  
  
 <span data-ttu-id="785cf-189">Les erreurs (dont le niveau est généralement compris entre 20 et 25) qui mettent fin à la connexion de base de données ne sont pas gérées par le bloc CATCH, car l'exécution est annulée lorsque la connexion est terminée.</span><span class="sxs-lookup"><span data-stu-id="785cf-189">Errors that terminate the database connection, usually with severity from 20 through 25, are not handled by the CATCH block because execution is aborted when the connection terminates.</span></span>  
  
 <span data-ttu-id="785cf-190">Pour plus d’informations, consultez [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="785cf-190">For more information, see [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span></span>  
  
## <a name="retrieving-error-severity"></a><span data-ttu-id="785cf-191">extraction de la gravité des erreurs</span><span class="sxs-lookup"><span data-stu-id="785cf-191">Retrieving Error Severity</span></span>  
 <span data-ttu-id="785cf-192">La fonction système ERROR_SEVERITY permet de récupérer le niveau de gravité de l’erreur qui a causé l’exécution du bloc CATCH d’une construction TRY...CATCH.</span><span class="sxs-lookup"><span data-stu-id="785cf-192">The ERROR_SEVERITY system function can be used to retrieve the severity of the error that caused the CATCH block of a TRY...CATCH construct to be run.</span></span> <span data-ttu-id="785cf-193">ERROR_SEVERITY retourne NULL s'il est appelé en dehors de la portée d'un bloc CATCH.</span><span class="sxs-lookup"><span data-stu-id="785cf-193">ERROR_SEVERITY returns NULL if called outside the scope of a CATCH block.</span></span> <span data-ttu-id="785cf-194">Pour plus d’informations, consultez [ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="785cf-194">For more information, see [ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785cf-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="785cf-195">See Also</span></span>  
 <span data-ttu-id="785cf-196">[Présentation des erreurs du moteur de base de données](../native-client-ole-db-errors/errors.md) </span><span class="sxs-lookup"><span data-stu-id="785cf-196">[Understanding Database Engine Errors](../native-client-ole-db-errors/errors.md) </span></span>  
 <span data-ttu-id="785cf-197">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span><span class="sxs-lookup"><span data-stu-id="785cf-197">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span></span>  
 <span data-ttu-id="785cf-198">[Fonctions système &#40;Transact-SQL&#41;](/sql/t-sql/functions/system-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="785cf-198">[System Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/system-functions-transact-sql) </span></span>  
 [<span data-ttu-id="785cf-199">TRY...CATCH &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="785cf-199">TRY...CATCH &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/try-catch-transact-sql)  
  
  