---
title: Outils de calcul (onglet actions, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123fa38ea2decb6af914e93fcefda4508f08545e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602530"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="dbf17-102">Outils de calcul (onglet Actions, Concepteur de cube) (Analysis Services - Données multidimensionnelles)</span><span class="sxs-lookup"><span data-stu-id="dbf17-102">Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="dbf17-103">Utilisez le volet **Outils de calcul** sur l'onglet **Actions** du Concepteur de cube afin d'explorer les métadonnées, les fonctions et les modèles disponibles en vue de leur utilisation dans des actions, des actions d'extraction et des actions du rapport.</span><span class="sxs-lookup"><span data-stu-id="dbf17-103">Use the **Calculation Tools** pane on the **Actions** tab in Cube Designer to explore metadata, functions, and templates available for use in actions, drillthrough actions, and report actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dbf17-104">Options</span><span class="sxs-lookup"><span data-stu-id="dbf17-104">Options</span></span>  
 <span data-ttu-id="dbf17-105">**Métadonnées**</span><span class="sxs-lookup"><span data-stu-id="dbf17-105">**Metadata**</span></span>  
 <span data-ttu-id="dbf17-106">Affiche les métadonnées du cube sélectionné.</span><span class="sxs-lookup"><span data-stu-id="dbf17-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="dbf17-107">Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d’action**, **Éditeur de formulaire d’action d’extraction**ou **Éditeur de formulaire d’action du rapport** pour inclure la syntaxe MDX (Multidimensional Expressions) de cet élément à l’emplacement sélectionné dans le volet.</span><span class="sxs-lookup"><span data-stu-id="dbf17-107">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="dbf17-108">**Fonctions**</span><span class="sxs-lookup"><span data-stu-id="dbf17-108">**Functions**</span></span>  
 <span data-ttu-id="dbf17-109">Affiche les fonctions disponibles pour les expressions et les conditions.</span><span class="sxs-lookup"><span data-stu-id="dbf17-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="dbf17-110">Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'action**, **Éditeur de formulaire d'action d'extraction**ou **Éditeur de formulaire d'action de rapport** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.</span><span class="sxs-lookup"><span data-stu-id="dbf17-110">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbf17-111">En mode projet, la boîte de dialogue **Outils de calcul** lit les informations de cette option dans un fichier XML nommé MDXFunctions.xml inclus dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbf17-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="dbf17-112">En mode en ligne, les informations de cette option sont récupérées de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS pour l'instance.</span><span class="sxs-lookup"><span data-stu-id="dbf17-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="dbf17-113">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="dbf17-113">**Templates**</span></span>  
 <span data-ttu-id="dbf17-114">Permet d'afficher les modèles prédéfinis disponibles relatifs aux actions.</span><span class="sxs-lookup"><span data-stu-id="dbf17-114">Displays the predefined templates available for actions.</span></span>  
  
 <span data-ttu-id="dbf17-115">Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'action**, **Éditeur de formulaire d'action d'extraction**ou **Éditeur de formulaire d'action de rapport** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.</span><span class="sxs-lookup"><span data-stu-id="dbf17-115">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="dbf17-116">Menu contextuel</span><span class="sxs-lookup"><span data-stu-id="dbf17-116">Context Menu</span></span>  
 <span data-ttu-id="dbf17-117">Le menu contextuel propose les options suivantes. Vous y accédez en cliquant avec le bouton droit sur un élément du volet **Outils de calcul** :</span><span class="sxs-lookup"><span data-stu-id="dbf17-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
|<span data-ttu-id="dbf17-118">Option</span><span class="sxs-lookup"><span data-stu-id="dbf17-118">Option</span></span>|<span data-ttu-id="dbf17-119">Définition</span><span class="sxs-lookup"><span data-stu-id="dbf17-119">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="dbf17-120">**Copier**</span><span class="sxs-lookup"><span data-stu-id="dbf17-120">**Copy**</span></span>|<span data-ttu-id="dbf17-121">Sélectionnez cette option pour copier l'élément sélectionné dans **Métadonnées** ou **Fonctions** dans le Presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="dbf17-121">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span><br /><br /> <span data-ttu-id="dbf17-122">Notez que cette option ne s’affiche pas si **modèles** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="dbf17-122">Note that this option is not displayed if **Templates** is selected.</span></span> <span data-ttu-id="dbf17-123">Notez également que cette option est désactivée si le membre sélectionné ne peut pas être copié, tel que le dossier **ensembles** d’une dimension affichée dans **métadonnées** ou le dossier de groupe de fonctions pour une fonction affichée dans **fonctions**.</span><span class="sxs-lookup"><span data-stu-id="dbf17-123">Also note that this option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>|  
|<span data-ttu-id="dbf17-124">**Filtrer les membres**</span><span class="sxs-lookup"><span data-stu-id="dbf17-124">**Filter Members**</span></span>|<span data-ttu-id="dbf17-125">Sélectionnez cette option pour afficher la boîte de dialogue **Filtrer les membres** et filtrer les membres affichés pour l'élément sélectionné dans **Métadonnées**.</span><span class="sxs-lookup"><span data-stu-id="dbf17-125">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="dbf17-126">Pour plus d’informations sur la boîte de dialogue **Filtrer les membres**, consultez [Boîte de dialogue Filtrer les membres &#40;Analysis Services - Données multidimensionnelles&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span><span class="sxs-lookup"><span data-stu-id="dbf17-126">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="dbf17-127">Notez que cette option s’affiche uniquement si **métadonnées** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="dbf17-127">Note that this option is displayed only if **Metadata** is selected.</span></span> <span data-ttu-id="dbf17-128">Notez également que cette option est activée uniquement si le niveau d’un attribut est sélectionné dans **métadonnées**.</span><span class="sxs-lookup"><span data-stu-id="dbf17-128">Also note that this option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>|  
|<span data-ttu-id="dbf17-129">**Ajouter un Modèle**</span><span class="sxs-lookup"><span data-stu-id="dbf17-129">**Add Template**</span></span>|<span data-ttu-id="dbf17-130">Permet d'ajouter au cube une nouvelle action, action d'extraction ou action de rapport s'appuyant sur le modèle sélectionné et d'afficher, selon le type d'action, l' **Éditeur de formulaire d'action**, l' **Éditeur de formulaire d'action d'extraction**ou l' **Éditeur de formulaire d'action de rapport**.</span><span class="sxs-lookup"><span data-stu-id="dbf17-130">Select to add a new action, drillthrough action, or report action based on the selected template to the cube and display, respectively, the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor**.</span></span><br /><br /> <span data-ttu-id="dbf17-131">Remarque : cette option s’affiche uniquement si **métadonnées** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="dbf17-131">Note: This option is displayed only if **Metadata** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbf17-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbf17-132">See Also</span></span>  
 <span data-ttu-id="dbf17-133">[Notions de base de l’écriture de scripts MDX &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-133">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="dbf17-134">[Actions &#40;le concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-134">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dbf17-135">[Barre d’outils &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-135">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dbf17-136">[Organisateur d’action &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-136">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dbf17-137">[Éditeur de formulaire d’action &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-137">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dbf17-138">[Éditeur de formulaire d’action d’extraction &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dbf17-138">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="dbf17-139">Éditeur de formulaire d’action de rapport &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;</span><span class="sxs-lookup"><span data-stu-id="dbf17-139">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  