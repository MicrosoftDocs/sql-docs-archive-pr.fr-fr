---
title: Effectuer une recherche de façon interactive dans des documents
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- interactive searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], interactive
- Query Editor [SQL Server Management Studio], interactive search
ms.assetid: dae65ac5-67af-45c6-a6e0-952fea26d680
author: rothja
ms.author: jroth
ms.openlocfilehash: 5603db77ea4f58d4bb036635a23ec3cfa400a818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613964"
---
# <a name="search-documents-interactively"></a>Effectuer une recherche de façon interactive dans des documents
  La boîte de dialogue **Rechercher et remplacer** vous permet d’effectuer une recherche dans un ou plusieurs fichiers ouverts, ou encore dans une ou plusieurs fenêtres ouvertes, puis de faire défiler les occurrences trouvées l’une après l’autre. Cette technique vous permet de voir chaque occurrence trouvée dans le contexte du texte qui la contient. Vous avez également la possibilité d’effectuer des opérations de recherche en bloc et de voir les occurrences trouvées dans un format de rapport à l’aide de la boîte de dialogue **Rechercher et remplacer** .  
  
### <a name="to-search-all-open-documents"></a>Pour effectuer une recherche dans tous les documents ouverts  
  
1.  Ouvrez les éléments dans lesquels vous voulez effectuer la recherche.  
  
2.  Dans le menu **Modifier** , pointez sur **Rechercher et remplacer** , puis cliquez sur **Recherche rapide**.  
  
3.  Dans la zone de texte **Rechercher et remplacer** , entrez le texte à rechercher.  
  
4.  Dans la liste **Regarder dans** , sélectionnez **Tous les documents ouverts**.  
  
    > [!NOTE]  
    >  Quand vous sélectionnez **Tous les documents ouverts** , il est possible que certains fichiers ouverts soient ignorés pendant la recherche. Seuls les fichiers ouverts dans une vue texte, telle que la vue Code, sont inclus dans les recherches. Les fichiers dans une vue Concepteur de ne sont pas inclus.  
  
5.  Sélectionnez d'autres options pour affiner la recherche.  
  
6.  Cliquez sur **Suivant** pour lancer la recherche et continuez de cliquer sur **Suivant** jusqu’à ce que le dernier fichier ait été analysé.  
  
 Lorsque la recherche atteint le début ou la fin du document, un message s'affiche dans la barre d'état. Lorsqu'elle revient à son point de départ, une boîte de message apparaît.  
  
#### <a name="to-replace-in-all-active-files-interactively"></a>Pour effectuer un remplacement interactif dans tous les fichiers actifs  
  
1.  Dans le menu **Edition** , pointez sur **Rechercher et remplacer**, puis cliquez sur **Remplacement rapide**.  
  
2.  Dans la zone de texte **Rechercher** , entrez le texte à rechercher.  
  
3.  Dans la zone de texte **Remplacer par** , entrez le texte qui doit remplacer le texte recherché.  
  
4.  Dans la liste **Regarder dans** , sélectionnez **Tous les documents ouverts**.  
  
5.  Cliquez sur **Remplacer**et continuez de cliquer sur **Remplacer** jusqu’à ce que la dernière occurrence trouvée dans le dernier fichier ait été remplacée. Cliquez sur **Suivant** pour ignorer une occurrence que vous ne souhaitez pas remplacer.  
  
     -ou-  
  
     Cliquez sur **Remplacer tout** pour remplacer toutes les occurrences. Un message affiche alors le nombre total de remplacements effectués.  
  
 La commande **Remplacer tout** remplace toutes les occurrences trouvées, y compris celles que vous avez ignorées en cliquant sur le bouton **Suivant** . Pour annuler l’action du bouton **Remplacer tout**, cliquez sur **Annuler** dans le menu **Edition** avant de fermer un fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectuer une recherche incrémentielle dans un document actif](search-an-active-document-incrementally.md)   
 [Recherche et remplacement](search-and-replace.md)   
 [Effectuer une recherche dans des documents à l'aide des listes de résultats](search-documents-using-results-lists.md)   
 [Rechercher du texte avec des caractères génériques](search-text-with-wildcards.md)   
 [Rechercher du texte avec des expressions régulières](search-text-with-regular-expressions.md)  
  
  
