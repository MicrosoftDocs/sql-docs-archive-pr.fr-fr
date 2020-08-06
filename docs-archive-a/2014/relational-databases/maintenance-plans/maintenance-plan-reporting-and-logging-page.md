---
title: Plan de maintenance (page Création de rapports et enregistrement) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603977"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Plan de maintenance, (Page Création de rapports et enregistrement)
  La boîte de dialogue **Création de rapport et enregistrement** vous permet de configurer les rapports et les enregistrements qui sont générés lors de l'exécution des plans de maintenance.  
  
## <a name="options"></a>Options  
 **Générer un rapport de fichier texte**  
 Indiquez si [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit écrire un rapport de fichier texte.  
  
 **Créer un nouveau fichier**  
 Crée un nouveau fichier de rapport pour chaque exécution du plan de maintenance. Par défaut, les fichiers de rapport sont enregistrés sur l'ordinateur hébergeant l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant ce plan de maintenance, dans le dossier qui a été défini en tant que dossier des journaux par défaut au moment de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour spécifier un autre dossier, entrez le chemin d’accès complet du dossier dans la zone de texte **Dossier** ou cliquez sur le bouton Parcourir ( **...** ) pour naviguer jusqu’au dossier de votre choix.  
  
 **Ajouter au fichier**  
 Ajoutez le rapport généré pour chaque exécution du plan au fichier spécifié dans la zone de texte **Nom de fichier** . Vous pouvez également spécifier un autre fichier en cliquant sur le bouton Parcourir et en sélectionnant un fichier dans la boîte de dialogue.  
  
 **Envoyer le rapport à un destinataire de messagerie**  
 Transmet le résultat de l'exécution d'un plan de maintenance par courrier électronique. Cette option est uniquement disponible si la messagerie de base de données est activée et correctement configurée.  
  
 **Opérateur d'agent**  
 Sélectionnez dans la liste l'opérateur d'agent qui sera le destinataire du message électronique. Cette option est uniquement disponible si la messagerie est activée et correctement configurée.  
  
 **Enregistrer les informations étendues**  
 Permet d'inclure plus d'informations dans le journal. L'utilisation de cette option augmente la taille de l'historique du plan de maintenance qui est stocké sur l'ordinateur.  
  
 **Connexion à un serveur distant**  
 Enregistre l'historique du plan de maintenance sur un serveur distant.  
  
 **Connection**  
 Spécifie les informations de connexion à utiliser pour se connecter à un serveur distant.  
  
 **Nouveau**  
 Affiche la boîte de dialogue **Propriétés de connexion** . Sert à configurer les nouvelles informations de connexion permettant de se connecter à un serveur distant.  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](maintenance-plans.md)   
 [Messagerie de base de données](../database-mail/database-mail.md)  
  
  
