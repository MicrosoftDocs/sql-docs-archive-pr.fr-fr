---
title: Activer la journalisation des packages dans SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610768"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a>Activer la journalisation des packages dans les outils de données SQL Server
  Cette procédure décrit comment ajouter des journaux à un package, configurer la journalisation au niveau du package et enregistrer la configuration dans un fichier XML. Vous ne pouvez ajouter des journaux qu'au niveau du package, mais le package n'a pas besoin d'effectuer une journalisation pour activer la journalisation dans les conteneurs inclus dans ce package.  
  
> [!IMPORTANT]  
>  Si vous déployez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le niveau de journalisation que vous définissez pour l'exécution du package remplace l'enregistrement du package que vous configurez dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Par défaut, les conteneurs du package utilisent la même configuration de journalisation que leur conteneur parent. Pour plus d’informations sur la définition des options de journalisation pour les conteneurs individuels, consultez [Configurer la journalisation à l’aide d’un fichier de configuration enregistré](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).  
  
### <a name="to-enable-logging-in-a-package"></a>Pour activer la journalisation dans un package  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans le menu **SSIS** , cliquez sur **Enregistrement**.  
  
3.  Sélectionnez un module fournisseur d'informations dans la liste **Type de fournisseur** , puis cliquez sur **Ajouter**.  
  
4.  Dans la colonne **Configuration**, sélectionnez un gestionnaire de connexions ou cliquez sur **\<New connection>** afin de créer un gestionnaire de connexions du type approprié pour le module fournisseur d’informations. En fonction du module fournisseur sélectionné, utilisez l'un des gestionnaires de connexions suivants :  
  
    -   Pour les fichiers texte, utilisez un gestionnaire de connexions de fichiers. Pour plus d’informations, consultez [File Connection Manager](connection-manager/file-connection-manager.md)  
  
    -   Pour [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], utilisez un gestionnaire de connexions de fichiers.  
  
    -   Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], utilisez un gestionnaire de connexions OLE DB. Pour plus d’informations, consultez [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).  
  
    -   Pour le journal des événements Windows, ne faites rien : [!INCLUDE[ssIS](../includes/ssis-md.md)] crée automatiquement le journal.  
  
    -   Pour les fichiers XML, utilisez un gestionnaire de connexions de fichiers.  
  
5.  Répétez les étapes 3 et 4 pour chaque journal à utiliser dans le package.  
  
    > [!NOTE]  
    >  Un package peut utiliser plusieurs journaux du même type.  
  
6.  Vous pouvez également cocher la case du niveau du package, sélectionner les journaux à utiliser pour la journalisation au niveau du package, puis cliquer sur l’onglet **Détails** .  
  
7.  Sur l'onglet **Détails** , activez **Événements** pour enregistrer toutes les entrées de journal ou désactivez **Événements** pour sélectionner des événements individuels.  
  
8.  Éventuellement, cliquez sur **Avancé** pour spécifier les informations à journaliser.  
  
    > [!NOTE]  
    >  Par défaut, toutes les informations sont journalisées.  
  
9. Sous l’onglet **Détails** , cliquez sur **Enregistrer**. La boîte de dialogue **Enregistrer sous** s’affiche. Recherchez l'emplacement où enregistrer la configuration de journalisation, tapez un nom de fichier pour la nouvelle configuration de journal, puis cliquez sur **Enregistrer**.  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;la journalisation SSIS&#41;](performance/integration-services-ssis-logging.md)   
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
