---
title: Instance de serveur principal (Configurer l’Assistant Sécurité de mise en miroir de bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701838"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a>Instance de serveur principal (Configurer l'Assistant Sécurité de mise en miroir de bases de données)
  Cette page vous permet de spécifier des informations sur l'instance de serveur de la base de données principal. La base de données principale est la copie de la base de données qui commence la session de mise en miroir. Une fois que la session a commencé, la base de données principale est la copie de la base de données qui accepte les modifications d'utilisateur. (Lorsqu'un basculement a lieu, les rôles principal et de mise en miroir sont échangés ; par conséquent, la base de données principale initiale peut ne pas demeurer la base de données principale.)  
  
 **Pour configurer la mise en miroir de bases de données à l'aide de SQL Server Management Studio**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **Instance de serveur principal**  
 Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , la mise en miroir de base de données est toujours configurée à partir du serveur principal ; c'est pourquoi l'instance de serveur active est toujours l'instance de serveur principal.  
  
 **Port de l’écouteur**  
 Le comportement de cette option varie comme suit selon qu'il existe ou non un point de terminaison de mise en miroir pour cette instance du serveur :  
  
-   Si le port d’écoute n’existe pas pour cette instance de serveur, le numéro de port 5022 est affiché dans la zone de texte **Port** . Vous pouvez utiliser n'importe quel numéro de port disponible, tel que 7022.  
  
-   Si le point de terminaison de mise en miroir existe déjà, son numéro de port est affiché. Si vous devez modifier le port, utilisez une commande ALTER ENDPOINT. Pour plus d’informations, consultez [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
> [!NOTE]  
>  Un numéro de port est obligatoire.  
  
 **Nom du point de terminaison**  
 Si le point de terminaison de mise en miroir existe pour cette instance du serveur, le nom du point de terminaison est affiché ici. Si le point de terminaison n'existe pas, vous pouvez spécifier son nom.  
  
 **Chiffrer les données envoyées via ce point de terminaison**  
 Par défaut, le chiffrement est activé. Lorsqu'il est activé, il devient obligatoire (et non simplement pris en charge) et il utilise les valeurs par défaut pour toutes les options de chiffrement. Pour plus d’informations, consultez [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Pour désactiver le chiffrement, désactivez la case à cocher. Pour réactiver le chiffrement, activez la case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
