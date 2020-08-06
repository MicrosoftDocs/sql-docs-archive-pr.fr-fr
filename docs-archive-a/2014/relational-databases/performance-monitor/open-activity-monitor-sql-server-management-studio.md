---
title: Ouvrir le Moniteur d’activité (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea74122ad18a0a1ede5eef1e09684606ca0ce073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707399"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a>Ouvrir le Moniteur d'activité (SQL Server Management Studio)
  Cette rubrique décrit la façon d'ouvrir le Moniteur d'activité pour obtenir des informations sur les processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la façon dont ces processus affectent l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elle explique également comment définir l'intervalle d'actualisation du Moniteur d'activité.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour ouvrir le Moniteur d'activité à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **Pour définir l’intervalle d’actualisation avec :**  [SQL Server Management Studio](#Refresh)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
 Le Moniteur d'activité exécute des requêtes sur l'instance analysée afin d'obtenir des informations pour ses volets d'informations. Si l'intervalle d'actualisation est défini sur une valeur inférieure à 10 secondes, le temps nécessaire à l'exécution de ces requêtes peut affecter les performances du serveur.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Pour afficher le Moniteur d'activité, un utilisateur doit disposer de l'autorisation VIEW SERVER STATE. Pour afficher la section E/S du fichier de données du Moniteur d'activité, vous devez disposer de l'autorisation CREATE DATABASE, ALTER ANY DATABASE ou VIEW ANY DEFINITION en plus de VIEW SERVER STATE.  
  
 Pour pouvoir mettre fin (KILL) à un processus, un utilisateur doit être membre des rôles serveur fixe sysadmin ou processadmin.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a>Pour ouvrir le Moniteur d'activité dans SQL Server Management Studio  
  
1.  Dans la barre d'outils standard [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , cliquez sur **Moniteur d'activité**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , sélectionnez le nom de serveur et le mode d'authentification, puis cliquez sur **Se connecter**.  
  
 Vous pouvez également ouvrir le Moniteur d'activité à tout moment en appuyant sur CTRL+ALT A.  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a>Pour ouvrir le Moniteur d'activité dans l'Explorateur d'objets  
  
-   Dans l'Explorateur d'objets, cliquez avec le bouton droit sur le nom de l'instance, puis sélectionnez **Moniteur d'activité**.  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a>Pour ouvrir le Moniteur d'activité lors de l'ouverture de SQL Server Management Studio  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez **Environnement**, puis sélectionnez **Général**.  
  
3.  Dans la zone **Au démarrage** , sélectionnez **Ouvrir l'Explorateur d'objets et le Moniteur d'activité**.  
  
4.  Pour activer les modifications, fermez et rouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a>Pour définir l’intervalle d’actualisation du moniteur d’activité  
  
-   Ouvrez le Moniteur d'activité.  
  
-   Cliquez avec le bouton droit sur **Vue d’ensemble**, sélectionnez **Intervalle d’actualisation**, puis choisissez l’intervalle dans lequel le Moniteur d’activité doit obtenir de nouvelles informations sur l’instance.  
  
  
