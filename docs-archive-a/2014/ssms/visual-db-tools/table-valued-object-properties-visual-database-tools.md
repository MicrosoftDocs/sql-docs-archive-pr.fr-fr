---
title: Propriétés de l’objet table (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f1c1e6414d0059dfd1d43bbbb40eabdfc9470b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704599"
---
# <a name="table-valued-object-properties-visual-database-tools"></a><span data-ttu-id="d33d3-102">Propriétés de l'objet table (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d33d3-102">Table-Valued Object Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="d33d3-103">Ces propriétés figurent dans la fenêtre Propriétés lorsque vous sélectionnez un objet table dans le **Concepteur de requêtes et de vues**.</span><span class="sxs-lookup"><span data-stu-id="d33d3-103">These properties appear in the Properties window when you select a table-valued object in **Query and View Designer**.</span></span> <span data-ttu-id="d33d3-104">L'objet table peut être une vue, un synonyme, une table dérivée ou une fonction table.</span><span class="sxs-lookup"><span data-stu-id="d33d3-104">The table-valued object could be a view, synonym, derived table, or table-valued function.</span></span> <span data-ttu-id="d33d3-105">Sauf indication contraire, ces propriétés sont en lecture seule dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="d33d3-105">Unless otherwise noted, these properties are read-only in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d33d3-106">Les propriétés mentionnées dans cette rubrique sont classées par catégorie et non par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="d33d3-106">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d33d3-107">Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition.</span><span class="sxs-lookup"><span data-stu-id="d33d3-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d33d3-108">Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="d33d3-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="d33d3-109">**Catégorie Identité**</span><span class="sxs-lookup"><span data-stu-id="d33d3-109">**Identity Category**</span></span>  
 <span data-ttu-id="d33d3-110">Peut être développée pour afficher les propriétés **Nom** et **Type TVO** .</span><span class="sxs-lookup"><span data-stu-id="d33d3-110">Expands to show the **Name** and **TVO Type** properties.</span></span>  
  
 <span data-ttu-id="d33d3-111">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d33d3-111">**Name**</span></span>  
 <span data-ttu-id="d33d3-112">Affiche le nom de l'objet table sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d33d3-112">Shows the name of the selected table-valued object.</span></span>  
  
 <span data-ttu-id="d33d3-113">**Type TVO**</span><span class="sxs-lookup"><span data-stu-id="d33d3-113">**TVO Type**</span></span>  
 <span data-ttu-id="d33d3-114">Affiche le type d'objet table.</span><span class="sxs-lookup"><span data-stu-id="d33d3-114">Shows which type of table-valued object.</span></span> <span data-ttu-id="d33d3-115">Il peut être une table de base, une vue, une fonction table ou une table dérivée.</span><span class="sxs-lookup"><span data-stu-id="d33d3-115">It can be either a base table, view, table-valued function, or a derived table.</span></span>  
  
 <span data-ttu-id="d33d3-116">**Catégorie Concepteur de requêtes**</span><span class="sxs-lookup"><span data-stu-id="d33d3-116">**Query DesignerCategory**</span></span>  
 <span data-ttu-id="d33d3-117">Peut être développée pour afficher les propriétés de **Alias**, **Liste de colonnes**, **Nom complet**et **Liste de paramètres**.</span><span class="sxs-lookup"><span data-stu-id="d33d3-117">Expands to show properties for **Alias**, **Column List**, **Full Name**, and **Parameter List**.</span></span>  
  
 <span data-ttu-id="d33d3-118">**Alias**</span><span class="sxs-lookup"><span data-stu-id="d33d3-118">**Alias**</span></span>  
 <span data-ttu-id="d33d3-119">Affiche l'alias de l'objet table sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d33d3-119">Shows the alias for the selected table-valued object.</span></span> <span data-ttu-id="d33d3-120">Pour ajouter ou modifier un alias, tapez son nom dans le champ.</span><span class="sxs-lookup"><span data-stu-id="d33d3-120">To add or change an alias, type it into the field.</span></span>  
  
 <span data-ttu-id="d33d3-121">**Liste de colonnes**</span><span class="sxs-lookup"><span data-stu-id="d33d3-121">**Column List**</span></span>  
 <span data-ttu-id="d33d3-122">Affiche les colonnes incluses dans l'objet table sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d33d3-122">Shows the columns included in the selected table-valued object.</span></span> <span data-ttu-id="d33d3-123">Pour les afficher dans une fenêtre distincte, cliquez sur Liste de colonnes, puis sur le bouton de sélection (…) à droite de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d33d3-123">To see them in a separate window, click Column List and then click the ellipses (...) to the right of the property.</span></span>  
  
 <span data-ttu-id="d33d3-124">**Nom complet**</span><span class="sxs-lookup"><span data-stu-id="d33d3-124">**Full Name**</span></span>  
 <span data-ttu-id="d33d3-125">Affiche le nom de l'objet table sélectionné, notamment des informations supplémentaires telles que le schéma ou la source de données de l'objet.</span><span class="sxs-lookup"><span data-stu-id="d33d3-125">Shows the name of the selected table-valued object, including additional information such as the schema or data source of the object.</span></span>  
  
 <span data-ttu-id="d33d3-126">**Liste de paramètres**</span><span class="sxs-lookup"><span data-stu-id="d33d3-126">**Parameter List**</span></span>  
 <span data-ttu-id="d33d3-127">Affiche les paramètres définis pour l'objet table sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d33d3-127">Shows the parameters defined for selected table-valued function.</span></span> <span data-ttu-id="d33d3-128">Si vous souhaitez définir une valeur pour les paramètres, cliquez sur Liste de paramètres, puis sur le bouton de sélection (…) à droite de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d33d3-128">To define a value for the parameters, click Parameter List and then click the ellipses (...) to the right of the property.</span></span> <span data-ttu-id="d33d3-129">Dans la boîte de dialogue Paramètres de fonction, tapez les valeurs.</span><span class="sxs-lookup"><span data-stu-id="d33d3-129">In the Function Parameters dialog box, type in values.</span></span> <span data-ttu-id="d33d3-130">Cette propriété est disponible uniquement lorsqu'une fonction table est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="d33d3-130">This property is only available when a table-valued function is selected.</span></span>  
  
  