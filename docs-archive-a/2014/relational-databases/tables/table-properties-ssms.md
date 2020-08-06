---
title: Propriétés de la table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610522"
---
# <a name="table-properties"></a>Propriétés de la table
  Cette rubrique décrit les propriétés de table qui sont affichées dans la boîte de dialogue Propriétés d'une table dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations sur la façon d’afficher ces propriétés, consultez [Afficher la définition de table](view-the-table-definition.md).  
  
 **Dans cette rubrique**  
  
1.  [Page Général](#GeneralPage)  
  
2.  [Page de suivi des modifications](#ChangeTracking)  
  
3.  [Page de la table de fichier](#FileTable)  
  
4.  [Page de stockage](#Storage)  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> Page Général  
 **Sauvegarde de la base de données**  
 Nom de la base de données qui contient cette table.  
  
 **Serveur**  
 Nom de l'instance actuelle du serveur.  
  
 **Utilisateur**  
 Nom de l'utilisateur de cette connexion.  
  
 **Date de création**  
 Date et heure de création de la table.  
  
 **Nom**  
 Nom de la table.  
  
 **Schéma**  
 Schéma auquel appartient la table.  
  
 **Objet système**  
 Indique que cette table est une table système, utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour contenir des informations internes. Les tables système ne peuvent pas être référencées ou modifiées directement par les utilisateurs.  
  
 **Valeurs ANSI NULL**  
 Indique si l'objet a été créé avec l'option ANSI NULL activée (ON). Pour plus d’informations, consultez [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).  
  
 **Identificateur entre guillemets**  
 Indique si l'objet a été créé avec l'option d'identificateur entre guillemets activée (ON). Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **Escalade de verrous**  
 Indique la granularité de l'escalade de verrous de la table. Pour plus d'informations sur le verrouillage dans le moteur de base de données, consultez [Guide du verrouillage des transactions et du contrôle de version de ligne SQL Server](https://msdn.microsoft.com/library/jj856598.aspx). Les valeurs possibles sont les suivantes :  
  
 AUTO  
 Cette option permet au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] de sélectionner la granularité de l'escalade de verrous appropriée pour le schéma de la table.  
  
-   Si la table est partitionnée, l'escalade de verrous sera autorisée jusqu'à la granularité de segment de mémoire ou d'arbre B (B-tree) (HoBT, Heap or B-tree). Une fois que le verrou a atteint le niveau HoBT, il n'est plus escaladé jusqu'à la granularité TABLE.  
  
-   Si la table n'est pas partitionnée, l'escalade de verrous continue jusqu'à la granularité TABLE.  
  
 TABLE  
 L'escalade de verrous continue jusqu'à la granularité TABLE que la table soit ou non partitionnée. TABLE est la valeur par défaut.  
  
 DISABLE  
 Empêche l'escalade de verrous dans la plupart des cas. Les verrous de niveau table ne sont pas totalement interdits. Par exemple, lorsque vous analysez une table ne contenant aucun index cluster sous le niveau d'isolement sérialisable, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit prendre un verrou de table pour protéger l'intégrité des données.  
  
 **Table répliquée**  
 Indique lorsqu'une table est répliquée vers une autre base de données à l'aide de la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les valeurs possibles sont `True` ou `False`.  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a>Page Change Tracking  
 **Suivi des modifications**  
 Indique si le suivi des modifications est activé pour la table. La valeur par défaut est `False`.  
  
 Cette option est disponible uniquement lorsque le suivi des modifications est activé pour la base de données.  
  
 Pour activer le suivi des modifications, la table doit disposer d'une clé primaire et vous devez posséder une autorisation de modifier la table. Vous pouvez configurer le suivi des modifications en utilisant [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).  
  
 **Suivre les colonnes mises à jour**  
 Indique si le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] effectue un suivi des colonnes mises à jour.  
  
 Pour plus d’informations sur le suivi des modifications, consultez [À propos du suivi des modifications &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
##  <a name="filetable-page"></a><a name="FileTable"></a>Page filetable  
 Affiche les propriétés de la table associée aux FileTables. Pour plus d’informations, consultez [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).  
  
 **Classement de la colonne de noms de FileTable**  
 Classement appliqué à la colonne **Nom** dans un FileTable. La colonne de **nom** contient des noms de fichier et de répertoire.  
  
 **Nom du répertoire FileTable**  
 Dossier racine pour le FileTable.  
  
 **Espace de noms FileTable activé**  
 Lorsque `True` est défini, cette valeur indique que la table est un FileTable. Si vous remplacez cette valeur par `False`, vous modifiez le FileTable pour en faire une table utilisateur ordinaire. Si vous souhaitez ultérieurement remodifier la table pour en faire un FileTable, la table devra réussir la vérification de cohérence de FileTable pour la conversion puisse aboutir.  
  
##  <a name="storage-page"></a><a name="Storage"></a>Page de stockage  
 Affiche les propriétés de stockage de la table sélectionnée.  
  
### <a name="compression"></a>Compression  
 **Type de compression**  
 Type de compression de la table. Cette propriété est disponible uniquement pour les tables qui ne sont pas partitionnées. Pour plus d’informations, consultez [Compression de données](../data-compression/data-compression.md).  
  
 **Partitions utilisant la compression de page**  
 Numéros des partitions qui utilisent la compression de page. Cette propriété est disponible uniquement pour les tables partitionnées.  
  
 **Partitions non compressées**  
 Numéros des partitions qui ne sont pas compressées. Cette propriété est disponible uniquement pour les tables partitionnées.  
  
 **Partitions utilisant la compression de ligne**  
 Numéros des partitions qui utilisent la compression de ligne. Cette propriété est disponible uniquement pour les tables partitionnées.  
  
### <a name="filegroup"></a>Groupe de fichiers  
 **Groupe de fichiers de texte**  
 Nom du groupe de fichiers qui contient les données texte de la table.  
  
 **Groupe de fichiers**  
 Nom du groupe de fichiers contenant la table.  
  
 **Table partitionnée**  
 Les valeurs possibles sont `True` et `False`.  
  
 **Groupe de fichiers Filestream**  
 Indiquez le nom du groupe de fichiers de données FILESTREAM si la table contient une colonne `varbinary(max)` avec l'attribut FILESTREAM. La valeur par défaut est le groupe de fichiers de données FILESTREAM par défaut.  
  
 Si la table ne contient pas de données FILESTREAM, ce champ est vierge.  
  
### <a name="general"></a>Général  
 **Le format de stockage VarDecimal est activé**  
 Lorsque `True` la valeur est, cette valeur en lecture seule indique que les `decimal` `numeric` types de données et sont stockés à l’aide du format de stockage vardecimal. Pour modifier cette option, utilisez l' `vardecimal storage format` option de [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql). Le format de stockage vardecimal est déconseillé. Utilisez plutôt la compression ROW.  
  
 **Espace d'index**  
 Quantité d'espace occupée par les index dans la table, en mégaoctets. Cette valeur n'inclut pas l'utilisation de l'espace des index XML pour la table. Si les index XML appartiennent à la table, utilisez plutôt [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) .  
  
 **Nombre de lignes**  
 Nombre de lignes du tableau.  
  
 **Espace de données**  
 Quantité d'espace occupée par les données dans la table, en mégaoctets.  
  
### <a name="partitioning"></a>Partitionnement  
 Cette section est disponible uniquement si la table est partitionnée. Pour plus d’informations, consultez [Tables et index partitionnés](../partitions/partitioned-tables-and-indexes.md).  
  
 **Colonne de partition**  
 Nom de la colonne sur laquelle la table est partitionnée.  
  
 **Schéma de partition**  
 Nom du schéma de partition si la table est partitionnée. Si la table n'est pas partitionnée, le champ est vide.  
  
 **Nombre de partitions**  
 Nombre de partitions de la table.  
  
 **Schéma de partition FILESTREAM**  
 Nom du schéma de partition FILESTREAM, si la table est partitionnée. Si la table n'est pas partitionnée, le champ est vide.  
  
 Le schéma de partition FILESTREAM doit être symétrique avec le schéma spécifié dans l'option **Schéma de partition** .  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la définition de la table](view-the-table-definition.md)   
 [Modifier des colonnes &#40;moteur de base de données&#41;](../tables/modify-columns-database-engine.md)  
  
  
