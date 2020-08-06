---
title: DDL, fonctions, procédures stockées et vues FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], database objects
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3fca483581a47720cf0d923506f4439e3e614520
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707612"
---
# <a name="filetable-ddl-functions-stored-procedures-and-views"></a>DDL, fonctions, procédures stockées et vues FileTable
  Répertorie les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et les objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été ajoutés ou modifiés afin de prendre en charge la fonctionnalité FileTable dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La colonne d'état dans les tableaux suivants indique si l'élément est nouveau dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ou bien s'il était présent dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais a été modifié dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour prendre en charge la recherche sémantique.  
  
 Pour obtenir la liste des instructions et des objets de base de données qui prennent en charge FILESTREAM, consultez [FILESTREAM DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Instructions DDL (Data Definition Language, langage de définition de données) Transact-SQL  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)<br /><br /> [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)|Modifié|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)|Modifié|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)|Modifié|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)|Modifié|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)<br /><br /> [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)|Modifié||  
  
##  <a name="functions"></a><a name="func"></a> Fonctions  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|**Ajouté**|[Travailler avec des répertoires et des chemins d’accès dans des FileTables](work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="stored-procedures"></a><a name="sproc"></a> Procédures stockées  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
  
##  <a name="catalog-views"></a><a name="cv"></a> Affichages catalogue  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)|**Ajouté**|[Activer les conditions préalables pour les FileTables](enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)|**Ajouté**|[Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Modifié|[Gérer des FileTables](manage-filetables.md)|  
  
##  <a name="dynamic-management-views"></a><a name="dmv"></a> Vues de gestion dynamique  
  
|Object|Statut|Informations complémentaires|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)|**Ajouté**|[Gérer des FileTables](manage-filetables.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des FileTables](manage-filetables.md)  
  
  
