---
title: Utiliser la fonction EVENTDATA | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- EVENTDATA function
- DDL triggers, EVENTDATA function
ms.assetid: 675b8320-9c73-4526-bd2f-91ba42c1b604
author: rothja
ms.author: jroth
ms.openlocfilehash: 57fb59a3954fb00ab943944c58cccd352c7270d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613870"
---
# <a name="use-the-eventdata-function"></a>Utiliser la fonction EVENTDATA
  Les informations sur un événement qui lance un déclencheur DDL sont capturées à l'aide de la fonction EVENTDATA. Cette fonction retourne une valeur `xml`. Le schéma XML inclut des informations sur les éléments suivants :  
  
-   l'heure de l'événement ;  
  
-   le SPID (System Process ID) de la connexion lorsque le déclencheur s'est exécuté ;  
  
-   le type d'événement qui a lancé le déclencheur.  
  
 Selon le type d'événement, le schéma inclut ensuite des informations complémentaires, telles que la base de données dans laquelle s'est produit l'événement, l'objet sur lequel il s'est produit et l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] de l'événement. Pour plus d'informations, consultez [DDL Triggers](ddl-triggers.md).  
  
 Par exemple, le déclencheur DDL ci-dessous est créé dans l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
```  
  
 L'instruction `CREATE TABLE` suivante est ensuite exécutée :  
  
 `CREATE TABLE NewTable (Column1 int);`  
  
 L’instruction `EVENTDATA()` du déclencheur DDL capture le texte de l’instruction `CREATE TABLE` qui n’est pas autorisé. Cela est possible en utilisant une instruction XQuery sur les `xml` données générées par EventData et en extrayant l' \<CommandText> élément. Pour plus d’informations, consultez [Informations de référence sur le langage XQuery &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).  
  
> [!CAUTION]  
>  EVENTDATA capture les données des événements CREATE_SCHEMA ainsi que l'<élément_de_schéma> de la définition CREATE SCHEMA correspondante, s'il existe. En outre, EVENTDATA reconnaît la définition <élément_de_schéma> en tant qu'événement distinct. En conséquence, un déclencheur DDL créé à la fois sur un événement CREATE_SCHEMA et sur un événement représenté par l'<élément_de_schéma> de la définition CREATE SCHEMA, peut retourner deux fois les mêmes données d'événement, telles que les données `TSQLCommand`. Par exemple, considérez qu'un déclencheur DDL est créé sur les deux événements CREATE_SCHEMA et CREATE_TABLE et que le traitement suivant est exécuté :  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  Si l'application récupère les données `TSQLCommand` de l'événement CREATE_TABLE, soyez conscient que ces données peuvent apparaître deux fois : une fois lorsque l'événement CREATE_SCHEMA se produit et de nouveau lorsque l'événement CREATE_TABLE a lieu. Évitez de créer des déclencheurs DDL sur les événements CREATE_SCHEMA et sur les textes <élément_de_schéma> de toute définition CREATE SCHEMA correspondante, ou construisez la logique dans votre application de sorte que le même événement ne soit pas traité deux fois.  
  
## <a name="alter-table-and-alter-database-events"></a>Événements ALTER TABLE et ALTER DATABASE  
 Les données d'événements pour les événements ALTER_TABLE et ALTER_DATABASE incluent également les noms et types d'autres objets affectés par l'instruction DDL et l'action effectuée sur ces objets. Les données d'événements ALTER_TABLE incluent les noms des colonnes, contraintes ou déclencheurs affectés par l'instruction TABLE ALTER et l'action (créer, modifier, supprimer, activer ou désactiver) effectuée sur les objets affectés. Les données d'événements ALTER_DATABASE incluent les noms des fichiers ou groupes de fichiers affectés par l'instruction ALTER DATABASE et l'action (créer, modifier ou supprimer) effectuée sur les objets affectés.  
  
 Par exemple, créez le déclencheur DDL ci-dessous dans l'exemple de base de données AdventureWorks :  
  
```  
CREATE TRIGGER ColumnChanges  
ON DATABASE   
FOR ALTER_TABLE  
AS  
-- Detect whether a column was created/altered/dropped.  
SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]', 'nvarchar(max)')  
RAISERROR ('Table schema cannot be modified in this database.', 16, 1);  
ROLLBACK;  
```  
  
 Ensuite, exécutez l'instruction ALTER TABLE suivante qui enfreint une contrainte :  
  
```  
ALTER TABLE Person.Address ALTER COLUMN ModifiedDate date;   
```  
  
 L’instruction EVENTDATA() du déclencheur DDL capture le texte de l’instruction `ALTER TABLE` qui n’est pas autorisé.  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser la fonction EVENTDATA pour créer un journal des événements. Dans l'exemple suivant, une table est créée pour stocker des informations sur l'événement. Un déclencheur DDL est ensuite créé sur la base de données active qui remplit la table avec les informations ci-dessous, chaque fois qu'un événement DDL se produit au niveau de la base de données :  
  
-   l'heure de l'événement (avec la fonction GETDATE) ;  
  
-   l'utilisateur de la base de données sur la session de qui l'événement s'est produit (avec la fonction CURRENT_USER) ;  
  
-   le type de l'événement ;  
  
-   l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] comprenant l'événement.  
  
 Là encore, les deux derniers éléments sont capturés en utilisant XQuery sur les données `xml` générées par EVENTDATA.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger  
CREATE TABLE TestTable (a int)  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
```  
  
> [!NOTE]  
>  Pour retourner des données d'événement, nous vous recommandons d'utiliser la méthode XQuery `value()` à la place de la méthode `query()`. La méthode `query()` retourne des instances XML et CR/LF (retour chariot/saut de ligne) à échappement &amp; dans les résultats, alors que la méthode `value()` rend les instances CR/LF invisibles dans le résultat.  
  
 L'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] fournit un exemple similaire de déclencheur DDL. Pour trouver cet exemple, accédez au dossier des déclencheurs de base de données à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ce dossier se trouve dans le dossier **Programmabilité** de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Cliquez avec le bouton droit sur **ddlDatabaseTriggerLog** et sélectionnez **Générer un script du déclencheur de la base de données en tant que**. Par défaut, le déclencheur DDL **ddlDatabaseTriggerLog** est désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements DDL](../triggers/ddl-events.md)   
 [Groupes d’événements DDL](../triggers/ddl-event-groups.md)  
  
  
