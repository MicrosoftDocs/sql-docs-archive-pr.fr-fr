---
title: Déployer à partir de SQL Server Data Tools (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8bc8008e7c79e1652b54b21e6afb116301d1700b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610874"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a>Déployer à partir de SQL Server Data Tools (SSAS Tabulaire)
  Utilisez les tâches de cette rubrique pour déployer une solution de modèle tabulaire à l'aide de la commande Déployer de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Sections de cette rubrique :  
  
-   [Configurer les propriétés Options de déploiement et Serveur de déploiement](#bkmk_deploy)  
  
-   [Déployer une solution de modèle tabulaire](#bkmk_deploy_proc)  
  
-   [État du déploiement](#bkmk_deploy_status)  
  
##  <a name="configure-deployment-options-and-deployment-server-properties"></a><a name="bkmk_deploy"></a>Configurer les propriétés options de déploiement et serveur de déploiement  
 Avant de déployer votre solution de modèle tabulaire, vous devez spécifier les propriétés Options de déploiement et Serveur de déploiement. Pour plus d’informations sur les paramètres et les propriétés de déploiement, consultez [Déploiement d’une solution de modèle tabulaire &#40;SSAS Tabulaire&#41;](tabular-model-solution-deployment-ssas-tabular.md).  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a>Pour configurer les propriétés Options de déploiement et Serveur de déploiement  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis sélectionnez **Propriétés**.  
  
2.  Dans la boîte de dialogue ** \<project name> Propriétés** , dans **options de déploiement**, spécifiez les paramètres de propriété s’ils sont différents des paramètres par défaut.  
  
    > [!NOTE]  
    >  Pour les modèles en mode mis en cache, **Mode de requête** a toujours la valeur **In-Memory**.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas spécifier de **Paramètres d’emprunt d’identité** pour les modèles en mode DirectQuery.  
  
3.  Dans **Serveur de déploiement**, spécifiez les paramètres de propriété **Serveur** (nom), **Édition**, **Base de données** (nom) et **Nom du cube** , s’ils sont différents des paramètres par défaut, puis cliquez sur **OK**.  
  
> [!NOTE]  
>  Vous pouvez également spécifier le paramètre de propriété Serveur de déploiement par défaut afin que tous les nouveaux projets que vous créez soient automatiquement déployés sur le serveur spécifié. Pour plus d’informations, consultez [Configurer les propriétés par défaut de modélisation des données et de déploiement &#40;SSAS Tabulaire&#41;](properties-ssas-tabular.md).  
  
##  <a name="deploy-a-tabular-model-solution"></a><a name="bkmk_deploy_proc"></a>Déployer une solution de modèle tabulaire  
  
#### <a name="to-deploy-a-tabular-model-solution"></a>Pour déployer une solution de modèle tabulaire  
  
-   Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , dans le menu **générer** , cliquez **sur \<project name> déployer **.  
  
     La boîte de dialogue **Déployer** apparaît et indique l’état du déploiement des métadonnées et du traitement (sauf si la propriété Option de traitement a la valeur Ne pas traiter) de chaque table incluse dans le modèle. Lorsque le déploiement est terminé, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour vous connecter à l'instance d'Analysis Services et vérifier que le nouvel objet de base de données model a été créé ou utilisez une application de création de rapports cliente pour vous connecter au modèle déployé.  
  
##  <a name="deploy-status"></a><a name="bkmk_deploy_status"></a>État du déploiement  
 La boîte de dialogue **Déployer** vous permet de surveiller la progression d'une opération de déploiement. Une opération de déploiement peut également être arrêtée.  
  
 **État**  
 Indique si l'opération de déploiement a abouti.  
  
 **Détails**  
 Répertorie les éléments de métadonnées déployés, l'état pour chaque élément de métadonnées, et affiche un message en cas de problèmes.  
  
 **Arrêter le déploiement**  
 Cliquez pour arrêter l'opération de déploiement. Cette option est utile si l'opération de déploiement prend trop de temps ou génère trop d'erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de solutions de modèles tabulaires &#40;&#41;SSAS tabulaire](tabular-model-solution-deployment-ssas-tabular.md)   
 [Configurer les propriétés par défaut de modélisation des données et de déploiement &#40;SSAS Tabulaire&#41;](properties-ssas-tabular.md)  
  
  
