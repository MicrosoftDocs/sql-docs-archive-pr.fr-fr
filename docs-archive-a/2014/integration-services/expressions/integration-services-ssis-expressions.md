---
title: Expressions Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff0bd46034108537ebede7567b042997c94871ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701436"
---
# <a name="integration-services-ssis-expressions"></a><span data-ttu-id="99549-102">Expressions Integration Services (SSIS)</span><span class="sxs-lookup"><span data-stu-id="99549-102">Integration Services (SSIS) Expressions</span></span>
  <span data-ttu-id="99549-103">Une expression est une combinaison de symboles (identificateurs, littéraux, fonctions et opérateurs) qui génère une seule valeur de données.</span><span class="sxs-lookup"><span data-stu-id="99549-103">An expression is a combination of symbols-identifiers, literals, functions, and operators-that yields a single data value.</span></span> <span data-ttu-id="99549-104">Les expressions simples peuvent être une constante unique, une variable ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="99549-104">Simple expressions can be a single constant, variable, or function.</span></span> <span data-ttu-id="99549-105">Généralement, les expressions sont complexes, car elles utilisent plusieurs opérateurs et fonctions, et référencent plusieurs colonnes et variables.</span><span class="sxs-lookup"><span data-stu-id="99549-105">More frequently, expressions are complex, using multiple operators and functions and referencing multiple columns and variables.</span></span> <span data-ttu-id="99549-106">Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez utiliser des expressions pour définir des conditions dans les instructions CASE, créer et mettre à jour des valeurs dans des colonnes de données, mettre à jour ou remplir des propriétés au moment de l’exécution, définir des contraintes dans des contraintes de précédence et fournir les expressions utilisées par le conteneur de boucles For.</span><span class="sxs-lookup"><span data-stu-id="99549-106">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expressions can be used to define conditions for CASE statements, create and update values in data columns, assign values to variables, update or populate properties at run time, define constraints in precedence constraints, and provide the expressions used by the For Loop container.</span></span>  
  
 <span data-ttu-id="99549-107">Les expressions sont basées sur un langage d'expressions et sur l'évaluateur d'expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-107">Expressions are based on an expression language, and the expression evaluator.</span></span> <span data-ttu-id="99549-108">L'évaluateur d'expression analyse l'expression et détermine si elle respecte les règles du langage d'expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-108">The expression evaluator parses the expression and determines whether the expression follows the rules of the expression language.</span></span> <span data-ttu-id="99549-109">Pour plus d'informations sur la syntaxe d'expression, les littéraux et les identificateurs pris en charge, consultez les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="99549-109">For more information about the expression syntax and supported literals and identifiers, see the following topics.</span></span>  
  
