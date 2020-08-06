---
title: Prise en charge des ensembles de lignes de schéma (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- SQL Server Native Client OLE DB provider, schema rowsets
- rowsets [OLE DB], schema
ms.assetid: a75b4b69-b095-4690-9b31-a2b32a67489e
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c99141cd9d05769a967bc47ce80c320180a3d46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602101"
---
# <a name="schema-rowset-support-ole-db"></a>Prise en charge des ensembles de lignes de schéma (OLE DB)
  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend également en charge le retour des informations de schéma à partir d’un serveur lié lors du traitement des [!INCLUDE[tsql](../../../includes/tsql-md.md)] requêtes distribuées.  
  
> [!NOTE]  
>  Bien que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prenne en charge les synonymes, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne retourne pas les métadonnées de ces derniers.  
  
 Les tableaux suivants répertorient les ensembles de lignes de schéma et les colonnes de restriction prises en charge par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client.  
  
|Ensemble de lignes de schéma|Colonnes de restriction|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Les colonnes supplémentaires suivantes sont propres à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :<br /><br /> -COLUMN_LCID, qui est l’ID de paramètres régionaux du classement. COLUMN_LCID affiche une valeur identique à un LCID Windows.<br />-COLUMN_COMPFLAGS définit les comparaisons prises en charge pour le classement. Le format de données est le même que DBPROB_FINDCOMPAREOPS.<br />-COLUMN_SORTID, qui est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] style de tri du classement.<br />-COLUMN_TDSCOLLATION, qui est le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] classement de la colonne.<br />-IS_COMPUTED, qui est VARIANT_TRUE si la colonne est une colonne calculée et VARIANT_FALSE dans le cas contraire.|  
|DBSCHEMA_FOREIGN_KEYS|Toutes les restrictions sont prises en charge.<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|Les restrictions 1, 2, 3 et 5 sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Toutes les restrictions sont prises en charge.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|Les restrictions 1, 2, et 3 sont prises en charge.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES retourne uniquement des procédures que l'utilisateur actuel peut exécuter ou pour lesquelles l'autorisation VIEW DEFINITION lui a été accordée.|  
|DBSCHEMA_PROVIDER_TYPES|Toutes les restrictions sont prises en charge.<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|Toutes les restrictions sont prises en charge.<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|Toutes les restrictions sont prises en charge.<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](schema-rowsets-distributed-query-support.md)  
  
 [Ensemble de lignes LINKEDSERVERS &#40;OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)   
 [Utilisation des types définis par l'utilisateur](../features/using-user-defined-types.md)  
  
  
