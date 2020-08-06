---
title: Page Sélectionner les bases de données (Assistant Nouveau groupe de disponibilité-Assistant Ajout d’une base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c626b8f0953f18a6dd4661124a09b7f542caeb82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707892"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a>Page Sélectionner les bases de données (Assistant Nouveau groupe de disponibilité-Assistant Ajout d’une base de données)
   Cette rubrique d’aide décrit les options de la page **Spécifier les bases de données**. Cette rubrique s'applique à l' [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] et à l' [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a>Options de sélection de bases de données  
 La grille **Bases de données utilisateur sur cette instance de SQL Server** répertorie chaque base de données utilisateur locale. Les colonnes sont les suivantes :  
  
 **Nom**  
 Affiche le nom d'une base de données utilisateur locale.  
  
 **Taille**  
 Affiche la taille de la base de données, si cette information est connue de l'Assistant.  
  
 **État**  
 Affiche un lien hypertexte dont le texte indique si une base de données particulière réunit les conditions préalables requises en vue de l'ajout à un groupe de disponibilité. Si l'état est «**Répond aux conditions requises**», vous pouvez ajouter la base de données au groupe de disponibilité. Si une base de données ne réunit pas l'ensemble des conditions préalables requises, le lien hypertexte **État** fournit une brève explication de la raison pour laquelle la base de données n'est pas éligible. Pour plus d'informations, cliquez sur le lien hypertexte.  
  
 Vous pouvez laisser l'Assistant sur la page **Sélectionner une base de données** lorsque vous agissez sur une base de données afin qu'elle remplisse une condition préalable. Lorsque vous revenez à la page **Sélectionner les bases de données** , cliquez sur **Actualiser** pour mettre à jour la grille.  
  
 **Actualiser**  
 Cliquez pour actualiser la grille. Cette action est utile lorsque vous agissez sur une base de données afin qu'elle remplisse une condition préalable.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
