---
title: Fonctionnalités de Master Data Services dépréciées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce532e9f407ec475f7e59c0d79659265a9e0bf3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695768"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a>Fonctionnalités Master Data Services déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="staging-process"></a>Processus de site  
 Le processus de site utilisé dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] n'est plus disponible dans l'application Web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ; toutefois il l'est encore dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Les erreurs du processus de site de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ne sont plus affichées dans l'interface utilisateur. Les codes d’erreur qui sont remplis pendant le processus de site sont toujours disponibles dans les tables de mise en lots et se trouvent ici : [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx) .  
  
 Les tables de mise en lots (tblStgMember, tblStgMemberAttribute et tblStgRelationship) sont toujours disponibles dans la base de données. La procédure stockée utilisée pour initialiser le processus de site (mdm.udpStagingSweep) est encore disponible dans la base de données.  
  
 Les méthodes de service Web qui appellent le processus de site sont toujours disponibles.  
  
 L'intervalle de mise en lots défini dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] s'applique au processus de site dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] et [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Un nouveau processus de site plus performant a été implémenté dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [Importation de données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
## <a name="metadata"></a>Métadonnées  
 Bien que le modèle de métadonnées soit toujours affiché dans l'application Web de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], il ne doit pas être utilisé. Elle sera supprimée dans une version ultérieure. Les utilisateurs ne peuvent plus afficher les métadonnées dans la zone fonctionnelle **Explorateur** et vous ne pouvez plus créer de versions du modèle de métadonnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités Master Data Services supprimées dans SQL Server 2014](discontinued-master-data-services-features.md)  
  
  
