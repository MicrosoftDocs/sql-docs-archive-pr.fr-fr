---
title: Afficher un plan d’exécution réel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f384e2d2752b7601fbb46b8ee7f7b56a2615651c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698004"
---
# <a name="display-an-actual-execution-plan"></a>Afficher un plan d'exécution réel
  Cette rubrique explique comment générer des plans d'exécution graphiques réels à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Lorsque des plans d'exécution réels sont générés, les requêtes ou les traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] sont exécutés. Le plan d'exécution généré affiche le plan d'exécution réel que le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilise pour exécuter les requêtes.  
  
 Pour être en mesure d'utiliser cette fonction, les utilisateurs doivent bénéficier des autorisations permettant d'exécuter les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] pour lesquelles un plan d'exécution graphique est actuellement généré. Qui plus est, les utilisateurs doivent se voir accorder l'autorisation SHOWPLAN pour toutes les bases de données référencées par la requête.  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a>Pour inclure un plan d'exécution pour une requête durant l'exécution  
  
1.  Dans la barre d’outils [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , cliquez sur **Requête de moteur de base de données**. Vous pouvez également ouvrir une requête existante et afficher le plan d’exécution estimé en cliquant sur le bouton **Ouvrir un fichier** dans la barre d’outils puis en choisissant la requête existante.  
  
2.  Entrez la requête pour laquelle vous souhaitez afficher le plan d'exécution réel.  
  
3.  Dans le menu **requête** , cliquez sur **inclure le plan d’exécution réel** ou cliquez sur le bouton inclure le plan d' **exécution réel** .  
  
4.  Exécutez la requête en cliquant sur le bouton de la barre d’outils **Exécuter** . Le plan utilisé par l’optimiseur de requête est affiché sous l’onglet **Plan d’exécution** dans le volet de résultats. Placez le curseur de la souris sur les opérateurs logiques et physiques pour visualiser la description et les propriétés des opérateurs dans l'info-bulle affichée.  
  
     Il est également possible d'afficher les propriétés des opérateurs dans la fenêtre Propriétés. Si Propriétés n’est pas visible, cliquez avec le bouton droit sur un opérateur et sélectionnez **Propriétés**. Sélectionnez l'opérateur de votre choix.  
  
5.  Si vous voulez modifier l’affichage du plan d’exécution, cliquez avec le bouton droit sur le plan d’exécution et sélectionnez **Zoom avant**, **Zoom arrière**, **Zoom personnalisé**ou **Zoom pour ajuster**. Les options**Zoom avant** et **Zoom arrière** vous permettent d’effectuer un zoom avant ou arrière sur le plan d’exécution. Quant à l’option **Zoom personnalisé** , elle vous permet de définir votre propre zoom, par exemple, un pourcentage de zoom de 80. Enfin, l’option**Zoom pour ajuster** agrandit le plan de sorte que sa taille soit ajustée en fonction de celle du volet de résultats.  
  
  
