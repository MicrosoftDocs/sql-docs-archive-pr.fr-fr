---
title: Vérifier et s’abonner à la stratégie Nom financier | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2bfe6f463d03fe8b95f000dc6f34dc0718a7729f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600841"
---
# <a name="subscribe-to-and-check-the-finance-name-policy"></a>Vérifier et s'abonner à la stratégie Nom financier
  Dans cette tâche, vous allez configurer la base de données Finance de manière à l'abonner à la catégorie de stratégies Finance. Ensuite, vous allez tester la stratégie Nom financier.  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a>Pour abonner la base de données à la catégorie de stratégies Finance  
  
1.  Dans l’Explorateur d’objets, développez **bases de données**, cliquez avec le bouton droit `Finance` , pointez sur **stratégies**, puis cliquez sur **catégories**.  
  
2.  Activez la case à cocher **abonné** pour la `Finance` catégorie.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a>Pour tester l'application de la stratégie Nom financier  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une fenêtre de requête. Exécutez les instructions suivantes qui essaient de créer une table qui enfreint la stratégie **Nom financier** . La table enfreint la stratégie car le nom de table ne commence pas par les lettres **fintbl**.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     Remarquez que la stratégie empêche la création de la table et retourne un message d'information qui indique le nom de la stratégie.  
  
2.  Pour fournir un nom valide, modifiez le code comme suit et réexécutez l'instruction.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
     Cette fois-ci, la table est créée.  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a>Pour appliquer la stratégie à tout le serveur  
  
1.  Actuellement, seule la base de données Finance est abonnée à la catégorie de stratégie Finance. Dans de nombreux cas, il est plus facile d'appliquer la catégorie de stratégie à l'ensemble du serveur. Dans l’Explorateur d’objets, développez **Gestion**, cliquez avec le bouton droit sur **Gestion de la stratégie**, puis cliquez sur **Gérer les catégories**.  
  
2.  Dans la boîte de dialogue **Administration des catégories de stratégie** , recherchez la catégorie Finance et cochez la case **Abonnements à la base de données autorisée** pour la catégorie Finance.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Désormais, la catégorie Finance s’applique à toutes les bases de données, mais la condition que vous avez créée restreint la stratégie Nom financier à la base de données Finance. Cela démontre la manière dont vous pouvez utiliser des combinaisons de conditions complexes pour cibler des stratégies pour une application correcte sur de nombreux serveurs.  
  
## <a name="summary"></a>Récapitulatif  
 Ce didacticiel vous a montré comment créer des conditions, des stratégies et des groupes de stratégies de la Gestion basée sur des stratégies et comment appliquer des filtres et vérifier la conformité des cibles de la Gestion basée sur des stratégies.  
  
## <a name="next"></a>Suivant  
 Ce didacticiel est terminé. Pour revenir au début, cliquez sur [Didacticiel : Administration de serveurs à l’aide de la Gestion basée sur des stratégies](tutorial-administering-servers-by-using-policy-based-management.md).  
  
 Pour obtenir la liste des didacticiels, consultez [les didacticiels pour SQL Server 2014](../../tutorials/tutorials-for-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](administer-servers-by-using-policy-based-management.md)  
  
  
