---
title: Utilisation des types de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbffc1c59eb12fa0f448a7fcb26157d5e18dba3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602006"
---
# <a name="working-with-data-types"></a>Utilisation des types de données
  Il existe des données de nombreux types et tailles différents, telles qu'une chaîne qui a une longueur définie, un nombre qui a une précision spécifique ou un type de données défini par l'utilisateur qui est un autre objet ayant son propre ensemble de règles. L' <xref:Microsoft.SqlServer.Management.Smo.DataType> objet classe le type de données afin qu’il puisse être géré correctement par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . L'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> est associé aux objets qui acceptent des données. Les objets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) suivants acceptent des données qui doivent être définies par une propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> :  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 La propriété `DataType` pour les objets qui acceptent des données peut être définie de plusieurs façons.  
  
-   Utilisez le constructeur par défaut et spécifiez des propriétés d'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> explicitement.  
  
-   Utilisez un constructeur surchargé et spécifiez les propriétés <xref:Microsoft.SqlServer.Management.Smo.DataType> comme paramètres.  
  
-   Spécifiez le type <xref:Microsoft.SqlServer.Management.Smo.DataType> inline dans le constructeur d'objet.  
  
-   Utilisez l'un des membres statiques de la classe <xref:Microsoft.SqlServer.Management.Smo.DataType>, par exemple `Int`. Cela retourne en fait une instance d'un objet <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> a plusieurs propriétés qui définissent le type de données. Par exemple, la propriété <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> spécifie le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les valeurs constantes qui représentent des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont répertoriées dans l'énumération <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Cela fait référence à des types de données tels que `varchar`, `nchar`, `currency`, `integer`, `float` et `datetime`.  
  
 Lorsque le type de données est établi, des propriétés spécifiques doivent être définies pour les données. Par exemple, s'il s'agit d'un type `nchar`, la longueur des données de chaîne doit être définie dans la propriété `Length`. La même règle s'applique aux valeurs numériques, pour lesquelles il vous faudrait spécifier la précision et l'échelle.  
  
 Les types de données <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> font référence à des objets qui contiennent la définition du type de données défini par l'utilisateur. Le type <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> est basé sur les types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de l'énumération <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Le <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> est basé sur les [!INCLUDE[msCoName](../../../includes/msconame-md.md)] types de données .net. En général, ces types représentent des données d'un type spécifique qui est fréquemment réutilisé par la base de données à cause de règles d'entreprise définies par l'organisation. Par exemple, un type de données qui stocke une somme d'argent et un dénominateur de devise serait utile dans une société qui négocie dans plusieurs devises.  
  
 L'énumération <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> contient une liste de tous les types de données pris en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Exemples  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Construction d'un objet DataType avec la spécification dans le constructeur en Visual Basic  
 Cet exemple de code montre comment utiliser le constructeur pour créer des instances de types de données basées sur différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Les types <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et XML requièrent tous une valeur de nom afin d'identifier l'objet.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Construction d'un objet DataType avec la spécification dans le constructeur en Visual C#  
 Cet exemple de code montre comment utiliser le constructeur pour créer des instances de types de données basées sur différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Les types <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et XML requièrent tous une valeur de nom afin d'identifier l'objet.  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguments specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Construction d'un objet DataType à l'aide du constructeur par défaut en Visual Basic  
 Cet exemple de code montre comment utiliser le constructeur par défaut pour créer des instances de types de données basées sur différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Les propriétés sont ensuite utilisées pour spécifier le type de données.  
  
 **Remarque** Les <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> types, et XML requièrent tous une valeur de nom pour identifier l’objet.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Construction d'un objet DataType à l'aide du constructeur par défaut en Visual C#  
 Cet exemple de code montre comment utiliser le constructeur par défaut pour créer des instances de types de données basées sur différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Les propriétés sont ensuite utilisées pour spécifier le type de données.  
  
 **Remarque** Les <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> types, et XML requièrent tous une valeur de nom pour identifier l’objet.  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
