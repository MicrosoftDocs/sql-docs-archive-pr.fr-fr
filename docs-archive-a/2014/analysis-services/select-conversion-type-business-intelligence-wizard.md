---
title: Sélectionner le type de conversion (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f83fdf566b52a5fe79bea7a4a676274423d1091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602339"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a><span data-ttu-id="5e671-102">Sélectionner le type de conversion (Assistant Business Intelligence)</span><span class="sxs-lookup"><span data-stu-id="5e671-102">Select Conversion Type (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="5e671-103">La page **Sélectionner le type de conversion** permet de définir la relation entre les devises locales et celles des rapports pour des transactions stockées dans plusieurs devises.</span><span class="sxs-lookup"><span data-stu-id="5e671-103">Use the **Select Conversion Type** page to define the relationship between local currencies and reporting currencies for transactions stored in multiple currencies.</span></span> <span data-ttu-id="5e671-104">Une devise locale est une devise dans laquelle les transactions des mesures sélectionnées dans **Sélectionnez les mesures** sont stockées.</span><span class="sxs-lookup"><span data-stu-id="5e671-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span> <span data-ttu-id="5e671-105">Une devise de rapport est celle dans laquelle sont traduites les transactions sélectionnées dans la page **Sélectionnez les mesures** .</span><span class="sxs-lookup"><span data-stu-id="5e671-105">A reporting currency is the currency in which the transactions selected in the **Select Measures** page are translated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e671-106">Cette page ne s’affiche pas si l’Assistant Business Intelligence a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e671-106">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e671-107">Options</span><span class="sxs-lookup"><span data-stu-id="5e671-107">Options</span></span>  
 <span data-ttu-id="5e671-108">**Plusieurs-à-plusieurs**</span><span class="sxs-lookup"><span data-stu-id="5e671-108">**Many-to-many**</span></span>  
 <span data-ttu-id="5e671-109">Permet de stocker les transactions en utilisant des devises locales.</span><span class="sxs-lookup"><span data-stu-id="5e671-109">Stores transactions using local currencies.</span></span> <span data-ttu-id="5e671-110">La fonctionnalité de conversion monétaire convertit ce type de transactions dans la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** , puis dans une ou plusieurs devises pour les rapports.</span><span class="sxs-lookup"><span data-stu-id="5e671-110">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
 <span data-ttu-id="5e671-111">Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en euros (EUR), en dollars australiens (AUD) et en pesos mexicains (MXN).</span><span class="sxs-lookup"><span data-stu-id="5e671-111">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5e671-112">Cette option convertit ces transactions de leur devise locale dans la devise pivot. Ensuite, les transactions converties sont de nouveau converties de la devise pivot dans les devises de rapport spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5e671-112">Selecting this option converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5e671-113">Résultat : les transactions peuvent être stockées dans les devises locales spécifiées et affichées soit dans la devise pivot indiquée, soit dans l'une des devises de rapport mentionnées à la page **Spécifier les devises pour les rapports** .</span><span class="sxs-lookup"><span data-stu-id="5e671-113">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
 <span data-ttu-id="5e671-114">**Plusieurs-à-un**</span><span class="sxs-lookup"><span data-stu-id="5e671-114">**Many-to-one**</span></span>  
 <span data-ttu-id="5e671-115">Permet de stocker les transactions en utilisant des devises locales.</span><span class="sxs-lookup"><span data-stu-id="5e671-115">Stores transactions using local currencies.</span></span> <span data-ttu-id="5e671-116">La fonctionnalité de conversion monétaire convertit ce type de transactions dans la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** .</span><span class="sxs-lookup"><span data-stu-id="5e671-116">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page.</span></span> <span data-ttu-id="5e671-117">La devise pivot est la seule devise pour les rapports spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5e671-117">The pivot currency serves as the only specified reporting currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e671-118">La page **Spécifier les devises pour les rapports** n’apparaît pas quand cette option est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="5e671-118">If this option is selected, the **Specify Reporting Currencies** page does not appear.</span></span>  
  
 <span data-ttu-id="5e671-119">Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en euros (EUR), en dollars australiens (AUD) et en pesos mexicains (MXN).</span><span class="sxs-lookup"><span data-stu-id="5e671-119">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5e671-120">Cette option convertit ces transactions de leurs devises locales spécifiées dans la devise pivot.</span><span class="sxs-lookup"><span data-stu-id="5e671-120">Selecting this option converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="5e671-121">Résultat : les transactions peuvent être stockées dans les devises locales spécifiées et être affichées dans la devise pivot  mentionnée.</span><span class="sxs-lookup"><span data-stu-id="5e671-121">The result is that transactions can be stored in the specified local currencies and viewed in the specified pivot currency.</span></span>  
  
 <span data-ttu-id="5e671-122">**Un-à-plusieurs**</span><span class="sxs-lookup"><span data-stu-id="5e671-122">**One-to-many**</span></span>  
 <span data-ttu-id="5e671-123">Permet de stocker les transactions en utilisant la devise pivot spécifiée dans la page **Définir les options de conversion monétaire** , puis dans une ou plusieurs devises pour les rapports.</span><span class="sxs-lookup"><span data-stu-id="5e671-123">Store transactions using the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e671-124">La page **Définir le référencement pour les devises locales** n’apparaît pas quand cette option est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="5e671-124">If this option is selected, the **Define Local Currency Reference** page does not appear.</span></span>  
  
 <span data-ttu-id="5e671-125">Par exemple, la devise pivot peut correspondre à des dollars américains (USD) et la table de faits peut stocker les transactions en USD.</span><span class="sxs-lookup"><span data-stu-id="5e671-125">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="5e671-126">Cette option convertit ces transactions de la devise pivot dans les devises de rapport spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5e671-126">Selecting this option converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5e671-127">Résultat : les transactions peuvent être stockées dans la devise pivot spécifiée et être affichées soit dans la devise pivot indiquée, soit dans l'une des devises de rapport mentionnées à la page **Spécifier les devises pour les rapports** .</span><span class="sxs-lookup"><span data-stu-id="5e671-127">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e671-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e671-128">See Also</span></span>  
 <span data-ttu-id="5e671-129">[Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5e671-129">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="5e671-130">[Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5e671-130">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5e671-131">Concepteur de dimensions &#40;Analysis Services-données multidimensionnelles&#41;</span><span class="sxs-lookup"><span data-stu-id="5e671-131">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  