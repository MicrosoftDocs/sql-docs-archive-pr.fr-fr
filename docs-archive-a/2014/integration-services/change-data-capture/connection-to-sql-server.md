---
title: Connexion à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6639118b3bd531e5cece8899eb0d68e00e566186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602267"
---
# <a name="connection-to-sql-server"></a>Connexion à SQL Server
  Quand une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner** ) à la base de données MSXDBCDC tente de créer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui dispose d’une autorisation d’accès en écriture à la base de données MSXDBCDC (tel est notamment le cas du rôle de base de données **db_owner** ) pour créer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
### <a name="server-name"></a>Nom du serveur  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Authentication  
 Sélectionnez l’un des suivants :  
  
-   Authentification Windows  
  
-   **Authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper **l’identifiant** et le **mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
### <a name="options"></a>Options  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) pendant lequel le programme attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de générer une erreur de délai d’expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) pendant lequel le programme attend la fin d’exécution d’une commande SQL avant de générer une erreur de délai d’expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: Sélectionnez **Chiffrer la connexion** pour garantir que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] établie est chiffrée afin d’assurer la protection des données.  
  
-   **Avancé**: Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server nécessaires pour le service CDC](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
