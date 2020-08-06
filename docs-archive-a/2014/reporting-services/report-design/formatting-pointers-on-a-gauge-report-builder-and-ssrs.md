---
title: Mise en forme des pointeurs sur une jauge (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fdf670a-5237-48fe-813d-97657c5c77d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c74cb4d4c61c18d25069dab062bf09804f5935b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695375"
---
# <a name="formatting-pointers-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="ed92d-102">Mise en forme des pointeurs sur une jauge (Générateur de rapports et SSRS)</span><span class="sxs-lookup"><span data-stu-id="ed92d-102">Formatting Pointers on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ed92d-103">Un pointeur de jauge indique la valeur actuelle de la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-103">A gauge pointer indicates the current value of the gauge.</span></span> <span data-ttu-id="ed92d-104">Par défaut, lorsqu'un champ est ajouté, les valeurs contenues dans le champ sont agrégées en une valeur représentée par le pointeur sur la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-104">By default, when a field is added, the values that are contained in the field are aggregated into one value that is shown by the pointer on the gauge.</span></span> <span data-ttu-id="ed92d-105">Vous pouvez ajouter plusieurs pointeurs à la jauge pour indiquer plusieurs valeurs sur la même échelle ou ajouter plusieurs échelles et un pointeur pour chaque échelle ajoutée.</span><span class="sxs-lookup"><span data-stu-id="ed92d-105">You can add multiple pointers to the gauge to point at multiple values on the same scale, or add multiple scales and a pointer for every scale you have added.</span></span> <span data-ttu-id="ed92d-106">Après avoir ajouté un champ à une jauge, vous devez définir les valeurs maximale et minimale sur l'échelle correspondante pour donner le contexte de la valeur du pointeur.</span><span class="sxs-lookup"><span data-stu-id="ed92d-106">After you add a field to a gauge, you must set the maximum and minimum values on the corresponding scale to give context to the pointer value.</span></span> <span data-ttu-id="ed92d-107">Vous avez également la possibilité de définir des valeurs minimale et maximale sur une plage qui représente une zone critique sur l'échelle.</span><span class="sxs-lookup"><span data-stu-id="ed92d-107">You also have the option of setting the minimum and maximum values on a range, which shows a critical area on the scale.</span></span>  
  
 <span data-ttu-id="ed92d-108">Vous pouvez définir des propriétés d’apparence pour le pointeur en cliquant avec le bouton droit sur le pointeur et en sélectionnant **Propriétés du pointeur radial** ou **Propriétés du pointeur linéaire**.</span><span class="sxs-lookup"><span data-stu-id="ed92d-108">You can set appearance properties on the pointer by right-clicking on the pointer and selecting **Radial Pointer Properties** or **Linear Pointer Properties**.</span></span> <span data-ttu-id="ed92d-109">Chaque pointeur de jauge comporte le même jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="ed92d-109">Each gauge pointer contains the same set of properties.</span></span> <span data-ttu-id="ed92d-110">Il existe également des propriétés d'apparence uniques propres à chaque type de jauge :</span><span class="sxs-lookup"><span data-stu-id="ed92d-110">There are also corresponding appearance properties unique to each gauge type:</span></span>  
  
-   <span data-ttu-id="ed92d-111">Sur une jauge radiale, vous pouvez spécifier un pointeur de type aiguille et l'extrémité de fin d'une aiguille.</span><span class="sxs-lookup"><span data-stu-id="ed92d-111">On a radial gauge, you can specify a needle pointer and a needle cap.</span></span>  
  
-   <span data-ttu-id="ed92d-112">Sur une jauge linéaire, vous pouvez spécifier un pointeur de type thermomètre, qui est une variation du pointeur de type barre.</span><span class="sxs-lookup"><span data-stu-id="ed92d-112">On a linear gauge, you can specify a thermometer pointer, which is a variation of the bar pointer.</span></span> <span data-ttu-id="ed92d-113">Le pointeur de type thermomètre vous permet de spécifier la forme du bulbe.</span><span class="sxs-lookup"><span data-stu-id="ed92d-113">The thermometer pointer lets you specify the shape of the bulb.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="how-the-pointer-is-connected-to-data"></a><a name="HowPointer"></a> <span data-ttu-id="ed92d-114">Comment le pointeur est associé aux données</span><span class="sxs-lookup"><span data-stu-id="ed92d-114">How the Pointer is Connected to Data</span></span>  
 <span data-ttu-id="ed92d-115">Par défaut, lorsqu'une jauge est ajoutée, elle contient un pointeur sans champ associé.</span><span class="sxs-lookup"><span data-stu-id="ed92d-115">By default, when a gauge is added, it contains one pointer that has no associated field.</span></span> <span data-ttu-id="ed92d-116">C'est ce que l'on appelle un pointeur vide.</span><span class="sxs-lookup"><span data-stu-id="ed92d-116">This is known as an empty pointer.</span></span> <span data-ttu-id="ed92d-117">Il affichera la valeur zéro jusqu'à ce qu'un champ soit ajouté au volet des données.</span><span class="sxs-lookup"><span data-stu-id="ed92d-117">It will display zero until a field is added to the data pane.</span></span> <span data-ttu-id="ed92d-118">Lorsque vous ajoutez un champ au volet des données, le pointeur est associé à ce champ.</span><span class="sxs-lookup"><span data-stu-id="ed92d-118">When you add a field to the data pane, the pointer is connected to that field.</span></span> <span data-ttu-id="ed92d-119">Si vous supprimez un champ du volet des données, le pointeur associé à ce champ est également supprimé.</span><span class="sxs-lookup"><span data-stu-id="ed92d-119">If you delete a field from the data pane, the pointer that is associated with that field is also deleted.</span></span>  
  
 <span data-ttu-id="ed92d-120">Une fois les données ajoutées, quand vous cliquez avec le bouton droit sur le pointeur, vous obtenez les options **Effacer la valeur du pointeur** et **Supprimer le pointeur** .</span><span class="sxs-lookup"><span data-stu-id="ed92d-120">After data is added, when you right-click on the pointer, you will get **Clear Pointer** and **Delete Pointer** options.</span></span> <span data-ttu-id="ed92d-121">L'option **Effacer la valeur du pointeur** supprime le champ associé à la jauge, mais le pointeur apparaît toujours sur la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-121">The **Clear Pointer Value** option will remove the field that is attached to the gauge, but the pointer will still appear on the gauge.</span></span> <span data-ttu-id="ed92d-122">L'option **Supprimer le pointeur** supprime le champ de la jauge et le pointeur de la vue.</span><span class="sxs-lookup"><span data-stu-id="ed92d-122">The **Delete Pointer** option will remove the field from the gauge and delete the pointer from view.</span></span> <span data-ttu-id="ed92d-123">Si vous ajoutez à nouveau un champ à la jauge, le pointeur par défaut réapparaît.</span><span class="sxs-lookup"><span data-stu-id="ed92d-123">If you re-add a field to the gauge, the default pointer will reappear.</span></span> <span data-ttu-id="ed92d-124">Lorsque vous affectez à la propriété **masqué** du pointeur la valeur `True` , le pointeur n’est pas masqué sur l’aire de conception, mais il est masqué au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ed92d-124">When you set the pointer's **Hidden** property to `True`, the pointer is not hidden on the design surface, but it is hidden at run time.</span></span>  
  
  
##  <a name="displaying-multiple-pointers-on-the-gauge"></a><a name="DisplayingMultiple"></a> <span data-ttu-id="ed92d-125">Affichage de plusieurs pointeurs sur la jauge</span><span class="sxs-lookup"><span data-stu-id="ed92d-125">Displaying Multiple Pointers on the Gauge</span></span>  
 <span data-ttu-id="ed92d-126">Vous pouvez ajouter plusieurs pointeurs à la jauge pour représenter plusieurs valeurs sur la même échelle.</span><span class="sxs-lookup"><span data-stu-id="ed92d-126">You can add multiple pointers to the gauge to point at multiple values on the same scale.</span></span> <span data-ttu-id="ed92d-127">Cela peut être utile pour afficher une valeur basse et une valeur haute en même temps.</span><span class="sxs-lookup"><span data-stu-id="ed92d-127">This can be useful for showing a low and a high value at the same time.</span></span> <span data-ttu-id="ed92d-128">Pour spécifier plusieurs pointeurs sur la jauge pour la même échelle, cliquez avec le bouton droit n’importe où à l’intérieur de la jauge et cliquez sur **Ajouter un pointeur** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="ed92d-128">To specify more than one pointer on the gauge for the same scale, right-click anywhere inside the gauge and click **Add Pointer** on the shortcut menu.</span></span> <span data-ttu-id="ed92d-129">Vous pouvez également ajouter une échelle en cliquant avec le bouton droit n’importe où dans la jauge et en cliquant sur **Ajouter une échelle**.</span><span class="sxs-lookup"><span data-stu-id="ed92d-129">Alternatively, you can add a scale by right-clicking anywhere in the gauge and clicking **Add Scale**.</span></span> <span data-ttu-id="ed92d-130">Vous pouvez ensuite ajouter un nouveau pointeur, qui sera automatiquement associé à la dernière échelle.</span><span class="sxs-lookup"><span data-stu-id="ed92d-130">Then you can add a new pointer, and it will automatically be associated with the last scale.</span></span>  
  
 <span data-ttu-id="ed92d-131">Lorsque des pointeurs se chevauchent, l'ordre de dessin des pointeurs est déterminé par l'ordre dans lequel ils sont ajoutés à la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-131">When pointers overlap, the drawing order of the pointers is determined by the order in which they are added to the gauge.</span></span> <span data-ttu-id="ed92d-132">Vous ne pouvez pas modifier l'ordre des pointeurs en modifiant l'ordre des champs dans le volet des données.</span><span class="sxs-lookup"><span data-stu-id="ed92d-132">You cannot reorder the drawing order of the pointers by changing the order of the fields in the data pane.</span></span> <span data-ttu-id="ed92d-133">Pour modifier l’ordre de dessin de plusieurs pointeurs, ouvrez le volet Propriétés et cliquez sur **Pointeurs (...)** . Modifiez l'ordre des pointeurs dans la collection de pointeurs.</span><span class="sxs-lookup"><span data-stu-id="ed92d-133">To change the order of drawing for multiple pointers, open the Properties pane and click **Pointers (...)**. Then, change the order of the pointers in the Pointer collection.</span></span>  
  
  
##  <a name="setting-gradients-on-a-needle-cap"></a><a name="SettingGradients"></a> <span data-ttu-id="ed92d-134">Définition des dégradés sur la base d'une aiguille</span><span class="sxs-lookup"><span data-stu-id="ed92d-134">Setting Gradients on a Needle Cap</span></span>  
 <span data-ttu-id="ed92d-135">Vous pouvez spécifier la base d'une aiguille qui peut être dessinée au-dessus ou au-dessous du pointeur sur une jauge radiale uniquement.</span><span class="sxs-lookup"><span data-stu-id="ed92d-135">You can specify a needle cap that can be drawn on top or underneath the pointer on a radial gauge only.</span></span> <span data-ttu-id="ed92d-136">Tous les styles de base d'aiguille sont dessinés à l'aide de dégradés intégrés qui ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="ed92d-136">All needle cap styles are drawn by using built-in gradients that cannot be modified.</span></span> <span data-ttu-id="ed92d-137">La seule exception est le style `RoundedDark`, qui vous permet de spécifier une couleur et un style de dégradé.</span><span class="sxs-lookup"><span data-stu-id="ed92d-137">The exception is the `RoundedDark` style, where you can specify a gradient color and gradient style.</span></span>  
  
  
##  <a name="setting-a-snapping-interval"></a><a name="SettingSnappingInterval"></a> <span data-ttu-id="ed92d-138">Définition d'un intervalle d'alignement</span><span class="sxs-lookup"><span data-stu-id="ed92d-138">Setting a Snapping Interval</span></span>  
 <span data-ttu-id="ed92d-139">Un intervalle d'alignement définit le multiple auquel les valeurs sont arrondies.</span><span class="sxs-lookup"><span data-stu-id="ed92d-139">A snapping interval defines the multiple to which values are rounded.</span></span> <span data-ttu-id="ed92d-140">Par défaut, la jauge pointera sur la valeur exacte du champ que vous avez spécifiée dans le volet des données.</span><span class="sxs-lookup"><span data-stu-id="ed92d-140">By default, the gauge will point to the exact value of the field you have specified in the data pane.</span></span> <span data-ttu-id="ed92d-141">Toutefois, vous pouvez arrondir la valeur exacte à la valeur supérieure ou inférieure afin que le pointeur s'aligne sur un intervalle prédéfini.</span><span class="sxs-lookup"><span data-stu-id="ed92d-141">However, you might want to round the exact value up or down so that the pointer will snap to a pre-set interval.</span></span> <span data-ttu-id="ed92d-142">Par exemple, si la valeur sur votre jauge est 34,2 et que vous spécifiez un intervalle d'alignement de 5, le pointeur de jauge pointera sur 35.</span><span class="sxs-lookup"><span data-stu-id="ed92d-142">For example, if the value on your gauge is 34.2 and you specify a snapping interval of 5, the gauge pointer will point to 35.</span></span> <span data-ttu-id="ed92d-143">Si la valeur sur votre jauge est 31,2 et que vous spécifiez un intervalle d'alignement de 5, le pointeur de jauge pointera sur 30.</span><span class="sxs-lookup"><span data-stu-id="ed92d-143">If the value on your gauge is 31.2 and you specify a snapping interval of 5, the gauge pointer will point to 30.</span></span> <span data-ttu-id="ed92d-144">Pour plus d’informations, consultez [définir un intervalle d’alignement sur une jauge &#40;générateur de rapports et des&#41;SSRS ](../set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="ed92d-144">For more information, see [Set a Snapping Interval on a Gauge &#40;Report Builder and SSRS&#41;](../set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
  
##  <a name="specifying-an-image-as-a-pointer-on-a-radial-gauge"></a><a name="SpecifyingImage"></a> <span data-ttu-id="ed92d-145">Spécification d'une image en tant que pointeur sur une jauge radiale</span><span class="sxs-lookup"><span data-stu-id="ed92d-145">Specifying an Image as a Pointer on a Radial Gauge</span></span>  
 <span data-ttu-id="ed92d-146">En plus de la liste intégrée de styles de pointeur, vous pouvez choisir une image comme pointeur.</span><span class="sxs-lookup"><span data-stu-id="ed92d-146">In addition to the built-in list of pointer styles, you can specify an image as a pointer.</span></span> <span data-ttu-id="ed92d-147">Cela fonctionne très bien lorsque vous utilisez une image pour remplacer un style de pointeur de type aiguille existant.</span><span class="sxs-lookup"><span data-stu-id="ed92d-147">This is most effective when you use an image to replace an existing needle pointer style.</span></span> <span data-ttu-id="ed92d-148">L'image est superposée au pointeur, mais toutes les fonctionnalités du pointeur sont conservées.</span><span class="sxs-lookup"><span data-stu-id="ed92d-148">The image is superimposed over the pointer, but all pointer functionality is applicable.</span></span> <span data-ttu-id="ed92d-149">Les options de couleur et de dégradé ne sont pas applicables lorsqu'une image est utilisée comme pointeur.</span><span class="sxs-lookup"><span data-stu-id="ed92d-149">Color and gradient options are not applicable when an image is used for the pointer.</span></span>  
  
 <span data-ttu-id="ed92d-150">Si l'image du pointeur a une forme irrégulière, vous devez définir la couleur comme transparente afin de masquer les zones de votre image qui ne doivent pas apparaître sur la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-150">If the pointer image is an irregular shape, you should define the color as transparent to hide the areas of your image that should not appear on the gauge.</span></span> <span data-ttu-id="ed92d-151">Lorsque vous définissez une couleur transparente, la jauge transpose l'image sur votre pointeur existant et rogne l'image afin que seule la forme du pointeur apparaisse.</span><span class="sxs-lookup"><span data-stu-id="ed92d-151">When you define a transparent color, the gauge transposes the image on top of your existing pointer and trims the image so that only the shape of the pointer appears.</span></span> <span data-ttu-id="ed92d-152">La jauge recadre l'image en fonction de la taille de votre pointeur.</span><span class="sxs-lookup"><span data-stu-id="ed92d-152">The gauge rescales the image to fit the size of your pointer.</span></span> <span data-ttu-id="ed92d-153">Lorsque vous spécifiez une image comme pointeur, tout pointeur ajouté ultérieurement sur la jauge est dessiné sous l'image.</span><span class="sxs-lookup"><span data-stu-id="ed92d-153">When you specify an image for a pointer, any subsequent pointer that is added on top of the gauge will be drawn underneath the image.</span></span> <span data-ttu-id="ed92d-154">C'est pourquoi il est préférable de ne pas spécifier d'image pour le pointeur s'il y a plusieurs pointeurs sur la jauge.</span><span class="sxs-lookup"><span data-stu-id="ed92d-154">For this reason, it is better not to specify an image for the pointer if there are multiple pointers on the gauge.</span></span> <span data-ttu-id="ed92d-155">Pour plus d’informations, consultez [spécifier une image en tant que pointeur sur une jauge &#40;générateur de rapports et les&#41;SSRS ](../specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="ed92d-155">For more information, see [Specify an Image as a Pointer on a Gauge &#40;Report Builder and SSRS&#41;](../specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="ed92d-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed92d-156">See Also</span></span>  
 <span data-ttu-id="ed92d-157">[Mise en forme des échelles sur une jauge &#40;Générateur de rapports et SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed92d-157">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ed92d-158">[Mise en forme de plages sur une jauge &#40;Générateur de rapports et SSRS&#41;](formatting-ranges-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ed92d-158">[Formatting Ranges on a Gauge &#40;Report Builder and SSRS&#41;](formatting-ranges-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ed92d-159">Jauges &#40;Générateur de rapports et SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ed92d-159">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  