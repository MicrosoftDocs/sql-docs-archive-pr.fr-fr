---
title: Boîte de dialogue nouvelle base de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.newdatabase.f1
ms.assetid: ddc7804b-acb0-4ae4-a88f-e8cdf704c341
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07eeee6136965671b000923dc3f240de06ce0bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605789"
---
# <a name="new-database-dialog-box-analysis-services"></a>Boîte de dialogue Nouvelle base de données (Analysis Services)
  Utilisez la boîte de dialogue **Nouvelle base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour créer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vide. Pour afficher la boîte de dialogue **Nouvelle base de données** , cliquez avec le bouton droit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans **l’Explorateur d’objets** , puis sélectionnez **Nouvelle base de données**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom de la base de données**|Tapez le nom de la nouvelle base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Utiliser un nom d'utilisateur et un mot de passe spécifiques**|Sélectionnez cette option pour que la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d'identification de sécurité d'un compte utilisateur spécifié. Les informations d’identification spécifiées sont utilisées pour le traitement, les requêtes ROLAP, les liaisons hors-ligne, les cubes locaux, les modèles d’exploration, les partitions distantes, les objets liés et la synchronisation entre la cible et la source. Cependant, pour les instructions DMX OPENQUERY, les informations d'identification de l'utilsateur courant sont utilisées.|  
|**Nom d'utilisateur**|Tapez le domaine et le nom du compte d’utilisateur à utiliser par la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionnée. Utilisez le format suivant :<br /><br /> *\<Domain name>* **\\** *\<User account name>*<br /><br /> Remarque : Cette option est activée uniquement si vous avez sélectionné **Utiliser un nom d’utilisateur et un mot de passe spécifiques** .|  
|**Mot de passe**|Tapez le mot de passe du compte d’utilisateur spécifié dans **Nom d’utilisateur**.|  
|**Utiliser le compte de service**|Sélectionnez cette option pour que la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d’identification de sécurité associées au service [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère la base de données. Les informations d'identification du compte de service sont utilisées pour le traitement, les requêtes ROLAP, les partitions distantes, les objets liés et la synchronisation entre la cible et la source. Pour les instructions DMX OPENQUERY, les cubes locaux et les modèles d'exploration, les informations d'identification de l'utilisateur courant sont utilisées. Cette option n'est pas prise en charge pour les liaisons hors ligne.|  
|**Utiliser les informations d'identification de l'utilisateur actuel**|Sélectionnez cette option afin que la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d'identification de sécurité de l'utilisateur courant pour les liaisons hors ligne, les instructions DMX OPENQUERY, les cubes locaux et les modèles d'exploration. Cette option n'est pas prise en charge pour le traitement, les requêtes ROLAP, les partitions distantes, les objets liés et la synchronisation entre la cible et la source.|  
|**Par défaut**|Sélectionnez cette option pour utiliser les informations d’identification du compte d’utilisateur par défaut de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette option utilise le paramètre par défaut de la base de données pour traiter les objets, synchroniser les serveurs et exécuter les instructions **Open Query** d’exploration des données. Pour plus d’informations sur la spécification des paramètres par défaut au niveau de la base de données, consultez [Définir les propriétés de base de données multidimensionnelle &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md).<br /><br /> Par défaut, la `DataSourceImpersonationInfo` propriété de base de données est définie pour **utiliser le compte de service**. Quelle que soit la valeur de la propriété `DataSourceImpersonationInfo`, les informations d'identification de l'utilisateur en cours sont utilisées pour les liaisons hors ligne, les requêtes ROLAP, les cubes locaux et les modèles d'exploration de données.|  
|**Description**|Tapez la description de la nouvelle base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
