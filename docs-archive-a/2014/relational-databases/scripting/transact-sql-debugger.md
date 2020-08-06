---
title: Débogueur Transact-SQL
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, introduction
ms.assetid: 6e914699-0d85-46c2-aa2d-3e339ac2c4ce
author: rothja
ms.author: jroth
ms.openlocfilehash: a4312e8ac0989664e447a6ebe1cd3f05ce750f23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697871"
---
# <a name="transact-sql-debugger"></a>Débogueur Transact-SQL
  Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] vous permet de détecter les erreurs dans le code [!INCLUDE[tsql](../../includes/tsql-md.md)] en étudiant le comportement du code au moment de l'exécution. Après avoir défini la fenêtre de l'éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] en mode débogage, vous pouvez suspendre l'exécution du code au niveau de lignes spécifiques et inspecter les informations et les données qui sont utilisées ou retournées par ces instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="stepping-through-transact-sql-code"></a>Exécution pas à pas du code Transact-SQL  
 Les options suivantes fournies par le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] vous permettent de parcourir le code [!INCLUDE[tsql](../../includes/tsql-md.md)] lorsque la fenêtre de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est en mode débogage :  
  
-   Définir des points d'arrêt sur des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] individuelles.  
  
     Un point d'arrêt spécifie un point auquel vous voulez interrompre l'exécution afin de pouvoir examiner les données. Lorsque vous démarrez le débogueur, celui-ci s'arrête à la première ligne de code dans la fenêtre de l'éditeur de requête. Pour exécuter le code jusqu’au premier point d’arrêt que vous avez défini, vous pouvez utiliser la fonctionnalité **Continuer** . Vous pouvez également utiliser la fonctionnalité **Continuer** pour exécuter le code à partir de l’emplacement où la fenêtre est actuellement arrêtée, quel qu’il soit, jusqu’au prochain point d’arrêt. Vous pouvez modifier les points d’arrêt pour spécifier des actions telles que les conditions dans lesquelles l’exécution doit être interrompue, les informations à imprimer dans la fenêtre **Sortie** , de même que vous pouvez modifier l’emplacement des points d’arrêt.  
  
-   Effectuer un pas à pas détaillé dans l'instruction suivante.  
  
     Cette option vous permet de parcourir un jeu d'instructions une par une et d'observer leur comportement au fur et à mesure que vous avancez.  
  
-   Effectuer un pas à pas détaillé ou principal dans un appel à une procédure stockée ou fonction.  
  
     Si vous êtes certain qu'une procédure stockée ne comporte aucune erreur, vous pouvez faire un pas à pas principal. La procédure est exécutée en entier, et les résultats sont retournés au code.  
  
     Si vous souhaitez déboguer une procédure stockée ou une fonction, vous pouvez effectuer un pas à pas détaillé dans le module. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ouvre une nouvelle fenêtre de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] remplie avec le code source pour le module, place la fenêtre en mode débogage, puis suspend l’exécution à la première instruction dans le module. Vous pouvez ensuite parcourir le code du module, en définissant par exemple des points d'arrêt ou en exécutant le code pas à pas.  
  
 Pour plus d’informations sur les différentes façons dont vous pouvez parcourir le code avec le débogueur, consultez [Exécuter pas à pas du code Transact-SQL](step-through-transact-sql-code.md).  
  
## <a name="viewing-debugger-information"></a>Affichage des informations du débogueur  
 Chaque fois que le débogueur suspend l'exécution du code à une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifique, vous pouvez utiliser les fenêtres suivantes du débogueur pour afficher l'état d'exécution actuel :  
  
-   **Variables locales** et **Espion** Ces fenêtres affichent les expressions [!INCLUDE[tsql](../../includes/tsql-md.md)] actuellement allouées. Les expressions sont des clauses [!INCLUDE[tsql](../../includes/tsql-md.md)] qui ont pour valeur une expression scalaire unique. Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] prend en charge l’affichage d’expressions qui font référence à des variables et à des paramètres [!INCLUDE[tsql](../../includes/tsql-md.md)], ou les fonctions intégrées dont le nom commence par @@. Ces fenêtres affichent également les valeurs de données qui sont actuellement attribuées aux expressions.  
  
-   **Espion express.** Cette fenêtre affiche la valeur d’une expression [!INCLUDE[tsql](../../includes/tsql-md.md)] et vous permet d’enregistrer cette expression dans une fenêtre **Espion** .  
  
-   **Points d’arrêt.** Cette fenêtre affiche les points d'arrêt actuellement définis et vous permet de les gérer.  
  
-   **Pile des appels.** Cette fenêtre affiche l'emplacement d'exécution actuel. Elle fournit également des informations sur la façon dont l'exécution a atteint l'emplacement d'exécution actuel à partir de la fenêtre de l'éditeur de requête d'origine via des fonctions, des procédures stockées ou des déclencheurs.  
  
-   **Sortie.** Cette fenêtre affiche divers messages et données du programme, notamment des messages système du débogueur.  
  
-   **Résultats** et **Messages.** Ces onglets de la fenêtre de l'éditeur de requête affichent les résultats des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées précédemment.  
  
## <a name="transact-sql-debugger-tasks"></a>Tâches du débogueur Transact-SQL  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment configurer le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] pour le débogage distant.|[Configurer le débogueur Transact-SQL](configure-firewall-rules-before-running-the-tsql-debugger.md)|  
|décrit comment démarrer, arrêter et contrôler l'opération de débogage.|[Exécuter le débogueur Transact-SQL](transact-sql-debugger.md)|  
|Décrit comment utiliser le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] pour parcourir le code.|[Exécuter pas à pas du code Transact-SQL](step-through-transact-sql-code.md)|  
|Décrit comment utiliser le débogueur pour afficher des données [!INCLUDE[tsql](../../includes/tsql-md.md)] (telles que des paramètres et des variables) et des informations système.|[Informations du débogueur Transact-SQL](transact-sql-debugger-information.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
