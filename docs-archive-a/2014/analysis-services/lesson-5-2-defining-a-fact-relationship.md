---
title: Définition d’une relation de faits | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614214"
---
# <a name="defining-a-fact-relationship"></a><span data-ttu-id="74238-102">Définition d'une relation de faits</span><span class="sxs-lookup"><span data-stu-id="74238-102">Defining a Fact Relationship</span></span>
  <span data-ttu-id="74238-103">Les utilisateurs souhaitent parfois pouvoir dimensionner des mesures par élément de données se trouvant dans la table de faits ou exécuter des requêtes sur la table de faits pour obtenir des informations spécifiques connexes supplémentaires, telles que des numéros de factures ou de bons de commande associés à des ventes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="74238-103">Users sometimes want to be able to dimension measures by data items that are in the fact table or to query the fact table for specific additional related information, such as invoice numbers or purchase order numbers related to specific sales facts.</span></span> <span data-ttu-id="74238-104">Quand vous définissez une dimension basée sur un élément de table de faits de ce type, la dimension est appelée *dimension de fait*.</span><span class="sxs-lookup"><span data-stu-id="74238-104">When you define a dimension based on such a fact table item, the dimension is called a *fact dimension*.</span></span> <span data-ttu-id="74238-105">Les dimensions de fait sont aussi appelées dimensions dégénérées.</span><span class="sxs-lookup"><span data-stu-id="74238-105">Fact dimensions are also known as degenerate dimensions.</span></span> <span data-ttu-id="74238-106">Les dimensions de fait servent à regrouper des lignes connexes de la table de faits, par exemple toutes les lignes concernant un numéro de facture particulier.</span><span class="sxs-lookup"><span data-stu-id="74238-106">Fact dimensions are useful for grouping together related fact table rows, such as all the rows that are related to a particular invoice number.</span></span> <span data-ttu-id="74238-107">Bien qu'il soit possible de stocker cette information dans une table de dimensions distincte dans la base de données relationnelles, la création d'une table de dimensions distincte pour cette information n'offre aucun avantage, car la table de dimensions augmente à la même vitesse que la table de faits et le seul résultat obtenu est la duplication des données et une plus grande complexité, ce qui est inutile.</span><span class="sxs-lookup"><span data-stu-id="74238-107">Although you can put this information in a separate dimension table in the relational database, creating a separate dimension table for the information provides no benefit because the dimension table would grow at the same rate as the fact table, and would just create duplicate data and unnecessary complexity.</span></span>

 <span data-ttu-id="74238-108">Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous pouvez déterminer s'il est nécessaire de dupliquer les données des dimensions de fait dans la structure de dimensions MOLAP pour augmenter les performances des requêtes ou s'il est nécessaire de définir les dimensions de fait en tant que dimensions ROLAP pour gagner de l'espace de stockage aux dépens des performances des requêtes.</span><span class="sxs-lookup"><span data-stu-id="74238-108">Within [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can determine whether to duplicate the fact dimension data in a MOLAP dimension structure for increased query performance, or whether to define the fact dimension as a ROLAP dimension to save storage space at the expense of query performance.</span></span> <span data-ttu-id="74238-109">Lorsque vous stockez une dimension avec le mode de stockage MOLAP, tous les membres de dimension sont stockés dans l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans une structure MOLAP avec un taux de compression élevé et sont aussi stockés dans les partitions du groupe de mesures.</span><span class="sxs-lookup"><span data-stu-id="74238-109">When you store a dimension with the MOLAP storage mode, all the dimension members are stored in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in a highly compressed MOLAP structure, in addition to being stored in the measure group's partitions.</span></span> <span data-ttu-id="74238-110">Lorsque vous stockez une dimension avec le mode de stockage ROLAP, seule la définition de la dimension est stockée dans la structure MOLAP. les membres de la dimension sont interrogés à partir de la table de faits relationnelle sous-jacente au moment de la requête.</span><span class="sxs-lookup"><span data-stu-id="74238-110">When you store a dimension with the ROLAP storage mode, only the dimension definition is stored in the MOLAP structure-the dimension members themselves are queried from the underlying relational fact table at query time.</span></span> <span data-ttu-id="74238-111">Le mode de stockage approprié se choisit en fonction de la fréquence à laquelle les requêtes sont exécutées sur la dimension de fait, du nombre de lignes retournées par une requête classique, de la performance de la requête et enfin, du coût de traitement.</span><span class="sxs-lookup"><span data-stu-id="74238-111">You decide the appropriate storage mode based on how frequently the fact dimension is queried, the number of rows returned by a typical query, the performance of the query, and the processing cost.</span></span> <span data-ttu-id="74238-112">Pour définir une dimension ROLAP, il n'est pas nécessaire que tous les cubes qui utilisent la dimension soient également stockés avec le mode de stockage ROLAP.</span><span class="sxs-lookup"><span data-stu-id="74238-112">Defining a dimension as ROLAP does not require that all cubes that use the dimension also be stored with the ROLAP storage mode.</span></span> <span data-ttu-id="74238-113">Le mode de stockage pour chaque dimension peut être configuré indépendamment.</span><span class="sxs-lookup"><span data-stu-id="74238-113">The storage mode for each dimension can be configured independently.</span></span>

 <span data-ttu-id="74238-114">Lorsque vous définissez une dimension de fait, vous pouvez définir la relation entre cette dimension et le groupe de mesures comme étant une relation de faits.</span><span class="sxs-lookup"><span data-stu-id="74238-114">When you define a fact dimension, you can define the relationship between the fact dimension and the measure group as a fact relationship.</span></span> <span data-ttu-id="74238-115">Les contraintes suivantes s'appliquent aux relations de faits :</span><span class="sxs-lookup"><span data-stu-id="74238-115">The following constraints apply to fact relationships:</span></span>

