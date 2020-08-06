---
title: Se connecter au serveur (page Propriétés de connexion) — Moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41f2aa3fd5004a371515ee5d8905c7bb73699829
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706931"
---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Se connecter au serveur (page Propriétés de connexion) — Moteur de base de données
  Utilisez cet onglet pour afficher ou spécifier les options de connexion à une instance du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ou d’inscription du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans **Serveurs inscrits**. **Se connecter** et **Options** ne s’affichent dans cette boîte de dialogue que quand vous vous connectez à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. **Tester** et **Enregistrer** s’affichent uniquement dans cette boîte de dialogue lors de l’inscription du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="options"></a>Options  
 **Connecter à la base de données**  
 Dans la liste, sélectionnez une base de données à laquelle se connecter. Si vous sélectionnez **\<default>** , vous serez connecté à la base de données par défaut pour le serveur. Si vous sélectionnez **\<Browse server>** , vous pouvez parcourir le serveur à la recherche de la base de données à laquelle se connecter.  
  
 Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
 Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez la [vue d’ensemble de Azure SQL Database](/azure/sql-database/sql-database-technical-overview).  
  
 **Protocole réseau**  
 Sélectionnez un protocole dans la liste. Les protocoles client disponibles sont ceux que vous avez configurés à l'aide de la configuration du réseau client dans Gestion de l'ordinateur.  
  
 **Taille du paquet réseau**  
 Entrez la taille des paquets à envoyer. La valeur par défaut est 4096 octets.  
  
 **Délai de connexion**  
 Entrez le nombre de secondes d’attente de l’établissement d’une connexion avant expiration du délai d’attente. La valeur par défaut est 15 secondes.  
  
 **Délai d’exécution**  
 Entrez le nombre de secondes que peut prendre l'exécution d'une tâche sur le serveur. La valeur par défaut est égale à zéro seconde, ce qui définit un délai d'attente illimité.  
  
 **Chiffrer la connexion**  
 Force le chiffrement de la connexion.  
  
 **Utiliser une couleur personnalisée**  
 Sélectionnez cette option pour spécifier la couleur d'arrière-plan de la barre d'état dans une fenêtre de l'éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Pour spécifier la couleur, cliquez sur **Sélectionner**. Dans la boîte de dialogue **Couleur** , sélectionnez une couleur prédéfinie dans la grille **Couleurs de base** ou cliquez sur **Définir les couleurs personnalisées** pour définir et utiliser une couleur personnalisée.  
  
-   Quand vous spécifiez une couleur pour une entrée de serveur dans le volet **Explorateur d’objets** , cette couleur est utilisée quand vous ouvrez une fenêtre de l’éditeur de requête. Pour ouvrir une fenêtre de l’éditeur de requête, cliquez avec le bouton droit sur l’entrée de serveur et sélectionnez **Nouvelle requête**; ou bien, quand le volet **Explorateur d’objets** est actif et que le focus est sur ce serveur, cliquez sur **Nouvelle requête** dans la barre d’outils.  
  
-   Quand vous spécifiez une couleur pour une entrée de serveur dans le volet **Serveurs inscrits** , cette couleur est utilisée quand vous ouvrez une fenêtre de l’éditeur de requête. Pour ouvrir une fenêtre de l’éditeur de requête, cliquez avec le bouton droit sur l’entrée de serveur et sélectionnez **Nouvelle requête**; ou bien, quand le volet **Serveurs inscrits** est actif et que le focus est sur ce serveur, cliquez sur **Nouvelle requête** dans la barre d’outils.  
  
-   Dans le menu **Fichier** , quand vous cliquez sur **Nouveau** puis sur **Requête de moteur de base de données**, la couleur que vous spécifiez dans la boîte de dialogue **Se connecter au serveur** s’applique à cette fenêtre de l’éditeur de requête.  
  
 **Réinitialiser tout**  
 Remplace toutes les valeurs des propriétés de connexion spécifiées manuellement par les valeurs par défaut.  
  
 **Connexion**  
 Tente d'établir une connexion à l'aide des valeurs indiquées.  
  
 **Options**  
 Cliquez sur cette option pour modifier l’apparence de la boîte de dialogue en masquant les options de connexion serveur supplémentaires, comme la mémorisation du mot de passe.  
  
 **Test**  
 Quand vous inscrivez [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans **Serveurs inscrits**, cliquez ici pour tester la connexion.  
  
 **Save**  
 Enregistre les paramètres dans **Serveurs inscrits**.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de connexion (boîte de dialogue)](../../database-engine/connection-properties-dialog-box.md)  
  
  
