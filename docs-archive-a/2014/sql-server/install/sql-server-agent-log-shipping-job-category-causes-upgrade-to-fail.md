---
title: SQL Server Agent catégorie de travaux d’envoi de journaux provoque l’échec de la mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710139"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a>La catégorie affectée à l'opération de copie des journaux de transaction de l'Agent SQL Server provoque l'échec de la mise à niveau
  Le processus de mise à niveau échouera si une catégorie de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nommée Copie des journaux de transactions existe.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 Il y a une catégorie de travail système nommée Copie des journaux de transactions. Si une installation en cours de mise à niveau contient déjà une catégorie de travail créée par l'utilisateur, nommée Copie des journaux de transaction, vous devez la renommer avant de procéder à la mise à niveau ; sinon, le processus de mise à niveau échouera.  
  
## <a name="see-also"></a>Voir aussi  
 [L’envoi de journaux ne s’exécutera pas après la mise à niveau](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)   
 [La mise à niveau va remplacer le SQL Server Agent compte proxy de l’utilisateur par le UpgradedProxyAccount temporaire](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Problèmes de mise à niveau de l'Agent SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
