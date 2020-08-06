---
title: Configuration de Analysis Services-approvisionnement de comptes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 109b5d9ddddf2b78c0bb8947cfa876d233f804ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604986"
---
# <a name="analysis-services-configuration---account-provisioning"></a>Configuration Analysis Services – Mise en service de compte
  Utilisez cette page pour définir le mode serveur et pour accorder des autorisations administratives aux utilisateurs ou services qui requièrent un accès non restreint à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le programme d’installation n’ajoute pas automatiquement le groupe Windows local BUILTIN\Administrateurs au rôle des administrateurs de serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de l’instance que vous installez. Si vous souhaitez ajouter le groupe Administrateurs local au rôle des administrateurs de serveur, vous devez spécifier explicitement ce groupe.  
  
 Si vous installez [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], vous devez accorder des autorisations administratives aux administrateurs de batterie de serveurs SharePoint ou aux administrateurs de service qui sont responsables d'un déploiement de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans une batterie de serveurs [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. Pour plus d’informations sur les [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] exigences relatives aux comptes d’installation et de service, consultez [installer les fonctionnalités BI de SQL Server avec SharePoint &#40;PowerPivot et Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="options"></a>Options  
 **Mode serveur** - Le mode serveur spécifie le type des bases de données Analysis Services qui peuvent être déployées sur le serveur. Les modes serveur sont déterminés pendant l'installation et ne peuvent pas être modifiés par la suite. Tous les modes s'excluent mutuellement, ce qui signifie que vous aurez besoin de deux instances d'Analysis Services, chacune configurée pour un mode différent, pour prendre en charge à la fois les solutions de modèle tabulaire et OLAP classiques.  
  
 **Spécifier les administrateurs** - Vous devez spécifier au moins un administrateur de serveur pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les utilisateurs ou groupes que vous spécifiez deviendront membres du rôle des administrateurs de serveur de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que vous installez. Ceux-ci doivent être des comptes d'utilisateur de domaine Windows dans le même domaine que l'ordinateur sur lequel vous installez le logiciel.  
  
> [!NOTE]  
>  Le contrôle de compte d'utilisateur est une fonctionnalité de sécurité Windows qui requiert qu'un administrateur approuve de façon spécifique les actions ou applications administratives avant qu'elles soient autorisées à s'exécuter. Dans la mesure où le contrôle de compte d'utilisateur est activé par défaut, vous serez invité à autoriser des opérations spécifiques qui requièrent des privilèges élevés. Vous pouvez configurer le contrôle de compte d'utilisateur de manière à modifier son comportement par défaut ou à le personnaliser pour des programmes spécifiques. Pour plus d’informations sur UAC et la configuration UAC, consultez [Guide pas à pas du contrôle de compte d’utilisateur](https://go.microsoft.com/fwlink/?linkid=196350) et [contrôle de compte d’utilisateur (Wikipédia)](https://go.microsoft.com/fwlink/?linkid=196351).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les comptes de service &#40;Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md)   
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
