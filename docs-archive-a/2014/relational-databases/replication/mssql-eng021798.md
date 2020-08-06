---
title: MSSQL_ENG021798 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 327b4a373c28376701ea12400215ab00367df66a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697925"
---
# <a name="mssql_eng021798"></a>MSSQL_ENG021798
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21798|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le travail de l'Agent « %1!s! » doit être ajouté à l'aide de « %2!s! » avant de continuer. Consultez la documentation de '%s'.|  
  
## <a name="explanation"></a>Explication  
 Pour créer une publication, vous devez être membre du rôle de serveur fixe **sysadmin** sur le serveur de publication, ou membre du rôle de base de données fixe **db_owner** dans la base de données de publication. Si vous êtes membre du rôle **db_owner** , cette erreur est émise si :  
  
-   Vous exécutez des scripts à partir de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Le modèle de sécurité a changé dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]et ces scripts doivent être mis à jour.  
  
-   La procédure stockée **sp_addpublication** est exécutée avant l’exécution de [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql). Ceci s'applique à toutes les publications transactionnelles.  
  
-   La procédure stockée **sp_addpublication** est exécutée avant l’exécution de [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql). Cela s’applique aux publications transactionnelles qui sont activées pour les abonnements de mise à jour en attente (valeur TRUE pour le **@allow_queued_tran** paramètre de **sp_addpublication**).  
  
 Les procédures stockées **sp_addlogreader_agent** et **sp_addqreader_agent** créent chacune un travail d'Agent et vous permettent de spécifier le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent s'exécute. Pour les utilisateurs membres du rôle **sysadmin** , les travaux d'Agents sont créés implicitement si **sp_addlogreader_agent** et **sp_addqreader_agent** ne sont pas exécutées ; les Agents s'exécutent dans le contexte du compte de service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le serveur de distribution. Bien que **sp_addlogreader_agent** et **sp_addqreader_agent** ne soient pas nécessaires pour les utilisateurs membres du rôle **sysadmin** , il est recommandé par mesure de sécurité de spécifier un compte distinct pour les Agents. Pour plus d’informations, voir [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Veillez à exécuter les procédures dans le bon ordre. Pour plus d’informations, consultez [créer une publication](publish/create-a-publication.md), mettre à jour ces scripts pour inclure les procédures stockées et les paramètres requis par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures. Pour plus d’informations, consultez [Mettre à niveau les scripts de réplication &#40;programmation Transact-SQL de la réplication&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
