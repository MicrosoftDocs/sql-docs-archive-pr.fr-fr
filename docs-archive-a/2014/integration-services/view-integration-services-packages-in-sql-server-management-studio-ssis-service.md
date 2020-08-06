---
title: Afficher les packages de Integration Services dans SQL Server Management Studio (service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ba86320f1b1a685eab6e80399f3e8c21bd110eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695803"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a>Afficher les packages Integration Services dans SQL Server Management Studio (Service SSIS)
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Cette procédure explique comment se connecter à [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et visualiser la liste des packages gérés par le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-connect-to-integration-services"></a>Pour se connecter à Integration Services  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , sélectionnez **Integration Services** dans la liste **Type de serveur** , indiquez un nom de serveur dans la zone **Nom du serveur** , puis cliquez sur **Se connecter**.  
  
    > [!IMPORTANT]  
    >  Si vous ne pouvez pas vous connecter à [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], il est probable que le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne soit pas en cours d'exécution. Pour connaître l'état du service, cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Microsoft SQL Server**, sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**. Dans le volet gauche, cliquez sur **Services SQL Server**. Dans le volet droit, recherchez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Démarrez le service, il n'est pas déjà en cours d'exécution.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] s'ouvre. Par défaut, la fenêtre Explorateur d'objets est ouverte et positionnée dans l'angle inférieur gauche de SQL Server Management Studio. Si l'Explorateur d'objets n'est pas ouvert, dans le menu **Affichage** , cliquez sur **Explorateur d'objets** .  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a>Pour visualiser les packages gérés par le service Integration Services  
  
1.  Dans l'Explorateur d'objets, développez le dossier Packages stockés.  
  
2.  Développez les sous-dossiers du dossier Packages stockés afin d'afficher les packages.  
  
## <a name="see-also"></a>Voir aussi  
 [Package Management &#40;service SSIS&#41;](service/package-management-ssis-service.md)   
 [Utiliser SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  
