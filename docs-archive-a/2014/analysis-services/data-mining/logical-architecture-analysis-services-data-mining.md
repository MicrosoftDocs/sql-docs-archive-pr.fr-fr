---
title: Architecture logique (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], about mining structures
- logical architecture [Data Mining]
- architecture [Analysis Services], mining models
- mining models [Analysis Services], about data mining models
- architecture [Analysis Services]
ms.assetid: 4e0cbf46-cc60-4e91-a292-9a69f29746f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: e1af06d7ffe12301f6b8b678f41665e5c3146a13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698898"
---
# <a name="logical-architecture-analysis-services---data-mining"></a>Architecture logique (Analysis Services - Exploration de données)
  L'exploration de données est un processus qui implique l'interaction de plusieurs composants.  
  
-   Vous accédez aux sources de données dans une base de données SQL Server ou à toute autre source de données à utiliser pour l’apprentissage, le test ou les prédictions.  
  
-   Vous définissez des structures et des modèles d'exploration de données à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou Visual Studio.  
  
-   Vous gérez des objets d'exploration de données et créez des prédictions ainsi que des requêtes avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   Quand la solution est complète, vous pouvez la déployer sur une instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Le processus de création de ces objets de solution a déjà été décrit. Pour plus d’informations, consultez [Solutions d’exploration de données](data-mining-solutions.md).  
  

  
##  <a name="data-mining-source-data"></a><a name="bkmk_SourceData"></a>Données sources de l’exploration de données  
 Les données utilisées dans l'exploration de données ne sont pas stockées dans la solution d'exploration de données ; seules les liaisons sont stockées. Les données peuvent résider dans une base de données créée dans une version précédente de SQL Server, un système CRM, ou même un fichier plat. Lors de l'apprentissage de la structure ou du modèle par traitement, un résumé statistiques des données est créé et stocké dans un cache qui peut être rendu persistant pour une utilisation dans des opérations ultérieures, ou supprimé après le traitement. Pour plus d’informations, consultez [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md).  
  
 Vous combinez des données disparates dans l’objet de vue de source de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , qui fournit une couche d’abstraction sur votre source de données. Vous pouvez spécifier des jointures entre les tables ou ajouter des tables qui ont une relation plusieurs-à-un pour créer des colonnes de table imbriquée. La définition de ces objets, la source de données et la vue de source de données sont stockées dans la solution avec les extensions de noms de fichiers *.ds et \*.dsv. Pour plus d’informations sur la création et l’utilisation de sources de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et de vues de sources de données, consultez [sources de données prises en charge &#40;&#41;multidimensionnels SSAS ](../multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Vous pouvez également définir et modifier des sources de données et des vues de source de données en utilisant AMO ou XMLA. Pour plus d’informations sur l’utilisation de ces objets par programmation, consultez [Vue d’ensemble de l’architecture logique &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md).  
  

  
##  <a name="mining-structures"></a><a name="bkmk_Structures"></a>Structures d’exploration de données  
 Une structure d'exploration de données est un conteneur de données logiques qui définit le domaine de données à partir duquel les modèles d'exploration de données sont créés. Une structure d'exploration de données unique peut prendre en charge plusieurs modèles d'exploration de données.  
  
 Lorsque vous devez utiliser les données de la solution d'exploration de données, Analysis Services les lit à partir de la source et génère un cache d'agrégats et d'autres informations. Par défaut ce cache est persistant afin que les données d'apprentissage puissent être réutilisées pour prendre en charge les modèles supplémentaires. Si vous devez supprimer le cache, donnez à la propriété `CacheMode` sur l'objet de structure d'exploration de données la valeur `ClearAfterProcessing`. Pour plus d’informations, consultez [Classes d’exploration de données AMO](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] permet également de séparer vos données en jeux de données d’apprentissage et de test afin de tester vos modèles d’exploration de données sur un jeu de données représentatif et sélectionné aléatoirement. Les données ne sont pas réellement stockées séparément ; en revanche, les données de cas dans le cache de la structure sont identifiées par une propriété qui indique si ce cas particulier est utilisé pour l'apprentissage ou pour le test. Si le cache est supprimé, ces informations ne peuvent pas être récupérées.  
  
 Pour plus d’informations, consultez [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md).  
  
 Une structure d'exploration de données peut contenir des tables imbriquées. Une table imbriquée fournit des détails supplémentaires sur le cas modélisé dans la table de données primaire. Pour plus d’informations, consultez [Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](nested-tables-analysis-services-data-mining.md).  
  
 
  
##  <a name="mining-models"></a><a name="bkmk_Models"></a>Modèles d’exploration de données  
 Avant le traitement, un modèle d'exploration de données n'est qu'une combinaison de propriétés de métadonnées. Ces propriétés spécifient une structure d'exploration de données, un algorithme d'exploration de données ainsi qu’une collection définie de paramétrages et de paramètres de filtre qui affectent les données utilisées et leur mode de traitement. Pour plus d’informations, consultez [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-models-analysis-services-data-mining.md).  
  
 Lorsque vous traitez le modèle, les données d'apprentissage qui étaient stockées dans le cache de la structure d'exploration de données sont utilisées pour générer des schémas, basés sur les propriétés statistiques des données et sur l'heuristique définie par l'algorithme et ses paramètres. Ceci porte le nom *d’apprentissage* du modèle.  
  
 Le résultat de l’apprentissage est un jeu de données de synthèse, qui figure dans le *contenu de modèle*et décrit les schémas trouvés, et fournit les règles selon lesquelles les prédictions sont générées. Pour plus d’informations, consultez [Contenu du modèle d’exploration &#40;Analysis Services - Exploration de données&#41;](mining-model-content-analysis-services-data-mining.md).  
  
 Dans certains cas, la structure logique du modèle peut également être exportée dans un fichier qui représente des formules de modèle et des liaisons de données conformément à un format standard, le langage PMML (Predictive Modeling Markup Language). Cette structure logique peut être importée dans d'autres systèmes qui utilisent PMML et le modèle ainsi décrit peut ensuite être utilisé pour la prédiction. Pour plus d’informations, consultez [Présentation de l’instruction DMX Select](/sql/dmx/understanding-the-dmx-select-statement).  
  

  
##  <a name="custom-data-mining-objects"></a><a name="bkmk_CustomObjects"></a>Objets d’exploration de données personnalisés  
 D'autres objets que vous utilisez dans le contexte d'un projet d'exploration de données, tels que les graphiques d'analyse de précision ou des requêtes de prédiction, ne sont pas conservés dans la solution, mais peuvent faire l'objet d'un script à l'aide d'ASSL ou être générés à l'aide d'AMO.  
  
 En outre, vous pouvez étendre les services et les fonctionnalités disponibles sur une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en ajoutant ces objets personnalisés :  
  
 **Assemblys personnalisés**  
 Les assemblys .NET peuvent être définis à l'aide du langage compatible CLR ou COM, puis enregistrés avec une instance de SQL Server. Les fichiers d'assemblys sont chargés à partir de l'emplacement défini par l'application et une copie est enregistrée avec les données, dans le serveur. La copie du fichier d'assembly est utilisée pour charger l'assembly chaque fois que le service est démarré.  
  
 Pour plus d’informations, consultez [Gestion des assemblys de modèles multidimensionnels](../multidimensional-models/multidimensional-model-assemblies-management.md).  
  
 **Procédures stockées personnalisées**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] L’exploration de données prend en charge l’utilisation de procédures stockées pour utiliser des objets d’exploration de données. Vous pouvez créer vos propres procédures stockées pour étendre les fonctionnalités et utiliser plus facilement les données retournées par des requêtes de prédiction et des requêtes de contenu.  
  
 [Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
 Les procédures stockées suivantes sont prises en charge pour être utilisées dans les validations croisées.  
  
 [Procédures stockées d’exploration de données &#40;Analysis Services - Exploration de données&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
 En outre, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contient de nombreuses procédures stockées système qui sont utilisées en interne pour l'exploration de données. Bien que les procédures stockées système sont réservées à un usage interne, elles peuvent s'avérer d'utiles raccourcis. Microsoft se réserve le droit de modifier ces procédures stockées si nécessaire ; par conséquent, dans un environnement de production, nous vous recommandons de créer des requêtes avec DMX, AMO, ou XMLA.  
  
 **Algorithmes de plug-in personnalisés**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit un mécanisme pour créer vos propres algorithmes, puis ajouter les algorithmes sous forme de nouveau service d’exploration de données à l’instance de serveur.  
  
 Analysis Services utilise ces interfaces COM pour communiquer avec les algorithmes de plug-in. Pour en savoir plus sur la manière d’implémenter de nouveaux algorithmes, consultez [Algorithmes de plug-in](plugin-algorithms.md).  
  
 Vous devez inscrire chaque nouveau algorithme avant de pouvoir l'utiliser. Pour inscrire un algorithme, ajoutez les métadonnées requises pour les algorithmes dans le fichier .ini de l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous devez ajouter les informations à chaque instance dans laquelle vous envisagez d'utiliser le nouvel algorithme. Après avoir ajouté l'algorithme, vous pouvez redémarrer l'instance, puis utilisez l'ensemble de lignes de schéma MINING_SERVICES pour afficher le nouvel algorithme, y compris les options et les fournisseurs que l'algorithme prend en charge.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Traitement d’objets de modèle multidimensionnel](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Référence DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