-   <span data-ttu-id="74238-116">L'attribut de granularité doit correspondre à la colonne clé de la dimension, ce qui crée une relation un-à-un entre la dimension et les faits de la table de faits.</span><span class="sxs-lookup"><span data-stu-id="74238-116">The granularity attribute must be the key column for the dimension, which creates a one-to-one relationship between the dimension and the facts in the fact table.</span></span>

-   <span data-ttu-id="74238-117">Une dimension peut avoir une relation de faits avec un seul groupe de mesures uniquement.</span><span class="sxs-lookup"><span data-stu-id="74238-117">A dimension can have a fact relationship with only a single measure group.</span></span>

> [!NOTE]
>  <span data-ttu-id="74238-118">Les dimensions de fait doivent être mises à jour de façon incrémentielle après chaque mise à jour vers le groupe de mesures auquel la relation de faits se réfère.</span><span class="sxs-lookup"><span data-stu-id="74238-118">Fact dimensions must be incrementally updated after every update to the measure group that the fact relationship references.</span></span>

 <span data-ttu-id="74238-119">Pour plus d’informations, consultez [Relations de dimension](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)et [Définir une relation de fait et des propriétés de relation de fait](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span><span class="sxs-lookup"><span data-stu-id="74238-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span></span>

 <span data-ttu-id="74238-120">Au cours des tâches de cette rubrique, vous allez ajouter une nouvelle dimension de cube basée sur la colonne **CustomerPONumber** dans la table de faits **FactInternetSales** .</span><span class="sxs-lookup"><span data-stu-id="74238-120">In the tasks in this topic, you add a new cube dimension based on the **CustomerPONumber** column in the **FactInternetSales** fact table.</span></span> <span data-ttu-id="74238-121">Vous allez ensuite définir la relation entre cette nouvelle dimension de cube et le groupe de mesures **Internet Sales** en tant que relation de faits.</span><span class="sxs-lookup"><span data-stu-id="74238-121">You then define the relationship between this new cube dimension and the **Internet Sales** measure group as a fact relationship.</span></span>

## <a name="defining-the-internet-sales-orders-fact-dimension"></a><span data-ttu-id="74238-122">Définition de la dimension de faits Internet Sales Orders</span><span class="sxs-lookup"><span data-stu-id="74238-122">Defining the Internet Sales Orders Fact Dimension</span></span>

1.  <span data-ttu-id="74238-123">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Dimensions**, puis cliquez sur **Nouvelle dimension**.</span><span class="sxs-lookup"><span data-stu-id="74238-123">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="74238-124">Dans la page **Assistant Dimension** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="74238-124">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="74238-125">Dans la page **Sélectionner la méthode de création** , vérifiez que l’option **Utiliser une table existante** est sélectionnée, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="74238-125">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="74238-126">Dans la page **Spécifier des informations sur la source** , vérifiez que la vue de source des données **Adventure Works DW 2012** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="74238-126">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>

5.  <span data-ttu-id="74238-127">Dans la liste **Table principale** , sélectionnez **InternetSales**.</span><span class="sxs-lookup"><span data-stu-id="74238-127">In the **Main table** list, select **InternetSales**.</span></span>

6.  <span data-ttu-id="74238-128">Dans la liste **Colonnes clés** , vérifiez que **SalesOrderNumber** et **SalesOrderLineNumber** sont mentionnées.</span><span class="sxs-lookup"><span data-stu-id="74238-128">In the **Key columns** list, verify that **SalesOrderNumber** and **SalesOrderLineNumber** are listed.</span></span>

7.  <span data-ttu-id="74238-129">Dans la liste **Colonne de nom** , sélectionnez **SalesOrderLineNumber**.</span><span class="sxs-lookup"><span data-stu-id="74238-129">In the **Name column** list, select **SalesOrderLineNumber**.</span></span>

8.  <span data-ttu-id="74238-130">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="74238-130">Click **Next**.</span></span>

9. <span data-ttu-id="74238-131">Dans la page **Sélectionner les tables associées** , décochez les cases à côté de toutes les tables, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="74238-131">On the **Select Related Tables** page, clear the check boxes beside all of the tables, and then click **Next**.</span></span>

10. <span data-ttu-id="74238-132">Dans la page **Sélectionner les attributs de la dimension** , cliquez deux fois sur la case à cocher de l’en-tête pour décocher toutes les cases.</span><span class="sxs-lookup"><span data-stu-id="74238-132">On the **Select Dimension Attributes** page, click the check box in the header twice to clear all of the check boxes.</span></span> <span data-ttu-id="74238-133">L’attribut **Sales Order Number** reste sélectionné car il s’agit de l’attribut de clé.</span><span class="sxs-lookup"><span data-stu-id="74238-133">The **Sales Order Number** attribute will remain selected because it is the key attribute.</span></span>

11. <span data-ttu-id="74238-134">Sélectionnez l’attribut **Customer PO Number** , puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="74238-134">Select the **Customer PO Number** attribute, and then click **Next**.</span></span>

12. <span data-ttu-id="74238-135">Dans la page **Fin de l’Assistant** , remplacez le nom par **Internet Sales Order Details** , puis cliquez sur **Terminer** pour fermer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="74238-135">On the **Completing the Wizard** page, change the name to **Internet Sales Order Details** and then click **Finish** to complete the wizard.</span></span>

13. <span data-ttu-id="74238-136">Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="74238-136">On the **File** menu, click **Save All**.</span></span>

14. <span data-ttu-id="74238-137">Dans le volet **attributs** du concepteur de dimensions pour la dimension **Internet Sales Order Details** , sélectionnez **Sales Order Number**, puis remplacez la propriété **Name** de la fenêtre Propriétés par`Item Description.`</span><span class="sxs-lookup"><span data-stu-id="74238-137">In the **Attributes** pane of the Dimension Designer for the **Internet Sales Order Details** dimension, select **Sales Order Number**, and then change the **Name** property in the Properties window to `Item Description.`</span></span>

15. <span data-ttu-id="74238-138">Dans la cellule de propriété **NameColumn** , cliquez sur le bouton Parcourir **(...)**. Dans la boîte de dialogue **colonne de nom** , sélectionnez **Product** dans la liste **table source** , sélectionnez **EnglishProductName** pour la **colonne source**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="74238-138">In the **NameColumn** property cell, click the browse button **(...)**. In the **Name Column** dialog box, select **Product** from the **Source table** list, select **EnglishProductName** for the **Source column**, and then click **OK**.</span></span>

16. <span data-ttu-id="74238-139">Ajoutez l’attribut **Sales Order Number** à la dimension. Pour cela, faites glisser la colonne **SalesOrderNumber** de la table **InternetSales** du volet **Vue de source de données** vers le volet **Attributs** .</span><span class="sxs-lookup"><span data-stu-id="74238-139">Add the **Sales Order Number** attribute to the dimension by dragging the **SalesOrderNumber** column from the **InternetSales** table in the **Data Source View** pane to the **Attributes** pane.</span></span>

17. <span data-ttu-id="74238-140">Remplacez la propriété **Name** du nouvel attribut **Sales Order Number** par `Order Number` , puis remplacez la valeur de la propriété **orderby** par **Key**.</span><span class="sxs-lookup"><span data-stu-id="74238-140">Change the **Name** property of the new **Sales Order Number** attribute to `Order Number`, and change the **OrderBy** property to **Key**.</span></span>

18. <span data-ttu-id="74238-141">Dans le volet **hiérarchies** , créez une hiérarchie utilisateur **Internet Sales Orders** qui contient les niveaux de description de l' `Order Number` **élément** et, dans cet ordre.</span><span class="sxs-lookup"><span data-stu-id="74238-141">In the **Hierarchies** pane, create an **Internet Sales Orders** user hierarchy that contains the `Order Number` and **Item Description** levels, in that order.</span></span>

19. <span data-ttu-id="74238-142">Dans le volet **Attributs**, sélectionnez **Internet Sales Order Details** et vérifiez la valeur de la propriété **StorageMode** dans la fenêtre des propriétés.</span><span class="sxs-lookup"><span data-stu-id="74238-142">In the **Attributes** pane, select **Internet Sales Order Details**, and then review the value for the **StorageMode** property in the Properties window.</span></span>

     <span data-ttu-id="74238-143">Notez que cette dimension est stockée par défaut en tant que dimension MOLAP.</span><span class="sxs-lookup"><span data-stu-id="74238-143">Notice that, by default, this dimension is stored as a MOLAP dimension.</span></span> <span data-ttu-id="74238-144">Si l'utilisation du mode de stockage ROLAP en lieu et place du mode MOLAP permet de réduire le temps de traitement et de gagner de l'espace de stockage, elle se fait toutefois au dépend des performances des requêtes.</span><span class="sxs-lookup"><span data-stu-id="74238-144">Although changing the storage mode to ROLAP will save processing time and storage space, it occurs at the expense of query performance.</span></span> <span data-ttu-id="74238-145">Dans le cadre de ce didacticiel, vous allez utiliser le mode de stockage MOLAP.</span><span class="sxs-lookup"><span data-stu-id="74238-145">For the purposes of this tutorial, you will use MOLAP as the storage mode.</span></span>

20. <span data-ttu-id="74238-146">Pour ajouter la dimension créée récemment au cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] comme dimension du cube, basculez vers le **Concepteur de cube**.</span><span class="sxs-lookup"><span data-stu-id="74238-146">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="74238-147">Sous l’onglet **Structure de cube** , cliquez avec le bouton droit dans le volet **Dimensions** et sélectionnez **Ajouter une dimension de cube**.</span><span class="sxs-lookup"><span data-stu-id="74238-147">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

