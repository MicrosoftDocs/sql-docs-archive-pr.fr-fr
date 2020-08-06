---
title: Options (éditeur de texte-toutes les langues-page onglets) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 13f791e34b2099e8c0492c25886ee6b37ef1a1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613126"
---
# <a name="options-text-editor---all-languages--tabs-page"></a>Options (Éditeur de texte - Toutes les langues - Page Onglets)
  Cette boîte de dialogue vous permet de définir le comportement de tabulation des cinq éditeurs de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour afficher ces options, sélectionnez **Options** dans le menu **Outils** . Sélectionnez le dossier **Éditeur de texte** , développez le dossier **Tous les langages** , puis cliquez sur **Tabulations**.  
  
## <a name="tabbing-options-by-editor"></a>Options de tabulation par éditeur  
 Vous devez utilisez les boîtes de dialogue **Tous les langages** pour définir les options des éditeurs DMX, MDX et SQL Server Compact. Les options définies ici s'appliquent aussi aux éditeurs de texte brut, Transact-SQL et XML, mais vous pouvez définir les options de ces éditeurs séparément en développant les sous-dossiers de ces langages et en sélectionnant leur page d'options. Certains langages ne prennent pas en charge toutes les options de tabulation.  
  
> [!CAUTION]  
>  Si vous définissez une option à l’aide de cette boîte de dialogue, mais que vous voulez un paramétrage différent pour les éditeurs de texte brut, Transact-SQL ou XML, vous devrez définir les options de ces éditeurs après avoir appliqué les sélections effectuées dans la boîte de dialogue **Tous les langages**.  
  
 Le message « Les paramètres de mise en retrait (ou de tabulation) pour les formats de texte individuels sont en conflit » s'affiche lorsque différents paramètres ont été sélectionnés pour des éditeurs particuliers. Ce rappel s'affiche notamment si l'option **Mise en retrait** est sélectionnée pour **Texte brut**, et **Aucun** pour **XML**.  
  
## <a name="indenting"></a>Mise en retrait  
 **Aucun**  
 Lorsque cette option est activée, la nouvelle ligne créée grâce à la touche ENTRÉE n'est pas mise en retrait. Le curseur est placé au niveau de la première colonne de la nouvelle ligne.  
  
 **Bloquer**  
 Lorsque cette option est activée, la nouvelle ligne créée grâce à la touche ENTRÉE est automatiquement mise en retrait à la même distance que la ligne précédente.  
  
 **Intelligente**  
 Lorsque cette option est activée, la nouvelle ligne créée grâce à la touche ENTRÉE est positionnée en fonction du contexte.  
  
## <a name="tabs"></a>Tabulations  
 **Taille des tabulation**  
 Définit la distance en espaces entre les taquets de tabulation. La valeur par défaut est quatre espaces.  
  
 **Taille du retrait**  
 Définit la taille en espaces d'une mise en retrait automatique. La valeur par défaut est quatre espaces. Des tabulations et/ou des espaces seront insérés pour occuper la taille spécifiée.  
  
 **Insérer des espaces**  
 Lorsque cette option est activée, les opérations de mise en retrait insèrent uniquement des espaces et non des tabulations. Si l'option **Taille du retrait** a la valeur 5, par exemple, cinq espaces sont insérés lorsque vous appuyez sur TAB ou que vous cliquez sur le bouton **Augmenter le retrait** de la barre d'outils de la fenêtre principale de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 **Conserver les tabulations**  
 Lorsque cette option est activée, les opérations de mise en retrait insèrent autant de tabulations que possible. Chaque tabulation remplit le nombre d'espaces spécifié dans **Taille de tabulation**. Si la valeur de **Taille du retrait** n'est pas un multiple pair de la valeur de **Taille de tabulation**, des espaces sont ajoutés pour remplir la différence.  
  
  
