---
title: MSSQLSERVER_21889 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702928"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21889|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21889|  
|Texte du message|L'instance '%s' de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas un serveur de publication de réplication. Exécutez `sp_adddistributor` sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] '%s' avec le serveur de distribution '%s' afin de permettre à l'instance d'héberger la base de données de publication '%s'. Veillez à spécifier la même connexion et mot de passe que ceux utilisés pour le serveur de publication d'origine.|  
  
## <a name="explanation"></a>Explication  
 Afin d'héberger la base de données du serveur de publication, l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être un serveur de publication de réplication. `sp_validate_redirected_publisher` appelle `sp_helpdistributor` sur le serveur distant pour déterminer si le serveur est un serveur de publication de réplication. Cette erreur est retournée lorsque l'exécution de la procédure stockée `sp_helpdistributor` indique que l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas un serveur de publication de réplication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez `sp_adddistributor` dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de publication. Lors de l'exécution de `sp_adddistributor`, spécifiez le serveur de distribution correct. Utilisez la même valeur pour le *@password* paramètre que celle utilisée lors de la `sp_adddistributor` première exécution sur le serveur de distribution.  
  
  
