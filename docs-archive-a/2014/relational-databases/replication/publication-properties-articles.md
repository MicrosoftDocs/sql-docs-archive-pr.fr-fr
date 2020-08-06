---
title: Propriétés de la publication, Articles | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.articles.f1
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b88c54a6fc8c33193af7573ebd9b7c9931d8fbe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702696"
---
# <a name="publication-properties-articles"></a><span data-ttu-id="acaba-102">Propriétés de la publication, Articles</span><span class="sxs-lookup"><span data-stu-id="acaba-102">Publication Properties, Articles</span></span>
  <span data-ttu-id="acaba-103">La page **Articles** de la boîte de dialogue **Propriétés de la publication** reprend les informations sur les articles contenus dans une publication, vous permet d'ajouter ou de supprimer des articles de publications existantes, ainsi que de modifier les propriétés des articles et le filtrage s'appuyant sur des colonnes.</span><span class="sxs-lookup"><span data-stu-id="acaba-103">The **Articles** page of the **Publication Properties** dialog box: contains information about the articles contained in a publication; allows you to add articles to and drop articles from existing publications; and allows you to change article properties and column filtering.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acaba-104">Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané.</span><span class="sxs-lookup"><span data-stu-id="acaba-104">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="acaba-105">Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées.</span><span class="sxs-lookup"><span data-stu-id="acaba-105">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="acaba-106">Pour plus d’informations, consultez [Modifier les propriétés des publications et des articles](publish/change-publication-and-article-properties.md) et [Ajouter et supprimer des articles de publications existantes](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-106">For more information, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
 <span data-ttu-id="acaba-107">Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets de base de données, vous devez publier tous les objets référencés.</span><span class="sxs-lookup"><span data-stu-id="acaba-107">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="acaba-108">Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.</span><span class="sxs-lookup"><span data-stu-id="acaba-108">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="acaba-109">Une icône rouge apparaît en regard des objets ne pouvant pas être publiés, avec une explication dans le panneau d'information se trouvant en bas de la page de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="acaba-109">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="acaba-110">Les objets suivants ne peuvent pas être publiés :</span><span class="sxs-lookup"><span data-stu-id="acaba-110">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="acaba-111">Les objets chiffrés.</span><span class="sxs-lookup"><span data-stu-id="acaba-111">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="acaba-112">Les vues indexées contenant des colonnes autorisant la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="acaba-112">Indexed views containing columns that allow NULL.</span></span>  
  
