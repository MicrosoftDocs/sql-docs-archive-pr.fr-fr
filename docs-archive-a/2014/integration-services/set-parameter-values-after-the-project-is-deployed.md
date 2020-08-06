---
title: Définir les valeurs des paramètres après le déploiement du projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709752"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Définir des valeurs de paramètres après le déploiement du projet
  L'Assistant Déploiement vous permet de définir des valeurs de paramètre par défaut du serveur lorsque vous déployez votre projet dans le catalogue. Une fois votre projet dans le catalogue, vous pouvez utiliser l'Explorateur d'objets SQL Server Management Studio (SSMS) ou Transact-SQL pour définir les valeurs par défaut du serveur.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Pour définir les valeurs par défaut du serveur avec l'Explorateur d'objets SSMS :  
  
1.  Sélectionnez le projet sous le nœud **Integration Services**, puis cliquez dessus avec le bouton droit.  
  
2.  Cliquez sur **Propriétés** pour ouvrir la fenêtre de dialogue **Propriétés du projet** .  
  
3.  Ouvrez la page des paramètres en cliquant sur **Paramètres** sous **Sélectionner une page**.  
  
4.  Sélectionnez le paramètre souhaité dans la liste **Paramètres** . Remarque : la colonne **Conteneur** permet de faire la distinction entre les paramètres du projet et les paramètres du package.  
  
5.  Dans la colonne **Valeur** , spécifiez la valeur de paramètre du serveur par défaut souhaitée.  
  
 Pour définir les paramètres par défaut du serveur avec Transact-SQL, utilisez la procédure stockée [catalog.set_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Pour afficher les valeurs par défaut actuelles du serveur, interrogez la vue [catalog.object_parameters &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Pour effacer une valeur par défaut du serveur, utilisez la procédure stockée [catalog.clear_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de&#41; Integration Services &#40;SSIS](integration-services-ssis-package-and-project-parameters.md)  
  
  
