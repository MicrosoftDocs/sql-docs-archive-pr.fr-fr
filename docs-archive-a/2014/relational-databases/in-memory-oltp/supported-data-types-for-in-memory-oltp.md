---
title: Types de données pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a7dda500486c39a66f871d5934f957028fc51e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708344"
---
# <a name="supported-data-types"></a>Types de données pris en charge
  Les types de données suivants sont **pris en charge** dans les tables optimisées en mémoire et les procédures stockées compilées en mode natif :  
  
 **Types de données numériques**  
  
|Type de données|Informations supplémentaires|  
|---------------|--------------------------|  
|int|[int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|bigint|[int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|SMALLINT|[int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|TINYINT|[int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|Décimal|[decimal et numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|numeric|[decimal et numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|float|[float et real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|real|[float et real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[money et smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|SMALLMONEY|[money et smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **Types de données de chaîne**  
  
|Type de données|Informations supplémentaires|  
|---------------|--------------------------|  
|char(n)|[char et varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar (n) <sup>1</sup>|[char et varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar et nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar (n) <sup>1</sup>|[nchar et nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar et nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup> la limite est de 8060 octets par ligne au total, en comptant (n) dans les types de longueur variable.  
  
 Pour plus d'informations sur les classements pris en charge, voir [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
 **Types de données de date et d’heure**  
  
|Type de données|Informations supplémentaires|  
|---------------|--------------------------|  
|Date|[date &#40;Transact-SQL&#41;](/sql/t-sql/data-types/date-transact-sql)|  
|time|[time &#40;Transact-SQL&#41;](/sql/t-sql/data-types/time-transact-sql)|  
|DATETIME|[datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **Types de données binaires**  
  
|Type de données|Informations supplémentaires|  
|---------------|--------------------------|  
|bit|[bit &#40;Transact-SQL&#41;](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[binary et varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary (n) <sup>1</sup>|[binary et varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup> la limite est de 8060 octets par ligne au total, en comptant (n) dans les types de longueur variable.  
  
 **Autres types de données**  
  
|Type de données|Informations supplémentaires|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[uniqueidentifier &#40;Transact-SQL&#41;](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **Types de données non pris en charge**  
  
 Les types de données suivants ne sont pas pris en charge.  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|Objets de grande taille (LOB). Par exemple, varchar(max), nvarchar(max), varbinary(max), image, xml, text et ntext.|ROWVERSION|  
|sql_variant|Fonctions CLR|Types définis par l'utilisateur (UDT)|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'OLTP en mémoire par Transact-SQL](transact-sql-support-for-in-memory-oltp.md)   
 [Implémentation de colonnes LOB dans une table optimisée en mémoire](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [Implémentation de SQL_VARIANT dans un tableau mémoire optimisé](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
