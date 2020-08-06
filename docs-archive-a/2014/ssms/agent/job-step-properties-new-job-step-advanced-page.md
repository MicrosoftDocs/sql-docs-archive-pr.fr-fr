---
title: 'Propriétés de l’étape du travail : nouvelle étape du travail (page avancé) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705860"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a>Propriétés de l’étape du travail : Nouvelle étape du travail (page Avancé)
  Utilisez cette page pour afficher et modifier les propriétés d’une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étape de travail de l’agent.  
  
## <a name="options"></a>Options  
 **Action en cas de succès**  
 Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit exécuter si l'étape de travail réussit.  
  
 **Nouvelles tentatives**  
 Définit le nombre de tentatives effectuées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour reprendre une étape de travail qui a échoué.  
  
 **Intervalle de reprise (minutes)**  
 Définit le délai d'attente entre les tentatives de reprise par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Action en cas d'échec**  
 Définit l'action que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit exécuter si l'étape de travail échoue.  
  
## <a name="options-for-transact-sql-job-steps"></a>Options des étapes de travail Transact-SQL  
 **Fichier de sortie**  
 Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
 **...**  
 Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
 **Visualiser**  
 Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , ce bouton est désactivé pour l’affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
 **Ajouter la sortie au fichier existant**  
 Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
 **Enregistrer un journal dans la table**  
 Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
 **Visualiser**  
 Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
 **Ajouter la sortie à l'entrée existante dans la table**  
 Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
 **Inclure la sortie de l'étape dans l'historique**  
 Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
 **Exécuter en tant qu'utilisateur**  
 Si vous êtes membre du rôle serveur fixe **sysadmin** , vous pouvez sélectionner une autre connexion SQL pour exécuter cette étape de travail.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Options des étapes de travail du système d'exploitation (CmdExec)  
 **Fichier de sortie**  
 Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
 **...**  
 Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
 **Visualiser**  
 Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , ce bouton est désactivé pour l’affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
 **Ajouter la sortie au fichier existant**  
 Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
 **Enregistrer un journal dans la table**  
 Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
 **Visualiser**  
 Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
 **Ajouter la sortie à l'entrée existante dans la table**  
 Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
 **Inclure la sortie de l'étape dans l'historique**  
 Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-powershell-job-steps"></a>Options des étapes de travail PowerShell  
 **Fichier de sortie**  
 Définit le fichier à utiliser comme sortie avec l'étape de travail.  
  
 **...**  
 Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
 **Visualiser**  
 Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , ce bouton est désactivé pour l’affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
 **Ajouter la sortie au fichier existant**  
 Ajoute la sortie de l'étape de travail au contenu précédent du fichier à chaque exécution.  
  
 **Enregistrer un journal dans la table**  
 Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
 **Visualiser**  
 Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
 **Ajouter la sortie à l'entrée existante dans la table**  
 Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
 **Inclure la sortie de l'étape dans l'historique**  
 Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Options des étapes de travail de l'Agent de lecture de file d'attente de la réplication  
 **Serveur**  
 Définit le serveur à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
 **Sauvegarde de la base de données**  
 Définit la base de données à utiliser pour l'étape de travail de l'Agent de lecture de file d'attente de la réplication.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Options des étapes de travail de SQL Server Analysis Services  
 **Fichier de sortie**  
 Définit le fichier à utiliser comme sortie avec l'étape de travail. Cette option est disponible uniquement pour les membres du rôle serveur fixe **sysadmin** .  
  
 **...**  
 Permet de rechercher le fichier à utiliser comme sortie pour les résultats de l'étape de travail.  
  
 **Visualiser**  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ce bouton est désactivé pour l'affichage des fichiers de sortie. Utilisez plutôt le Bloc-Notes pour afficher les fichiers de sortie d'étape de travail.  
  
 **Ajouter la sortie au fichier existant**  
 Ajoute la sortie au contenu existant du fichier. Sinon, le contenu précédent du fichier est remplacé à chaque exécution de l'étape de travail.  
  
 **Enregistrer un journal dans la table**  
 Consigne la sortie de l'étape de travail dans la table **sysjobstepslogs** de la base de données **msdb** .  
  
 **Visualiser**  
 Quand l'étape de travail a été exécutée au moins une fois, cliquez sur **Afficher** pour afficher sa sortie dans la table.  
  
 **Ajouter la sortie à l'entrée existante dans la table**  
 Ajoute la sortie au contenu existant de la table. Sinon, le contenu précédent de la table est remplacé à chaque exécution de l'étape de travail.  
  
 **Inclure la sortie de l'étape dans l'historique**  
 Sélectionnez cette option pour inclure la sortie de l'étape de travail dans l'historique des travaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les étapes de travail](manage-job-steps.md)  
  
  
