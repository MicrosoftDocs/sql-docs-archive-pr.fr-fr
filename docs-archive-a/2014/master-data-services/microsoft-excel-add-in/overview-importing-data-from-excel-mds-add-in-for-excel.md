---
title: Publication de données (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab37a353469d1902394a3e2cd8060d9be82abb40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704284"
---
# <a name="publishing-data-mds-add-in-for-excel"></a>Publication des données (Complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publiez les données dans le référentiel MDS lorsque vous souhaitez les partager avec d’autres utilisateurs. Dès que les données sont publiées, elles peuvent être téléchargées par les autres utilisateurs du complément.  
  
 Quand vous publiez des données, toutes celles que vous avez ajoutées ou mises à jour sont publiées dans le référentiel MDS. Les données que vous avez supprimées ne sont pas publiées, vous devez les supprimer séparément. Pour plus d’informations, consultez [Supprimer une ligne &#40;Complément MDS pour Excel&#41;](delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  La publication ne peut pas être utilisée pour créer une entité. Pour plus d’informations sur la création d’entités, consultez [Créer une entité &#40;Complément MDS pour Excel&#41;](create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Lorsque plusieurs utilisateurs publient en même temps  
 Plusieurs utilisateurs peuvent publier des mises à jour sur les mêmes données. Lorsqu'un utilisateur publie, la mise à jour est enregistrée dans la base de données. Cela signifie qu'un utilisateur qui ne travaille pas sur des données récemment mises à jour peut toujours modifier leurs valeurs lorsqu'il les publie.  
  
 Seules les modifications que vous apportez sont publiées dans la base de données. Aucune donnée obsolète dans la feuille de calcul n'est publiée.  
  
## <a name="transactions-and-annotations"></a>Transactions et annotations  
 Chaque modification publiée est enregistrée comme une transaction. Si vous le souhaitez, vous pouvez ajouter des annotations (commentaires) à une transaction, pour expliquer pourquoi vous avez effectué la modification.  
  
-   Vous ne pouvez pas annoter les suppressions, bien que celles-ci soient enregistrées en tant que transactions qui peuvent être inversées par un administrateur.  
  
-   Si vous modifiez la valeur de **code** d’un membre, celle-ci n’est pas enregistrée en tant que transaction et toutes les transactions précédentes pour le membre ne sont pas disponibles.  
  
-   Vous pouvez afficher les transactions effectuées sur un membre par d'autres utilisateurs. Vous pouvez également afficher toutes les transactions que vous avez effectuées sur un membre, même si vous n’avez plus l’autorisation d’accès aux attributs spécifiques.  
  
 Vous pouvez afficher toutes les transactions effectuées sur un membre. Pour plus d’informations, consultez [Afficher toutes les annotations ou transactions pour un membre &#40;Complément MDS pour Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Si vous entrez une annotation de plus de 500 caractères, elle sera automatiquement tronquée.  
  
## <a name="business-rule-and-other-validation"></a>Règle d'entreprise et autres validations  
 Quand vous publiez des données, une validation est exécutée pour garantir que les données sont exactes avant d’être ajoutées au référentiel MDS. Si les données ne répondent pas aux critères spécifiés, elles ne seront pas publiées dans le référentiel. Pour plus d’informations, consultez [Validation des données &#40;Complément MDS pour Excel&#41;](validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Publiez des données à partir de la feuille de calcul active vers le référentiel MDS.|[Publier des données d’Excel dans MDS &#40;Complément MDS pour Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Supprimez une ligne du référentiel MDS et de la feuille de calcul en même temps.|[Supprimer une ligne &#40;Complément MDS pour Excel&#41;](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Actualisation des données &#40;Complément MDS pour Excel&#41;](refreshing-data-mds-add-in-for-excel.md)  
  
-   [Complément Master Data Services pour Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
