---
title: SQL Server Profiler-organiser les colonnes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b63c2f7d882bac05fc6baf10614170ec23125c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705388"
---
# <a name="sql-server-profiler---organize-columns"></a>Générateur de profils SQL Server - Organiser les colonnes
  Utilisez la boîte de dialogue **Organiser les colonnes** pour sélectionner des colonnes de données en vue de regrouper ou d'agréger des événements affichés dans une trace et faciliter ainsi la consultation et l'analyse des tables ou des fichiers de trace volumineux.  
  
 L'agrégation déplace et réduit tous les événements de la trace sous leur type de classe d'événements respectif. Un signe plus ( **+** ) apparaît à gauche du nom de la classe d’événements. Si vous cliquez sur le signe plus, la classe d'événements se développe et affiche tous les événements de ce type.  
  
 Le regroupement regroupe toutes les classes d'événements d'un type spécifique dans l'affichage de la fenêtre de trace. Les événements ne sont toutefois pas réduits sous le type de classe d'événements.  
  
 Lorsque vous regroupez ou agrégez des événements dans l'affichage d'une fenêtre de trace, les colonnes sélectionnées pour le regroupement ou l'agrégation restent fixes dans la fenêtre d'affichage, mais vous pouvez faire défiler l'affichage vers la droite ou la gauche pour visualiser toutes les autres colonnes de données.  
  
 Pour accéder à cette boîte de dialogue, ouvrez une table ou un fichier de trace existant, puis cliquez sur **Propriétés** dans le menu [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** de. Dans la boîte de dialogue **Propriétés de la trace** , cliquez sur l'onglet **Sélection des événements** , puis sur **Organiser les colonnes**. Vous pouvez également cliquer sur **Organiser les colonnes** sous l'onglet **Sélection des événements** lorsque vous créez une nouvelle trace.  
  
## <a name="options"></a>Options  
 **Groupes**  
 Déplacez des noms de colonne de données sous **Groupes** pour regrouper ou agréger des classes d’événements dans la fenêtre de trace.  
  
 Pour agréger des événements, déplacez une colonne de données vers **Groupes**. Tous les événements d'un type spécifique sont alors réduits sous le nom du type de la classe d'événements dans l'affichage de la fenêtre de trace. Un signe plus ( **+** ) apparaît à gauche du nom de la classe d’événements. Cliquez sur ce signe plus pour développer le type de la classe d'événements et afficher tous les événements. Vous pouvez activer et désactiver l'agrégation et le regroupement en cliquant sur **Vue agrégée** ou sur **Vue groupée** dans le menu **Affichage** .  
  
 Pour regrouper des événements, déplacez plusieurs colonnes de données vers **Groupes**. Tous les événements d'un type spécifique sont alors regroupés dans l'affichage de la fenêtre de trace, mais les événements ne sont pas réduits sous chaque nom de type de classe d'événements. Vous pouvez basculer entre une vue groupée et une vue non groupée en cliquant sur **Vue groupée** dans le menu Affichage. Lorsque plusieurs colonnes de données sont déplacées vers **Groupes**, l'option de basculement vers **Vue agrégée** n'est pas disponible.  
  
 **Colonnes**  
 Répertorie les colonnes de données qui peuvent être déplacées vers **Groupes**. Cliquez sur le signe plus ( **+** ) à gauche de **colonnes** pour développer la liste.  
  
 **Haut**  
 Lorsque vous avez sélectionné une colonne de données, cliquez sur **Haut** pour déplacer des colonnes de données vers le haut dans **Groupes**. Vous pouvez également cliquer sur **Haut** pour réorganiser l'affichage des colonnes dans l'affichage de la fenêtre de trace.  
  
 **Descendre**  
 Lorsque vous avez sélectionné une colonne de données, cliquez sur **Bas** pour déplacer des colonnes de données vers le bas dans **Groupes**. Vous pouvez également cliquer sur **Bas** pour réorganiser l'affichage des colonnes dans l'affichage de la fenêtre de trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Organiser les colonnes affichées dans une trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Créer un &#40;de trace SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Créer un modèle de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)   
 [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
