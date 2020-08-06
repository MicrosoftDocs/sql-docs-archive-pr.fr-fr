---
title: Page Configuration de base de données (Gestionnaire de configuration Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 800eb48d602c799bcc609e283d83c1b1a72c3303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703028"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>Page Configuration de base de données (Gestionnaire de configuration Master Data Services)
  Utilisez la page **Configuration de la base de données** pour modifier les paramètres système d'une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Les paramètres système affectent l'ensemble des applications Web et services Web associés à la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sélectionnée. Vous devez sélectionner ou créer une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] avant que les paramètres système ne soient activés et disponibles pour la configuration.  
  
## <a name="current-database"></a>Base de données active  
 Sélectionnez une base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] existante ou créez une base de données pour laquelle modifier les paramètres système. La nouvelle base de données est sélectionnée une fois qu'elle a été créée.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Instance SQL Server**|Affiche le nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sélectionnée. Cette valeur est vide tant que vous n'êtes pas connecté à une instance et que vous n'avez pas sélectionné ou créé une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Base de données Master Data Services**|Affiche le nom de la base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sélectionnée. Cette valeur est vide tant que vous n'êtes pas connecté à une instance et que vous n'avez pas sélectionné ou créé une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Version de base de données Master Data Services**|Version du schéma de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Créer une base de données**|Ouvre l'Assistant **Création d'une base de données** à partir duquel vous vous connectez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et créez une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour cette instance.|  
|**Sélectionner la base de données**|Ouvre la boîte de dialogue **Connexion à une base de données** à partir de laquelle vous vous connectez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Mettre à niveau la base de données**|Ouvre un Assistant à partir duquel vous pouvez mettre à niveau une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] spécifiée. Ce bouton est activé uniquement lorsque la base de données spécifiée requiert une mise à niveau.|  
|**Base de données de réparation**|Cliquez sur ce bouton pour vous assurer que la base de données MDS est installée correctement. Cela peut être utile si vous sauvegardez et restaurez une base de données MDS sur une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui n'a jamais hébergé une base de données MDS.|  
  
## <a name="system-settings"></a>Paramètres système  
 Modifiez les paramètres système pour l'ensemble des applications Web et services Web associés à la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sélectionnée.  
  
 Ces paramètres sont disponibles dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] et stockés dans la base de données, dans la table System Settings (mdm.tblSystemSetting). Pour obtenir la liste de tous les paramètres, consultez [Paramètres système &#40;Master Data Services&#41;](system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la base de données et le site Web pour Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Configuration requise pour la base de données &#40;Master Data Services&#41;](install-windows/database-requirements-master-data-services.md)  
  
  
