---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611101"
---
# <a name="mssqlserver_18452"></a>MSSQLSERVER_18452
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|18452|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOGON_INVALID_CONNECT|  
|Texte du message|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Il s’agit d’un compte de connexion SQL Server, qui ne peut pas être utilisé avec l’authentification Windows.%.\*ls.|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur a essayé de se connecter à l'aide d'informations d'identification qui ne peuvent pas être validées. Les causes possibles sont :  
  
-   La connexion peut être une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais le serveur accepte uniquement l'authentification Windows.  
  
-   Vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais la connexion utilisée n'existe pas sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La connexion peut utiliser l'authentification Windows mais elle constitue un principal Windows non reconnu. Un principal Windows non reconnu signifie que la connexion ne peut pas être vérifiée par Windows. Cela peut être dû au fait que la connexion Windows s'effectue à partir d'un domaine non approuvé.  
  
 Des problèmes similaires peuvent provoquer l'erreur 18456 moins spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré en mode Authentification mixte.  
  
 Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existe.  
  
 Si vous essayez de vous connecter à l'aide de l'authentification Windows, vérifiez que vous êtes correctement connecté au domaine approprié.  
  
  
