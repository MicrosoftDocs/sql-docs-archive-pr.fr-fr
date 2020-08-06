---
title: Propriétés de la base de données (page Fichiers) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.files.f1
ms.assetid: 3c030e51-db82-4b43-b1e5-8547ddd3de87
author: stevestein
ms.author: sstein
ms.openlocfilehash: 955a17857ce0d847fb712473dddd581a072ab83d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695700"
---
# <a name="database-properties-files-page"></a>Propriétés de la base de données (page Fichiers)
  Cette page vous permet de créer une nouvelle base de données, ainsi que d'afficher et de modifier les propriétés de la base de données sélectionnée. Cette rubrique s’applique aux **Propriétés de la base de données (page Fichiers)** pour les bases de données existantes et à la **Nouvelle base de données (page Général)** .  
  
## <a name="ui-element-list"></a>Liste d’éléments UI  
 **Nom de la base de données**  
 Ajoutez ou affichez le nom de la base de données.  
  
 **Propriétaire**  
 Spécifiez le propriétaire de la base de données en le sélectionnant dans la liste.  
  
 **Utiliser l'indexation de texte intégral**  
 Cette case à cocher est activée et grisée, car l'indexation de texte intégral est toujours activée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [Recherche en texte intégral](../search/full-text-search.md).  
  
 **Fichiers de base de données**  
 Ajoutez, affichez, modifiez ou supprimez les fichiers de base de données de la base de données associée. Les fichiers de base de données ont les propriétés suivantes :  
  
 **Nom logique**  
 Entrez ou modifiez le nom du fichier.  
  
 **Type de fichier**  
 Sélectionnez le type de fichier dans la liste. Le type de fichier peut être **Données**, **Journal**ou **Données Filestream**. Vous ne pouvez pas modifier le type de fichier d'un fichier existant.  
  
 Sélectionnez **Données Filestream** si vous ajoutez des fichiers (conteneurs) à un groupe de fichiers optimisé en mémoire.  
  
 Pour ajouter des fichiers (conteneurs) à un groupe de fichiers de données Filestream, FILESTREAM doit être activé. Vous pouvez activer FILESTREAM à l’aide de la boîte de dialogue [Propriétés du serveur (page Avancé)](../../database-engine/configure-windows/server-properties-advanced-page.md) .  
  
 **Groupe de fichiers**  
 Sélectionnez le groupe de fichiers du fichier dans la liste. Par défaut, le groupe de fichiers est PRIMARY. Vous pouvez créer un nouveau groupe de fichiers en sélectionnant **\<new filegroup>** , puis en entrant les informations sur le groupe de fichiers dans la boîte de dialogue **Nouveau groupe de fichiers**. Il est également possible de créer un groupe de fichiers dans la page **Groupe de fichiers** . Vous ne pouvez pas modifier le groupe de fichiers d'un fichier existant.  
  
 Lors de l’ajout de fichiers (conteneurs) à un groupe de fichiers optimisé en mémoire, le champ **Groupe de fichiers** est rempli avec le nom du groupe de fichiers optimisé en mémoire de la base de données.  
  
 **Taille initiale**  
 Entrez ou modifiez la taille initiale du fichier en mégaoctets. Par défaut, il s’agit de la valeur de la base de données **model** .  
  
 Ce champ n'est pas valide pour les fichiers FILESTREAM.  
  
 Pour les fichiers des groupes de fichiers optimisés en mémoire, ce champ ne peut pas être modifié.  
  
 **Croissance automatique**  
 Sélectionnez ou affichez les propriétés de croissance automatique du fichier. Ces propriétés contrôlent la manière dont le fichier croît une fois qu'il a atteint sa taille maximale. Pour modifier les valeurs de croissance automatique, cliquez sur le bouton Modifier en regard des propriétés de croissance automatique du fichier de votre choix, puis modifiez les valeurs dans la boîte de dialogue **Modifier la croissance automatique** . Par défaut, il s’agit des valeurs de la base de données **model** .  
  
 Ce champ n'est pas valide pour les fichiers FILESTREAM.  
  
 Pour les fichiers des groupes de fichiers optimisés en mémoire, ce champ doit avoir la valeur **Illimité**.  
  
 **Chemin d’accès**  
 Affiche le chemin d'accès du fichier sélectionné. Pour spécifier le chemin d'accès d'un nouveau fichier, cliquez sur le bouton Modifier en regard du chemin d'accès du fichier et parcourez l'arborescence jusqu'au dossier de destination. Vous ne pouvez pas modifier le chemin d'accès d'un fichier existant.  
  
 Pour les fichiers FILESTREAM, le chemin d'accès est un dossier. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] crée les fichiers sous-jacents dans ce dossier.  
  
 **Nom de fichier**  
 Affiche le nom du fichier.  
  
 Ce champ n'est pas valide pour les fichiers FILESTREAM, ce qui inclut les fichiers dans les groupes de fichiers optimisés en mémoire.  
  
 **Ajouter**  
 Ajoutez un nouveau fichier à la base de données.  
  
 **Remove**  
 Supprimez le fichier sélectionné de la base de données. Un fichier ne peut pas être supprimé s'il n'est pas vide. Le fichier de données primaire et le fichier journal ne peuvent pas être supprimés.  
  
 Pour plus d’informations sur les fichiers, consultez [Groupes de fichiers et fichiers de base de données](database-files-and-filegroups.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
