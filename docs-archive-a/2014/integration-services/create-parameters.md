---
title: Créer des paramètres | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602239"
---
# <a name="create-parameters"></a>Créer des paramètres
  Vous pouvez utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer les paramètres de projet et de package. Les procédures suivantes fournissent des instructions pas-à-pas pour créer les paramètres de package/projet.  
  
> [!NOTE]  
>  Si vous convertissez un projet que vous avez créé à l'aide d'une version antérieure de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en modèle de déploiement de projet, vous pouvez utiliser l' **Assistant Conversion de projet Integration Services** pour créer les paramètres en fonction des configurations. Pour plus d’informations, consultez [Déployer des projets sur le serveur Integration Services](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
### <a name="to-create-package-parameters"></a>Pour créer les paramètres de package  
  
1.  Ouvrez le package dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], puis cliquez sur l'onglet **Paramètres** dans le Concepteur SSIS.  
  
     ![Onglet Paramètres de package](media/denali-package-parameters.gif "Onglet Paramètres de package")  
  
2.  Cliquez sur le bouton **Ajouter un paramètre** de la barre d'outils.  
  
     ![Bouton Ajouter une barre d’outils](media/denali-parameter-add.gif "Bouton de barre d’outils Ajouter")  
  
3.  Entrez les valeurs des propriétés **Nom**, **Type de données**, **Valeur**, **Sensible**et **Requis** dans la liste elle-même ou dans la fenêtre **Propriétés** . Le tableau suivant décrit ces propriétés.  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |Nom|Nom du paramètre.|  
    |Type de données|Type de données du paramètre.|  
    |Valeur par défaut|Valeur par défaut du paramètre affecté au moment de la conception. Cette valeur est aussi appelée « valeur de conception par défaut ».|  
    |Sensible|Les valeurs de paramètre sensibles sont chiffrées dans le catalogue et apparaissent sous la forme d'une valeur Null lorsqu'elles sont affichées avec Transact-SQL ou SQL Server Management Studio.|  
    |Obligatoire|Nécessite qu'une valeur, autre que la valeur de conception par défaut, soit spécifiée pour que le package puisse s'exécuter.|  
    |Description|Pour faciliter la maintenance, description du paramètre. Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], définissez la description des paramètres dans la fenêtre Propriétés de Visual Studio lorsque le paramètre est sélectionné dans la fenêtre des paramètres applicables.|  
  
    > [!NOTE]  
    >  Lorsque vous déployez un projet dans le catalogue, plusieurs autres propriétés sont associées au projet. Pour afficher toutes les propriétés pour tous les paramètres dans le catalogue, utilisez la vue [catalog.object_parameters &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database).  
  
4.  Enregistrez le projet pour sauvegarder les modifications apportées aux paramètres. Les valeurs de paramètre sont stockées dans le fichier du projet.  
  
    > [!WARNING]  
    >  Vous pouvez effectuer sur place des modifications dans la liste ou utiliser la fenêtre **Propriétés** pour modifier les valeurs des propriétés de paramètre. Vous pouvez supprimer un paramètre à l'aide du bouton **Supprimer (X)** de la barre d'outils. À l'aide du dernier bouton de la barre d'outils, vous pouvez spécifier une valeur de paramètre qui n'est utilisée que lorsque vous exécutez le package dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
    > [!NOTE]  
    >  Si vous rouvrez le fichier de package sans ouvrir le projet dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], l'onglet **Paramètres** est vide et désactivé.  
  
### <a name="to-create-project-parameters"></a>Pour créer les paramètres de projet  
  
1.  Ouvrez le projet dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
2.  Cliquez avec le bouton droit sur **Project.params** dans l'Explorateur de solutions, puis cliquez sur **Ouvrir** ou double-cliquez sur **Project.params** pour l'ouvrir.  
  
     ![Fenêtre Paramètres du projet](media/denali-project-parameters.gif "Fenêtre Paramètres du projet")  
  
3.  Cliquez sur le bouton **Ajouter un paramètre** de la barre d'outils.  
  
     ![Bouton Ajouter une barre d’outils](media/denali-parameter-add.gif "Bouton de barre d’outils Ajouter")  
  
4.  Entrez les valeurs des propriétés **Nom**, **Type de données**, **Valeur**, **Sensible**et **Requis** .  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |Nom|Nom du paramètre.|  
    |Type de données|Type de données du paramètre.|  
    |Valeur par défaut|Valeur par défaut du paramètre affecté au moment de la conception. Cette valeur est aussi appelée « valeur de conception par défaut ».|  
    |Sensible|Les valeurs de paramètre sensibles sont chiffrées dans le catalogue et apparaissent sous la forme d'une valeur Null lorsqu'elles sont affichées avec Transact-SQL ou SQL Server Management Studio.|  
    |Obligatoire|Nécessite qu'une valeur, autre que la valeur de conception par défaut, soit spécifiée pour que le package puisse s'exécuter.|  
    |Description|Pour faciliter la maintenance, description du paramètre. Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], définissez la description des paramètres dans la fenêtre Propriétés de Visual Studio lorsque le paramètre est sélectionné dans la fenêtre des paramètres applicables.|  
  
5.  Enregistrez le projet pour sauvegarder les modifications apportées aux paramètres. Les valeurs de paramètres sont stockées dans des configurations au sein du fichier projet. Enregistrez le fichier projet pour valider sur disque toutes les modifications apportées aux valeurs de paramètres.  
  
    > [!WARNING]  
    >  Vous pouvez effectuer sur place des modifications dans la liste ou utiliser la fenêtre **Propriétés** pour modifier les valeurs des propriétés de paramètre. Vous pouvez supprimer un paramètre à l'aide du bouton **Supprimer (X)** de la barre d'outils. En cliquant sur le dernier bouton de la barre d'outils pour ouvrir la boîte de dialogue **Gérer les valeurs de paramètre** , vous pouvez spécifier une valeur pour un paramètre utilisé uniquement lors de l'exécution du package dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de&#41; Integration Services &#40;SSIS](integration-services-ssis-package-and-project-parameters.md)  
  
  
