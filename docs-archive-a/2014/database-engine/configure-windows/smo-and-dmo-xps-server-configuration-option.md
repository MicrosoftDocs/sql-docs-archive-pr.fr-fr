---
title: SMO and DMO XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f18fc6fafcf033113c983f990700158a10aec92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707848"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (option de configuration de serveur)
  Utilisez l'option SMO and DMO XPs pour activer les procédures stockées étendues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) sur ce serveur.  
  
 Remarque : à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO a été supprimé de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les valeurs possibles sont décrites dans le tableau suivant :  
  
|Valeur|Signification|  
|-----------|-------------|  
|0|Les procédures étendues SMO ne sont pas disponibles.|  
|1|Les procédures étendues SMO sont disponibles. Il s’agit de la valeur par défaut.|  
  
 Le paramètre prend effet immédiatement.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active les procédures stockées étendues de SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
