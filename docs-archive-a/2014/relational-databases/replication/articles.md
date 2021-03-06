---
title: Articles | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.articles.f1
ms.assetid: 7c743dc6-6c6d-4c92-b711-842e1b0b273e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91336314a9538633af7c528d756d8461f7e8fe13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709227"
---
# <a name="articles"></a>Articles
  La page **Articles** permet de définir les objets de base de données à inclure sous forme d'articles dans la publication. Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets de base de données, vous devez publier tous les objets référencés. Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.  
  
 Une icône rouge apparaît en regard des objets ne pouvant pas être publiés, avec une explication dans le panneau d'information se trouvant en bas de la page de l'Assistant. Les objets suivants ne peuvent pas être publiés :  
  
-   Les objets chiffrés.  
  
-   Les tables ne possédant pas de clé primaire ne peuvent pas être publiées dans des publications transactionnelles.  
  
-   Les tables ne peuvent en effet pas être publiées à la fois dans une publication de fusion et une publication transactionnelle avec l'option de mise à jour d'abonnements en attente activée. Pour plus d’informations sur la publication d’un article dans plusieurs publications, consultez la section « Publication de tables dans plusieurs publications » dans [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md).  
  
## <a name="oracle-publishers"></a>Serveurs de publication Oracle  
 Des points supplémentaires sont également à prendre en compte dans le cas d'utilisation de serveur de publication Oracle :  
  
-   Pour obtenir la liste des objets pouvant être publiés d'un serveur Oracle, consultez [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md). Les objets qui ne peuvent pas être publiés ne sont pas affichés.  
  
-   Pour obtenir la liste des types de données pouvant être publiés, consultez [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md). Les colonnes dont le type de données ne peut pas être publié ne sont pas affichées.  
  
## <a name="column-filters"></a>Filtres de colonnes  
 Vous pouvez filtrer les colonnes de cette page en développant une table dans le volet **Objets à publier** , puis en ne sélectionnant que les colonnes nécessaires (les lignes peuvent en effet être filtrées à partir de la page **Filtrer les lignes de la table** de ce même Assistant). Le filtrage de colonnes s'avère utile pour de nombreuses raisons, notamment en ce qui a trait à la sécurité (contribuant à protéger des données sensibles contre toute réplication) et aux performances (empêchant par exemple la réplication d'objets binaires volumineux, appelés également Blob pour Bynary Large OBjects). Pour plus d’informations sur le filtrage de colonnes, notamment pour connaître la liste des types de colonne éligibles au filtrage, consultez [Filtrer des données publiées](publish/filter-published-data.md).  
  
## <a name="options"></a>Options  
 Le volet **Objets à publier** vous permet :  
  
-   d'afficher tous les objets disponibles à la réplication ;  
  
-   d'inclure un objet dans une publication en activant sa case à cocher ;  
  
-   d'inclure tous les objets d'un type donné (par exemple, une table) se trouvant dans la publication, en activant la case à cocher en regard du type de l'objet (dans notre cas, **Tables**).  
  
-   de développer les nœuds de la table pour en afficher les colonnes ;  
  
-   de filtrer les colonnes d'une table depuis une publication en désactivant la case à cocher des colonnes ;  
  
-   enfin, de cliquer sur un objet dans le volet avec le bouton droit de la souris afin d'afficher un menu répertoriant les commandes applicables à cet objet.  
  
 **Propriétés de l'article**  
 Cliquez sur **Propriétés de l’article**, puis effectuez l’une des opérations suivantes :  
  
-   Cliquez sur **Définir les propriétés de l’article de \<ObjectType> en surbrillance** pour ouvrir la boîte de dialogue **Propriétés de l’article - \<ObjectName>** . Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet en surbrillance dans le volet Objet de la page **Articles**.  
  
-   Cliquez sur **Définir les propriétés de tous les \<ObjectType>articles**  pour ouvrir la boîte de dialogue **Propriétés pour tous les \<ObjectType> articles**. Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet Objet de la page **Articles**, notamment ceux qui ne sont pas encore sélectionnés pour la publication.  
  
    > [!NOTE]  
    >  Les modifications de propriétés apportées dans la boîte de dialogue **Propriétés pour tous les \<ObjectType> articles** remplacent celles apportées dans la boîte de dialogue **Propriétés de l’article - \<ObjectName>** . Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
 **La table sélectionnée est en téléchargement seul**  
 Réplication de fusion uniquement. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Permet d'indiquer que les modifications sont interdites au niveau de l'Abonné si l'abonnement d'un client est utilisé. Étant donné que les articles disponibles uniquement par téléchargement ne peuvent pas être mis à jour sur l'abonné, le suivi des métadonnées n'est pas envoyé aux abonnés. Cela peut aboutir à une réduction du stockage sur les abonnés et à un gain de performances, notamment si la connexion réseau est lente. Cette option équivaut à la valeur **Téléchargement seul pour l'Abonné, interdire les modifications de l'Abonné** pour l'option **Direction de la synchronisation** dans la boîte de dialogue **Propriétés de l'article** . Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Afficher uniquement les objets activés dans la liste**  
 Activez cette case à cocher pour n'afficher que les articles sélectionnés dans le volet des objets.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)  
  
  
