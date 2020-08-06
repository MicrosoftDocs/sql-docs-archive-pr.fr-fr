---
title: 'Leçon 1 : création du package de base et du projet | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a9ddc36ef242cc4e4b146e90dfa9de470e68d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605571"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a>Leçon 1 : Création du package de base et du package du projet
  Au cours de cette leçon, vous allez créer un package ETL simple qui extrait des données d'une seule source de fichier plat, transforme ces données en utilisant deux composants de transformation de recherche et les écrit dans la table de faits **FactCurrency** de la base de données **AdventureWorksDW2012**. Dans le cadre de cette leçon, vous allez apprendre à créer de nouveaux packages, ajouter et configurer des sources de données et des destinations et enfin, à utiliser le nouveau flux de contrôle et les composants de flux de données.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d’informations sur l’installation et le déploiement de **AdventureWorksDW2012**, consultez [Microsoft SQL Server des exemples de produits : Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).  
  
## <a name="understanding-the-package-requirements"></a>Connaissances préalables à la création d'un package  
 Ce didacticiel nécessite Microsoft SQL Server Data Tools.  
  
 Pour plus d’informations sur l’installation de SQL Server Data Tools, consultez [Télécharger SSDT (SQL Server Data Tools)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).  
  
 Avant de créer un package, vous devez maîtriser les connaissances relatives au formatage utilisé pour les données sources et la destination. Une fois ces connaissances maîtrisées, vous êtes prêt à définir les transformations nécessaires pour mapper les données source avec les données de destination.  
  
### <a name="looking-at-the-source"></a>Étude de la source  
 Dans le cadre de ce didacticiel, les données sources sont représentées par un ensemble de données monétaires d'historique contenu dans le fichier plat SampleCurrencyData.txt. Les données sources contiennent les quatre colonnes suivantes : le taux moyen de la devise, une clé de devise, une clé de date et le taux de clôture.  
  
 Voici un exemple des données sources contenues dans le fichier SampleCurrencyData.txt :  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 Pour bien utiliser des données sources issues d'un fichier plat, il est important de comprendre comment le Gestionnaire de connexions de fichiers plats interprète les données du fichier plat. Si la source du fichier plat est au format Unicode, le gestionnaire de connexions de fichiers plats définit toutes les colonnes avec le type [DT_WSTR] et une largeur par défaut égale à 50. Si la source du fichier plat est au format ANSI, les colonnes sont définies avec le type [DT_STR] et une largeur égale à 50. Il vous faudra probablement modifier ces valeurs par défaut pour affecter aux colonnes des types String plus appropriés à vos données. Pour cela, vous allez examiner le type de données de la destination dans laquelle les données seront enregistrées, puis choisir le type de données qui convient dans le Gestionnaire de connexions de fichiers plats.  
  
### <a name="looking-at-the-destination"></a>Étude de la destination  
 La destination finale des données sources est la table de faits **FactCurrency** dans la base de données **AdventureWorksDW**. La table de faits **FactCurrency** contient quatre colonnes et des relations avec deux tables de dimension, comme illustré ci-après.  
  
|Nom de la colonne|Type de données|Table de recherche|colonne de recherche|  
|-----------------|---------------|------------------|-------------------|  
|AverageRate|float|None|None|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|None|None|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a>Mappage des données sources pour la compatibilité avec la destination  
 L'analyse du format des données sources et de destination indique que des recherches seront nécessaires pour les valeurs **CurrencyKey** et **DateKey** . Les transformations qui effectueront ces recherches obtiendront les valeurs **CurrencyKey** et **DateKey** en utilisant les autres clés des tables de dimension **DimCurrency** et **DimDate** .  
  
|Colonne de fichier plat|Nom de la table|Nom de la colonne|Type de données|  
|----------------------|----------------|-----------------|---------------|  
|0|FactCurrency|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|Date|  
|3|FactCurrency|EndOfDayRate|float|  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Création d’un nouveau projet Integration Services](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Étape 2 : Ajout et configuration d’un Gestionnaire de connexions de fichiers plats](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Étape 3 : Ajout et configuration d’un Gestionnaire de connexions OLE DB](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Étape 4 : Ajout d’une tâche de flux de données au package](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Étape 5 : Ajout et configuration de la source de fichier plat](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Étape 6 : Ajout et configuration des transformations de recherche](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Étape 7 : Ajout et configuration de la destination OLE DB](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Étape 8 : Comment rendre le package de la leçon 1 plus facile à assimiler](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Étape 9 : Test du package du tutoriel de la leçon 1](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Création d’un nouveau projet Integration Services](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