-   <span data-ttu-id="acaba-113">Les tables ne possédant pas de clé primaire ne peuvent pas être publiées dans des publications transactionnelles.</span><span class="sxs-lookup"><span data-stu-id="acaba-113">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="acaba-114">Les tables ne peuvent en effet pas être publiées à la fois dans une publication de fusion et une publication transactionnelle avec l'option de mise à jour d'abonnements en attente activée.</span><span class="sxs-lookup"><span data-stu-id="acaba-114">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="acaba-115">Pour plus d’informations sur la publication d’un article dans plusieurs publications, consultez la section « Publication de tables dans plusieurs publications » dans [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-115">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="acaba-116">Serveurs de publication Oracle</span><span class="sxs-lookup"><span data-stu-id="acaba-116">Oracle Publishers</span></span>  
 <span data-ttu-id="acaba-117">Des points supplémentaires sont également à prendre en compte dans le cas d'utilisation de serveur de publication Oracle :</span><span class="sxs-lookup"><span data-stu-id="acaba-117">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="acaba-118">Pour obtenir la liste des objets pouvant être publiés d'un serveur Oracle, consultez [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-118">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="acaba-119">Les objets qui ne peuvent pas être publiés ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="acaba-119">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="acaba-120">Pour obtenir la liste des types de données pouvant être publiés, consultez [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-120">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="acaba-121">Les colonnes dont le type de données ne peut pas être publié ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="acaba-121">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="acaba-122">Filtres de colonnes</span><span class="sxs-lookup"><span data-stu-id="acaba-122">Column Filters</span></span>  
 <span data-ttu-id="acaba-123">Vous pouvez filtrer les colonnes de cette page en développant une table dans le volet **Objets à publier** , puis en ne sélectionnant que les colonnes nécessaires (les lignes peuvent en effet être filtrées à partir de la page **Filtrer les lignes de la table** de ce même Assistant).</span><span class="sxs-lookup"><span data-stu-id="acaba-123">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="acaba-124">Le filtrage de colonnes s'avère utile pour de nombreuses raisons, notamment en ce qui a trait à la sécurité (contribuant à protéger des données sensibles contre toute réplication) et aux performances (empêchant par exemple la réplication d'objets binaires volumineux, appelés également Blob pour Bynary Large OBjects).</span><span class="sxs-lookup"><span data-stu-id="acaba-124">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="acaba-125">Pour plus d’informations sur le filtrage de colonnes, notamment pour connaître la liste des types de colonne éligibles au filtrage, consultez [Filtrer des données publiées](publish/filter-published-data.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-125">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="acaba-126">Options</span><span class="sxs-lookup"><span data-stu-id="acaba-126">Options</span></span>  
 <span data-ttu-id="acaba-127">Le volet **Objets à publier** vous permet :</span><span class="sxs-lookup"><span data-stu-id="acaba-127">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="acaba-128">d'afficher tous les objets disponibles à la réplication ;</span><span class="sxs-lookup"><span data-stu-id="acaba-128">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="acaba-129">d'ajouter un article à une publication en activant la case à cocher en regard de l'objet ;</span><span class="sxs-lookup"><span data-stu-id="acaba-129">Add an article to a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="acaba-130">de supprimer un article d'une publication en désactivant la case à cocher en regard de l'objet.</span><span class="sxs-lookup"><span data-stu-id="acaba-130">Drop an article from a publication by clearing the check box next to that object.</span></span> <span data-ttu-id="acaba-131">Pour savoir quand les articles peuvent être supprimés, consultez [Ajouter et supprimer des articles de publications existantes](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-131">For information about when articles can be dropped, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="acaba-132">d'inclure tous les objets d'un type donné (par exemple, une table) se trouvant dans la publication, en activant la case à cocher en regard du type de l'objet (dans notre cas, **Tables**).</span><span class="sxs-lookup"><span data-stu-id="acaba-132">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="acaba-133">de développer les nœuds de la table pour en afficher les colonnes ;</span><span class="sxs-lookup"><span data-stu-id="acaba-133">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="acaba-134">de filtrer les colonnes d'une table d'une publication en désactivant la case à cocher en regard de la colonne, ou encore d'inclure les colonnes non publiées en activant au contraire leurs cases à cocher ;</span><span class="sxs-lookup"><span data-stu-id="acaba-134">Filter table columns out of a publication by clearing the check box next to the column or include unpublished columns by selecting the check box.</span></span>  
  
-   <span data-ttu-id="acaba-135">enfin, de cliquer sur un objet dans le volet avec le bouton droit de la souris afin d'afficher un menu répertoriant les commandes applicables à cet objet.</span><span class="sxs-lookup"><span data-stu-id="acaba-135">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="acaba-136">**Propriétés de l'article**</span><span class="sxs-lookup"><span data-stu-id="acaba-136">**Article Properties**</span></span>  
 <span data-ttu-id="acaba-137">Cliquez sur **Propriétés de l'article** , puis effectuez l'une des actions ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="acaba-137">Click **Article Properties** , and then click one of the following:</span></span>  
  
-   <span data-ttu-id="acaba-138">Cliquez sur **Définir les propriétés de l’article de \<ObjectType> en surbrillance** pour ouvrir la boîte de dialogue **Propriétés de l’article - \<ObjectName>** . Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet en surbrillance dans le volet Objet de la page **Articles**.</span><span class="sxs-lookup"><span data-stu-id="acaba-138">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="acaba-139">Cliquez sur **Définir les propriétés de tous les \<ObjectType>articles**  pour ouvrir la boîte de dialogue **Propriétés pour tous les \<ObjectType> articles**. Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet Objet de la page **Articles**, notamment ceux qui ne sont pas encore sélectionnés pour la publication.</span><span class="sxs-lookup"><span data-stu-id="acaba-139">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="acaba-140">Les modifications de propriétés apportées dans la boîte de dialogue **Propriétés pour tous les \<ObjectType> articles** remplacent celles apportées dans la boîte de dialogue **Propriétés de l’article - \<ObjectName>** .</span><span class="sxs-lookup"><span data-stu-id="acaba-140">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="acaba-141">Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles.</span><span class="sxs-lookup"><span data-stu-id="acaba-141">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="acaba-142">Définissez ensuite les propriétés des objets individuels.</span><span class="sxs-lookup"><span data-stu-id="acaba-142">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="acaba-143">**La table sélectionnée est en téléchargement seul**</span><span class="sxs-lookup"><span data-stu-id="acaba-143">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="acaba-144">Réplication de fusion uniquement.</span><span class="sxs-lookup"><span data-stu-id="acaba-144">Merge replication only.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="acaba-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement.</span><span class="sxs-lookup"><span data-stu-id="acaba-145">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="acaba-146">Permet d'indiquer que les modifications sont interdites au niveau de l'Abonné si l'abonnement d'un client est utilisé.</span><span class="sxs-lookup"><span data-stu-id="acaba-146">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="acaba-147">Étant donné que les articles disponibles uniquement par téléchargement ne peuvent pas être mis à jour sur l'abonné, le suivi des métadonnées n'est pas envoyé aux abonnés.</span><span class="sxs-lookup"><span data-stu-id="acaba-147">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="acaba-148">Cela peut aboutir à une réduction du stockage sur les abonnés et à un gain de performances, notamment si la connexion réseau est lente.</span><span class="sxs-lookup"><span data-stu-id="acaba-148">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="acaba-149">Cette option équivaut à la valeur **Téléchargement seul pour l'Abonné, interdire les modifications de l'Abonné** pour l'option **Direction de la synchronisation** dans la boîte de dialogue **Propriétés de l'article** .</span><span class="sxs-lookup"><span data-stu-id="acaba-149">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="acaba-150">Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span><span class="sxs-lookup"><span data-stu-id="acaba-150">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="acaba-151">**Afficher uniquement les objets activés dans la liste**</span><span class="sxs-lookup"><span data-stu-id="acaba-151">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="acaba-152">Activez cette case à cocher pour n'afficher que les articles sélectionnés dans le volet des objets.</span><span class="sxs-lookup"><span data-stu-id="acaba-152">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acaba-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acaba-153">See Also</span></span>  
 <span data-ttu-id="acaba-154">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="acaba-154">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="acaba-155">[Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="acaba-155">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="acaba-156">[Créer et appliquer l’instantané initial](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="acaba-156">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="acaba-157">[Réinitialiser un abonnement](reinitialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="acaba-157">[Reinitialize a Subscription](reinitialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="acaba-158">Publier des données et des objets de base de données</span><span class="sxs-lookup"><span data-stu-id="acaba-158">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  