---
title: Définir une taille maximale de table de trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f48efbe02e300e06faf857ed0fb36ae340ad979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694919"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>Définir une taille maximale de table de trace (SQL Server Profiler)
  Cette rubrique explique comment définir une taille maximale de table de trace à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>Pour définir une taille maximale de table de trace  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de SQL Server.  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** , tapez un nom pour la trace.  
  
3.  Dans la liste **Nom du modèle**, sélectionnez un modèle de trace.  
  
4.  Cochez la case **Enregistrer dans la table**.  
  
5.  Connectez-vous au serveur sur lequel vous voulez stocker la trace.  
  
     La boîte de dialogue **Table de destination** s’affiche.  
  
6.  Sélectionnez une base de données pour la trace dans la liste **Base de données** .  
  
7.  Dans la zone **Table** , tapez ou sélectionnez un nom pour la table.  
  
8.  Sélectionnez **Définir le nombre de lignes maximal** , puis spécifiez un nombre de lignes maximal pour la table de trace.  
  
    > [!NOTE]  
    >  Quand le nombre de lignes dans la table dépasse le maximum spécifié, les événements de la trace ne sont plus enregistrés, mais la trace continue.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
