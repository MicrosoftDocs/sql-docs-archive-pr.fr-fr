---
title: Fonctions déterministes et non déterministes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- built-in functions [SQL Server]
- nondeterministic functions
- extended stored procedures [SQL Server], functions that call
- deterministic functions
- user-defined functions [SQL Server], deterministic
ms.assetid: 2f3ce5f5-c81c-4470-8141-8144d4f218dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e755532e06d64e273408c7e81936a1c2d370697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708140"
---
# <a name="deterministic-and-nondeterministic-functions"></a>Fonctions déterministes et non déterministes
  Les fonctions déterministes retournent toujours le même résultat quel que soit le moment auquel elles sont appelées avec un ensemble spécifique de valeurs d'entrée et sur la base du même état de la base de données. Les fonctions non déterministes peuvent retourner différents résultats chaque fois qu'elles sont appelées avec un ensemble spécifique de valeurs d'entrée, même si l'état de la base de données à laquelle elles accèdent demeure inchangé. Par exemple, la fonction AVG retourne toujours le même résultat pour les conditions ci-dessus, mais la fonction GETDATE, qui retourne la valeur datetime actuelle, retourne toujours un résultat différent.  
  
 Plusieurs propriétés de fonctions définies par l’utilisateur déterminent la possibilité pour le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] d’indexer les résultats d’une fonction, par le biais d’index sur des colonnes calculées qui appellent la fonction, ou de vues indexées qui y font référence. Le déterminisme d'une fonction est l'une de ces propriétés. Par exemple, un index cluster ne peut pas être créé sur une vue si celle-ci fait référence à une fonction non déterministe. Pour plus d’informations sur les propriétés des fonctions, dont le déterminisme, consultez [Fonctions définies par l’utilisateur](user-defined-functions.md).  
  
 Cette rubrique identifie le déterminisme des fonctions système intégrées, ainsi que l'effet sur la propriété déterministe des fonctions définies par l'utilisateur lorsqu'elle contient un appel à des procédures stockées étendues.  
  
## <a name="built-in-function-determinism"></a>Déterminisme des fonctions intégrées  
 Vous ne pouvez pas influer sur le déterminisme d'une fonction intégrée. Chaque fonction intégrée est déterministe ou non déterministe en fonction de son implémentation par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, spécifier une clause ORDER BY dans une requête ne modifie pas le déterminisme d'une fonction utilisée dans cette requête.  
  
 Toutes les fonctions de chaîne intégrées sont déterministes. Pour obtenir la liste de ces fonctions, consultez [Fonctions de chaîne &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).  
  
 Les fonctions intégrées suivantes, qui ne sont pas des fonctions de chaîne, sont toujours déterministes :  
  
||||  
|-|-|-|  
|ABS|DATEDIFF|POWER|  
|ACOS|DAY|RADIANS|  
|ASIN|DEGREES|ROUND|  
|ATAN|EXP|SIGN|  
|ATN2|FLOOR|SIN|  
|CEILING|ISNULL|SQUARE|  
|COALESCE|ISNUMERIC|SQRT|  
|COS|LOG|TAN|  
|COT|LOG10|YEAR|  
|DATALENGTH|MONTH||  
|DATEADD|NULLIF||  
  
 Les fonctions suivantes ne sont pas toujours déterministes mais peuvent être utilisées dans les vues indexées ou les index de colonnes calculées si elles sont spécifiées de manière déterministe :  
  
