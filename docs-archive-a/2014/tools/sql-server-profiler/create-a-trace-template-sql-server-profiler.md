---
title: Créer un modèle de trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 355f97c7fecd8a9e31f10de881d1ae6df3b8f122
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694939"
---
# <a name="create-a-trace-template-sql-server-profiler"></a>Créer un modèle de trace (SQL Server Profiler)
  Cette rubrique décrit la façon de créer un nouveau modèle de trace au moyen du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-create-a-trace-template"></a>Pour créer un modèle de trace  
  
1.  Dans le menu **Fichier** , pointez sur **Modèles**, puis cliquez sur **Nouveau modèle**.  
  
2.  Dans la boîte de dialogue **Propriétés du modèle de trace** , sélectionnez un type de serveur dans la liste **Sélectionner le type de serveur**.  
  
3.  Dans la zone **Nom du nouveau modèle** , entrez un nom de modèle.  
  
4.  Éventuellement, cliquez sur **Baser le nouveau modèle sur un modèle existant**, puis sélectionnez un modèle dans la liste.  
  
     Tous les événements, les colonnes de données et les filtres sont initialement définis comme spécifiés dans le modèle sélectionné.  
  
5.  Éventuellement, cliquez sur **Utiliser comme modèle par défaut pour le type de serveur sélectionné**.  
  
6.  Sous l’onglet **Sélection des événements** , ajoutez, supprimez ou modifiez des événements, des colonnes de données ou des filtres.  
  
7.  Sous l’onglet **Sélection des événements**, utilisez le contrôle de la grille pour ajouter ou supprimer des événements et des colonnes de données dans le fichier de trace comme suit :  
  
    -   Pour ajouter un événement, développez la catégorie d’événements appropriée dans la colonne **Événements** , puis sélectionnez le nom de l’événement.  
  
    -   Lorsque vous ajoutez un événement, toutes les colonnes de données sont incluses par défaut. Pour supprimer une colonne de données d'un événement dans une trace, désactivez la case à cocher dans la colonne de données de l'événement.  
  
    -   Pour ajouter des filtres, cliquez sur le nom de la colonne de données et définissez les critères de filtrage dans la boîte de dialogue **Modifier le filtre** . Vous pouvez également cliquer avec le bouton droit sur le nom de la colonne de données et cliquer sur **Modifier le filtre des colonnes** pour ouvrir la boîte de dialogue **Modifier le filtre** . Cliquez sur **OK** pour ajouter le filtre.  
  
8.  Cliquez sur **Enregistrer.**  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
