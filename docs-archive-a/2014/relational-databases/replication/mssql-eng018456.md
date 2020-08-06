---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b05ca549781215e0c4f247110fee87f6def56f04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702787"
---
# <a name="mssql_eng018456"></a>MSSQL_ENG018456
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|18456|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Échec de la connexion pour l’utilisateur '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Explication  
 L'erreur MSSQL_ENG018456 se produit chaque fois qu'une tentative de connexion échoue. Si le message d'erreur inclut le compte **distributor_admin** (Échec de la connexion pour l'utilisateur 'distributor_admin'.), le problème vient d'un compte utilisé par la réplication. La réplication crée un serveur distant, **repl_distributor**, qui permet la communication entre le serveur de distribution et le serveur de publication. Le nom de connexion **distributor_admin** est associé à ce serveur distant et doit avoir un mot de passe valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que vous avez spécifié un mot de passe pour ce compte. Pour plus d’informations, consultez [Protéger le serveur de distribution](security/secure-the-distributor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