21. <span data-ttu-id="74238-148">Dans la boîte de dialogue **Ajouter une dimension de cube**, sélectionnez **Internet Sales Order Details** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="74238-148">In the **Add Cube Dimension**.dialog box, select **Internet Sales Order Details** and then click **OK**.</span></span>

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a><span data-ttu-id="74238-149">Définition d'une relation de faits pour la dimension de fait</span><span class="sxs-lookup"><span data-stu-id="74238-149">Defining a Fact Relationship for the Fact Dimension</span></span>

1.  <span data-ttu-id="74238-150">Dans le Concepteur de cube du cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , cliquez sur l’onglet **Utilisation de la dimension** .</span><span class="sxs-lookup"><span data-stu-id="74238-150">In the Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="74238-151">Notez que la dimension de cube **Internet Sales Order Details** est configurée automatiquement avec une relation de faits, comme le montre l’icône unique.</span><span class="sxs-lookup"><span data-stu-id="74238-151">Notice that the **Internet Sales Order Details** cube dimension is automatically configured as having a fact relationship, as shown by the unique icon.</span></span>

2.  <span data-ttu-id="74238-152">Cliquez sur le bouton Parcourir (**...**) dans la cellule **Description** de l’élément, à l’intersection du groupe de mesures **Internet Sales** et de la dimension **Internet Sales Order Details** , pour passer en revue les propriétés de la relation de faits.</span><span class="sxs-lookup"><span data-stu-id="74238-152">Click the browse button (**...**) in the **Item Description** cell, at the intersection of the **Internet Sales** measure group and the **Internet Sales Order Details** dimension, to review the fact relationship properties.</span></span>

     <span data-ttu-id="74238-153">La boîte de dialogue **Définir une relation** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="74238-153">The **Define Relationship** dialog box opens.</span></span> <span data-ttu-id="74238-154">Notez que vous ne pouvez pas configurer les propriétés.</span><span class="sxs-lookup"><span data-stu-id="74238-154">Notice that you cannot configure any of the properties.</span></span>

     <span data-ttu-id="74238-155">L’illustration suivante montre les propriétés de la relation de faits dans la boîte de dialogue **Définir une relation** .</span><span class="sxs-lookup"><span data-stu-id="74238-155">The following image shows the fact relationship properties in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="74238-156">![Boîte de dialogue définir une relation](../../2014/tutorials/media/l5-factrelationship-2.gif "Boîte de dialogue Définir une relation")</span><span class="sxs-lookup"><span data-stu-id="74238-156">![Define Relationship dialog box](../../2014/tutorials/media/l5-factrelationship-2.gif "Define Relationship dialog box")</span></span>

