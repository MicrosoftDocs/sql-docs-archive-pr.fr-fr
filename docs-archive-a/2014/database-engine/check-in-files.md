---
title: Archiver des fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 070c1dfa5dd057cf777980f7022752a97a4dc84c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611320"
---
# <a name="check-in-files"></a>Archiver des fichiers
  Pour mettre à la disposition d'autres utilisateurs des fichiers sous contrôle de code source auxquels vous avez apporté des modifications, vous devez archiver ces fichiers dans le contrôle de code source. Lorsque vous archivez un fichier, la version que vous archivez s'inscrit dans le fournisseur de contrôle de code source et devient la dernière version de ce fichier.  
  
 Vous pouvez utiliser la commande **Archiver** pour archiver les fichiers. Lorsque vous utilisez cette commande pour archiver une solution ou un projet, tous les fichiers figurant dans cette solution ou dans ce projet sont également archivés. Lorsque vous archivez un fichier de code source individuel, cela n'entraîne toutefois pas l'archivage du projet ou de la solution dont il fait partie.  
  
### <a name="to-check-in-a-file"></a>Pour archiver un fichier  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le fichier à archiver, puis cliquez sur **Archiver**.  
  
2.  Si la boîte de dialogue **Archivage** apparaît, sélectionnez les options appropriées, puis cliquez sur **OK**.  
  
     **Date d'arrivée**  
     Archive tous les éléments sélectionnés.  
  
     **Colonnes**  
     Identifiez les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
     **Commentaires**  
     Ajoutez un commentaire à associer à l'opération d'archivage.  
  
     **Ne pas afficher la boîte de dialogue Archiver lors de l'archivage d'éléments**  
     Supprime la boîte de dialogue pendant les archivages.  
  
     **Affichage en 2D**  
     Affiche les fichiers que vous archivez sous forme de liste en 2D sous leur connexion de contrôle de code source.  
  
     **Nom**  
     Affiche le nom des éléments à archiver. Les cases à cocher en regard des éléments affichés sont activées. Si vous ne souhaitez pas archiver un élément donné, désactivez la case à cocher correspondante.  
  
     **Options**  
     Affiche des options d'archivage propres au plug-in de contrôle de code source lorsque vous cliquez sur la flèche située à droite du bouton.  
  
     **Sort**  
     Permet d'ordonner les colonnes d'affichage.  
  
     **Arborescence**  
     Affiche la hiérarchie des dossiers et des fichiers pour les éléments que vous archivez.  
  
 Si le fichier que vous avez archivé ne fait pas partie d'une extraction partagée, l'environnement [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] archive alors immédiatement le fichier. Sinon, il peut vous demander de fusionner votre version avec celles créées par d'autres utilisateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la liste des fichiers modifiés](../../2014/database-engine/view-a-list-of-modified-files.md)   
 [Gérer les archivages](../../2014/database-engine/manage-checkins.md)  
  
  
