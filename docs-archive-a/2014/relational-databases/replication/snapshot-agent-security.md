---
title: Sécurité de l’Agent d’instantané | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 288dc294b7ace9ea5cb098c8deec53c3ae4569a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614497"
---
# <a name="snapshot-agent-security"></a>Sécurité de l'Agent d'instantané
  La boîte de dialogue **Sécurité de l'Agent d'instantané** permet de définir :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent d'instantané s'exécute le serveur de distribution. Ce compte Windows est également baptisé *compte de processus*du fait que le processus agent s'exécute sous ce compte.  
  
-   Le contexte sous lequel l’Agent d’instantané établit des connexions au serveur de publication [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent d'instantané établit des connexions au serveur de publication, même si le serveur de publication et le serveur de distribution se trouvent sur le même ordinateur. L'Agent d'instantané établit également des connexions au serveur de distribution ; ces connexions sont toujours établies en imitant le compte Windows sous lequel l'Agent s'exécute.  
  
     Pour les serveurs de publication Oracle, définissez le contexte sous lequel l'Agent d'instantané se connecte au serveur de publication dans la boîte **Propriétés du serveur de publication** (accessible depuis la boîte de dialogue **Propriété du serveur de distribution** ). Pour plus d’informations, consultez [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Compte de processus**  
 Entrez le compte Windows sous lequel l'Agent d'instantané s'exécute sur le serveur de distribution. Le compte Windows que vous définissez doit :  
  
-   être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution ;  
  
-   pouvoir écrire dans le partage de fichiers de instantanés.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Connexion au serveur de publication**  
 Indiquez si l'Agent d'instantané doit établir des connexions au serveur de publication en imitant le compte défini dans la zone de texte **Compte de processus** en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Il est recommandé de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les comptes de connexion et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md)  
  
  
