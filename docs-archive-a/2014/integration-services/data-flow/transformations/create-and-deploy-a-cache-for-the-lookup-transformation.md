---
title: Créer et déployer un cache pour la transformation de recherche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33b00b84f1f1448c2ee80882aedc3a330ba0a5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600150"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a>Créer et déployer un cache pour la transformation de recherche
  Vous pouvez créer et déployer un fichier cache (.caw) pour la transformation de recherche. Le dataset de référence est stocké dans le fichier cache.  
  
 La transformation de recherche effectue des recherches en joignant les données des colonnes d’entrée d’une source de données connectée aux colonnes du dataset de référence.  
  
 Vous créez un fichier cache en utilisant un gestionnaire de connexions du cache et une transformation du cache. Pour plus d’informations, consultez [Gestionnaire de connexions du cache](../../connection-manager/cache-connection-manager.md) et [Transformation du cache](cache-transform.md).  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Transformation de recherche](lookup-transformation.md).  
  
### <a name="to-create-a-cache-file"></a>Pour créer un fichier cache  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] qui contient le package souhaité, puis ouvrez le package.  
  
2.  Sous l’onglet **Flux de contrôle** , ajoutez une tâche de flux de données.  
  
3.  Sous l’onglet **Flux de données** , ajoutez une transformation du cache au flux de données, puis connectez la transformation à une source de données.  
  
     Configurez la source de données selon vos besoins.  
  
4.  Double-cliquez sur la transformation du cache puis, dans **l’Éditeur de transformation du cache**, dans la page **Gestionnaire de connexions** , cliquez sur **Nouveau** pour créer un gestionnaire de connexions du cache.  
  
5.  Dans **l’Éditeur du gestionnaire de connexions du cache**, sous l’onglet **Général** , configurez le gestionnaire de connexions du cache pour enregistrer le cache en sélectionnant les options suivantes :  
  
    1.  Sélectionnez **Utiliser le cache de fichier**.  
  
    2.  Dans la zone **Nom de fichier**, entrez le chemin du fichier.  
  
     Le système crée le fichier lorsque vous exécutez le package.  
  
    > [!NOTE]  
    >  Le niveau de protection du package ne s'applique pas au fichier cache. Si le fichier cache contient des informations sensibles, utilisez une liste de contrôle d'accès (ACL) pour restreindre l'accès à l'emplacement ou au dossier dans lequel vous stockez le fichier. Vous devez autoriser l'accès à certains comptes uniquement. Pour plus d’informations, consultez [Accéder aux fichiers utilisés par des packages](../../access-to-files-used-by-packages.md).  
  
6.  Cliquez sur l’onglet **Colonnes** , puis spécifiez quelles colonnes sont les colonnes d’index en utilisant l’option **Position d’index** .  
  
     Pour les colonnes qui ne sont pas des index, la position d'index est 0. Pour les colonnes d'index, la position d'index est un nombre séquentiel, positif.  
  
    > [!NOTE]  
    >  Lorsque la transformation de recherche est configurée pour utiliser un gestionnaire de connexions du cache, seules les colonnes d'index dans le dataset de référence peuvent être mappées avec des colonnes d'entrée. En outre, toutes les colonnes d’index doivent être mappées.  
  
     Pour plus d’informations, consultez [Éditeur du gestionnaire de connexions du cache](../../cache-connection-manager-editor.md).  
  
7.  Configurez la transformation du cache selon vos besoins.  
  
     Pour plus d’informations, consultez [Éditeur de transformation du cache &#40;page Gestionnaire de connexions&#41;](../../cache-transformation-editor-connection-manager-page.md) et [Éditeur de transformation du cache &#40;page Mappages&#41;](../../cache-transformation-editor-mappings-page.md).  
  
8.  Exécutez le package.  
  
### <a name="to-deploy-a-cache-file"></a>Pour déployer un fichier cache  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] qui contient le package souhaité, puis ouvrez le package.  
  
2.  Vous pouvez éventuellement créer une configuration de package. Pour plus d’informations, consultez [Créer des configurations de package](../../create-package-configurations.md).  
  
3.  Ajoutez le fichier cache au projet en procédant comme suit :  
  
    1.  Dans l'Explorateur de solutions, sélectionnez le projet que vous avez ouvert à l'étape 1.  
  
    2.  Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.  
  
    3.  Sélectionnez le fichier de cache, puis cliquez sur **Ajouter**.  
  
     Le fichier apparaît dans le dossier **Divers** de l’Explorateur de solutions.  
  
4.  Configurez le projet afin de créer un utilitaire de déploiement, puis créez le projet. Pour plus d’informations, consultez [Créer un utilitaire de déploiement](../../create-a-deployment-utility.md).  
  
     Un fichier manifeste, \<*project name*>.SSISDeploymentManifest.xml, est créé. Il liste les divers fichiers du projet, les packages et les configurations des packages.  
  
5.  Déployez le package dans le système de fichiers. Pour plus d’informations, consultez [Déployer des packages à l’aide de l’utilitaire de déploiement](../../deploy-packages-by-using-the-deployment-utility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un utilitaire de déploiement](../../create-a-deployment-utility.md)  
  
  
