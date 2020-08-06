---
title: Codes de retour OLE Automation et informations sur les erreurs| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- return codes [SQL Server]
- OLE Automation [SQL Server], return codes
- OLE Automation [SQL Server], errors
ms.assetid: 9696fb05-e9e8-4836-b359-d4de0be0eeb2
author: stevestein
ms.author: sstein
ms.openlocfilehash: aecdbaedca42b7456dbdbda0407760959e546f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615115"
---
# <a name="ole-automation-return-codes-and-error-information"></a>Codes de retour OLE Automation et informations sur les erreurs
  Les procédures stockées système OLE Automation retournent un code de retour de type `int` qui équivaut au HRESULT retourné par l'opération OLE Automation sous-jacente. Une valeur HRESULT égale à 0 indique que l'opération a réussi. Un HRESULT différent de zéro est un code d’erreur OLE de forme hexadécimale 0x800*nnnnn*, mais lorsqu’il est retourné comme `int` valeur dans un code de retour de procédure stockée, HRESULT se présente sous la forme 214*nnnnnnn*.  
  
 Par exemple, en passant un nom d’objet non valide (SQLDMO. Xyzzy) à sp_OACreate fait en sorte que la procédure retourne un `int` HRESULT de 2147221005, qui est à 0x800401f3 au format hexadécimal.  
  
 Vous pouvez utiliser `CONVERT(binary(4), @hresult)` pour convertir un HRESULT `int` en une valeur `binary`. Toutefois, l'utilisation de `CONVERT(char(10), CONVERT(binary(4), @hresult))` produit une chaîne illisible, car chaque octet du HRESULT est converti en un seul caractère ASCII. Vous pouvez utiliser l’exemple suivant de procédure stockée HexToChar pour convertir un `int` HRESULT en une `char` valeur qui contient une chaîne hexadécimale lisible.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT name FROM sys.objects  
          WHERE name = N'dbo.sp_HexToChar')  
    DROP PROCEDURE HexToChar;  
GO  
CREATE PROCEDURE dbo.sp_HexToChar  
    @BinValue varbinary(255),  
    @HexCharValue nvarchar(255) OUTPUT  
AS  
    DECLARE @CharValue nvarchar(255);  
    DECLARE @Position int;  
    DECLARE @Length int;  
    DECLARE @HexString nchar(16);  
    SELECT @CharValue = N'0x';  
    SELECT @Position = 1;  
    SELECT @Length = DATALENGTH(@BinValue);  
    SELECT @HexString = N'0123456789ABCDEF';  
    WHILE (@Position <= @Length)  
    BEGIN  
        DECLARE @TempInt int;  
        DECLARE @FirstInt int;  
        DECLARE @SecondInt int;  
        SELECT @TempInt = CONVERT(int, SUBSTRING(@BinValue,@Position,1));  
        SELECT @FirstInt = FLOOR(@TempInt/16);  
        SELECT @SecondInt = @TempInt - (@FirstInt*16);  
        SELECT @CharValue = @CharValue +  
            SUBSTRING(@HexString, @FirstInt+1, 1) +  
            SUBSTRING(@HexString, @SecondInt+1, 1);  
        SELECT @Position = @Position + 1;  
    END  
    SELECT @HexCharValue = @CharValue;  
GO  
DECLARE @BinVariable varbinary(35);  
DECLARE @CharValue nvarchar(35);  
  
SET @BinVariable = 123456;  
  
EXECUTE dbo.sp_HexToChar  
    @binvalue = @BinVariable,  
    @HexCharValue = @CharValue OUTPUT;  
  
SELECT @BinVariable AS BinaryValue,  
    @CharValue AS CharacterRep;  
GO  
```  
  
 Vous pouvez utiliser l’exemple suivant de procédure stockée **sp_displayoaerrorinfo** pour afficher les informations d’erreurs OLE Automation lorsqu’une de ces procédures retourne un code de retour HRESULT différent de zéro. Cet exemple de procédure stockée utilise `HexToChar` .  
  
```  
CREATE PROCEDURE dbo.sp_DisplayOAErrorInfo  
    @Object int,  
    @HResult int  
AS  
    DECLARE @Output nvarchar(255);  
    DECLARE @HRHex nchar(10);  
    DECLARE @HR int;  
    DECLARE @Source nvarchar(255);  
    DECLARE @Description nvarchar(255);  
    PRINT N'OLE Automation Error Information';  
    EXEC HexToChar @HResult, @HRHex OUT;  
    SELECT @Output = N'  HRESULT: ' + @HRHex;  
    PRINT @Output;  
    EXEC @HR = sp_OAGetErrorInfo  
        @Object,  
        @Source OUT,  
        @Description OUT;  
    IF @HR = 0  
    BEGIN  
        SELECT @Output = N'  Source: ' + @Source;  
        PRINT @Output;  
        SELECT @Output = N'  Description: '  
               + @Description;  
        PRINT @Output;  
    END  
    ELSE  
    BEGIN  
       PRINT N' sp_OAGetErrorInfo failed.';  
       RETURN;  
    END  
GO  
```  
  
## <a name="related-content"></a>Contenu associé  
 [sp_OAGetErrorInfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
  
