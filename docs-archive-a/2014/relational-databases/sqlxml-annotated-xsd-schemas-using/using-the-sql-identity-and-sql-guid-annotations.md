---
title: 'Utilisation des annotations SQL : Identity et SQL : GUID | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc5c08f158911edb0a1a0638fc4bcee1e05a248c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605354"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Utilisation des annotations sql:identity et sql:guid
  Vous pouvez spécifier les `sql:identity` `sql:guid` annotations et dans un schéma XSD sur tout nœud qui est mappé à une colonne de base de données dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le format de code de mise à jour (updategram) prend en charge les attributs `updg:at-identity` et `updg:guid`, contrairement au format de DiffGram. L'attribut `updg:at-identity` définit le comportement de mise à jour d'une colonne de type IDENTITY. L'attribut `updg:guid` permet d'obtenir une valeur GUID à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de l'utiliser dans le code de mise à jour (updategram). Pour plus d’informations et pour obtenir des exemples fonctionnels, consultez [insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Les annotations `sql:identity` et `sql:guid` étendent ces fonctionnalités aux DiffGrams.  
  
 Lorsque vous exécutez un DiffGram, il est d'abord converti en un code de mise à jour (updategram), puis le code de mise à jour (updategram) est exécuté. En spécifiant les annotations `sql:identity` et `sql:guid` dans le schéma XSD, vous définissez en fait le comportement d'un code de mise à jour (updategram). Par conséquent, toutes les annotations sont décrites dans le contexte d'un code de mise à jour (updategram). Les annotations peuvent être utilisées à la fois pour les DiffGrams et les codes de mise à jour (updategram) ; toutefois, les codes de mise à jour (updategram) offrent déjà un moyen plus puissant pour gérer l'identité et les valeurs GUID.  
  
 Les annotations `sql:identity` et `sql:guid` peuvent être définies sur un élément de contenu complexe.  
  
## <a name="sqlidentity-annotation"></a>Annotation sql:identity  
 Vous pouvez spécifier l'annotation `sql:identity` dans le schéma XSD de n'importe quel nœud mappé sur une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit le mode de mise à jour de la colonne de type IDENTity (à l’aide de la valeur fournie dans mise à jour pour modifier la colonne ou en ignorant la valeur, auquel cas une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeur générée est utilisée pour cette colonne).  
  
 Deux valeurs peuvent être assignées à l'annotation `sql:identity` :  
  
 ignore  
 Ordonne au code de mise à jour (updategram) d'ignorer toute valeur fournie dans le code de mise à jour (updategram) pour cette colonne et de compter sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer la valeur d'identité.  
  
 useValue  
 Ordonne au code de mise à jour (updategram) d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour mettre à jour la colonne de type IDENTITY. Un code de mise à jour (updategram) ne vérifie pas si la colonne est une valeur d'identité ou pas.  
  
 Si le code de mise à jour (updategram) spécifie une valeur pour la colonne de type IDENTITY, l'annotation `sql:identity="useValue"` doit être spécifiée dans le schéma.  
  
## <a name="sqlguid-annotation"></a>Annotation sql:guid  
 Un code de mise à jour (updategram) peut faire en sorte que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une valeur GUID, puis utiliser cette valeur dans le code de mise à jour (updategram). Dans le contexte de DiffGrams, vous pouvez utiliser l'annotation `sql:guid` pour spécifier s'il faut utiliser une valeur GUID générée par SQL Server ou utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.  
  
 Deux valeurs peuvent être assignées à l'annotation `sql:guid` :  
  
 générer  
 Spécifie que le GUID généré par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être utilisé pour cette colonne de l'opération de mise à jour.  
  
 useValue  
 Spécifie que la valeur spécifiée dans le code de mise à jour (updategram) doit être utilisée pour la colonne. Valeur par défaut.  
  
  
