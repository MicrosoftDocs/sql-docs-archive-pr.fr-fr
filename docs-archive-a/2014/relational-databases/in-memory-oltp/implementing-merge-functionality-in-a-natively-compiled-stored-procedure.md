---
title: Implémentation de la fonctionnalité de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604009"
---
# <a name="implementing-merge-functionality"></a>Implémentation de la fonctionnalité MERGE
  Une base de données devra peut-être effectuer l'insertion d'une mise à jour, selon qu'une ligne particulière existe déjà ou non dans la base de données.  
  
 Sans utiliser l'instruction `MERGE`, voici une approche que vous pouvez utiliser dans [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Autre méthode [!INCLUDE[tsql](../../includes/tsql-md.md)] pour implémenter une fusion :  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 Pour une procédure stockée compilée en mode natif  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Constructions Transact-SQL non prises en charge par In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
