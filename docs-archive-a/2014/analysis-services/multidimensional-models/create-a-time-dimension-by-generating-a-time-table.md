---
title: Créer une dimension de temps en générant une table de temps | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time dimensions [Analysis Services]
- dimensions [Analysis Services], time
- time periods [Analysis Services]
- range-based time dimensions [Analysis Services]
- server time dimensions [Analysis Services]
- calendars [Analysis Services]
- table-based time dimensions [Analysis Services]
ms.assetid: 58303326-1361-4c0e-9f3d-642ce69c4f6a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 978db9a5592654e44e021b5a2fe0a20e42794ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705603"
---
# <a name="create-a-time-dimension-by-generating-a-time-table"></a><span data-ttu-id="987b5-102">Create a Time Dimension by Generating a Time Table</span><span class="sxs-lookup"><span data-stu-id="987b5-102">Create a Time Dimension by Generating a Time Table</span></span>
  <span data-ttu-id="987b5-103">Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez utiliser l’Assistant dimension dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour créer une dimension de temps lorsque aucune table de temps n’est disponible dans la base de données source.</span><span class="sxs-lookup"><span data-stu-id="987b5-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a time dimension when no time table is available in the source database.</span></span> <span data-ttu-id="987b5-104">Pour ce faire, sélectionnez l'une des options suivantes dans la page **Sélectionner la méthode de création** :</span><span class="sxs-lookup"><span data-stu-id="987b5-104">You do this by selecting one of the following options on the **Select Creation Method** page:</span></span>  
  
-   <span data-ttu-id="987b5-105">**Générer une table de temps dans la source de données** Sélectionnez cette option lorsque vous disposez de l'autorisation de créer des objets dans la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="987b5-105">**Generate a time table in the data source** Select this option when you have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="987b5-106">L'Assistant génère ensuite une table de temps et stocke cette table dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="987b5-106">The wizard will then generate a time table and store this table in the data source.</span></span> <span data-ttu-id="987b5-107">L'Assistant crée ensuite la dimension de temps à partir de cette table de temps.</span><span class="sxs-lookup"><span data-stu-id="987b5-107">The wizard then creates the time dimension from this time table.</span></span>  
  
