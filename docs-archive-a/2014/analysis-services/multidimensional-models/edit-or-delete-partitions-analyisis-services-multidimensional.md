---
title: Modifier ou supprimer des partitions (services Analysis-multidimensionnels) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying partitions
- partitions [Analysis Services], modifying
ms.assetid: fb7a64ca-d021-4926-b92d-83476fbc40a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e611ac51ce4a6495225d8e8e7ce05b0c0a83b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613647"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a>Modifier ou supprimer des partitions (Analysis Services - Multidimensionnel)
  Les partitions de cube sont modifiées à l’aide de l’onglet **Partitions** du Concepteur de cube dans [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]. L’onglet **Partitions** répertorie les partitions pour tous les groupes de mesures d’un cube. Il répertorie également les partitions d'écriture différée pour lesquelles l'écriture différée est activée.

 Pour modifier les partitions d’un groupe de mesures, développez le groupe de mesures sous l’onglet **partitions** . les partitions d’un groupe de mesures sont répertoriées par nombre ordinal dans un format de table avec les colonnes répertoriées dans le tableau suivant.

 Les paramètres d'un groupe de mesures lié doivent être modifiés dans le cube source.

 La suppression de partitions se produit automatiquement lorsque vous fusionnez une partition source dans une partition de destination. La partition spécifiée comme source est supprimée une fois la fusion terminée. Vous pouvez également supprimer des partitions manuellement dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou dans l'onglet Partitions de [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]. Cliquez avec le bouton droit, puis sélectionnez **Supprimer**. N'oubliez pas que la suppression d'une partition supprime également les données et les agrégations. Par mesure de précaution, assurez-vous que vous disposez d'une sauvegarde récente de la base de données au cas où vous devriez annuler cette étape ultérieurement.

> [!NOTE]
>  Vous pouvez également utiliser des scripts XMLA qui automatisent les tâches de création, de fusion et de suppression de partitions. Un script XMLA peut être créé et exécuté dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]ou dans des packages SSIS personnalisés qui s’exécutent en tant que tâche planifiée. Pour plus d’informations, consultez [Automatiser les tâches d’administration Analysis Services avec SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).

## <a name="partition-source"></a>Source de partition
 Spécifie la table source ou la requête nommée pour la partition. Pour modifier la table source, cliquez sur la cellule, puis sur le bouton Parcourir (**...**).

 ![Colonne source dans le volet Partition](../media/ssas-partitionsource.png "Colonne source dans le volet Partition")

 Si la partition est basée sur une requête, cliquez sur le bouton Parcourir (**…**) pour modifier la requête. Ceci modifie la propriété **Source** de la partition. Pour plus d’informations, consultez [Modifier une source de partition afin d’utiliser une table de faits différente](change-a-partition-source-to-use-a-different-fact-table.md).

 Vous pouvez spécifier une table dans la vue de source de données qui a la même structure que la table source d'origine (dans la source de données externe à partir de laquelle les données sont récupérées). La source peut se trouver dans une source de données ou une vue de source de données quelconque de la base de données de cube.

## <a name="storage-settings"></a>Paramètres de stockage
 Dans le Concepteur de cube, sous l'onglet Partitions, vous pouvez cliquer sur **Paramètres de stockage** pour sélectionner l'un des paramètres standard pour le stockage MOLAP, ROLAP ou HOLAP, ou configurer des paramètres personnalisés pour le mode de stockage et la mise en cache proactive. La valeur par défaut est MOLAP car elle offre les performances de requête les plus rapides. Pour plus d’informations sur chaque paramètre, consultez [Définir un stockage de partitions &#40;Analysis Services – Multidimensionnel&#41;](set-partition-storage-analysis-services-multidimensional.md).

 Le stockage peut être configuré séparément pour chacune des partitions de chaque groupe de mesures d'un cube. Vous pouvez également configurer les paramètres de stockage par défaut pour un cube ou un groupe de mesures. Le stockage est configuré sous l'onglet **Partitions** de l'Assistant Cube.

## <a name="see-also"></a>Voir aussi
 [Créer et gérer une partition locale &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [concevoir des agrégations &#40;Analysis Services-partitions de fusion&#41;multidimensionnelles](designing-aggregations-analysis-services-multidimensional.md) [dans Analysis Services &#40;SSAS-multidimensionnel&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md)


