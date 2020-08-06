---
title: Les composants de compatibilité descendante IIS n’ont pas été détectés (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a5aad54a01b3840e121c6a63de0ea26f35921fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613781"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>Les composants de compatibilité descendante IIS n'ont pas été détectés (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau n'a pas détecté les composants et paramètres IIS qui fournissent des informations utilisées par le programme d'installation pour créer les nouvelles URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 IIS inclut des composants qui fournissent des informations sur les répertoires virtuels du serveur de rapports et du Gestionnaire de rapports, et ces composants ne sont pas installés sur l'ordinateur serveur de rapports. La mise à niveau peut continuer, mais les URL du serveur de rapports et du Gestionnaire de rapports ne seront pas recréées par la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Une fois la mise à niveau terminée, utilisez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour définir les URL pour le serveur de rapports ou le Gestionnaire de rapports. Utilisez le Gestionnaire des services IIS pour supprimer les répertoires virtuels dont vous n'avez plus besoin.  
  
 Pour plus d’informations, consultez [configurer une URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation en ligne de.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
