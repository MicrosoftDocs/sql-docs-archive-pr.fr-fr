---
title: Identité et contrôle d’accès (réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ae16d0908efa211a773b278fc8e86b1bf1966d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701040"
---
# <a name="identity-and-access-control-replication"></a>Identité et contrôle d'accès (réplication)
  L'authentification est le processus selon lequel une entité (généralement un ordinateur) vérifie qu'une autre entité, également appelée *entité principale*, (généralement un autre ordinateur ou un autre utilisateur) est bien ce qu'elle prétend être. L'autorisation est le processus selon lequel une entité principale authentifiée bénéficie de l'accès aux ressources, telles qu'un fichier du système de fichiers ou une table d'une base de données.  
  
 La sécurité de réplication fait appel à l'authentification et à l'autorisation pour contrôler l'accès aux objets de base de données répliqués, aux ordinateurs et aux agents impliqués dans le traitement de la réplication. Trois mécanismes régissent son fonctionnement :  
  
-   Sécurité de l’agent : le modèle de sécurité de l’agent de réplication permet un contrôle affiné sur les comptes sous lesquels les agents de réplication s’exécutent et effectuent des connexions. Pour plus d'informations sur le modèle de sécurité de l'agent, consultez [Replication Agent Security Model](replication-agent-security-model.md). Pour plus d’informations sur la définition des connexions et des mots de passe pour les agents, consultez [Gérer les connexions et les mots de passe dans la réplication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).  
  
-   Rôles d’administration : Assurez-vous que les rôles de serveur et de base de données corrects sont utilisés pour la configuration, la maintenance et le traitement de la réplication. Pour plus d’informations, voir [Security Role Requirements for Replication](security-role-requirements-for-replication.md).  
  
-   La liste d’accès à la publication (PAL) : accorde l’accès aux publications via la PAL. La liste d'accès à la publication fonctionne de manière similaire à une liste de contrôle d'accès [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Lorsqu'un Abonné se connecte au serveur de publication ou au serveur de distribution et souhaite accéder à une publication, les informations d'authentification passées par l'agent sont comparées à celles de la liste d'accès à la publication. Pour obtenir plus d’informations et pour connaître les bonnes pratiques concernant la liste d’accès à la publication, consultez [Sécuriser le serveur de publication](secure-the-publisher.md).  
  
## <a name="filtering-published-data"></a>Filtrage des données publiées  
 Outre l'utilisation de l'authentification et de l'autorisation pour contrôler l'accès aux données et aux objets répliqués, la réplication comprend deux options permettant de contrôler les données disponibles sur un Abonné : filtrage des colonnes et filtrage des lignes. Pour plus d’informations sur le filtrage, consultez [Filtrer des données publiées](../publish/filter-published-data.md).  
  
 Lorsque vous définissez un article, vous pouvez publier uniquement les colonnes nécessaires pour la publication et omettre celles dont vous n'avez pas besoin ou qui comportent des données sensibles. Par exemple, lorsque vous publiez la table **Customer** de la base de données Adventure Works à l'attention des commerciaux sur le terrain, vous pouvez omettre la colonne **AnnualSales** , qui ne concerne que les cadres de l'entreprise.  
  
 Le filtrage des données publiées vous permet de restreindre l'accès aux données et de spécifier les données qui sont disponibles sur l'Abonné. Par exemple, vous pouvez filtrer la table **Customer** afin que les partenaires de l'entreprise ne reçoivent que les informations sur les clients dont la colonne **ShareInfo** possède la valeur « Oui ». Pour les réplications de fusion, vous devez tenir compte de certains points de sécurité si vous utilisez un filtre paramétré qui inclut HOST_NAME(). Pour plus d'informations, consultez la section « Filtrage avec HOST_NAME() » dans [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  

## <a name="manage-logins-and-passwords-in-replication"></a>Gérer les connexions et les mots de passe dans la réplication
  Spécifiez les connexions et les mots de passe des agents de réplication lors de la configuration de la réplication. Après la configuration de la réplication, vous pouvez modifier les connexions et les mots de passe. Pour plus d’informations, consultez [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md). Si vous changez le mot de passe d’un compte utilisé par un agent de réplication, exécutez [sp_changereplicationserverpasswords &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de sécurité de l’Agent de réplication](replication-agent-security-model.md)   
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sécurité Réplication SQL Server](view-and-modify-replication-security-settings.md)   
 [Atténuation des menaces et des vulnérabilités de réplication](threat-and-vulnerability-mitigation-replication.md)   

  
  