|Fonction|Commentaires|  
|--------------|--------------|  
|Toutes les fonctions d'agrégation|Toutes les fonctions d'agrégation sont déterministes, sauf si elles sont spécifiées avec les clauses OVER et ORDER BY. Pour obtenir la liste de ces fonctions, consultez [Fonctions d’agrégation &#40;Transact-SQL&#41;](/sql/t-sql/functions/aggregate-functions-transact-sql).|  
|CAST|Déterministe sauf si elle est utilisée avec `datetime`, `smalldatetime` ou `sql_variant`.|  
|CONVERT|Déterministe sauf dans l'un des cas suivants :<br /><br /> Le type de source est `sql_variant`.<br /><br /> Le type de cible est `sql_variant` et son type de source est non déterministe.<br /><br /> Le type de source ou de cible est `datetime` ou `smalldatetime`, l'autre type de cible ou de source est une chaîne de caractères et un style non déterministe est spécifié. Pour être déterministe, le paramètre de style doit être une constante. De plus, les styles inférieurs ou égaux à 100 sont non-déterministes, à l'exception des styles 20 et 21. Les styles supérieurs à 100 sont déterministes, à l'exception des styles 106, 107, 109 et 113.|  
|CHECKSUM|Déterministe, sauf CHECKSUM(*).|  
|ISDATE|Déterministe uniquement si utilisé avec la fonction CONVERT, si le paramètre de style CONVERT est spécifié et si le style est différent de 0, 100, 9 ou 109.|  
|RAND|RAND est déterministe uniquement quand un paramètre *seed* est spécifié.|  
  
 Toutes les fonctions relatives à la configuration, aux curseurs, aux métadonnées, à la sécurité et aux statistiques système sont non déterministes. Pour obtenir la liste de ces fonctions, consultez [Fonctions de configuration &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql), [Fonctions de curseur &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-functions-transact-sql), [Fonctions de métadonnées &#40;Transact-SQL&#41;](/sql/t-sql/functions/metadata-functions-transact-sql), [Fonctions de sécurité &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql) et [Fonctions statistiques du système &#40;Transact-SQL&#41;](/sql/t-sql/functions/system-statistical-functions-transact-sql).  
  
 Les fonctions intégrées suivantes, qui appartiennent à d'autres catégories, sont toujours non déterministes.  
  
|||  
|-|-|  
|@@CONNECTIONS|GETDATE|  
|@@CPU_BUSY|GETUTCDATE|  
|@@DBTS|GET_TRANSMISSION_STATUS|  
|@@IDLE|LAG|  
|@@IO_BUSY|LAST_VALUE|  
|@@MAX_CONNECTIONS|LEAD|  
|@@PACK_RECEIVED|MIN_ACTIVE_ROWVERSION|  
|@@PACK_SENT|NEWID|  
|@@PACKET_ERRORS|NEWSEQUENTIALID|  
|@@TIMETICKS|NEXT VALUE FOR|  
|@@TOTAL_ERRORS|NTILE|  
|@@TOTAL_READ|PARSENAME|  
|@@TOTAL_WRITE|PERCENTILE_CONT|  
|CUME_DIST|PERCENTILE_DISC|  
|CURRENT_TIMESTAMP|PERCENT_RANK|  
|DENSE_RANK|RAND|  
|FIRST_VALUE|RANK|  
||ROW_NUMBER|  
||TEXTPTR|  
  
## <a name="calling-extended-stored-procedures-from-functions"></a>Appel de procédures stockées étendues à partir de fonctions  
 Les fonctions qui appellent des procédures stockées étendues sont non déterministes car les procédures stockées étendues peuvent provoquer des effets secondaires sur la base de données. Ces effets secondaires sont des modifications de l'état global de la base de données, comme la mise à jour d'une table ou d'une ressource externe, telle qu'un fichier ou le réseau (par exemple la modification d'un fichier ou l'envoi d'un courrier électronique). Vous ne pouvez pas être assuré d'obtenir un jeu de résultats cohérent lors de l'exécution d'une procédure stockée étendue à partir d'une fonction définie par l'utilisateur. Les fonctions définies par l'utilisateur qui créent des effets secondaires sur la base de données ne sont pas recommandées.  
  
 Une procédure stockée étendue appelée depuis l'intérieur d'une fonction ne peut pas retourner de jeux de résultats au client. Toute API Open Data Services qui retourne des jeux de résultats au client aura un code de retour FAIL.  
  
 La procédure stockée étendue ne peut pas se reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cependant, la procédure ne peut pas joindre la même transaction que la fonction originale ayant appelé la procédure stockée étendue.  
  
 Comme pour les appels à partir d'une procédure stockée ou de traitement par lot, la procédure stockée étendue est exécutée dans le contexte du compte de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel fonctionne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le propriétaire de la procédure stockée étendue doit prendre ce fait en considération lorsqu'il accorde à d'autres utilisateurs la permission d'exécuter la procédure.  
  
  