3.  <span data-ttu-id="74238-157">Cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="74238-157">Click **Cancel**.</span></span>

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a><span data-ttu-id="74238-158">Exploration du cube en utilisant la dimension de fait</span><span class="sxs-lookup"><span data-stu-id="74238-158">Browsing the Cube by Using the Fact Dimension</span></span>

1.  <span data-ttu-id="74238-159">Dans le menu **Générer** , cliquez sur **Déployer Analysis Services Tutorial** pour déployer les modifications sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et traiter la base de données.</span><span class="sxs-lookup"><span data-stu-id="74238-159">On the **Build** menu, click **Deploy Analysis Services Tutorial** to deploy the changes to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and process the database.</span></span>

2.  <span data-ttu-id="74238-160">Une fois le déploiement terminé, cliquez sur l’onglet **Navigateur** dans le Concepteur de cube correspondant au cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Reconnexion** .</span><span class="sxs-lookup"><span data-stu-id="74238-160">After deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="74238-161">Désactivez toutes les mesures et toutes les hiérarchies du volet Données, puis ajoutez la mesure **Internet Sales-Sales Amount** à la zone de données du volet Données.</span><span class="sxs-lookup"><span data-stu-id="74238-161">Clear all measures and hierarchies from the data pane, and then add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="74238-162">Dans le volet Métadonnées, développez **Customer**, **Location**, **Customer Geography**, **Members**, **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, puis cliquez avec le bouton droit sur **Adam Powell**et choisissez **Ajouter au filtre**.</span><span class="sxs-lookup"><span data-stu-id="74238-162">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, right-click **Adam Powell**, and then click **Add to Filter**.</span></span>

     <span data-ttu-id="74238-163">L'application d'un filtre pour limiter les commandes retournées à un seul client permet à l'utilisateur d'explorer les données détaillées sous-jacentes dans une table de faits volumineuse sans enregistrer une diminution des performances des requêtes.</span><span class="sxs-lookup"><span data-stu-id="74238-163">Filtering to limit the sales orders returned to a single customer lets the user drill down to the underlying detail in a large fact table without suffering a significant loss in query performance.</span></span>

