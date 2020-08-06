---
title: Autres problèmes de mise à niveau de Moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db496112fc975304bb2d7da9d9ea1c52e6dd8bec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603217"
---
# <a name="other-database-engine-upgrade-issues"></a>Autres problèmes de mise à niveau du moteur de base de données
  Les problèmes de mise à niveau suivants ne peuvent pas être détectés par la version actuelle du Conseiller de mise à niveau. Passez en revue les problèmes répertoriés ci-dessous pour évaluer leur impact potentiel sur vos systèmes.  
  
## <a name="multiple-database-engine-deprecated-features"></a>Plusieurs fonctionnalités déconseillées du moteur de base de données  
 Les options ou instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes sont déconseillées :  
  
-   Options NO_LOG et TRUNCATE_ONLY de BACKUP LOG  
  
-   BACKUP TRANSACTION  
  
-   RESTORE TRANSACTION  
  
-   DUMP  
  
-   LOAD  
  
-   DBCC CONCURRENCYVIOLATION  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
-   syssegments  
  
 L’utilisation du protocole VIA pour se connecter à l' [!INCLUDE[ssDE](../../includes/ssde-md.md)] est déconseillée.  
  
## <a name="new-data-types"></a>Nouveaux types de données  
 Les éléments suivants sont des types système réservés. Renommez les types définis par l'utilisateur en conflit avant ou après la mise à niveau.  
  
-   Geography  
  
-   Géométrie  
  
-   Datetime2  
  
-   HierarchyID  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a>La table cible de la clause OUTPUT INTO ne peut pas contenir de déclencheur défini  
 La sortie dans une table cible lorsque la table contient des déclencheurs activés n’est pas prise en charge.  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a>Erreur de compilation des UDF lorsque la cible d'une clause OUTPUT INTO est une table  
 Les fonctions définies par l'utilisateur (UDF) ne permettent pas d'exécuter des actions qui modifient l'état des bases de données. Par exemple, une fonction définie par l'utilisateur ne peut exécuter aucune action DDL (CREATE/ALTER/DROP) ou DML (INSERT/UPDATE/DELETE) sur des objets, à l'exception des variables de table.  
  
## <a name="merge-is-a-reserved-keyword"></a>MERGE est un mot clé réservé  
 MERGE est un maintenant un mot clé entièrement réservé. Les applications ne peuvent plus contenir d'objets (table, colonne, etc.) appelés MERGE.  
  
## <a name="rename-cdc-schema"></a>Renommer le schéma CDC  
 Il y a un nom de schéma appelé CDC. Ce nom de schéma ne peut pas être utilisé si la **capture de données modifiées** est activée pour la base de données.  
  
 Vous devez supprimer le schéma CDC avant d’activer la **capture de données modifiées** pour la base de données. Cette procédure peut s'effectuer avant ou après la mise à niveau. Pour supprimer le schéma, procédez comme suit :  
  
1.  Transférez les objets du schéma CDC vers un nouveau schéma à l'aide de l'instruction ALTER SCHEMA.  
  
2.  Vérifiez les autorisations pour les objets dans le nouveau schéma.  
  
3.  Apportez les modifications nécessaires à l'application.  
  
4.  Supprimez le schéma CDC à l'aide de l'instruction DROP SCHEMA.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
