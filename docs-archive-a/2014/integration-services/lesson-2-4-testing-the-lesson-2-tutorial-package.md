---
title: 'Étape 4 : Test du package du didacticiel de la leçon 2 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c055f80cbe9e6748b82569204e3a2d82e2f437e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601559"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a>Étape 4 : Test du package du tutoriel de la leçon 2
  Une fois le conteneur de boucles Foreach et le gestionnaire de connexions de fichiers plats configurés, le package Lesson 2 peut parcourir l'ensemble des 14 fichiers plats dans le dossier Sample Data. À chaque fois qu'un nom de fichier correspondant au nom de fichier spécifié est trouvé, le conteneur de boucles Foreach remplace la variable définie par l'utilisateur par ce nom de fichier. Cette variable met à jour à son tour la propriété ConnectionString du Gestionnaire de connexions de fichiers plats, et une connexion au nouveau fichier plat est établie. Le conteneur de boucles Foreach exécute alors la tâche de flux de données inchangée sur les données du nouveau fichier plat avant de se connecter au fichier suivant dans le dossier.  
  
 Suivez la procédure ci-dessous pour tester la nouvelle fonctionnalité de bouclage que vous avez ajoutée à votre package.  
  
> [!NOTE]  
>  Si vous avez exécuté le package de la leçon 1, vous devez supprimer les enregistrements de dbo.FactCurrency dans AdventureWorksDW2012 avant d'exécuter le package de cette leçon, sans quoi il échouera avec une erreur indiquant une violation de contrainte de clé primaire. Vous obtiendrez les mêmes erreurs si vous exécutez le package en sélectionnant Déboguer/Démarrer le débogage (ou en appuyant sur F5), car la leçon 1 et la leçon 2 s'exécuteront en même temps. La leçon 2 essaiera d'insérer des enregistrements déjà insérés dans la leçon 1.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
 Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 2 contiennent les objets affichés dans les diagrammes suivants. Le flux de données doit être identique au flux de données de la leçon 1.  
  
 **Flux de contrôle**  
  
 ![Flux de contrôle dans le package](../../2014/tutorials/media/task4lesson2control.gif "Flux de contrôle dans le package")  
  
 **Flux de données**  
  
 ![Flux de données dans le package](../../2014/tutorials/media/task9lesson1data.gif "Flux de données dans le package")  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a>Pour tester le package du didacticiel de la leçon 2  
  
1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Lesson 2.dtsx** , puis cliquez sur **Exécuter le package**.  
  
     Le package est exécuté. Vous pouvez vérifier l’état de chaque boucle dans la fenêtre sortie ou en cliquant sur l’onglet **progression** . Par exemple, vous pouvez voir que 1097 lignes ont été ajoutées à la table de destination à partir du fichier Currency_VEB.txt.  
  
2.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 5 : Ajout de configurations de package pour le modèle de déploiement de package](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md)  
  
  