5.  <span data-ttu-id="74238-164">Ajoutez la hiérarchie définie par l’utilisateur **Internet Sales Orders** de la dimension **Internet Sales Order Details** vers la zone de lignes du volet Données.</span><span class="sxs-lookup"><span data-stu-id="74238-164">Add the **Internet Sales Orders** user-defined hierarchy from the **Internet Sales Order Details** dimension to the row area of the data pane.</span></span>

     <span data-ttu-id="74238-165">Notez que les bons de commande et les montants des ventes Internet correspondant au client Adam Powell apparaissent dans le volet Données.</span><span class="sxs-lookup"><span data-stu-id="74238-165">Notice that the sales order numbers and the corresponding Internet sales amounts for Adam Powell appear in the data pane.</span></span>

     <span data-ttu-id="74238-166">L'illustration suivante montre le résultat des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="74238-166">The following image shows the result of the previous steps.</span></span>

     <span data-ttu-id="74238-167">![Dimensionnement de Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensionnement de Internet Sales-Sales Amount")</span><span class="sxs-lookup"><span data-stu-id="74238-167">![Dimensioning of Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensioning of Internet Sales-Sales Amount")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="74238-168">Tâche suivante de la leçon</span><span class="sxs-lookup"><span data-stu-id="74238-168">Next Task in Lesson</span></span>
 [<span data-ttu-id="74238-169">Définition d’une relation plusieurs-à-plusieurs</span><span class="sxs-lookup"><span data-stu-id="74238-169">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a><span data-ttu-id="74238-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74238-170">See Also</span></span>
 <span data-ttu-id="74238-171">Les [relations de dimension](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [définissent une relation de fait et des propriétés de relation de fait](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="74238-171">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span></span>

