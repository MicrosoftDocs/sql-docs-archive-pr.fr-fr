---
title: À propos du Moteur de base de données SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93e3d7a749fe6be47cc84d43509a6f378476b2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701544"
---
# <a name="about-the-sql-server-database-engine"></a>À propos du moteur de base de données SQL Server
  Le composant [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est le service de base pour le stockage, le traitement et la protection des données. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] fournit un accès contrôlé et un traitement transactionnel rapide qui répondent aux exigences des applications les plus gourmandes en termes de données dans votre entreprise.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge jusqu’à 50 instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur un seul ordinateur. Pour créer une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation par défaut, consultez [installer SQL Server 2014 à partir de l’assistant installation &#40;&#41;d' ](install-sql-server-from-the-installation-wizard-setup.md)installation.  
  
 **Important** Pour des installations locales, vous devez exécuter le programme d’installation en tant qu’administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.  
  
 Les fonctionnalités suivantes sont installées quand vous sélectionnez **Moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** dans la page Composants à installer de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Réplication (composant facultatif)  
  
-   Recherche en texte intégral (composant facultatif)  
  
-   Data Quality Services est un composant facultatif  
  
    > [!NOTE]  
    >  Dans cette version, le fait de cocher la case **Data Quality Services** au moment de l’installation n’installe pas le serveur Data Quality Services (DQS). Vous devrez procéder à des étapes supplémentaires après l'installation pour installer le serveur DQS. Pour plus d’informations, consultez [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 Les fonctionnalités supplémentaires suivantes sont des options pour un grand nombre de scénarios utilisateur classiques :  
  
-   Data Quality Client  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Composants de connectivité  
  
-   Modèles de programmation  
  
-   Outils d'administration  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Composants de documentation  
  
> [!NOTE]  
>  Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour installer les exemples de bases de données et les exemples de code, consultez le [site web CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Éditions et composants de SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Effectuez une mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
