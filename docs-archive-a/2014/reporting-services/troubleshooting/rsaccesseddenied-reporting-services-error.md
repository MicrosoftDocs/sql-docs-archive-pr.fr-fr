---
title: rsAccessedDenied - Erreur Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605908"
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Erreur Reporting Services
  L’erreur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**rsAccessedDenied** se produit quand un utilisateur n’est pas autorisé à effectuer une action. Par exemple, il ne dispose pas de l'assignation de rôle lui permettant d'ouvrir un rapport ou il n'a pas ouvert son navigateur avec les autorisations requises.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; en mode SharePoint|  
  
-   Si l'erreur s'est produite en accédant au serveur de rapports directement par le biais d'une URL, l'exception est associée à une erreur HTTP 401.  
  
-   Si l'erreur s'est produite lors de l'utilisation du Gestionnaire de rapports ou d'un autre outil, l'erreur apparaît dans une page d'erreurs.  
  
-   Si l'erreur s'est produite pendant une opération planifiée, un abonnement ou une remise, l'erreur apparaît uniquement dans le fichier journal du serveur de rapports.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|**Nom du produit**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**ID d'événement**|rsAccessedDenied|  
|**Source de l'événement**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Composant**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Texte du message**|Les autorisations accordées à l'utilisateur 'mon_domaine\mon_compte' sont insuffisantes pour vous permettre d'accomplir cette opération. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'autorisation d'accéder au contenu et aux opérations d'un serveur de rapports est accordée par l'intermédiaire des attributions de rôles. Dans une nouvelle installation, seuls les administrateurs locaux ont accès à un serveur de rapports. Pour accorder l'accès à d'autres utilisateurs, un administrateur local doit créer une attribution de rôle qui spécifie un utilisateur de domaine ou un compte de groupe, un ou plusieurs rôles définissant les tâches que l'utilisateur peut effectuer, ainsi qu'une étendue (en général, le dossier de base ou le nœud racine de l'arborescence des dossiers du serveur de rapports). Vous pouvez utiliser le Gestionnaire de rapports pour créer les attributions de rôles. Pour plus d'informations, recherchez «Attributions de rôles » dans la documentation en ligne de SQL Server.  
  
 Cette erreur est également due à l'administration locale du serveur de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributions de rôles](../security/role-assignments.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](../security/granting-permissions-on-a-native-mode-report-server.md)   
 [Rôles et autorisations &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)  
  
  
