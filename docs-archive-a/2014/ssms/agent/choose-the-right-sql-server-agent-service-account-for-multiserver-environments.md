---
title: Choisir le bon compte de service SQL Server Agent pour les environnements multiserveurs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94ef890f5d2ef2b85d2f4d1023a93747e903a7f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614336"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Choisir le compte de service SQL Server Agent correct pour les environnements multiserveurs
  Le compte Windows que vous choisissez pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut affecter le comportement d'un environnement multiserveur de la manière suivante :  
  
-   Si vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent avec un compte n'appartenant pas au groupe Administrateurs local de Windows, l'inscription des serveurs cibles en serveurs maîtres risque d'échouer. Si tel est le cas, le message d'erreur suivant apparaît :  
  
     « Échec de l'inscription ».  
  
     Redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour résoudre ce problème.  
  
-   Lorsque vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent avec le compte système local, les opérations de serveur maître/serveur cible sont prises en charge uniquement si les serveurs maître et cible résident sur le même ordinateur. Si vous optez pour cette configuration, le message suivant apparaît lorsque vous inscrivez des serveurs cibles sur un serveur maître :  
  
     « Vérifiez que le compte de démarrage de l’agent pour *<nom_ordinateur_serveur_cible>* dispose des autorisations pour se connecter en tant que serveur cible. »  
  
     Vous pouvez ignorer ce message d'information. L'opération d'enregistrement doit se terminer correctement.  
  
 Pour plus d’informations sur le choix d’un compte pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md).  
  
  
