---
title: 'Démonstration : optimisation des performances de l’OLTP en mémoire | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4858e4c35263ab3dd1d9fdcf55a2b136dd8eeaf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605430"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a>Démonstration : Optimisation des performances de l'OLTP en mémoire
  Cet exemple illustre les améliorations des performances obtenues avec l'OLTP en mémoire en comparant les différences des temps de réponse lors de l'exécution d'une requête Transact-SQL identique sur des tables optimisées en mémoire et des tables sur disque classiques. En outre, une procédure stockée compilée en mode natif est également créée (selon la même requête), puis exécutée pour montrer que vous obtenez généralement les meilleurs temps de réponse lors de l'interrogation d'une table optimisée en mémoire avec une procédure stockée compilée en mode natif. Cet exemple ne montre qu'un aspect des améliorations des performances lors de l'accès aux données dans des tables optimisées en mémoire : l'efficacité de l'accès aux données lors de l'exécution d'insertions. Cet échantillon est monothread et ne tire pas profit des avantages de concurrence de l'OLTP en mémoire. Une charge de travail utilisant la concurrence aura des gains de performance supérieurs.  
  
> [!NOTE]  
>  Un autre exemple illustrant les tables optimisées en mémoire est disponible dans [l’exemple d’OLTP en mémoire SQL Server 2014](https://msftdbprodsamples.codeplex.com/releases/view/114491).  
  
 Pour exécuter cet exemple, vous allez effectuer les opérations suivantes :  
  
1.  Créez une base de données nommée **imoltp** et modifiez ses détails de fichier pour la configurer pour l’utilisation de l’OLTP en mémoire.  
  
2.  créer les objets de base de données pour notre exemple : trois tables et une procédure stockée compilée en mode natif ;  
  
3.  exécuter les différentes requêtes et afficher les temps de réponse pour chacune d'elles.  
  
 Pour configurer la base de données **imoltp** pour notre exemple, commencez par créer un dossier vide : **c:\ imoltp_data**, puis exécutez le code suivant :  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 Ensuite, exécutez le code suivant pour créer la table sur disque, deux (2) tables optimisées en mémoire et la procédure stockée compilée en mode natif pour illustrer les différentes méthodes d'accès aux données :  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 L'installation est terminée et nous sommes prêts à exécuter les requêtes qui affichent les temps de réponse comparant les performances entre les méthodes d'accès aux données.  
  
 Pour exécuter l'exemple, exécutez le code suivant plusieurs fois. Ignorez les résultats de la première exécution, qui sont négativement affectés par l'allocation de mémoire initiale.  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 Les résultats attendus fournissent les temps de réponse réels qui montrent comment l'utilisation des tables optimisées en mémoire et des procédures stockées compilées en mode natif offre généralement des temps de réponse plus courts que les mêmes charges de travail exécutées sur des tables sur disque classiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions à AdventureWorks pour présenter l’OLTP en mémoire](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md)   
 [OLTP en mémoire &#40;optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Tables optimisées en mémoire](memory-optimized-tables.md)   
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)   
 [Exigences liées à l’utilisation des tables à mémoire optimisée](requirements-for-using-memory-optimized-tables.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)   
 [CRÉER des tables à procédure et à mémoire optimisée](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
