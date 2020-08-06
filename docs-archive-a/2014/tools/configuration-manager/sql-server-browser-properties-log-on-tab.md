---
title: Propriétés de SQL Server Browser (onglet Ouvrir une session) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695059"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Propriétés de SQL Server Browser (onglet Ouvrir une session)
  Le programme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser s'exécute sur le serveur en tant que service. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l’écoute des demandes entrantes pour les ressources [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et fournit des informations sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l’ordinateur.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est à l’écoute d’un port UDP et accepte les demandes non authentifiées à l’aide du protocole SSRP ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol).  
  
 La modification du mot de passe d'un compte prend effet immédiatement sans redémarrer le service.  
  
## <a name="options"></a>Options  
 **Compte système local**  
 Exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser dans le contexte de sécurité du compte système local. Quand cela est possible, utilisez à la place de celui-ci un compte à faible niveau d'autorisation.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification Windows. Nous vous recommandons d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services. Pour plus d'informations sur la sélection d'un compte, consultez « Configuration des comptes de service Windows » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Parcourir**  
 Recherchez un principal de sécurité utilisateur ou intégré.  
  
> [!IMPORTANT]  
>  Utilisez un compte à faible niveau d'autorisation. Pour plus d’informations sur les autorisations nécessaires pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, consultez la section relative à la sécurité de la rubrique [Service SQL Server Browser](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 **Mot de passe**  
 Entrez le mot de passe du principal de sécurité.  
  
 **Confirmer le mot de passe**  
 Confirmez le mot de passe du principal de sécurité.  
  
 **État du service**  
 Indique si ce service est en cours d'exécution, arrêté ou désactivé. « **…** » indique qu’un changement d’état est en attente.  
  
 **Start**  
 Démarre le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Stop**  
 Arrête le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Suspendre**  
 Interrompt le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser.  
  
 **Reprendre**  
 Reprend un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser suspendu.  
  
## <a name="see-also"></a>Voir aussi  
 [Service SQL Server Browser](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
