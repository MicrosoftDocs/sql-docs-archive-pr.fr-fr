---
title: MSSQL_ENG014121 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04d4cbdd2197745d2d795814d88c4f7bc28eb90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599923"
---
# <a name="mssql_eng014121"></a>MSSQL_ENG014121
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14121|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer le distributeur '%s'. Des bases de données de distribution sont associées à ce distributeur.|  
  
## <a name="explanation"></a>Explication  
 Une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est configurée en tant que serveur de distribution ne peut pas être supprimée du rôle Serveur de distribution car il y a des bases de données de distribution associées à l'instance. Cette erreur se produit si vous tentez de supprimer une base de données de distribution qui est associée à un ou plusieurs serveurs de publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour trouver les noms des serveurs de publication et des bases de données de distribution associées à ce serveur de distribution, exécutez [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) à partir d’une base de données sur le serveur de distribution.  
  
 Exécutez [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) pour toutes les bases de données de distribution associées à ce serveur de distribution. Quand toutes les associations de base de données de distribution sont supprimées, vous pouvez désactiver la distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Configurer la distribution](configure-distribution.md)  
  
  
