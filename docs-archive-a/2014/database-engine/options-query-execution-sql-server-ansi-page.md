---
title: Options (exécution de la requête-SQL Server-page ANSI) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAnsi
ms.assetid: 0f4c6887-0562-417e-806c-b5cffb1e7c5c
author: rothja
ms.author: jroth
ms.openlocfilehash: 198505c5d14b9fda510d4635dbaa3d3d49483ddf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613602"
---
# <a name="options-query-execution-sql-server-ansi-page"></a><span data-ttu-id="d318b-102">Options (exécution de la requête-SQL Server-page ANSI)</span><span class="sxs-lookup"><span data-stu-id="d318b-102">Options (Query Execution-SQL Server-ANSI Page)</span></span>
  <span data-ttu-id="d318b-103">Ensemble, ces options SET ANSI (ISO) définissent l'environnement de traitement des requêtes pour la durée de la requête de l'utilisateur, de l'exécution d'un déclencheur ou d'une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="d318b-103">Together, these ANSI (ISO) standard SET options define the query processing environment for the duration of the user's query, a running trigger, or a stored procedure.</span></span> <span data-ttu-id="d318b-104">Toutefois, ces options SET ne contiennent pas toutes les options requises pour assurer la conformité à la norme ISO.</span><span class="sxs-lookup"><span data-stu-id="d318b-104">These SET options, however, do not include all of the options required to conform to the ISO standard.</span></span> <span data-ttu-id="d318b-105">Utilisez cette page pour spécifier que [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exécute les requêtes à l’aide de l’ensemble ou d’une partie des paramètres spécifiés dans la norme ISO.</span><span class="sxs-lookup"><span data-stu-id="d318b-105">Use this page to specify that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will run the queries using all or a portion of the settings specified in the ISO standard.</span></span> <span data-ttu-id="d318b-106">Les modifications apportées à ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d318b-106">Changes to these options are applied only to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="d318b-107">Pour modifier les options des requêtes en cours, cliquez sur **options de requête** dans le menu **requête** ou cliquez avec le bouton droit dans la fenêtre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requête et sélectionnez **options de requête**.</span><span class="sxs-lookup"><span data-stu-id="d318b-107">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window and select **Query Options**.</span></span> <span data-ttu-id="d318b-108">Dans la boîte de dialogue **Options de requête** , sous **Exécution**, cliquez sur **ANSI**.</span><span class="sxs-lookup"><span data-stu-id="d318b-108">In the **Query Options** dialog box, under **Execution**, click **ANSI**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d318b-109">Liste d’éléments d’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="d318b-109">UI element list</span></span>  
 <span data-ttu-id="d318b-110">**SET ANSI_DEFAULTS**</span><span class="sxs-lookup"><span data-stu-id="d318b-110">**SET ANSI_DEFAULTS**</span></span>  
 <span data-ttu-id="d318b-111">Activez cette case à cocher pour sélectionner tous les paramètres ISO par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-111">Select this check box to select all of the default ISO settings.</span></span> <span data-ttu-id="d318b-112">Les options ISO ne sont pas toutes sélectionnées par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-112">Not all ISO options are selected by default.</span></span>  
  
 <span data-ttu-id="d318b-113">**SET QUOTED_IDENTIFIER**</span><span class="sxs-lookup"><span data-stu-id="d318b-113">**SET QUOTED_IDENTIFIER**</span></span>  
 <span data-ttu-id="d318b-114">Lorsque cette case à cocher est activée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suit les règles ISO relatives aux guillemets délimitant les identificateurs et les chaînes littérales.</span><span class="sxs-lookup"><span data-stu-id="d318b-114">When this check box is selected, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] follows the ISO rules regarding quotation mark delimiting identifiers and literal strings.</span></span> <span data-ttu-id="d318b-115">Les identificateurs entre guillemets peuvent être des mots clés Transact-SQL réservés ou contenir des caractères qui ne sont généralement pas autorisés dans les règles syntaxiques Transact-SQL se rapportant aux identificateurs.</span><span class="sxs-lookup"><span data-stu-id="d318b-115">Identifiers delimited by quotation marks can be either Transact-SQL reserved keywords or can contain characters not usually allowed by the Transact-SQL syntax rules for identifiers.</span></span> <span data-ttu-id="d318b-116">Cette case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-116">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="d318b-117">**SET ANSI_NULL_DFLT_ON**</span><span class="sxs-lookup"><span data-stu-id="d318b-117">**SET ANSI_NULL_DFLT_ON**</span></span>  
 <span data-ttu-id="d318b-118">Lorsque cette option est activée, tous les types de données définis par l'utilisateur ou les colonnes qui ne sont pas définies explicitement comme NOT NULL dans une instruction CREATE TABLE ou ALTER TABLE autorisent, par défaut, les valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="d318b-118">When this value is set, all user-defined data types or columns that are not explicitly defined as NOT NULL during a CREATE TABLE or ALTER TABLE statement default to allowing null values.</span></span> <span data-ttu-id="d318b-119">Cette case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-119">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="d318b-120">**SET IMPLICIT_TRANSACTIONS**</span><span class="sxs-lookup"><span data-stu-id="d318b-120">**SET IMPLICIT_TRANSACTIONS**</span></span>  
 <span data-ttu-id="d318b-121">Lorsque cette case à cocher est activée, SET IMPLICIT_TRANSACTIONS met la connexion en mode de transaction implicite.</span><span class="sxs-lookup"><span data-stu-id="d318b-121">When this check box is selected, SET IMPLICIT_TRANSACTIONS sets the connection into implicit transaction mode.</span></span> <span data-ttu-id="d318b-122">Lorsque la case à cocher est désactivée, la connexion revient en mode de validation automatique.</span><span class="sxs-lookup"><span data-stu-id="d318b-122">When this check box is cleared, it returns the connection to autocommit transaction mode.</span></span> <span data-ttu-id="d318b-123">Pour passer en revue les instructions qui démarrent une transaction implicite quand elles sont sélectionnées, consultez [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-implicit-transactions-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="d318b-123">To review the statements that start an implicit transaction when selected, see [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-implicit-transactions-transact-sql).</span></span> <span data-ttu-id="d318b-124">Cette case à cocher est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-124">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="d318b-125">**SET CURSOR_CLOSE_ON_COMMIT**</span><span class="sxs-lookup"><span data-stu-id="d318b-125">**SET CURSOR_CLOSE_ON_COMMIT**</span></span>  
 <span data-ttu-id="d318b-126">Lorsque cette case à cocher est activée, tous les curseurs ouverts sont fermés automatiquement (conformément à ISO) lors de la validation d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="d318b-126">When this check box is selected, any open cursors are closed automatically (in compliance with ISO) when a transaction is committed.</span></span> <span data-ttu-id="d318b-127">Lorsque cette option est désactivée, les curseurs restent ouverts d'une transaction à l'autre, ne se fermant que lors de la fermeture de la connexion ou sur demande explicite.</span><span class="sxs-lookup"><span data-stu-id="d318b-127">When this value is set to OFF, cursors remain open across transaction boundaries, closing only when the connection is closed or when they are explicitly closed.</span></span> <span data-ttu-id="d318b-128">Cette case à cocher est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-128">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="d318b-129">**SET ANSI_PADDING**</span><span class="sxs-lookup"><span data-stu-id="d318b-129">**SET ANSI_PADDING**</span></span>  
 <span data-ttu-id="d318b-130">Contrôle la façon dont la colonne stocke les noms de valeurs dont la longueur est inférieure à la taille définie pour la colonne et les valeurs contenant des espaces de fin pour les données de type **char**, **varchar**, **binary**et **varbinary** .</span><span class="sxs-lookup"><span data-stu-id="d318b-130">Controls the way the column stores value names shorter than the defined size of the column, and the way the column stores values that have trailing blanks in **char**, **varchar**, **binary**, and **varbinary** data.</span></span> <span data-ttu-id="d318b-131">Cette valeur affecte uniquement la définition de nouvelles colonnes.</span><span class="sxs-lookup"><span data-stu-id="d318b-131">This setting affects only the definition of new columns.</span></span> <span data-ttu-id="d318b-132">Une fois la colonne créée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stocke les valeurs en fonction du paramètre en vigueur lors de la création de la colonne.</span><span class="sxs-lookup"><span data-stu-id="d318b-132">After the column is created, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the values based on the setting when the column was created.</span></span> <span data-ttu-id="d318b-133">Les colonnes existantes ne sont pas affectées par toute modification ultérieure du paramètre.</span><span class="sxs-lookup"><span data-stu-id="d318b-133">Existing columns are not affected by a later change to this setting.</span></span> <span data-ttu-id="d318b-134">Cette case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-134">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="d318b-135">**SET ANSI_WARNINGS**</span><span class="sxs-lookup"><span data-stu-id="d318b-135">**SET ANSI_WARNINGS**</span></span>  
 <span data-ttu-id="d318b-136">Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur :</span><span class="sxs-lookup"><span data-stu-id="d318b-136">Specifies ISO standard behavior for several error conditions:</span></span>  
  
-   <span data-ttu-id="d318b-137">Lorsque cette case à cocher est activée, si des valeurs de type NULL apparaissent dans des fonctions d'agrégation (telles que SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP ou COUNT), le système génère un message d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="d318b-137">When this check box is selected, if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT), a warning message is generated.</span></span> <span data-ttu-id="d318b-138">Lorsque cette case à cocher est désactivée, aucun avertissement n'est émis.</span><span class="sxs-lookup"><span data-stu-id="d318b-138">When OFF, no warning is issued.</span></span>  
  
-   <span data-ttu-id="d318b-139">Lorsque cette case à cocher est activée, les erreurs de division par zéro et de dépassement arithmétique provoquent l'annulation de l'instruction et l'émission d'un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="d318b-139">When this check box is cleared, divide-by-zero and arithmetic overflow errors cause the statement to be rolled back and an error message to be generated.</span></span> <span data-ttu-id="d318b-140">Lorsque la valeur est OFF, les erreurs de division par zéro et de dépassement arithmétique entraînent le renvoi de valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="d318b-140">When OFF, divide-by-zero and arithmetic overflow errors cause null values to be returned.</span></span> <span data-ttu-id="d318b-141">Une erreur de division par zéro ou de dépassement arithmétique provoque le retour de valeurs NULL si une opération INSERT ou UPDATE est tentée sur une colonne de type **character**, **Unicode** ou **binary** contenant une nouvelle valeur dont la longueur est supérieure à la taille maximale de la colonne.</span><span class="sxs-lookup"><span data-stu-id="d318b-141">The behavior in which a divide-by-zero or arithmetic overflow error causes null values to be returned occurs if an INSERT or UPDATE operation is attempted on a **character**, **Unicode**, or **binary** column in which the length of a new value exceeds the maximum size of the column.</span></span> <span data-ttu-id="d318b-142">Conformément à la norme ISO, si l'option SET ANSI_WARNINGS est activée, l'opération INSERT ou UPDATE est annulée.</span><span class="sxs-lookup"><span data-stu-id="d318b-142">If SET ANSI_WARNINGS is ON, the INSERT or UPDATE operation is canceled as specified by the ISO standard.</span></span> <span data-ttu-id="d318b-143">Les espaces blancs sont ignorés dans des colonnes de type caractère et les zéros sont ignorés dans les colonnes de type binaire.</span><span class="sxs-lookup"><span data-stu-id="d318b-143">Trailing blanks are ignored for character columns and trailing nulls are ignored for binary columns.</span></span> <span data-ttu-id="d318b-144">Lorsque la valeur est définie à OFF, les données sont tronquées de façon à correspondre à la taille de la colonne, et l'instruction s'exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="d318b-144">When OFF, data is truncated to the size of the column and the statement succeeds.</span></span>  
  
 <span data-ttu-id="d318b-145">Cette case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-145">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="d318b-146">**SET ANSI_NULLS**</span><span class="sxs-lookup"><span data-stu-id="d318b-146">**SET ANSI_NULLS**</span></span>  
 -   <span data-ttu-id="d318b-147">Spécifie le comportement conforme à la norme ISO pour les opérateurs de comparaison égal à (=) et différent de (<>), lorsqu'ils sont utilisés avec des valeurs Null.</span><span class="sxs-lookup"><span data-stu-id="d318b-147">Specifies ISO compliant behavior of the equals (=) and not equal to (<>) comparison operators when used with null values.</span></span> <span data-ttu-id="d318b-148">Conformément à la norme ISO, lorsque l'option SET ANSI_NULLS est activée, toutes les comparaisons effectuées par rapport à une valeur NULL renvoient la valeur UNKNOWN (inconnu).</span><span class="sxs-lookup"><span data-stu-id="d318b-148">When SET ANSI_NULLS is selected, all comparisons against a null value evaluate to UNKNOWN, the ISO compliant behavior.</span></span> <span data-ttu-id="d318b-149">Lorsque l'option SET ANSI_NULLS n'est pas activée, toutes les comparaisons effectuées par rapport à une valeur NULL renvoient la valeur TRUE.</span><span class="sxs-lookup"><span data-stu-id="d318b-149">When SET ANSI_NULLS is not selected, comparisons of all data against a null value evaluate to TRUE.</span></span> <span data-ttu-id="d318b-150">Cette case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="d318b-150">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="d318b-151">**Rétablir les valeurs par défaut**</span><span class="sxs-lookup"><span data-stu-id="d318b-151">**Reset to Default**</span></span>  
 <span data-ttu-id="d318b-152">Rétablit toutes les valeurs par défaut initiales des options de cette page.</span><span class="sxs-lookup"><span data-stu-id="d318b-152">Resets all values on this page to the original default values.</span></span>  
  
  