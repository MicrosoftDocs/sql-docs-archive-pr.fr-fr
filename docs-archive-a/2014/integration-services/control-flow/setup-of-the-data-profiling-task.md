---
title: Configuration de la tâche de profilage des données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], configuring
ms.assetid: fe050ca4-fe45-43d7-afa9-99478041f9a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fefe097905f2f5effaece8e352e21df095004e46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611205"
---
# <a name="setup-of-the-data-profiling-task"></a>Configuration de la tâche de profilage des données
  Avant de pouvoir examiner un profil des données sources, vous devez tout d'abord configurer et exécuter la tâche de profilage des données. Vous créez cette tâche dans un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour configurer la tâche de profilage des données, vous utilisez l'Éditeur de tâche de profilage de données. Cet éditeur vous permet de sélectionner l'emplacement de sortie des profils et les profils à calculer. Après avoir configuré la tâche, vous exécutez le package pour calculer les profils des données.  
  
## <a name="requirements-and-limitations"></a>Limitations et exigences  
 La tâche de profilage des données fonctionne uniquement avec les données stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elle ne fonctionne pas avec les sources de données tierces ou basées sur des fichiers.  
  
 En outre, pour exécuter un package qui contient la tâche de profilage des données, vous devez utiliser un compte qui dispose d'autorisations de lecture/écriture, notamment les autorisations CREATE TABLE, sur la base de données tempdb.  
  
## <a name="data-profiling-task-in-a-package"></a>Tâche de profilage des données dans un package  
 La tâche de profilage des données configure uniquement les profils et crée le fichier de sortie qui contient les profils calculés. Pour examiner ce fichier de sortie, vous devez utiliser la visionneuse du profil des données qui est un programme autonome. Étant donné que vous devez examiner la sortie séparément, vous pouvez utiliser la tâche de profilage des données dans un package qui ne contient pas d'autres tâches.  
  
 Toutefois, vous n'êtes pas tenu d'utiliser la tâche de profilage des données comme la seule tâche d'un package. Si vous souhaitez effectuer le profilage des données dans le flux de travail ou le flux de données d'un package plus complexe, vous avez le choix entre les options suivantes :  
  
-   Pour implémenter la logique conditionnelle basée sur le fichier de sortie de la tâche, dans le flux de contrôle du package, placez une tâche de script après la tâche de profilage des données. Vous pouvez ensuite utiliser cette tâche de script pour interroger le fichier de sortie.  
  
-   Pour profiler les données dans le flux de données une fois que les données ont été chargées et transformées, vous devez enregistrer les données modifiées temporairement dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ensuite, vous pouvez profiler les données enregistrées.  
  
 Pour plus d’informations, consultez [Incorporer une tâche de profilage des données dans le flux de travail du package](incorporate-a-data-profiling-task-in-package-workflow.md).  
  
