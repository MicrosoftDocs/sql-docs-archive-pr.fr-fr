---
title: Options (résultats de la requête-SQL Server-résultats dans la page de grille) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9cec7e544c295420a9ae2a25e96ea9aa82030b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703239"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a>Options (résultats de la requête-SQL Server-résultats dans la page de grille)
  Cette page vous permet de spécifier les options d'affichage du jeu de résultats d'une requête au format grille. Les modifications apportées à ces options sont appliquées uniquement aux nouvelles requêtes [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour modifier les options des requêtes en cours, cliquez sur **options de requête** dans le menu **requête** ou cliquez avec le bouton droit dans la fenêtre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requête et sélectionnez **options de requête**. Dans le volet gauche de la boîte de dialogue **Options de requête** , cliquez sur **Grille**sous **Résultats**.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
 **Inclure la requête dans l'ensemble de résultats**  
 Retourne le texte de la requête dans la sortie.  
  
 **Inclure des en-têtes de colonne lors de la copie ou de l'enregistrement de résultats**  
 Activez cette case à cocher pour inclure des en-têtes de colonne lorsque les résultats sont copiés dans le Presse-papiers ou enregistrés dans un fichier. Désactivez-la si vous ne voulez pas inclure ces en-têtes et que vous voulez limiter les résultats aux données uniquement.  
  
 **Ignorer les résultats après l'exécution**  
 Empêche les résultats de la requête d'être affichés dans le volet Révision. Les résultats sont ignorés immédiatement après l'exécution. La spécification de cette option aide à économiser de la mémoire.  
  
 **Afficher les résultats dans un onglet séparé**  
 Activez cette case à cocher pour afficher l'ensemble de résultats dans un nouvel onglet, et non au bas de la fenêtre de document de la requête.  
  
 **Basculer vers l'onglet des résultats après l'exécution de la requête**  
 Cliquez sur cette option pour que le volet de résultats devienne actif automatiquement après qu'une requête a été exécutée.  
  
 **Nombre maximal de caractères récupérés**  
 **Données non-XML :**  
  
 Entrez un nombre compris entre 1 et 65 535 pour indiquer le nombre maximal de caractères affichés dans chaque cellule.  
  
> [!NOTE]  
>  Si vous précisez un nombre trop élevé, les données de l'ensemble de résultats risquent d'être tronquées à l'affichage. Le nombre maximal de caractères affichés dans chaque cellule dépend de la taille de police. Si les ensembles de résultats retournés sont volumineux, il est préférable de ne pas spécifier une valeur trop élevée sans quoi vous risquez d'être confronté à une mémoire insuffisante pour l'exécution de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou à une dégradation des performances système.  
  
 **Données XML**:  
  
 Sélectionnez **1 Mo**, **2 Mo**ou **5 Mo**. Sélectionnez **Illimité** pour récupérer tous les caractères.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
