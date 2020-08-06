---
title: Maintenance d’une base de données de publication AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8f36d29049140b6e5bbdfc1a4e716d41a766a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604714"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a>Gestion d'une base de données de publication AlwaysOn (SQL Server)
  Cette rubrique comporte des remarques spécifiques sur la gestion d'une base de données de publication lors de l'utilisation de groupes de disponibilité AlwaysOn.  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a>Maintenance d’une base de données publiée dans un groupe de disponibilité  
 La gestion d'une base de données de publication AlwaysOn est quasiment identique à la gestion d'une base de données de publication standard. Il convient toutefois de prendre quelques précautions :  
  
-   L'administration doit être effectuée au niveau de l'hôte de réplica principal. Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], les publications apparaissent dans le dossier **Publications locales** pour l'hôte de réplica principal et également pour les réplicas secondaires lisibles. Après un basculement, il est possible que vous soyez contraint d'actualiser manuellement [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] pour que la modification soit prise en compte si le serveur secondaire qui est devenu le principal n'était pas lisible.  
  
-   Le moniteur de réplication affiche toujours les informations de publication sous le serveur de publication d'origine. Toutefois, ces informations peuvent être consultées dans le moniteur de réplication à partir de tout réplica en ajoutant le serveur de publication d'origine comme serveur.  
  
-   Si vous faites appel aux procédures stockées ou aux Replication Management Objects pour gérer la réplication sur le principal actuel, vous devez spécifier comme serveur de publication le nom de l'instance où la base de données est activée pour la réplication (le serveur de publication d'origine). Pour déterminer le nom approprié, utilisez la fonction `PUBLISHINGSERVERNAME`. Lorsqu'une base de données de publication joint un groupe de disponibilité, les métadonnées de réplication stockées dans les réplicas de bases de données secondaires sont identiques à celles du principal. Par conséquent, en cas de bases de données de publication activées pour la réplication sur le principal, le nom d'instance du serveur de publication stocké dans les tables système du serveur secondaire est celui du serveur principal, et non du serveur secondaire. Cela affecte la configuration et l'administration de la réplication si la base de données de publication bascule sur un serveur secondaire. Par exemple, si vous configurez la réplication avec des procédures stockées sur un serveur secondaire après le basculement et que vous souhaitez un abonnement par extraction à une base de données de publication qui a été activée sur un autre réplica, vous devez spécifier le nom du serveur de publication d’origine au lieu du serveur de publication actuel comme *@publisher* paramètre de `sp_addpullsubscription` ou `sp_addmergepulllsubscription` . Toutefois, si vous activez une base de données de publication après un basculement, le nom de l'instance du serveur de publication stocké dans les tables système est le nom de l'hôte principal actuel. Dans ce cas, vous devez utiliser le nom d’hôte du réplica principal actuel pour le *@publisher* paramètre.  
  
    > [!NOTE]  
    >  Pour certaines procédures, telles que `sp_addpublication` , le *@publisher* paramètre est pris en charge uniquement pour les serveurs de publication qui ne sont pas des instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; dans ce cas, il n’est pas pertinent pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.  
  
-   Pour synchroniser un abonnement dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] après un basculement, synchronisez les abonnements par extraction à partir de l'abonné, puis synchronisez les abonnements par émission de données à partir du serveur de publication actif.  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a> Suppression d'une base de données publiée d'un groupe de disponibilité  
 Considérez les points suivants lorsqu'une base de données publiée est supprimée d'un groupe de disponibilité, ou lorsqu'un groupe de disponibilité avec une base de données membre publiée est supprimé.  
  
-   Si la base de données de publication sur le serveur de publication d’origine est supprimée d’un réplica principal de groupe de disponibilité, vous devez exécuter `sp_redirect_publisher` sans spécifier de valeur pour le *@redirected_publisher* paramètre pour supprimer la redirection pour la paire serveur de publication/base de données.  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     La base de données restera à l'état de récupération dans le principal et devra être restaurée. Après cela, la réplication doit s'exécuter sans modification sur le serveur de publication d'origine.  
  
-   Si la base de données de publication bascule du serveur de publication d'origine vers un réplica et elle est supprimée du réplica principal de groupe de disponibilité, utilisez la procédure stockée `sp_redirect_publisher` pour rediriger explicitement le serveur de publication d'origine vers nouveau serveur de publication. La base de données restera à l'état de récupération et devra être restaurée. Après cela, la réplication doit continuer à fonctionner de la même manière qu'avec le groupe de disponibilité.  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     Ne supprimez pas le serveur distant du serveur de publication d'origine du serveur de distribution, même si le serveur n'est plus accessible. Les métadonnées du serveur du serveur de publication d'origine sont requises sur le serveur de distribution pour satisfaire les requêtes de métadonnées de publication.  
  
-   Si un groupe de disponibilité complet est supprimé, le comportement d'une base de données membre répliquée est le même que lorsqu'une base de données publiée est supprimée d'un groupe de disponibilité. La réplication peut être reprise à partir du dernier principal dès que la base de données a été restaurée et la redirection a été modifiée. Si la base de données est restaurée sur son serveur de publication d'origine, la redirection doit être supprimée. Si la base de données est restaurée sur un hôte différent, la redirection doit être explicitement dirigée vers le nouvel hôte.  
  
    > [!NOTE]  
    >  Lorsqu'un groupe de disponibilité comportant des bases de données membres publiées est supprimé, ou lorsqu'une base de données publiée est est supprimée d'un groupe de disponibilité, toutes les copies des bases de données publiées sont laissées à l'état de récupération. Si elles sont restaurées, chacune apparaîtra comme une base de données publiée. Une seule copie doit être conservée avec les métadonnées de publication. Pour désactiver la réplication d'une copie de base de données publiée, commencez par supprimer tous les abonnements et toutes les publications de la base de données.  
  
     Exécutez `sp_dropsubscription` pour supprimer les abonnements de publication. Veillez à définir le paramètre *@ignore_distributributor* sur 1 pour conserver les métadonnées de la base de données de publication active sur le serveur de distribution.  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     Exécutez `sp_droppublication` pour supprimer toutes les publications. Là encore, affectez la valeur 1 au paramètre *@ignore_distributor* pour conserver les métadonnées de la base de données de publication active sur le serveur de distribution.  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     Exécutez `sp_replicationdboption` pour désactiver la réplication pour la base de données.  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     À ce stade, la copie de la base de données publiée peut être conservée ou supprimée.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Configurer la réplication pour les groupes de disponibilité AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)  
  
-   [Réplication, Change Tracking, capture de données modifiées et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [FAQ sur l’administration de la réplication](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [Abonnés de réplication et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Groupes de disponibilité AlwaysOn : interopérabilité (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [Réplication SQL Server](../../../relational-databases/replication/sql-server-replication.md)  
  
  
