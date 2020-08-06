---
title: Vue d’ensemble des instructions Transact-SQL pour groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff25fecf54cfdd1d9c03d1586f0272896542bfa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708647"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a>Vue d'ensemble des instructions Transact-SQL pour les groupes de disponibilité AlwaysOn (SQL Server)
  Cette rubrique présente les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] qui prennent en charge le déploiement de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , ainsi que la création et la gestion d'un groupe de disponibilité donné, d'un réplica de disponibilité et d'une base de données de disponibilité.  
  
  
##  <a name="create-endpoint"></a><a name="CreateEndpoint"></a>CRÉER UN POINT DE TERMINAISON  
 [créer un point de terminaison... POUR DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) crée un point de terminaison de mise en miroir de bases de données, s’il n’en existe aucun sur l’instance de serveur. Chaque instance de serveur sur laquelle vous envisagez de déployer [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ou la mise en miroir de bases de données requiert un point de terminaison de mise en miroir de bases de données.  
  
 Exécutez cette instruction sur l'instance de serveur sur laquelle vous créez le point de terminaison. Vous pouvez créer un seul point de terminaison de mise en miroir de bases de données sur une instance de serveur donnée. Pour plus d’informations, consultez [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
##  <a name="create-availability-group"></a><a name="CreateAG"></a>CRÉER UN GROUPE DE DISPONIBILITÉ  
 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) crée un groupe de disponibilité et éventuellement un écouteur du groupe de disponibilité. Au minimum, vous devez spécifier votre instance de serveur locale, qui deviendra le réplica principal initial. Éventuellement, vous pouvez également spécifier jusqu'à quatre réplicas secondaires.  
  
 Exécutez CREATE AVAILABILITY GROUP sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que vous voulez utiliser pour héberger le réplica principal initial de votre nouveau groupe de disponibilité. Cette instance de serveur doit résider sur un nœud d’un cluster de basculement Windows Server (WSFC) (pour plus d’informations, consultez [conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="alter-availability-group"></a><a name="AlterAG"></a>ALTER AVAILABILITY GROUP  
 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) prend en charge la modification d’un groupe de disponibilité ou d’un écouteur de groupe de disponibilité existant, ainsi que le basculement d’un groupe de disponibilité.  
  
 Exécutez ALTER AVAILABILITY GROUP sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge le réplica principal actuel.  
  
##  <a name="alter-database--set-hadr-"></a><a name="AlterDb"></a>MODIFIER LA BASE DE DONNÉES... DÉFINIR HADR...  
 Les options de la clause [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) de l’instruction ALTER DATABASE vous permettent de joindre une base de données secondaire au groupe de disponibilité de la base de données primaire correspondante, de supprimer une base de données jointe, d’interrompre la synchronisation des données sur une base de données jointe et de reprendre la synchronisation des données.  
  
##  <a name="drop-availability-group"></a><a name="DropAG"></a>SUPPRIMER LE GROUPE DE DISPONIBILITÉ  
 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) supprime un groupe de disponibilité spécifié et tous ses réplicas. L'instruction DROP AVAILABILITY GROUP peut être exécutée à partir de n'importe quel nœud [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans le cluster de basculement WSFC.  
  
##  <a name="restrictions-on-the-availability-group-transact-sql-statements"></a><a name="Restrictions"></a>Restrictions sur les instructions Transact-SQL de groupe de disponibilité  
 Les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP et DROP AVAILABILITY GROUP ont les limitations suivantes :  
  
-   À l'exception de DROP AVAILABILITY GROUP, l'exécution de ces instructions requiert que le service HADR soit activé sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Ces instructions ne peuvent pas être exécutées dans des transactions ou des lots.  
  
-   Même si elles s'efforcent de procéder au nettoyage après une défaillance, ces instructions ne garantissent pas la restauration de toutes les modifications après une défaillance. Toutefois, les systèmes doivent être en mesure de gérer correctement, puis d'ignorer les défaillances partielles.  
  
-   Ces instructions ne prennent pas en charge les expressions ni les variables.  
  
-   Si une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] est exécutée alors qu'une autre récupération ou action de groupe de disponibilité est en cours, l'instruction retourne une erreur. Attendez la fin de l'action ou de la récupération, puis réessayez l'instruction, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
