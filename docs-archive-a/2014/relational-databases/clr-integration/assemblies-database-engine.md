---
title: Assemblys (Moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edb18ccfa9954fe52093f87948f956c2eacc1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704195"
---
# <a name="assemblies-database-engine"></a>Assemblys (moteur de base de données)
  Toutes les rubriques de cette section vous aident à mieux comprendre, concevoir et mettre en œuvre les assemblys.  
  
 Les assemblys sont des fichiers DLL utilisés dans une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour déployer des fonctions, des procédures stockées, des déclencheurs, des agrégats définis par l’utilisateur et des types définis par l’utilisateur qui sont écrits dans l’un des langages de code managé hébergés par le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) au lieu de [!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], un assembly est un objet qui fait référence à un module d'applications managées (fichier .dll) qui a été créé dans le Common Language Runtime (CLR) [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Un assembly contient des métadonnées de classe et du code managé. Le téléchargement d'un assembly dans une instance SQL Server constitue la première étape nécessaire à la création des objets de base de données suivants :  
  
-   Fonctions CLR. Pour plus d’informations, consultez [créer des fonctions CLR](../user-defined-functions/create-clr-functions.md).  
  
-   Procédures stockées CLR. Pour plus d’informations, consultez [procédures stockées CLR](../../database-engine/dev-guide/clr-stored-procedures.md).  
  
-   Déclencheurs CLR. Pour plus d’informations, consultez [créer des déclencheurs CLR](../triggers/create-clr-triggers.md).  
  
-   Fonctions d'agrégation définies par l'utilisateur. Pour plus d’informations, consultez [créer des agrégats définis par l’utilisateur](../user-defined-functions/create-user-defined-aggregates.md).  
  
-   Types définis par l'utilisateur. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../native-client/features/using-user-defined-types.md).  
  
 Les assemblys sont chargés des fonctions suivantes dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   Contenir le code managé qui exécute la fonctionnalité d'un ou de plusieurs objets de données CLR mentionnés précédemment.  
  
-   Contenir les métadonnées décrivant le numéro de version et la culture de l'assembly, une clé publique facultative qui identifie de manière unique la liste des classes de l'assembly, les méthodes définies dans l'assembly et l'architecture de processeur de l'assembly.  
  
-   Gérer le niveau d'accès du code managé aux ressources extérieures en régulant les autorisations d'accès au code.  
  
-   Contenir les métadonnées relatives aux dépendances avec les autres assemblys auxquelles fait référence l'assembly.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conception d'assemblys](assemblies-designing.md)|Explique les points à prendre en considération avant la création d'un assembly, notamment : assemblys à inclure, autorisations d'accès au code et autres restrictions.|  
|[Implémentation d'assemblys](assemblies-implementing.md)|Explique comment créer et supprimer des assemblys, comment et quand modifier des assemblys et comment récupérer les métadonnées relatives aux assemblys.|  
|[Obtention d'informations sur les assemblys](assemblies-getting-information.md)|Répertorie les affichages catalogue et les fonctions qu'il est possible d'interroger pour récupérer les métadonnées relatives aux assemblys.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation pour l’intégration du CLR &#40;Common Language Runtime&#41;](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
