---
title: Ajouter, mettre à jour et supprimer des données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5d3d0bf9460591a49cbaa2e5bcbfde6bc003d7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703076"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Ajouter, mettre à jour et supprimer des données (Master Data Services)
  Vous pouvez ajouter des données et apporter des modifications de données à un modèle en bloc dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
 **Composants requis**  
  
-   Vous devez avoir l’autorisation d’insérer des données dans le STG. \<name> _Leaf, STG. \<name> _Consolidated, STG. \<name> _Relationship table dans la [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
-   Vous devez disposer des autorisations pour exécuter la \<name> procédure stockée STG. udp_ _Leaf, STG. udp \_ \<name> _Consolidated ou stg. UDP \_ \<name> _Relationship dans la [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données.  
  
-   L'état du modèle ne doit pas être **Activé**.  
  
 **Pour ajouter, mettre à jour et supprimer des données dans la [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données**  
  
1.  Préparez les membres à importer dans la table de mise en lots appropriée de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , en fournissant aussi les valeurs pour les champs obligatoires. Pour obtenir une vue d’ensemble des tables de mise en lots, consultez [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Pour les membres feuille, la table est STG. \<name> _Leaf, où \<name> fait référence à l’entité correspondante. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des membres feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md).  
  
    -   Pour les membres consolidés, la table est STG. \<name> _Consolidated. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des membres consolidés &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Pour déplacer l’emplacement des membres dans les hiérarchies explicites, la table est STG. \<name> _Relationship. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des relations &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Pour obtenir une vue d’ensemble du déplacement de membres dans des hiérarchies explicites, consultez [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Utilisez la valeur du champ **ImportType** pour spécifier que vous créez des membres, que vous désactivez des membres ou que vous supprimez des membres. Pour plus d’informations sur les valeurs, consultez [Table de mise en lots des membres feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) et [Table de mise en lots des membres consolidés &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Pour obtenir une vue d’ensemble de la désactivation et de la suppression de membres, consultez [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l'instance du moteur de base de données pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Pour plus d’informations, consultez [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Importez les données dans les tables de mise en lots à l'aide de l'Assistant Importation et exportation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Pour plus d'informations, consultez [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Chargez les données depuis les tables de mise en lots dans les tables [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , en effectuant une des opérations suivantes :  
  
    -   Exécutez la procédure stockée de mise en lots qui correspond à la table de mise en lots vers laquelle vous voulez déplacer des données.  
  
         Pour obtenir une vue d’ensemble des procédures stockées et des tables de mise en lots intermédiaires, consultez [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Pour plus d’informations sur les paramètres des procédures stockées de mise en lots et un exemple de code, consultez [Procédure stockée de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Utilisez la zone de la fonction **Gestion de l'intégration** de la gestion des données de référence.  
  
         Dans la page **Lots intermédiaires** , sélectionnez le modèle auquel vous ajoutez des données dans la liste déroulante, puis cliquez sur **Démarrer les lots**. L'état du traitement par lots est indiqué dans le champ **État** . Pour plus d’informations sur les états, consultez [États d’importation &#40;Master Data Services&#41;](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Page Lots intermédiaires dans le Gestionnaire des données de référence](../../2014/master-data-services/media/mds-staging-batches.png "Page Lots intermédiaires dans le Gestionnaire des données de référence")  
  
         Le processus de site est démarré à des intervalles déterminés par le paramètre **Intervalle de lot intermédiaire** dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Afficher les erreurs rencontrées lors de la mise en lots. Pour plus d’informations, consultez [afficher les erreurs qui se produisent pendant le processus de site &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md) et les erreurs du processus de site [&#40;Master Data Services ](../../2014/master-data-services/staging-process-errors-master-data-services.md)&#41;.  
  
6.  Validation de données par rapport aux règles d'entreprise  
  
     Dans Master Data Manager, accédez à la zone de la fonction **Explorer** pour votre modèle, puis appliquez des règles d'entreprise pour valider les données. Pour plus d’informations, consultez [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Vous pouvez également utiliser une procédure stockée pour valider les données. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     Quand vous chargez des données à partir des tables de mise en lots, elles ne sont pas validées automatiquement par rapport aux règles d'entreprise. Pour plus d’informations sur la validation et quand elle a lieu, consultez [Validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
