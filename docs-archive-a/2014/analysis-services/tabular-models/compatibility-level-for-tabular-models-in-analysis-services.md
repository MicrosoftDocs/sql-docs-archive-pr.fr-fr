---
title: Niveau de compatibilité (SSAS tabulaire SP1) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2853cd5509b66dbfaadd78c578b9676399e81977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708692"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a>Niveau de compatibilité (SSAS Tabulaire SP1)
  Vous pouvez spécifier le *niveau de compatibilité* lors de la création de projets de modèles tabulaires, lors de la mise à niveau de projets de modèles tabulaires existants, lors de la mise à niveau de bases de données de modèles tabulaires déployées ou lors de l’importation de classeurs PowerPivot  
  
## <a name="compatibility-level"></a>Niveau de compatibilité  
 Il est courant d'installer les nouvelles versions et les Service Packs sur des ordinateurs de développement et de test avant de les installer sur des ordinateurs de production. Dans ce cas, il est important de comprendre le niveau de compatibilité des paramètres pour les nouveaux projets de modèles tabulaires, ainsi que pour ceux qui ont déjà été déployés dans un environnement de production.  
  
 Une instance [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services prend en charge les niveaux de compatibilité suivant (version de base de données) :  
  
-   SQL Server 2012 (1100)  
  
-   SQL Server 2012 SP1 (1103)  
  
-   SQL Server 2014 (1103)  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a>Définir le niveau de compatibilité lors de la création d'un projet de modèle tabulaire  
 Lorsque vous créez un nouveau projet de modèle tabulaire dans SQL Server Data Tools (SSDT), dans la boîte de dialogue **Options du nouveau projet tabulaire** , vous pouvez spécifier le niveau de compatibilité. Vous avez le choix entre créer un projet à déployer dans une instance [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou version ultérieure Analysis Services ou dans une instance SQL Server 2012 Analysis Services (sans le Service Pack 1).  
  
 Vous pouvez également spécifier un niveau de compatibilité par défaut en sélectionnant l'option **Ne plus afficher ce message** . Tous les projets suivants utiliseront le niveau de compatibilité que vous avez spécifié. Vous pouvez modifier le niveau de compatibilité par défaut dans SSDT sous Options.  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a>Mettre à niveau un projet de modèle tabulaire existant vers le niveau de compatibilité 1103  
 Vous pouvez mettre à niveau un projet de modèle tabulaire créé dans SSDT avant d’installer [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou une version ultérieure pour qu’il soit compatible avec la version 1103 de la base de données à l’aide de la propriété **niveau de compatibilité** dans la fenêtre **Propriétés** du modèle. Pour mettre à niveau un projet de modèle tabulaire, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou version ultérieure doit être installé sur l'ordinateur sur lequel est installé SSDT et [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou version ultérieure doit également être installé sur l'instance Analysis Services sur laquelle réside la base de données d'espace de travail. Vous ne pouvez pas mettre à niveau vers une version antérieure.  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a>Mettre à niveau une base de données model tabulaire déployée vers le niveau de compatibilité 1103  
 Vous pouvez mettre à niveau une base de données model tabulaire déployée existante vers la version de base de données 1103 compatible dans SQL Server Management Studio (SSMS) à l’aide de la propriété **niveau de compatibilité** dans **Propriétés de la base de données**. Pour mettre à niveau, [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ou version ultérieure doit être installé sur l'ordinateur sur lequel est installée l'instance SQL Server Analysis Services. Vous ne pouvez pas mettre à niveau une base de données model tabulaire déployée vers une version antérieure.  
  
### <a name="import-from-powerpivot"></a>Importer à partir de PowerPivot  
 Lorsque vous créez un projet de modèle tabulaire par importation à partir de PowerPivot, spécifiez si vous souhaitez mettre à niveau le niveau de compatibilité vers le niveau de compatibilité par défaut (s'il a été configuré précédemment dans SSDT) ou conserver le niveau de compatibilité déjà spécifié dans le classeur PowerPivot.  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a>Vérifier le niveau de compatibilité d'une base de données model tabulaire dans SSMS  
 Vous pouvez vérifier le niveau de compatibilité d’une base de données model tabulaire dans SSMS en consultant la propriété **niveau de compatibilité** (nouveauté de [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ) dans **Propriétés de la base de données**.  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a>Vérifier le niveau de compatibilité pris en charge pour une instance Analysis Services dans SSMS  
 Vous pouvez vérifier le niveau de compatibilité pris en charge dans SSMS en consultant la propriété **niveau de compatibilité pris en charge** dans la page **informations** (nouveauté de [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ) dans **Propriétés de Analysis Services**. Un niveau de compatibilité 1103 pris en charge indique que SQL Server SP1 ou version ultérieure est installé. Le niveau de compatibilité pris en charge ne peut pas être modifié.  
  
  
