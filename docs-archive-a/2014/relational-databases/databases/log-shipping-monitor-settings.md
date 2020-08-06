---
title: Paramètres du moniteur d’envoi des journaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709544"
---
# <a name="log-shipping-monitor-settings"></a>Paramètres du moniteur d'envoi des journaux
  Cette page vous permet de configurer et de modifier les propriétés du serveur moniteur d'envoi des journaux.  
  
 Pour obtenir des explications sur les concepts de copie des journaux de transaction, consultez [À propos de la copie des journaux de transaction &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Options  
 **Instance du serveur moniteur**  
 Affiche le nom de l'instance du serveur actuellement configurée comme serveur moniteur dans la configuration d'envoi des journaux.  
  
 **Connexion**  
 Sélectionnez et connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser comme serveur moniteur. Le compte utilisé pour se connecter doit être membre du rôle serveur fixe sysadmin sur l'instance de serveur secondaire.  
  
 **En imitant le compte proxy du travail**  
 L'envoi des journaux doit imiter le compte proxy de l'Agent SQL Server lors de la connexion à l'instance du serveur moniteur. Les processus de sauvegarde, copie et restauration doivent être capables de se connecter au serveur moniteur pour mettre à jour l'état des opérations d'envoi de journaux.  
  
 **En utilisant la connexion SQL Server suivante**  
 Permet à l'envoi des journaux d'utiliser une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifique lors de la connexion à l'instance du serveur moniteur. Les processus de sauvegarde, copie et restauration doivent être capables de se connecter au serveur moniteur pour mettre à jour l'état des opérations d'envoi de journaux. Choisissez cette option pour que l'envoi des journaux utilise une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifique, puis spécifiez le nom d'accès et le mot de passe.  
  
 **Supprimer l'historique après le**  
 Spécifiez la durée pendant laquelle il convient de conserver les informations de l'historique d'envoi des journaux sur le serveur moniteur avant de les supprimer.  
  
 **Nom du travail**  
 Spécifie le nom du travail d'alerte de l'Agent SQL Server utilisé par l'envoi des journaux pour déclencher des alertes lors du dépassement des seuils de sauvegarde ou de restauration. Lors de la création de ce travail, vous pouvez modifier son nom en le tapant dans cette zone.  
  
 **Planification**  
 Indique la planification en cours du travail d'alerte de l'Agent SQL Server.  
  
 **Modifier**  
 Modifiez les paramètres du travail d'alerte de l'Agent SQL Server.  
  
 **Désactiver ce travail**  
 Permet de suspendre le travail d'alerte de l'Agent SQL Server.  
  
  
