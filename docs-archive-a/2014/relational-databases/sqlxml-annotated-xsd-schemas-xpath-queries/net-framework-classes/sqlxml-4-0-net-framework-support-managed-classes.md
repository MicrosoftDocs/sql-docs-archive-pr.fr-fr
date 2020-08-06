---
title: Classes managées SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: rothja
ms.author: jroth
ms.openlocfilehash: bb8d2d4f2d2fc512901e4ad37f0e46cf696b9475
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599857"
---
# <a name="sqlxml-managed-classes"></a>classes managées SQLXML
  Les classes managées [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML expose les fonctionnalités de SQLXML 4.0 à l'intérieur de [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework. Avec les classes managées SQLXML, vous pouvez écrire une application C# pour accéder aux données XML à partir d'une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], placer les données dans l'environnement du .NET Framework, traiter les données et retourner les mises à jour à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme DiffGram pour qu'elles soient appliquées. Vous devez utiliser un schéma de mappage lors de l'application des mises à jour à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide des classes managées SQLXML. Pour obtenir un exemple fonctionnel, consultez [accès à la fonctionnalité SQLXML dans l’environnement .net](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Pour utiliser les classes managées SQLXML avec SQLXML 4.0, vous devez installer Microsoft Visual Studio.  
  
> [!NOTE]  
>  Le .NET Framework inclut le fournisseur de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Ce fournisseur peut être utilisé pour accéder à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir de l'environnement .NET ; toutefois, il ne peut gérer que les requêtes SQL traditionnelles (autrement dit, les requêtes de base de données relationnelle à l'exception des requêtes FOR XML). Vous ne pouvez pas exécuter les modèles XML ou les requêtes XPath côté serveur dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modèle objet de classes managées SQLXML](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 Documente les classes managées SQLXML, ainsi que leurs propriétés et leurs méthodes.  
  
 [Utilisation des classes managées SQLXML](sqlxml-4-0-net-framework-support-managed-classes.md)  
 Fournit des exemples d'utilisation des classes managées SQLXML.  
  
  
