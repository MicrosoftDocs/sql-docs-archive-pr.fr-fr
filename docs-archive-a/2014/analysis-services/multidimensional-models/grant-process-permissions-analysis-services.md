---
title: Accorder des autorisations de processus (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e41e8710bc167ef53eb2aad2cbf678019b96e0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703336"
---
# <a name="grant-process-permissions-analysis-services"></a>Octroyer des autorisations de traitement (Analysis Services)
  En tant qu'administrateur, vous pouvez créer un rôle dédié aux opérations de traitement Analysis Services, ce qui vous permet de déléguer cette tâche spécifique à d'autres utilisateurs ou à des applications utilisées pour le traitement planifié sans assistance. Les autorisations de traitement peuvent être accordées au niveau de la base de données, du cube, de la dimension et de la structure d'exploration de données. À moins de travailler sur une base de données de cube ou tabulaire très grande, nous vous recommandons d'accorder des droits de traitement au niveau de la base de données, y compris à tous les objets (même à ceux ayant des dépendances les uns envers les autres).  
  
 Les autorisations sont accordées par le biais de rôles qui associent des objets à des autorisations et des comptes d'utilisateurs ou de groupes Windows. N'oubliez pas que les autorisations s'ajoutent les unes aux autres. Si un rôle accorde l'autorisation de traiter un cube tandis qu'un second rôle accorde au même utilisateur l'autorisation de traiter une dimension, les autorisations des deux rôles différents se combinent pour accorder à l'utilisateur l'autorisation de traiter le cube et de traiter la dimension spécifiée dans cette base de données.  
  
> [!IMPORTANT]  
>  Un utilisateur dont le rôle ne dispose que d’autorisations de traitement ne peut pas utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour se connecter à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et traiter des objets. Ces outils nécessitent l'autorisation `Read Definition` pour accéder aux métadonnées des objets. Sans la capacité à utiliser l'un de ces outils, vous devez utiliser le script XMLA pour exécuter une opération de traitement.  
>   
>  Nous vous suggérons également d'accorder des autorisations `Read Definition` à des fins de test. Un utilisateur disposant des autorisations `Read Definition` et `Process Database` peut traiter des objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] de manière interactive. Pour plus d’informations, consultez [Octroyer des autorisations Lire la définition sur des métadonnées d’objets &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) .  
  
## <a name="set-processing-permissions-at-the-database-level"></a>Définir les autorisations de traitement au niveau de la base de données  
 Cette section explique comment les non-administrateurs peuvent activer le traitement de tous les cubes, dimensions, structures d'exploration et modèles d'exploration dans la base de données.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ouvrez le dossier Bases de données et sélectionnez une base de données.  
  
2.  Cliquez avec le bouton droit sur **rôles**  |  **nouveau rôle**. Entrez un nom et une description.  
  
3.  Dans le volet **général** , activez la `Process Database` case à cocher. En outre, sélectionnez cette option `Read Definition` pour activer également le traitement interactif via l’un des outils de SQL Server, tels que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
4.  Dans le volet **Appartenance** , ajoutez les comptes d’utilisateurs et de groupes Windows ayant l’autorisation de traiter tout objet dans cette base de données.  
  
5.  Cliquez sur **OK** pour terminer la définition du rôle.  
  
## <a name="set-processing-permissions-on-individual-objects"></a>Définir des autorisations de traitement sur des objets spécifiques  
 Vous pouvez définir des autorisations de traitement sur des cubes, des dimensions, des structures d'exploration de données ou des modèles spécifiques.  
  
 Le traitement peut échouer si vous excluez par inadvertance des objets qui doivent être traités ensemble (par exemple si vous activez le traitement d'un cube mais pas de ses dimensions associées). Comme il est facile d'oublier certaines dépendances d'objets, vous devez impérativement effectuer des tests rigoureux lors de la définition des autorisations sur des objets spécifiques.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ouvrez le dossier Bases de données et sélectionnez une base de données.  
  
2.  Cliquez avec le bouton droit sur **rôles**  |  **nouveau rôle**. Entrez un nom et une description.  
  
3.  Dans le volet **général** , désactivez la `Process Database` case à cocher. Les autorisations de base de données outrepassent la capacité à définir des autorisations sur des objets de niveau inférieur en grisant ou en rendant non sélectionnables des options de rôle.  
  
     Techniquement, aucune autorisation de base de données n'est nécessaire pour les rôles de traitement dédiés. Mais sans `Read Definition` au niveau de la base de données, vous ne pouvez pas afficher la base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , ce qui rend le test plus difficile.  
  
4.  Sélectionnez les objets à traiter :  
  
    -   Dans le volet **Cubes** , cochez la case **Traiter** correspondant à chaque cube.  
  
    -   Dans le volet **Dimensions** , sélectionnez **Toutes les dimensions de la base de données**, puis **Traiter** pour chaque dimension. Ou sélectionnez toutes les lignes, puis utilisez Maj+clic pour basculer entre les sélections de case à cocher.  
  
5.  Dans le volet **Appartenance** , ajoutez les comptes d’utilisateurs et de groupes Windows ayant l’autorisation de traiter ces objets.  
  
6.  Cliquez sur **OK** pour terminer la définition du rôle.  
  
## <a name="test-processing"></a>Tester le traitement  
  
1.  Maintenez enfoncée la touche Maj et cliquez avec le bouton droit sur [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionnez **Exécuter en tant qu’autre utilisateur** et connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’aide d’un compte Windows assigné au rôle que vous testez.  
  
2.  Ouvrez le dossier Bases de données et sélectionnez une base de données. Seules les bases de données accessibles aux rôles auxquels votre compte a une appartenance seront visibles.  
  
3.  Cliquez avec le bouton droit sur un cube ou une dimension et sélectionnez **Traiter**. Choisissez une option de traitement. Testez toutes les options pour toutes les combinaisons d'objets. Si des erreurs dues à des objets manquants se produisent, ajoutez les objets au rôle.  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a>Définir des autorisations de traitement sur une structure d'exploration de données  
 Vous pouvez créer un rôle accordant l'autorisation de traiter des structures d'exploration de données. Ceci comprend le traitement de tous les modèles d'exploration de données.  
  
 L' **extraction** et les `Read Definition` autorisations utilisées pour parcourir un modèle et une structure d’exploration de données sont atomiques et peuvent être ajoutées au même rôle, ou être séparées dans un rôle différent.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ouvrez le dossier Bases de données et sélectionnez une base de données.  
  
2.  Cliquez avec le bouton droit sur **rôles**  |  **nouveau rôle**. Entrez un nom et une description. Dans le volet **Général** , vérifiez que les cases d’autorisations de bases de données sont décochées. Les autorisations de base de données outrepassent la capacité à définir des autorisations sur des objets de niveau inférieur en grisant ou en rendant non sélectionnables des options de rôle.  
  
3.  Dans le volet **Structures d’exploration de données** , cochez la case **Traiter** correspondant à chaque structure d’exploration de données.  
  
4.  Dans le volet **Appartenance** , ajoutez les comptes d’utilisateurs et de groupes Windows ayant l’autorisation de traiter tout objet dans cette base de données.  
  
5.  Cliquez sur **OK** pour terminer la définition du rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Traiter la base de données, la table ou la partition](../tabular-models/process-database-table-or-partition-analysis-services.md)   
 [Traitement d’objets de modèle multidimensionnel](processing-a-multidimensional-model-analysis-services.md)   
 [Accorder des autorisations de base de données &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)   
 [Octroyer des autorisations Lire la définition sur des métadonnées d’objets &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
