---
title: Types de données et comportement de chargement en masse XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b03423f3bb88166d0d9ce5b0df450d4455e7ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611705"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Types de données et comportement du chargement en masse XML (SQLXML 4.0)
  Les types de données spécifiés dans le schéma de mappage (type XSD ou XDR et `sql:datatype`) sont ignorés en général, sauf dans les cas suivants :  
  
 Dans XSD :  
  
-   Si le type est `dateTime` ou `time`, vous devez spécifier `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Lorsque vous effectuez un chargement en masse dans une colonne de `uniqueidentifier` type dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que la valeur xsd est un GUID qui comprend des accolades ({et}), vous devez spécifier **SQL : datatype = "uniqueidentifier"** pour supprimer les accolades avant que la valeur ne soit insérée dans la colonne. Si `sql:datatype` n'est pas spécifié, la valeur est envoyée avec les accolades et l'insertion échoue.  
  
 Pour plus d’informations sur `sql:datatype` , consultez [forçages de type de données et l’annotation sql : DataType &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Dans XDR :  
  
-   Si `dt:type` est `datetime`, `time`, `dateTime.tz` ou `time.tz`, vous devez spécifier les types de données `dt:type` et `sql:datatype` car le chargement en masse XML effectue une conversion de données avant d'envoyer les données à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si vos données XML sont de type `uuid` , `sql:datatype` doit être spécifié ; **DT : type = "UUID"** est également requis, sauf si les données sont des données de chaîne. Si vous ne spécifiez pas `dt:uuid`, le chargement en masse XML accepte les chaînes avec accolades (et les supprime si nécessaire).  
  
-   Si les données XML sont `bin.base64` ou `bin.hex`, vous devez spécifier le type de données XML avec `dt:type`. Le chargement en masse XML charge ensuite les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous la forme d'une représentation hexadécimale des données.  
  
  