-   [<span data-ttu-id="99549-110">Syntaxe &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="99549-110">Syntax &#40;SSIS&#41;</span></span>](syntax-ssis.md)  
  
-   [<span data-ttu-id="99549-111">Littéraux &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="99549-111">Literals &#40;SSIS&#41;</span></span>](numeric-string-and-boolean-literals.md)  
  
-   [<span data-ttu-id="99549-112">Identificateurs &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="99549-112">Identifiers &#40;SSIS&#41;</span></span>](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a><span data-ttu-id="99549-113">Composants qui utilisent des expressions</span><span class="sxs-lookup"><span data-stu-id="99549-113">Components that Use Expressions</span></span>  
 <span data-ttu-id="99549-114">Les éléments suivants dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] peuvent utiliser des expressions :</span><span class="sxs-lookup"><span data-stu-id="99549-114">The following elements in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can use expressions:</span></span>  
  
-   <span data-ttu-id="99549-115">La transformation de fractionnement conditionnel met en œuvre une structure de décision, basée sur des expressions, pour diriger des lignes de données vers différentes destinations.</span><span class="sxs-lookup"><span data-stu-id="99549-115">The Conditional Split transformation implements a decision structure based on expressions to direct data rows to different destinations.</span></span> <span data-ttu-id="99549-116">Les expressions utilisées dans une transformation de fractionnement conditionnel doivent s'évaluer à `true` ou à `false`.</span><span class="sxs-lookup"><span data-stu-id="99549-116">Expressions used in a Conditional Split transformation must evaluate to `true` or `false`.</span></span> <span data-ttu-id="99549-117">Par exemple, les lignes qui répondent à la condition dans l'expression « Colonne1 > Colonne2 » peuvent être routées vers une sortie distincte.</span><span class="sxs-lookup"><span data-stu-id="99549-117">For example, rows that meet the condition in the expression "Column1 > Column2" can be routed to a separate output.</span></span>  
  
-   <span data-ttu-id="99549-118">La transformation de colonne dérivée utilise des valeurs créées au moyen d'expressions, soit pour remplir de nouvelles colonnes dans un flux de données, soit pour mettre à jour des colonnes existantes.</span><span class="sxs-lookup"><span data-stu-id="99549-118">The Derived Column transformation uses values created by using expressions either to populate new columns in a data flow, or to update existing columns.</span></span> <span data-ttu-id="99549-119">Par exemple, l'expression Colonne1 + "ABC" peut être utilisée pour mettre à jour une valeur ou pour créer une nouvelle valeur avec la chaîne concaténée.</span><span class="sxs-lookup"><span data-stu-id="99549-119">For example, the expression Column1 + " ABC" can be used to update a value or to create a new value with the concatenated string.</span></span>  
  
-   <span data-ttu-id="99549-120">Les variables utilisent une expression pour définir leur valeur.</span><span class="sxs-lookup"><span data-stu-id="99549-120">Variables use an expression to set their value.</span></span> <span data-ttu-id="99549-121">Par exemple, GETDATE() définit la valeur de la variable comme étant la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="99549-121">For example, GETDATE() sets the value of the variable to the current date.</span></span>  
  
-   <span data-ttu-id="99549-122">Les contraintes de précédence peuvent utiliser des expressions pour spécifier les conditions déterminant si le conteneur ou le package contraint est exécuté.</span><span class="sxs-lookup"><span data-stu-id="99549-122">Precedence constraints can use expressions to specify the conditions that determine whether the constrained task or container in a package runs.</span></span> <span data-ttu-id="99549-123">Les expressions utilisées dans une contrainte de précédence doivent s'évaluer à `true` ou à `false`.</span><span class="sxs-lookup"><span data-stu-id="99549-123">Expressions used in a precedence constraint must evaluate to `true` or `false`.</span></span> <span data-ttu-id="99549-124">Par exemple, l'expression \@A > \@B compare deux variables définies par l'utilisateur pour déterminer si la tâche contrainte est exécutée.</span><span class="sxs-lookup"><span data-stu-id="99549-124">For example, the expression \@A > \@B compares two user-defined variables to determine whether the constrained task runs.</span></span>  
  
-   <span data-ttu-id="99549-125">Le conteneur de boucles For peut utiliser des expressions pour créer les instructions d'initialisation, d'évaluation et d'incrémentation utilisées par la structure de bouclage.</span><span class="sxs-lookup"><span data-stu-id="99549-125">The For Loop container can use expressions to build the initialization, evaluation, and the incrementing statements that the looping structure uses.</span></span> <span data-ttu-id="99549-126">Par exemple, l'expression \@Counter = 1 initialise le compteur de boucles.</span><span class="sxs-lookup"><span data-stu-id="99549-126">For example, the expression \@Counter = 1 initializes the loop counter.</span></span>  
  
 <span data-ttu-id="99549-127">Les expressions peuvent également être utilisées pour mettre à jour les valeurs des propriétés des packages, les conteneurs tels que les conteneurs de boucles For et Foreach, les tâches, les gestionnaires de connexions aux niveaux des packages et du projet, les modules fournisseurs d'informations et les énumérateurs Foreach.</span><span class="sxs-lookup"><span data-stu-id="99549-127">Expressions can also be used to update the values of properties of packages, containers such as the For Loop and Foreach Loop, tasks, package and project level connection managers, log providers, and Foreach enumerators.</span></span> <span data-ttu-id="99549-128">Par exemple, en utilisant une expression de propriété, la chaîne « Localhost.AdventureWorks » peut être affectée à la propriété ConnectionName de la tâche Exécuter SQL.</span><span class="sxs-lookup"><span data-stu-id="99549-128">For example, using a property expression, the string "Localhost.AdventureWorks" can be assigned to the ConnectionName property of the Execute SQL task.</span></span> <span data-ttu-id="99549-129">Pour plus d’informations, consultez [Expressions de propriété dans des packages](use-property-expressions-in-packages.md).</span><span class="sxs-lookup"><span data-stu-id="99549-129">For more information, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="icon-markers-for-expressions"></a><span data-ttu-id="99549-130">Marqueurs d'icône pour les expressions</span><span class="sxs-lookup"><span data-stu-id="99549-130">Icon Markers for Expressions</span></span>  
 <span data-ttu-id="99549-131">Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], un marqueur d'icône spécial s'affiche en regard des gestionnaires de connexions, des variables et des tâches contenant des expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a special icon marker displays next to connection managers, variables, and tasks that have expressions set on them.</span></span> <span data-ttu-id="99549-132">La propriété **HasExpressions** est disponible sur tous les objets SSIS qui prennent en charge les expressions, à l’exception des variables.</span><span class="sxs-lookup"><span data-stu-id="99549-132">The **HasExpressions** property is available on all SSIS objects that support expresions, with the exception of variables.</span></span> <span data-ttu-id="99549-133">La propriété vous permet d'identifier facilement les objets qui ont des expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-133">The property enables you to easily identy which objects have expressions.</span></span>  
  
## <a name="expression-builder"></a><span data-ttu-id="99549-134">Générateur d’expressions</span><span class="sxs-lookup"><span data-stu-id="99549-134">Expression Builder</span></span>  
 <span data-ttu-id="99549-135">Le générateur d'expressions est un outil graphique de génération d'expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-135">The expression builder is a graphical tool for building expressions.</span></span> <span data-ttu-id="99549-136">Disponible dans les boîtes de dialogue **Éditeur de transformation de fractionnement conditionnel**, **Éditeur de transformation de colonne dérivée** et **Générateur d’expression** , il s’agit d’un outil graphique qui permet de créer des expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-136">It is available in the **Conditional Split Transformation Editor**, **Derived Column Transformation Editor** dialog boxes, and in the **Expression Builder** dialog box, is a graphical tool for building expressions.</span></span>  
  
 <span data-ttu-id="99549-137">Le générateur d'expression fournit des dossiers contenant des éléments spécifiques aux packages, et des dossiers contenant les fonctions, les conversions de type et les opérateurs fournis par le langage d'expressions.</span><span class="sxs-lookup"><span data-stu-id="99549-137">The expression builder provides folders that contain package-specific elements, and folders that contain the functions, type casts, and operators that the expression language provides.</span></span> <span data-ttu-id="99549-138">Les éléments spécifiques aux packages comprennent les variables système et les variables définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="99549-138">The package-specific elements include system variables and user-defined variables.</span></span> <span data-ttu-id="99549-139">Dans les boîtes de dialogue **Éditeur de transformation de fractionnement conditionnel** et **Éditeur de transformation de colonne dérivée** , vous pouvez également afficher des colonnes de données.</span><span class="sxs-lookup"><span data-stu-id="99549-139">In the **Conditional Split Transformation Editor** and **Derived Column Transformation Editor** dialog boxes, you can also view data columns.</span></span> <span data-ttu-id="99549-140">Pour générer des expressions pour les transformations, vous pouvez faire glisser des éléments des dossiers vers la colonne **Condition** ou **Expression** , ou vous pouvez taper l’expression directement dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="99549-140">To build expressions for the transformations, you can drag items from the folders to the **Condition** or **Expression** column or you can type the expression directly in the column.</span></span> <span data-ttu-id="99549-141">Le générateur d'expressions ajoute automatiquement les éléments syntaxiques requis, tels que le préfixe \@ des noms des variables.</span><span class="sxs-lookup"><span data-stu-id="99549-141">The expression builder automatically adds needed syntax elements such as the \@ prefix on variable names.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99549-142">Les noms des variables définies par l'utilisateur et des variables système respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="99549-142">The names of user-defined and system variables are case-sensitive.</span></span>  
  
 <span data-ttu-id="99549-143">Les variables ont une étendue et le dossier **Variables** dans le générateur d’expressions répertorie uniquement les variables qui sont dans l’étendue et utilisables.</span><span class="sxs-lookup"><span data-stu-id="99549-143">Variables have scope, and the **Variables** folder in the expression builder lists only variables that are in scope and available to use.</span></span> <span data-ttu-id="99549-144">Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).</span><span class="sxs-lookup"><span data-stu-id="99549-144">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="99549-145">Tâches associées</span><span class="sxs-lookup"><span data-stu-id="99549-145">Related Tasks</span></span>  
 [<span data-ttu-id="99549-146">Utiliser une expression dans un composant de flux de données</span><span class="sxs-lookup"><span data-stu-id="99549-146">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="99549-147">Contenu associé</span><span class="sxs-lookup"><span data-stu-id="99549-147">Related Content</span></span>  
 <span data-ttu-id="99549-148">Article technique, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="99549-148">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99549-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99549-149">See Also</span></span>  
 [<span data-ttu-id="99549-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="99549-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  