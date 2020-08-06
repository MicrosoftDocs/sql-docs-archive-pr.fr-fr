---
title: Bases de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- data warehouse [SQL Server]
- OLTP databases [SQL Server]
- databases [SQL Server], about databases
ms.assetid: 316eea58-81b8-4bf3-a1fc-801946740e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea3da64ce6da8cbcb32b5854f14e8d24349c0c25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709560"
---
# <a name="databases"></a>Bases de données
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , une base de données est constituée d'une collection de tables qui renferment un ensemble spécifique de données structurées. Une table se compose de lignes, également appelées enregistrements ou tuples, et de colonnes, également appelées attributs. Chaque colonne d'une table est conçue pour stocker un certain type d'informations, par exemple, des données, des noms, des valeurs monétaires ou des nombres.  
  
## <a name="basic-information-about-databases"></a>Informations générales sur les bases de données  
 Une ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être installées sur un ordinateur. Chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut contenir une ou plusieurs bases de données.  Dans une base de données, il existe un ou plusieurs groupes d'appropriation d'objets appelés schémas. Chaque schéma contient divers objets de base de données tels que des tables, des vues et des procédures stockées. Certains objets, tels que les certificats et les clés asymétriques, sont présents dans une base de données, mais pas dans un schéma. Pour plus d’informations sur la création de tables, consultez [Tables](../tables/tables.md).  
  
 Les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockées dans des fichiers du système de fichiers. Les fichiers peuvent être regroupés en groupes de fichiers. Pour plus d’informations sur les fichiers et groupes de fichiers, consultez [Groupes de fichiers et fichiers de base de données](database-files-and-filegroups.md).  
  
 Lorsque les utilisateurs accèdent à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ils sont identifiés comme connexion. Lorsque les utilisateurs accèdent à une base de données, ils sont identifiés comme utilisateur de base de données. Un utilisateur de base de données peut être basé sur une connexion. Si les bases de données autonomes sont activées, il est possible de créer un utilisateur de base de données qui n'est pas basé sur une connexion. Pour plus d’informations sur les utilisateurs, consultez [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
 Un utilisateur qui a accès à une base de données peut recevoir l'autorisation d'accéder aux objets de la base de données. Même si les autorisations peuvent être accordées aux utilisateurs de façon individuelle, nous vous recommandons de créer des rôles de base de données, d'ajouter les utilisateurs de la base de données aux rôles, puis d'accorder l'autorisation d'accès aux rôles. L'octroi d'autorisations à des rôles plutôt qu'aux utilisateurs contribue à garantir que les autorisations restent cohérentes et compréhensibles à mesure que le nombre d'utilisateurs augmente et évolue. Pour plus d’informations sur les autorisations des rôles, consultez [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql) et [Principaux &#40;moteur de base de données&#41;](../security/authentication-access/principals-database-engine.md).  
  
## <a name="working-with-databases"></a>Utilisation des bases de données  
 La plupart des personnes qui utilisent des bases de données emploient l'outil [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . L'outil [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] comporte une interface utilisateur graphique permettant de créer des bases de données et les objets à y inclure. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] fournit également un éditeur de requête permettant de rédiger des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] pour interagir avec les bases de données. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] peut être installé à partir du disque d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou téléchargé à partir de MSDN.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|||  
|-|-|  
|[Bases de données système](system-databases.md)|[Supprimer des fichiers de données ou des fichiers journaux d’une base de données](delete-data-or-log-files-from-a-database.md)|  
|[Bases de données autonomes](contained-databases.md)|[Afficher les informations sur l’espace occupé par les données et par le journal d’une base de données](display-data-and-log-space-information-for-a-database.md)|  
|[Fichiers de données SQL Server dans Azure](sql-server-data-files-in-microsoft-azure.md)|[Augmenter la taille d’une base de données](increase-the-size-of-a-database.md)|  
|[Groupes de fichiers et fichiers de base de données](database-files-and-filegroups.md)|[Renommer une base de données](rename-a-database.md)|  
|[États d’une base de données](database-states.md)|[Définir une base de données en mode mono-utilisateur](set-a-database-to-single-user-mode.md)|  
|[États des fichiers](file-states.md)|[Réduire une base de données](shrink-a-database.md)|  
|[Estimer la taille d'une base de données](estimate-the-size-of-a-database.md)|[Réduire un fichier](shrink-a-file.md)|  
|[Copier des bases de données sur d’autres serveurs](copy-databases-to-other-servers.md)|[Afficher ou modifier les propriétés d’une base de données](view-or-change-the-properties-of-a-database.md)|  
|[Attacher et détacher une base de données &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)|[Afficher une liste des bases de données sur une instance de SQL Server](view-a-list-of-databases-on-an-instance-of-sql-server.md)|  
|[Ajouter des fichiers de données ou journaux à une base de données](add-data-or-log-files-to-a-database.md)|[Afficher ou modifier le niveau de compatibilité d’une base de données](view-or-change-the-compatibility-level-of-a-database.md)|  
|[Modifier les paramètres de configuration d’une base de données](change-the-configuration-settings-for-a-database.md)|[Utiliser l'Assistant Plan de maintenance](../maintenance-plans/use-the-maintenance-plan-wizard.md)|  
|[Créer une base de données](create-a-database.md)|[Créer un alias de type de données défini par l’utilisateur](create-a-user-defined-data-type-alias.md)|  
|[Supprimer une base de données](delete-a-database.md)|[Instantanés de base de données &#40;SQL Server&#41;](database-snapshots-sql-server.md)|  
  
## <a name="related-content"></a>Contenu associé  
 [Index](../indexes/indexes.md)  
  
 [Views](../views/views.md)  
  
 [Procédures stockées &#40;moteur de base de données &#41;](../stored-procedures/stored-procedures-database-engine.md)  
  
  