## <a name="setup-of-the-task-output"></a>Configuration de la sortie de la tâche  
 Une fois que la tâche de profilage des données est dans un package, vous devez configurer la sortie pour les profils que la tâche calculera. Pour configurer la sortie des profils, vous devez utiliser la page **Général** de l'Éditeur de tâche de profilage des données. Outre la spécification de la destination de la sortie, la page **Général** vous offre également la possibilité d'effectuer un profil rapide des données. Lorsque vous sélectionnez **Profil rapide**, la tâche de profilage des données profile une table ou une vue en utilisant une partie ou la totalité des profils par défaut avec leurs paramètres par défaut.  
  
 Pour plus d’informations, consultez [Éditeur de tâche de profilage de données &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md) et [Formulaire de profil rapide de table simple &#40;tâche de profilage des données&#41;](data-profiling-task.md).  
  
> [!IMPORTANT]  
>  Le fichier de sortie peut contenir des données sensibles qui concernent votre base de données et les données qu'elle contient. Pour obtenir des suggestions sur la manière de sécuriser davantage ce fichier, consultez [Accéder aux fichiers utilisés par des packages](../access-to-files-used-by-packages.md).  
  
## <a name="selection-and-configuration-of-the-profiles-to-be-computed"></a>Sélection et configuration des profils à calculer  
 Après avoir configuré le fichier de sortie, vous devez sélectionner les profils de données à calculer. La tâche de profilage des données peut calculer huit profils de données différents. Cinq de ces profils analysent des colonnes individuelles, tandis que les trois autres analysent plusieurs colonnes ou les relations entre des colonnes et des tables. Dans une même tâche de profilage des données, vous pouvez calculer plusieurs profils pour plusieurs colonnes ou des combinaisons de colonnes dans plusieurs tables ou vues.  
  
 Le tableau suivant décrit les rapports calculés par chacun de ces profils ainsi que les types de données pour lesquels les profils sont valides.  
  
|Pour calculer|Afin d'identifier|Utilisez ce profil|  
|----------------|-------------------------|----------------------|  
|Toutes les longueurs distinctes des valeurs de chaîne dans la colonne sélectionnée, ainsi que le pourcentage de lignes dans la table que chaque longueur représente.|**Les valeurs de chaîne qui ne sont pas valides.** Par exemple, vous profilez une colonne supposée utiliser deux caractères pour les codes des États américains et découvrez des valeurs qui comportent plus de deux caractères.|**Distribution de longueurs de colonne-** Valide pour une colonne avec l’un de ces types de données :<br /><br /> Types de données de caractères : `char`, `nchar`, `varchar` et `nvarchar`|  
|Un ensemble d'expressions régulières qui reflètent le pourcentage spécifié de valeurs dans une colonne de chaîne.<br /><br /> Mais aussi pour rechercher des expressions régulières qui peuvent être utilisées dans le futur pour valider de nouvelles valeurs.|**Valeurs de chaîne qui ne sont pas valides ou dont le format est incorrect-** Par exemple, un profil de modèle d’une colonne de codes postaux peut générer les expressions régulières suivantes : \d {5} -\d {4} , \d {5} et \d {9} . Si la sortie contient d'autres expressions régulières, les données contiennent des valeurs qui ne sont pas valides ou dont le format est incorrect.|**Profil de motif de colonne-** Valide pour une colonne avec l’un de ces types de données :<br /><br /> Types de données de caractères : `char`, `nchar`, `varchar` et `nvarchar`|  
|Le pourcentage de valeurs Null dans la colonne sélectionnée.|**Un ratio élevé inattendu de valeurs Null dans une colonne.** Par exemple, vous profilez une colonne supposée contenir des codes postaux américains et découvrez un pourcentage élevé et inacceptable de codes manquants.|**Ratio de colonne null-** Valide pour une colonne avec ces types de données :<br /><br /> N'importe quel type de données. Cela inclut les types `image`, `text`, `xml`, les types définis par l'utilisateur et les types variant.|  
|Des statistiques, telles que la valeur minimale, la valeur maximale, la moyenne et l'écart type pour des colonnes numériques, ainsi que la valeur minimale et la valeur maximale pour des colonnes `datetime`.|**Les valeurs numériques et les dates qui ne sont pas valides.** Par exemple, vous profilez une colonne de dates historiques et découvrez une date maximale qui n’est pas encore passée.|**Profil de statistiques de colonnes-** Valide pour une colonne avec l’un de ces types de données :<br /><br /> Types de donnés numériques : types integer (sauf `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` et `numeric`.<br /><br /> Types de données de date et d'heure : `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` et `datetimeoffset`.<br />Remarque : pour une colonne comportant un type de données de date et d’heure, le profil calcule uniquement le minimum et le maximum.|  
|Toutes les valeurs distinctes dans la colonne sélectionnée, ainsi que le pourcentage de lignes dans la table que chaque valeur représente. Ou les valeurs qui représentent plus qu'un pourcentage spécifié dans la table.|**Un nombre incorrect de valeurs distinctes dans une colonne.** Par exemple, vous profilez une colonne qui contient les États américains et découvrez plus de 50 valeurs distinctes.|**Distribution de valeurs de colonne-** Valide pour une colonne avec l’un de ces types de données :<br /><br /> Types de donnés numériques : types integer (sauf `bit`), `money`, `smallmoney`, `decimal`, `float`, `real` et `numeric`.<br /><br /> Types de données de caractères : `char`, `nchar`, `varchar` et `nvarchar`<br /><br /> Types de données de date et d'heure : `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` et `datetimeoffset`.|  
|Si une colonne ou un ensemble de colonnes est une clé, ou une clé approximative, pour la table sélectionnée.|**Les valeurs dupliquées dans une colonne clé potentielle.** Par exemple, vous profilez les colonnes Name et Address d’une table Customers et découvrez des valeurs dupliquées là où les combinaisons nom et adresse doivent être uniques.|**Profil de clé candidate.** Un profil de plusieurs colonnes qui indique si une colonne ou un ensemble de colonnes est approprié pour servir de clé pour la table sélectionnée. Valide pour les colonnes avec l'un de ces types de données :<br /><br /> Types de données d'entiers : `bit`, `tinyint`, `smallint`, `int` et `bigint`.<br /><br /> Types de données de caractères : `char`, `nchar`, `varchar` et `nvarchar`<br /><br /> Types de données de date et d'heure : `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` et `datetimeoffset`.|  
|Degré de dépendance entre les valeurs d'une colonne (colonne dépendante) et celles d'une autre colonne ou d'un ensemble de colonnes (colonne déterminante).|**Les valeurs qui ne sont pas valides dans des colonnes dépendantes.** Par exemple, vous profilez la dépendance entre une colonne qui contient les codes postaux américains et une colonne qui contient les États américains. Le même code postal doit toujours être associé au même État. Toutefois, le profil détecte des violations de cette dépendance.|**Dépendance fonctionnelle-** Valide pour les colonnes avec l’un des types de données suivants :<br /><br /> Types de données d'entiers : `bit`, `tinyint`, `smallint`, `int` et `bigint`.<br /><br /> Types de données de caractères : `char`, `nchar`, `varchar` et `nvarchar`<br /><br /> Types de données de date et d'heure : `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` et `datetimeoffset`.|  
|Si une colonne ou un ensemble de colonnes est approprié pour servir de clé étrangère entre les tables sélectionnées.<br /><br /> Autrement dit, ce profil signale le chevauchement des valeurs entre deux colonnes ou ensembles de colonnes.|**Les valeurs qui ne sont pas valides.** Par exemple, vous profilez la colonne ProductID d’une table Sales et découvrez que la colonne contient des valeurs qui sont introuvables dans la colonne ProductID de la table Products.|**Profil d’inclusion de valeur.** Valide pour les colonnes avec l’un de ces types de données :<br /><br /> Types de données d'entiers : `bit`, `tinyint`, `smallint`, `int` et `bigint`.<br /><br /> Type de données caractère : `char` ,, `nchar` `varchar` et`nvarchar`<br /><br /> Types de données de date et d'heure : `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` et `datetimeoffset`.|  
  
 Pour sélectionner les profils à calculer, vous devez utiliser la page **Demandes de profil** de l'Éditeur de tâche de profilage des données. Pour plus d’informations, consultez [Éditeur de tâche de profilage de données &#40;page Général&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Dans la page **Demandes de profil** , vous spécifiez également la source de données et vous configurez les profils de données. Lorsque vous configurez la tâche, tenez compte des informations suivantes :  
  
-   Pour simplifier la configuration et faciliter la découverte des caractéristiques de données inconnues, vous pouvez utiliser le caractère générique **( \* )**, à la place d’un nom de colonne individuel. Si vous utilisez ce caractère générique, la tâche profilera chaque colonne dotée d'un type de données approprié, qui à son tour pourra ralentir le traitement.  
  
-   Lorsque la table ou la vue sélectionnée est vide, la tâche de profilage des données ne calcule pas de profils.  
  
-   Lorsque toutes les valeurs dans la colonne sélectionnée sont Null, la tâche de profilage des données calcule uniquement le profil de ratio de colonne Null. Elle ne calcule pas le profil de distribution de longueurs de colonne, de modèle de colonne, de statistiques de colonnes ou de distribution de valeurs de colonne pour la colonne vide.  
  
 Chacun des profils de données disponibles possède ses propres options de configuration. Pour plus d'informations sur ces options, consultez les rubriques suivantes :  
  
-   [Options Demande de profil de clé candidate &#40;tâche de profilage des données&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de distribution de longueurs de colonne &#40;tâche de profilage des données&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de ratio de colonne Null &#40;tâche de profilage des données&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de modèle de colonne &#40;tâche de profilage des données&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de statistiques de colonnes &#40;tâche de profilage des données&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de distribution de valeurs de colonne &#40;tâche de profilage des données&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil de dépendance fonctionnelle &#40;tâche de profilage des données&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Options Demande de profil d’inclusion de valeur &#40;tâche de profilage des données&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
## <a name="execution-of-the-package-that-contains-the-data-profiling-task"></a>Exécution du package qui contient la tâche de profilage des données  
 Après avoir configuré la tâche de profilage des données, vous pouvez l'exécuter. La tâche calcule ensuite les profils de données et génère en sortie ces informations au format XML dans un fichier ou dans une variable de package. La structure de ce code XML respecte le schéma DataProfile.xsd. Vous pouvez ouvrir le schéma dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou un autre éditeur de schéma, dans un éditeur XML ou dans un éditeur de texte tel que le bloc-notes. Ce schéma pour les informations sur la qualité des données peut être utile aux fins suivantes :  
  
-   pour échanger des informations sur la qualité des données au sein d'une organisation ou entre plusieurs organisations ;  
  
-   pour construire des outils personnalisés qui fonctionnent avec les informations sur la qualité des données.  
  
 L’espace de noms cible est identifié dans le schéma comme [https://schemas.microsoft.com/sqlserver/2008/DataDebugger/](https://schemas.microsoft.com/sqlserver/2008/DataDebugger/) .  
  
## <a name="next-step"></a>étape suivante  
 [Visionneuse du profil des données](data-profile-viewer.md).  
  
  
