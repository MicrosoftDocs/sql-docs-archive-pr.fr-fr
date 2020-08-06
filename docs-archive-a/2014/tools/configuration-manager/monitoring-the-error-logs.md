---
title: Surveillance des journaux d’erreurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604788"
---
# <a name="monitoring-the-error-logs"></a>Surveillance des journaux d'erreurs
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enregistre certains événements système ainsi que des événements définis par l’utilisateur dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Tous les événements consignés dans ces deux journaux sont automatiquement datés. Utilisez les informations du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour résoudre des problèmes liés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le journal des applications Windows fournit une vue d'ensemble des événements survenus dans le système d'exploitation Windows, ainsi que des événements survenus dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez l'Observateur d'événements Windows pour afficher le journal des applications Windows et filtrer les informations. Par exemple, vous pouvez filtrer des d'événements, comme les informations, les avertissements, les erreurs, les audits de succès et les audits d'échecs.  
  
## <a name="comparing-error-and-application-log-output"></a>comparaison des sorties des journaux d'erreurs et des applications  
 Vous pouvez utiliser le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le journal des applications Windows pour identifier les causes des problèmes. Par exemple, pendant la surveillance du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez rencontrer des messages d'erreur qui ne contiennent pas d'informations sur la cause. En comparant les dates et les heures des événements intervenus entre ces journaux, vous pouvez réduire la liste des causes possibles. La visionneuse du fichier journal de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] permet d'intégrer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les journaux Windows dans une même liste, facilitant ainsi la compréhension d'événements serveur et d'événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] liés. Pour plus d'informations, consultez la rubrique relative à la visionneuse du fichier journal dans la documentation en ligne de SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Consultation du journal des erreurs de SQL Server](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|Contient des informations sur le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la procédure pour l'afficher.|  
|[Affichage du journal des applications Windows](viewing-the-windows-application-log.md)|Contient des informations sur le journal des applications Windows et la procédure pour l'afficher.|  
  
  
