---
title: Créer, modifier et supprimer les index spatiaux | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601308"
---
# <a name="create-modify-and-drop-spatial-indexes"></a>Créer, modifier et supprimer les index spatiaux
  Un index spatial peut effectuer plus efficacement certaines opérations sur une colonne du `geometry` type de `geography` données ou (une *colonne spatiale*). Plusieurs index spatiaux peuvent être spécifiés sur une colonne spatiale. Cela peut s'avérer utile par exemple pour indexer différents paramètres de pavage dans une même colonne.  
  
 Il existe plusieurs restrictions applicables à la création d'index spatiaux. Pour plus d'informations, consultez [Restrictions sur les index spatiaux](#restrictions) dans cette rubrique.  
  
> [!NOTE]  
>  Pour plus d’informations sur la relation entre les index spatiaux et les partitions et groupes de fichiers, consultez la section « Remarques » dans [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> Création, modification et suppression d'index spatiaux  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> Pour créer un index spatial  
 **Pour créer un index spatial à l'aide de Transact-SQL**  
 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 **Pour créer un index spatial à l'aide de la boîte de dialogue Nouvel index dans Management Studio**  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a>Pour créer un index spatial dans Management Studio  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données qui contient la table dotée de l'index spécifié, puis développez **Tables**.  
  
3.  Développez la table pour laquelle vous souhaitez créer l'index.  
  
4.  Cliquez avec le bouton droit sur **Index** et sélectionnez **Nouvel index**.  
  
5.  Dans le champ **Nom de l'index** , entrez un nom pour l'index.  
  
6.  Dans la liste déroulante **Type d’index** , sélectionnez **Spatial**.  
  
7.  Pour spécifier la colonne spatiale à indexer, cliquez sur **Ajouter**.  
  
8.  Dans la boîte de dialogue **Sélectionner les colonnes à partir de** *\<table name>* , sélectionnez une colonne de type `geometry` ou `geography` en activant la case à cocher correspondante. Toutes les autres colonnes spatiales deviennent alors impossibles à modifier. Si vous souhaitez sélectionner une autre colonne spatiale, vous devez tout d'abord désactiver la colonne sélectionnée actuellement. Lorsque vous avez terminé, cliquez sur **OK**.  
  
9. Vérifiez votre sélection de colonne dans la grille **Colonnes clés d'index** .  
  
10. Dans le volet **Sélectionner une page** de la boîte de dialogue **Propriétés de l'index** , cliquez sur **Spatial**.  
  
11. Dans la page **Spatial** , spécifiez les valeurs que vous souhaitez utiliser pour les propriétés spatiales de l'index.  
  
     Lorsque vous créez un index sur une `geometry` colonne de type, vous devez spécifier les coordonnées **( *`X-min`* , *`Y-min`* )** et **( *`X-max`* , *`Y-max`* )** de la zone englobante. Pour un index sur une `geography` colonne de type, les champs de cadre englobant sont en lecture seule après que vous avez spécifié le schéma de pavage de **grille géographique** , car le pavage de grille géographique n’utilise pas de cadre englobant.  
  
     Si vous le souhaitez, vous pouvez spécifier des valeurs autres que les valeurs par défaut pour le champ **Cellules par objet** et pour la densité de grille à tout niveau du schéma de pavage. La quantité par défaut de cellules par objet est 16 pour [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ou 8 pour [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ou les versions supérieures, et la densité de grille par défaut est **Moyenne** pour [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
     Vous pouvez sélectionner GEOMETRY_AUTO_GRID ou GEOGRAPHY_AUTO_GRID pour le schéma de pavage dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque GEOMETRY_AUTO_GRID ou GEOGRAPHY_AUTO_GRID est sélectionné, les options de densité de la grille Niveau 1, Niveau 2, Niveau 3 et Niveau 4 sont désactivées.  
  
     Pour plus d'informations sur ces propriétés, consultez [Index Properties F1 Help](../indexes/index-properties-f1-help.md).  
  
12. Cliquez sur **OK**.  
  
> [!NOTE]  
>  Pour créer un autre index spatial sur la même colonne spatiale ou sur une colonne spatiale différente, répétez les étapes précédentes.  
  
  
 **Pour créer un index spatial à l'aide du Concepteur de tables dans Management Studio**  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a>Pour créer un index spatial dans le Concepteur de tables  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table pour laquelle vous souhaitez créer un index spatial, puis cliquez sur **Conception**.  
  
     La table s'ouvre dans le Concepteur de tables.  
  
2.  Sélectionnez une colonne `geometry` ou `geography` pour l'index.  
  
3.  Dans le menu **Concepteur de tables** , cliquez sur **Index spatial**.  
  
4.  Dans la boîte de dialogue **Index spatiaux** , cliquez sur **Ajouter**.  
  
5.  Sélectionnez le nouvel index dans la liste **Index spatial sélectionné** et, dans la grille située à droite, définissez les propriétés de l'index spatial. Pour plus d’informations sur les propriétés, consultez [Boîte de dialogue Index spatiaux &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> Pour modifier un index spatial  
  
-   [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  Pour modifier des options spécifiques à un index spatial, telles que BOUNDING_BOX ou GRID, vous pouvez utiliser une instruction CREATE SPATIAL INDEX qui spécifie DROP_EXISTING = ON ou supprimer l'index spatial et en créer un nouveau. Pour obtenir un exemple, consultez [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).  
  
-   [Modifier un index](../indexes/modify-an-index.md)  
  
-   [Déplacer un index existant dans un autre groupe de fichiers](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> Pour supprimer un index spatial  
 **Pour supprimer un index spatial à l'aide de Transact-SQL**  
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
 **Pour supprimer un index à l'aide de Management Studio**  
 [Suppression d'index](../indexes/delete-an-index.md)  
  
 **Pour supprimer un index spatial à l'aide du Concepteur de tables dans Management Studio**  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a>Pour supprimer un index spatial dans le Concepteur de tables  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table contenant l’index spatial que vous souhaitez supprimer et cliquez sur **Conception**.  
  
     La table s'ouvre dans le Concepteur de tables.  
  
2.  Dans le menu **Concepteur de tables** , cliquez sur **Index spatial**.  
  
     La boîte de dialogue **Index spatial** s'ouvre.  
  
3.  Cliquez sur l'index que vous souhaitez supprimer dans la colonne **Index spatial sélectionné** .  
  
4.  Cliquez sur **Supprimer**.  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> Restrictions sur les index spatiaux  
 Un index spatial peut être créé uniquement sur une colonne de type `geometry` ou `geography`.  
  
### <a name="table-and-view-restrictions"></a>Restrictions sur les tables et les vues  
 Les index spatiaux peuvent être définis uniquement sur une table dotée d'une clé primaire. Le nombre maximal de colonnes clés primaires sur la table est de 15.  
  
 La taille maximale des enregistrements de clés d'index est de 895 octets. Les tailles supérieures génèrent une erreur.  
  
> [!NOTE]  
>  Les métadonnées de clé primaire ne peuvent pas être modifiées pendant qu'un index spatial est défini sur une table.  
  
 Des index spatiaux ne peuvent pas être spécifiés sur des vues indexées.  
  
### <a name="multiple-spatial-index-restrictions"></a>Restrictions sur plusieurs index spatiaux  
 Vous pouvez créer jusqu'à 249 index spatiaux sur les colonnes spatiales dans une table prise en charge. La création de plusieurs index spatiaux sur la même colonne spatiale peut être utile, par exemple pour indexer des paramètres de pavage différents dans une même colonne.  
  
 Vous pouvez créer un seul index spatial à la fois.  
  
### <a name="spatial-indexes-and-process-parallelism"></a>Index spatiaux et parallélisme de processus  
 Une construction d'index peut utiliser le parallélisme de processus disponible.  
  
### <a name="version-restrictions"></a>Restrictions de version  
 Les pavages spatiaux introduits dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ne peuvent pas être répliqués dans [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Vous devez utiliser les pavages spatiaux [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] pour les index spatiaux lorsqu'une compatibilité descendante avec les bases de données [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] est une condition obligatoire.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des index spatiaux](spatial-indexes-overview.md)  
  
  
