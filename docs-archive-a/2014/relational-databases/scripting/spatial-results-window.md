---
title: Fenêtre Résultats spatiaux
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e018ec9f016dfc51ed1bb055ba94abf12bc878f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710544"
---
# <a name="spatial-results-window"></a>Fenêtre Résultats spatiaux
  La fenêtre **Résultats spatiaux** propose des outils de mappage visuel permettant d'afficher des données spatiales. Pour afficher des résultats spatiaux, vos résultats de requête doivent inclure une colonne spatiale avec des données géométriques ou géographiques.  
  
> [!NOTE]  
>  La fenêtre **Résultats spatiaux** est uniquement disponible si vos résultats sont retournés dans une grille dans la fenêtre **Résultats** . Si vous spécifiez que les résultats doivent être retournés sous forme de texte, cette fenêtre n'est pas disponible.  
  
## <a name="options"></a>Options  
 **Sélectionner la colonne spatiale**  
 À partir des colonnes spatiales figurant dans les résultats de requête, spécifiez la colonne spatiale à afficher. Vous ne pouvez sélectionner qu'une seule colonne à la fois.  
  
 **Sélectionner la colonne d'étiquette**  
 À partir des colonnes retournées dans les résultats de requête, spécifiez la colonne non spatiale qui servira à étiqueter les données spatiales. Vous ne pouvez sélectionner qu'une seule colonne à la fois.  
  
 Cette option n'est pas disponible lorsque des instances de point seulement sont retournées dans une requête.  
  
 **Sélectionner la projection**  
 Affichez les données géographiques selon l'une des quatre projections proposées : équirectangulaire, de Mercator, de Robinson ou de Bonne.  
  
 Cette option n'est pas disponible pour les données géométriques.  
  
 **Zoom**  
 Ajustez l'affichage du mappage sur une échelle exponentielle.  
  
 **Afficher le quadrillage**  
 Activez/désactivez le quadrillage des coordonnées.  
  
 Pour les formes polygonales, l'étiquette est affichée uniquement lorsque la forme est suffisamment grande pour contenir le texte d'étiquette. Pour afficher les étiquettes des petites formes, ajustez le zoom.  
  
> [!NOTE]  
>  Il est impossible d'étiqueter les instances de point.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher des données spatiales dans l'Explorateur d'objets](view-spatial-data-in-object-explorer.md)   
 [Données spatiales &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [Éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  
