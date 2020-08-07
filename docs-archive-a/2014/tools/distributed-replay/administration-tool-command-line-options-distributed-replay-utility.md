---
title: Options de ligne de commande de l’outil d’administration (Distributed Replay Utility) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 506be071f44937d82902585e5a0621212083dfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610913"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Options de ligne de commande de l'outil d'administration (Distributed Replay Utility)
  L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outil d’administration Distributed Replay, `DReplay.exe` , est un outil en ligne de commande que vous pouvez utiliser pour communiquer avec le contrôleur Distributed Replay. Utilisez l’outil d’administration pour initier, surveiller et annuler des opérations sur le contrôleur.  
  
 ![Icône de lien vers une rubrique](../../database-engine/media/topic-link.gif "Icône du lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez émettre les options de ligne de commande suivantes avec `DReplay.exe` :  
  
 **preprocess**  
 Initialise l'étape de prétraitement. Le contrôleur prépare les données de trace d'entrée, que vous avez capturées dans l'environnement de production, pour la relecture sur le serveur cible.  
  
 **relecture**  
 Initialise l'étape de relecture d'événement. Le contrôleur distribue des données de relecture aux clients spécifiés, lance la relecture distribuée et synchronise les clients. Éventuellement, chaque client sélectionné enregistre l'activité de relecture et enregistre des fichiers de trace de résultats localement.  
  
 **statut**  
 Interroge le contrôleur et affiche l'état en cours.  
  
 **cancel**  
 Annule l'opération actuelle qui s'exécute sur le contrôleur.  
  
 Pour obtenir des informations détaillées sur la syntaxe contenant les arguments de commande et des exemples, consultez les rubriques suivantes :  
  
-   [Option preprocess &#40;outil d’administration Distributed Replay&#41;](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Option replay &#40;outil d’administration Distributed Replay&#41;](replay-option-distributed-replay-administration-tool.md)  
  
-   [Option status &#40;outil d’administration Distributed Replay&#41;](status-option-distributed-replay-administration-tool.md)  
  
-   [Option cancel &#40;outil d’administration Distributed Replay&#41;](cancel-option-distributed-replay-administration-tool.md)  
  
 Les appels de procédure distante (RPC) sont rediffusés en tant que RPC et non comme événements de langage.  
  
## <a name="permissions"></a>Autorisations  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](distributed-replay-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