-   <span data-ttu-id="987b5-108">**Générer une table de temps sur le serveur** Sélectionnez cette option lorsque vous ne disposez pas de l'autorisation de créer des objets dans la source de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="987b5-108">**Generate a time table on the server** Select this option when you do not have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="987b5-109">L'Assistant génère et stocke ensuite une table sur le serveur au lieu de le faire dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="987b5-109">The wizard will then generate and store a table on the server instead of in the data source.</span></span> <span data-ttu-id="987b5-110">(La dimension créée à partir d'une table de temps sur le serveur est appelée *dimension de temps du serveur*.) L'Assistant crée ensuite la dimension de temps du serveur à partir de cette table.</span><span class="sxs-lookup"><span data-stu-id="987b5-110">(The dimension created from a time table on the server is called a *server time dimension*.) The wizard then creates the server time dimension from this table.</span></span>  
  
 <span data-ttu-id="987b5-111">Lorsque vous créez une dimension de temps du serveur, vous spécifiez les périodes, ainsi que les dates de début et de fin de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-111">When you create a time dimension, you specify the time periods, and also the start and end dates for the dimension.</span></span> <span data-ttu-id="987b5-112">L'Assistant utilise les périodes spécifiées pour créer les attributs de temps.</span><span class="sxs-lookup"><span data-stu-id="987b5-112">The wizard uses the specified time periods to create the time attributes.</span></span> <span data-ttu-id="987b5-113">Lorsque vous traitez la dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère et stocke les données requises pour prendre en charge les dates et les périodes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="987b5-113">When you process the dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates and stores the data that is required to support the specified dates and periods.</span></span> <span data-ttu-id="987b5-114">L'Assistant utilise les attributs créés pour une dimension de temps afin de recommander les hiérarchies de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-114">The wizard uses the attributes created for a time dimension to recommend hierarchies for the dimension.</span></span> <span data-ttu-id="987b5-115">Les hiérarchies font apparaître les relations entre les différentes périodes et tiennent compte des différents calendriers.</span><span class="sxs-lookup"><span data-stu-id="987b5-115">The hierarchies reflect the relationships between different time periods and take account of different calendars.</span></span> <span data-ttu-id="987b5-116">Par exemple, dans une hiérarchie de calendrier standard, un niveau Semaines apparaît sous un niveau Années, mais pas sous un niveau Mois, car les années se divisent en nombre égal de semaines, mais pas les mois.</span><span class="sxs-lookup"><span data-stu-id="987b5-116">For example, in a standard calendar hierarchy, a Weeks level appears under a Years level but not under a Months level, because weeks divide evenly into years but not into months.</span></span> <span data-ttu-id="987b5-117">En revanche, dans une hiérarchie de calendrier de fabrication ou de rapports, les mois se divisent en nombre égal de semaines, de sorte qu'un niveau Semaines apparaît sous un niveau Mois.</span><span class="sxs-lookup"><span data-stu-id="987b5-117">In contrast, in a manufacturing or reporting calendar hierarchy, weeks divide evenly months, so a Weeks level appears under a Months level.</span></span>  
  
## <a name="define-time-periods"></a><span data-ttu-id="987b5-118">Définition de périodes</span><span class="sxs-lookup"><span data-stu-id="987b5-118">Define Time Periods</span></span>  
 <span data-ttu-id="987b5-119">Utilisez la page **Définir des périodes** de l'Assistant pour spécifier les plages de dates que vous voulez inclure dans la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-119">You use the **Define Time Periods** page of the wizard to specify the range of dates that you want to include in the dimension.</span></span> <span data-ttu-id="987b5-120">Par exemple, vous pouvez sélectionner une plage qui débute le 1er janvier de l'année la plus ancienne dans vos données et se termine un ou deux ans après l'année en cours (pour autoriser les futures transactions).</span><span class="sxs-lookup"><span data-stu-id="987b5-120">For example, you might select a range that starts on January 1 of the earliest year in your data and that ends one or two years beyond the current year (to allow for future transactions).</span></span> <span data-ttu-id="987b5-121">Les transactions qui sont en dehors de la plage n'apparaissent pas ou apparaissent en tant que membres inconnus dans la dimension, selon la valeur de la propriété `UnknownMemberVisible` de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-121">Transactions that are outside the range either do not appear or appear as unknown members in the dimension, depending on the `UnknownMemberVisible` property setting for the dimension.</span></span> <span data-ttu-id="987b5-122">Vous pouvez également modifier le premier jour de la semaine utilisé par vos données (le jour par défaut est le dimanche).</span><span class="sxs-lookup"><span data-stu-id="987b5-122">You can also change the first day of the week used by your data (the default is Sunday).</span></span>  
  
 <span data-ttu-id="987b5-123">Sélectionnez les périodes de temps  à utiliser lorsque l'Assistant crée les hiérarchies qui s'appliquent à vos données, telles que Années, Semestres, Trimestres, Quadrimestres, Mois, Décades, Semaines ou Date.</span><span class="sxs-lookup"><span data-stu-id="987b5-123">Select the time periods to use when the wizard creates the hierarchies that apply to your data, such as Years, Half Years, Quarters, Trimesters, Months, Ten Days, Weeks, or Date.</span></span> <span data-ttu-id="987b5-124">Vous devez toujours sélectionner au moins la période Date.</span><span class="sxs-lookup"><span data-stu-id="987b5-124">You must always select at least the Date time period.</span></span> <span data-ttu-id="987b5-125">L'attribut Date étant l'attribut clé de la dimension, cette dernière ne peut pas fonctionner sans lui.</span><span class="sxs-lookup"><span data-stu-id="987b5-125">The Date attribute is the key attribute for the dimension, so the dimension cannot function without it.</span></span>  
  
 <span data-ttu-id="987b5-126">À côté de **Langue pour les noms des membres de temps**, sélectionnez la langue à utiliser pour étiqueter les membres de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-126">Next to **Language for time member names**, select the language to be used to label the members of the dimension.</span></span>  
  
 <span data-ttu-id="987b5-127">Une fois que vous avez créé une dimension de temps qui repose sur une plage de dates, vous pouvez utiliser le Concepteur de dimensions pour ajouter ou supprimer les attributs de temps.</span><span class="sxs-lookup"><span data-stu-id="987b5-127">After you create a time dimension that is based on a range of dates, you can use Dimension Designer to add or remove time attributes.</span></span> <span data-ttu-id="987b5-128">L'attribut Date étant l'attribut clé de la dimension, vous ne pouvez pas le supprimer de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-128">Because the Date attribute is the key attribute for the dimension, you cannot remove it from the dimension.</span></span> <span data-ttu-id="987b5-129">Pour masquer l'attribut Date aux utilisateurs, vous pouvez modifier la valeur de la propriété `AttributeHierarchyVisible` sur l'attribut par la valeur `False`.</span><span class="sxs-lookup"><span data-stu-id="987b5-129">To hide the Date attribute from users, you can change the `AttributeHierarchyVisible` property on the attribute to `False`.</span></span>  
  
## <a name="select-calendars"></a><span data-ttu-id="987b5-130">Sélection de calendriers</span><span class="sxs-lookup"><span data-stu-id="987b5-130">Select Calendars</span></span>  
 <span data-ttu-id="987b5-131">Le calendrier standard de 12 mois (grégorien), qui débute le 1er janvier et se termine le 31 décembre, est toujours inclus lorsque vous créez une dimension de temps.</span><span class="sxs-lookup"><span data-stu-id="987b5-131">The standard (Gregorian) 12-month calendar, starting on January 1 and ending on December 31, is always included when you create a time dimension.</span></span> <span data-ttu-id="987b5-132">Dans la page **Sélectionner des calendriers** de l'Assistant, vous pouvez spécifier des calendriers supplémentaires sur lesquels reposeront les hiérarchies de la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-132">On the **Select Calendars** page of the wizard, you can specify additional calendars on which to base hierarchies in the dimension.</span></span> <span data-ttu-id="987b5-133">Pour obtenir une description des types de calendrier, consultez [Créer une dimension de type Date](database-dimensions-create-a-date-type-dimension.md).</span><span class="sxs-lookup"><span data-stu-id="987b5-133">For descriptions of the calendar types, see [Create a Date type Dimension](database-dimensions-create-a-date-type-dimension.md).</span></span>  
  
 <span data-ttu-id="987b5-134">Selon les périodes que vous sélectionnez dans la page **Définir des périodes** de l'Assistant, les sélections de calendrier déterminent les attributs qui sont créés dans la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-134">Depending on which time periods you select on the **Define Time Periods** page of the wizard, the calendar selections determine attributes that are created in the dimension.</span></span> <span data-ttu-id="987b5-135">Par exemple, si vous sélectionnez les périodes **Année** et **Trimestre** dans la page **Définir des périodes** de l’Assistant et **Calendrier fiscal** dans la page **Sélectionner des calendriers** , les attributs FiscalYear, FiscalQuarter et FiscalQuarterOfYear sont créés pour le calendrier fiscal.</span><span class="sxs-lookup"><span data-stu-id="987b5-135">For example, if you select the **Year** and **Quarter** time periods on the **Define Time Periods** page of the wizard and select **Fiscalcalendar** on the **Select Calendars** page, the FiscalYear, FiscalQuarter, and FiscalQuarterOfYear attributes are created for the fiscal calendar.</span></span>  
  
 <span data-ttu-id="987b5-136">L’Assistant crée également des hiérarchies spécifiques aux calendriers qui se composent des attributs créés pour le calendrier.</span><span class="sxs-lookup"><span data-stu-id="987b5-136">The wizard also creates calendar-specific hierarchies that are composed of the attributes that are created for the calendar.</span></span> <span data-ttu-id="987b5-137">Pour chaque calendrier, chaque niveau de chaque hiérarchie est reporté dans le niveau immédiatement supérieur.</span><span class="sxs-lookup"><span data-stu-id="987b5-137">For every calendar, each level in every hierarchy rolls up into the level above it.</span></span> <span data-ttu-id="987b5-138">Par exemple, dans le calendrier standard de 12 mois, l'Assistant crée une hiérarchie d'Années et de Semaines ou d'Années et de Mois.</span><span class="sxs-lookup"><span data-stu-id="987b5-138">For example, in the standard 12-month calendar, the wizard creates a hierarchy of Years and Weeks or Years and Months.</span></span> <span data-ttu-id="987b5-139">Toutefois, les mois d'un calendrier standard ne contenant pas un nombre égal de semaines, il n'y a pas de hiérarchie d'Années, de Mois et de Semaines.</span><span class="sxs-lookup"><span data-stu-id="987b5-139">However, weeks are not contained evenly within months in a standard calendar, so there is no hierarchy of Years, Months, and Weeks.</span></span> <span data-ttu-id="987b5-140">À l'inverse, les mois d'un calendrier de fabrication ou de rapports contenant un nombre égal de semaines, les semaines dans ce calendrier sont regroupées dans les mois.</span><span class="sxs-lookup"><span data-stu-id="987b5-140">In contrast, weeks in a reporting or manufacturing calendar are evenly divided into months, so in these calendars weeks roll up into months.</span></span>  
  
## <a name="completing-the-dimension-wizard"></a><span data-ttu-id="987b5-141">Fin de l'Assistant Dimension</span><span class="sxs-lookup"><span data-stu-id="987b5-141">Completing the Dimension Wizard</span></span>  
 <span data-ttu-id="987b5-142">Dans la page **Fin de l'Assistant** , vérifiez les attributs et les hiérarchies créés par l'Assistant, puis attribuez un nom à la dimension de temps.</span><span class="sxs-lookup"><span data-stu-id="987b5-142">On the **Completing the Wizard** page, review the attributes and hierarchies created by the wizard, and then name the time dimension.</span></span> <span data-ttu-id="987b5-143">Cliquez sur **Terminer** pour terminer l'Assistant et créer la dimension.</span><span class="sxs-lookup"><span data-stu-id="987b5-143">Click **Finish** to complete the wizard and create the dimension.</span></span> <span data-ttu-id="987b5-144">Une fois la dimension terminée, vous pouvez la modifier à l'aide du Concepteur de dimensions.</span><span class="sxs-lookup"><span data-stu-id="987b5-144">After you complete the dimension, you can change it by using Dimension Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987b5-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="987b5-145">See Also</span></span>  
 <span data-ttu-id="987b5-146">[Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="987b5-146">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="987b5-147">[Créer une dimension de type date](database-dimensions-create-a-date-type-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="987b5-147">[Create a Date type Dimension](database-dimensions-create-a-date-type-dimension.md) </span></span>  
 <span data-ttu-id="987b5-148">[Propriétés d’une dimension de base de données](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md) </span><span class="sxs-lookup"><span data-stu-id="987b5-148">[Database Dimension Properties](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md) </span></span>  
 <span data-ttu-id="987b5-149">[Relations de dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="987b5-149">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="987b5-150">[Créer une dimension à l’aide d’une table existante](create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="987b5-150">[Create a Dimension by Using an Existing Table](create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="987b5-151">Créer une dimension en générant une table non temporelle dans la source de données</span><span class="sxs-lookup"><span data-stu-id="987b5-151">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  