---
title: Ajouter ou remplacer un témoin de mise en miroir de base de données (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dd14ace23956ceef114f1f032b5d4db5febcec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603036"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a>Ajouter ou remplacer un témoin de mise en miroir de base de données (SQL Server Management Studio)
  Si les points de terminaison de mise en miroir de base de données utilisent l'authentification Windows, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour ajouter ou remplacer un témoin. Lorsqu'un témoin est ajouté dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , la session passe en mode haute sécurité avec basculement automatique.  
  
> [!NOTE]  
>  Nous vous recommandons vivement de placer le témoin sur un ordinateur distinct de celui des partenaires. Le compte de service utilisé par le témoin doit être dans le même domaine que les comptes de service utilisés par les instances de serveur principal et miroir, ou il doit être situé dans un domaine approuvé.  
  
### <a name="to-add-or-replace-a-witness"></a>Pour ajouter ou remplacer un témoin  
  
1.  Après vous être connecté à l'instance du serveur principal, dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**, puis sélectionnez la base de données principale de la session dans laquelle vous ajoutez ou remplacez un témoin.  
  
3.  Cliquez avec le bouton droit sur la base de données, sélectionnez **Tâches**, puis cliquez sur **Miroir**. La page **Mise en miroir** de la boîte de dialogue **Propriétés de la base de données** s'affiche.  
  
4.  Cliquez sur **Configurer la sécurité**.  
  
5.  Si l’écran d’accueil **Configurer l’Assistant Sécurité de mise en miroir de bases de données** s’affiche, cliquez sur **Suivant**.  
  
6.  Dans la boîte de dialogue **Inclure un serveur témoin** , cliquez sur **Oui**, puis sur **Suivant**.  
  
7.  Dans la boîte de dialogue **Choisir les serveurs à configurer** , la case **Instance de serveur témoin** est automatiquement cochée. Cliquez sur **Suivant**.  
  
8.  Dans la boîte de dialogue **Instance de serveur principal** , conservez le port et le point de terminaison existants. Cliquez sur **Suivant**.  
  
9. Dans la boîte de dialogue **Instance de serveur témoin** , cliquez sur **Se connecter**.  
  
10. Dans la boîte de dialogue **Se connecter au serveur** , indiquez l’instance du serveur témoin dans le champ **Nom du serveur** et utilisez l’authentification Windows (valeur par défaut). Cliquez sur **Connecter**.  
  
11. Une fois qu’une connexion a été établie, le port d’écoute et le point de terminaison de mise en miroir de bases de données de l’instance du serveur témoin s’affichent dans la boîte de dialogue **Instance de serveur témoin** . Cliquez sur **Suivant**.  
  
12. La boîte de dialogue **Comptes de service** contient les champs des comptes de service de domaine des instances du serveur témoin, miroir et principal.  
  
    -   Si toutes les instances du serveur utilisent le même compte de service, laissez les champs vides.  
  
    -   Si l’instance du serveur témoin utilise un compte de service différent de celui des partenaires, entrez le nom du compte dans les champs **Principal**, **Miroir**et **Témoin** :  
  
         *NOM_DOMAINE* **\\** *nom_utilisateur*  
  
         Le nom de domaine doit être indiqué en majuscules.  
  
     Cliquez sur **Suivant**.  
  
13. Dans l’écran récapitulatif **Terminer l’Assistant** , vérifiez éventuellement la configuration du témoin, puis cliquez sur **Terminer**.  
  
14. Une fois l’Assistant exécuté, la boîte de dialogue **Propriétés de la base de données** s’affiche à nouveau, et l’adresse réseau du serveur du témoin apparaît désormais dans le champ **Témoin** . En outre, l’option **Mode haute sécurité avec basculement automatique (synchrone)** , qui est nécessaire avec un témoin, est automatiquement sélectionnée.  
  
     Pour activer le témoin et faire passer la session en mode haute sécurité avec basculement automatique, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Témoin de mise en miroir de base de données](database-mirroring-witness.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)   
 [Témoin de mise en miroir de base de données](database-mirroring-witness.md)  
  
  
