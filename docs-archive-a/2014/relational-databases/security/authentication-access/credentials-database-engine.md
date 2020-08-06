---
title: Informations d’identification (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: faa2b5be7cf6918b5d5232763a96ed4dbbc89e51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612732"
---
# <a name="credentials-database-engine"></a>Informations d'identification (moteur de base de données)
  Les informations d'identification correspondent à un enregistrement qui contient les informations d'authentification requises pour la connexion à une ressource en dehors de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ces informations sont utilisées en interne par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La plupart des informations d'identification contiennent un nom d'utilisateur et un mot de passe Windows.  
  
 Les informations stockées dans des informations d'identification permettent à un utilisateur connecté à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par le biais de l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'accéder à des ressources en dehors de l'instance du serveur. Lorsque la source externe est Windows, l'utilisateur est authentifié en tant qu'utilisateur Windows, tel que spécifié dans les informations d'identification. Un groupe d'informations d'identification peut être mappé à plusieurs connexions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . En revanche, une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut être mappée à un seul groupe d'informations d'identification.  
  
 Les informations d'identification système sont créées automatiquement et sont associées à des points de terminaison spécifiques. Le nom de ces informations d'identification système commence par deux signes dièse (##).  
  
 Pour plus d’informations sur les informations d’identification, consultez l’affichage catalogue [sys. Credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) .  
  
## <a name="related-content"></a>Contenu associé  
 [Créer des informations d’identification](../authentication-access/create-a-credential.md) [créer des informations d’identification &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [Sécurisation de SQL Server](../securing-sql-server.md)  
  
  
