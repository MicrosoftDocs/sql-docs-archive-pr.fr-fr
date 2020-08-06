---
title: Accéder aux données pour les opérations DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 515b087a8d16e44314d1a21d3dfbd6f13c767f5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701988"
---
# <a name="access-data-for-the-dqs-operations"></a>Accéder aux données pour les opérations DQS
  Pour utiliser vos données sources pour les opérations [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS), et exporter vos données traitées, vous pouvez effectuer l'une des opérations suivantes :  
  
-   Copiez vos données sources dans une table/vue dans la base de données DQS_STAGING_DATA, puis utilisez-les pour les opérations DQS. Vous pouvez également exporter les données traitées dans une nouvelle table de la base de données DQS_STAGING_DATA. Pour cela, votre compte d'utilisateur Windows doit être accordé l'accès en lecture/écriture à la base de données de DQS_STAGING_DATA.  
  
-   Utilisez votre propre base de données comme données sources pour les opérations DQS, et destination pour exporter les données traitées. Pour cela, vérifiez que votre base de données est dans la même instance SQL Server que les bases de données Data Quality Server. Sinon, la base de données ne sera pas disponible dans Data Quality Client pour les opérations DQS. De plus, votre compte d'utilisateur Windows doit avoir accès à la base de données DQS_STAGING_DATA pour exporter les résultats correspondants, car ceux-ci sont exportés en deux phases : en premier lieu, les résultats de correspondance sont exportés vers des tables temporaires dans la base de données DQS_STAGING_DATA, puis déplacés vers la table de votre base de données de destination.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez avoir terminé l'installation du [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe. Pour plus d’informations, consultez [Exécuter DQSInstaller.exe pour terminer l’installation du serveur DQS](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe approprié (tel que le securityadmin, le serveradmin, ou le sysadmin) dans l'instance du moteur de base de données à accorder/modifier l'accès à la connexion SQL sur les bases de données.  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a>Pour accorder l'accès en lecture/écriture à un utilisateur sur la base de données DQS_STAGING_DATA  
  
1.  Démarrez Microsoft SQL Server Management Studio.  
  
2.  Dans Microsoft SQL Server Management Studio, développez votre instance SQL Server, puis développez **Sécurité**et ensuite **Connexions**.  
  
3.  Cliquez avec le bouton droit sur une connexion SQL, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de la connexion** , cliquez sur la page de **Mappage de l'utilisateur** dans le volet gauche.  
  
5.  Dans le volet droit, cochez la case sous la colonne **Mappage** de la base de données **DQS_STAGING_DATA** , puis sélectionnez les rôles suivants dans le volet **Appartenance au rôle de base de données : DQS_STAGING_DATA** :  
  
    -   **db_datareader**: lire des données depuis des tables/vues.  
  
    -   **db_datawriter**: ajouter, supprimer ou modifier des données dans des tables.  
  
    -   **db_ddladmin**: créer, modifier ou supprimer des tables/vues.  
  
6.  Dans la boîte de dialogue **Propriétés de la connexion** , cliquez sur **OK** pour appliquer les modifications.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Essayez effectuer des opérations DQS qui accèdent à la base de données en tant que source de données pour l'opération DQS, puis exportez les données traitées vers la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Data Quality Services](install-data-quality-services.md)  
  
  
