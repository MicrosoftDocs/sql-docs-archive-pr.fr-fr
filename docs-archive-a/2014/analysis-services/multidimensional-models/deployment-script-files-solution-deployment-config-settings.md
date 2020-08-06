---
title: Spécification des paramètres de configuration pour le déploiement de solutions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b08ce2b6296a5098c1b21a3afa443668c481a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604200"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a>Spécification de paramètres de configuration pour le déploiement de solutions
  L' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistant Déploiement de lit les options de déploiement de partitions et de rôles que vous utilisez dans le script de déploiement à partir du \<*project name*> fichier. configsettings. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]crée ce fichier lorsque vous générez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]utilise les paramètres de configuration du projet actuel pour créer le \<*project name*> fichier. configsettings.  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>Examen des paramètres de configuration pour le déploiement  
 Les paramètres de configuration stockés dans le \<*project name*> fichier. configsettings sont les suivants :  
  
-   **Chaînes de connexion à la source de données** Il s'agit des chaînes de connexion pour chaque source de données, basées sur les valeurs spécifiées dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'ID et le mot de passe utilisateur sont systématiquement supprimés de la chaîne de connexion avant que le reste de la chaîne ne soit stocké dans ce fichier. Cependant, si l'Assistant Déploiement déploie directement vers une instance Analysis Services, vous pouvez ajouter les informations d'ID et de mot de passe utilisateur appropriées dans l'Assistant pour permettre le traitement correct de la base de données de déploiement. Ces informations de connexion ne seront pas stockées dans le script de déploiement proprement dit, si un script est enregistré par l'Assistant Déploiement.  
  
-   **Comptes d'emprunt d'identité** Ce paramètre spécifie le nom d'utilisateur que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise pour exécuter les instructions dans chaque source de données. Si aucun compte d'emprunt d'identité n'est spécifié, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise son compte d'ouverture de session pour exécuter les instructions. Si le compte d'ouverture de session [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] reçoit des autorisations directement dans la source de données, tous les administrateurs de base de données de toutes les bases de données de l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ont accès à la source de données à travers le compte d'ouverture de session. Si un mot de passe et un compte d'utilisateur sont spécifiés, ces informations sont systématiquement supprimées avant que les informations d'emprunt d'identité ne soient stockées dans ce fichier. Cependant, si l'Assistant Déploiement déploie directement vers une instance Analysis Services, vous pouvez ajouter les informations d'ID et de mot de passe utilisateur appropriées dans l'Assistant pour permettre le traitement correct de la base de données de déploiement. Ces informations d'emprunt d'identité ne sont pas stockées dans le script de déploiement proprement dit, si un script est enregistré par l'Assistant Déploiement.  
  
-   **Fichiers journaux d'erreurs de clé** Ce paramètre spécifie le nom de fichier et le chemin d'accès du fichier journal d'erreurs de clé pour chaque cube, groupe de mesures, partition et dimension de la base de données.  
  
-   **Emplacements de stockage** Ce paramètre spécifie l’emplacement de stockage pour chaque cube, groupe de mesures et partition dans la base de données. Si aucune valeur n'est fournie pour un objet, l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l'emplacement par défaut pour l'objet. Par exemple, les partitions utilisent l'emplacement pour le groupe de mesures, les groupes de mesures utilisent l'emplacement pour le cube et les cubes utilisent l'emplacement par défaut pour les objets sur l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'emplacement de stockage peut être un chemin d'accès local ou UNC (Universal Naming Convention).  
  
-   **Report Server** Ce paramètre spécifie le serveur de rapports et l'emplacement du dossier pour chaque action de rapport définie dans chaque cube de la base de données.  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>Modification des paramètres de configuration pour le déploiement  
 Dans certains cas, vous devrez peut-être déployer le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet à l’aide de paramètres de configuration différents de ceux stockés dans le \<*project name*> fichier. configsettings. Par exemple, vous pouvez modifier la chaîne de connexion à une ou plusieurs sources de données, ou spécifier des emplacements de stockage pour des partitions ou des groupes de mesures spécifiques.  
  
 Pour modifier le déploiement des partitions et des rôles dans un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet, vous devez modifier ces informations dans le \<*project name*> fichier. configsettings, comme décrit dans la procédure ci-dessous. Vous ne pouvez pas modifier les paramètres de partitions et de rôles au sein du projet, car la *\<project name>* boîte de dialogue **pages de propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] n’affiche pas ces options.  
  
> [!NOTE]  
>  Les paramètres de configuration peuvent s'appliquer à tous les objets ou uniquement aux objets nouvellement créés. Appliquez les paramètres de configuration uniquement aux objets nouvellement créés lorsque vous ajoutez des objets supplémentaires à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée antérieurement et que vous ne souhaitez pas recouvrir des objets existants. Pour spécifier si les paramètres de configuration s’appliquent à tous les objets ou uniquement à ceux qui viennent d’être créés, définissez cette option dans le \<*project name*> fichier. deploymentoptions. Pour plus d’informations, consultez [Spécification des options de déploiement de partitions et de rôles](deployment-script-files-partition-and-role-deployment-options.md).  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>Pour modifier des paramètres de configuration après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, dans la page **Paramètres de configuration** , spécifiez les paramètres de configuration pour les objets déployés.  
  
     -ou-  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     -ou-  
  
-   Modifiez le \<*project name*> fichier. configsettings à l’aide de n’importe quel éditeur de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de la cible d’installation](deployment-script-files-specifying-the-installation-target.md)   
 [Spécification des options de déploiement de partitions et de rôles](deployment-script-files-partition-and-role-deployment-options.md)   
 [Spécification d'options de traitement](deployment-script-files-specifying-processing-options.md)  
  
  
