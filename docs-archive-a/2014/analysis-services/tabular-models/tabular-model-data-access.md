---
title: Accès aux données du modèle tabulaire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6ae74a8b-0025-450d-94a5-4e601831d420
author: minewiskan
ms.author: owend
ms.openlocfilehash: e9d7c336c549513ff6bd7cc3a2b409ec8776e581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706783"
---
# <a name="tabular-model-data-access"></a>Accès aux données de modèle tabulaire
  Les bases de données model tabulaires dans Analysis Services sont accessibles par la plupart des mêmes clients, interfaces et langues que vous utilisez pour récupérer les données ou les métadonnées d'un modèle multidimensionnel. Pour plus d’informations, consultez [Accès aux données de modèles multidimensionnels &#40;Analysis Services - Données multidimensionnelles &#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md).  
  
 Cette rubrique décrit les clients, les langages de requête et les interfaces de programmation qui fonctionnent avec des modèles tabulaires.  
  
## <a name="clients"></a>Clients  
 Les applications clientes Microsoft suivantes prennent en charge les connexions natives aux bases de données model tabulaires de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
### <a name="excel"></a>Excel  
 Vous pouvez vous connecter aux bases de données model tabulaires Excel à l'aide des fonctionnalités de visualisation et d'analyse des données dans Excel pour travailler avec vos données. Pour accéder aux données, vous définissez une connexion de données Analysis Services, vous spécifiez un serveur qui s'exécute en mode serveur tabulaire, puis vous choisissez la base de données que vous souhaitez utiliser. Pour plus d'informations, consultez [Se connecter ou importer des données à partir de SQL Server Analysis Services](https://go.microsoft.com/fwlink/?linkID=215150).  
  
 Excel est également recommandé pour parcourir les modèles tabulaires dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. L'outil inclut une option **Analyser dans Excel** qui démarre une nouvelle instance Excel, crée un classeur Excel et ouvre une connexion de données entre le classeur et la base de données model d'espace de travail. Lorsque vous parcourez les données de modèle tabulaire dans Excel, sachez qu'Excel émet des requêtes sur le modèle à l'aide du client Tableau croisé dynamique Excel. Par conséquent, les opérations du classeur Excel provoquent l'envoi de requêtes MDX à la base de données d'espace de travail, et non de requêtes DAX. Si vous utilisez SQL Profiler ou un autre outil d'analyse pour surveiller les requêtes, vous verrez MDX et non DAX dans la trace de Profiler. Pour plus d’informations sur la fonctionnalité Analyser dans Excel, consultez [Analyser dans Excel &#40;SSAS Tabulaire&#41;](analyze-in-excel-ssas-tabular.md).  
  
### <a name="power-view"></a>Power View  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] est une application cliente Reporting Services qui s'exécute dans un environnement SharePoint 2010. Elle associe l'exploration de données, la création de requêtes et la disposition de présentation dans une expérience de rapports intégrée ad hoc. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] peut utiliser des modèles tabulaires comme sources de données, que le modèle soit stocké dans un classeur PowerPivot autonome, soit hébergé sur une instance d'Analysis Services s'exécutant en mode tabulaire ou soit extrait d'une banque de données relationnelles à l'aide du mode DirectQuery. Pour vous connecter à un modèle tabulaire dans [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], vous devez créer un fichier de connexion qui contient l'emplacement du serveur et de la base de données. Vous pouvez créer une source de données partagées Reporting Services ou un fichier de connexion de modèle sémantique BI dans SharePoint. Pour plus d’informations sur les connexions de modèle sémantique BI, consultez [connexion de modèle sémantique bi PowerPivot &#40;&#41;. BISM ](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md).  
  
 Le client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] détermine la structure du modèle spécifié en envoyant une requête à la source de données spécifiée, qui retourne un schéma pouvant être utilisé par le client pour créer des requêtes sur le modèle en tant que source de données et pour effectuer des opérations sur les données. Les opérations qui suivent dans l'interface utilisateur de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] pour filtrer les données, effectuer des calculs ou des agrégations et afficher les données associées sont contrôlées par le client et ne peuvent pas être manipulées par programme.  
  
 Les requêtes qui sont envoyées par le client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] au modèle sont émises en tant qu'instructions DAX, que vous pouvez surveiller en définissant une trace sur le modèle.  Le client envoie également une requête au serveur pour la définition de schéma initiale, qui est présentée en langage CSDL (Conceptual Schema Definition Language). Pour plus d’informations, consultez [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour gérer les instances qui hébergent des modèles tabulaires et pour interroger les métadonnées et les données qu'elles contiennent. Vous pouvez traiter des modèles ou les objets d'un modèle, créer et gérer des partitions et définir la sécurité qui peut être utilisée pour gérer l'accès aux données. Pour plus d'informations, voir les rubriques suivantes :  
  
-   [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
-   [Se connecter à Analysis Services](../instances/connect-to-analysis-services.md)  
  
-   [Monitor an Analysis Services Instance](../instances/monitor-an-analysis-services-instance.md)  
  
 Vous pouvez utiliser les fenêtres de requête MDX et XMLA dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour récupérer les données et les métadonnées d'une base de données de modèle tabulaire. Toutefois, notez les restrictions suivantes :  
  
-   Les instructions utilisant MDX et DMX ne sont pas prises en charge pour les modèles déployés en mode DirectQuery ; par conséquent, si vous devez créer une requête sur un modèle tabulaire en mode DirectQuery, vous devez utiliser une fenêtre de **Requête XMLA** à la place.  
  
-   Vous ne pouvez pas modifier le contexte de base de données de la fenêtre Requête XMLA après avoir ouvert la fenêtre **Requête** . Par conséquent, si vous devez envoyer une requête à une autre base de données ou à une autre instance, vous devez ouvrir cette base de données ou cette instance à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et ouvrir une nouvelle fenêtre **Requête XMLA** dans ce contexte.  
  
 Vous pouvez créer des traces sur un modèle tabulaire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comme sur une solution multidimensionnelle. Dans cette version, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit de nombreux nouveaux événements qui peuvent être utilisés pour suivre l'utilisation de la mémoire, les opérations de requête et de traitement et l'utilisation de fichiers. Pour plus d’informations, consultez [Événements de trace Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events).  
  
> [!WARNING]  
>  Si vous faites le suivi d'une base de données de modèle tabulaire, vous pouvez voir certains événements catégorisés en tant que requêtes DMX. Toutefois, l'exploration de données n'est pas prise en charge sur les données de modèle tabulaire et les requêtes DMX effectuées sur la base de données sont limitées aux instructions SELECT sur les métadonnées du modèle. Les événements sont catégorisés en tant que DMX uniquement parce que la même infrastructure d'analyseur est utilisée pour MDX.  
  
## <a name="query-languages"></a>Langages de requête  
 Les modèles tabulaires Analysis Services prennent en charge la plupart des mêmes langages de requête qui sont fournis pour accéder aux modèles multidimensionnels. À l'exception des modèles tabulaires qui ont été déployés en mode DirectQuery, ces derniers ne récupèrent pas les données d'une banque de données Analysis Services, mais directement d'une source de données SQL Server. Vous ne pouvez pas interroger ces modèles à l’aide de MDX, mais devez utiliser un client qui prend en charge la conversion des expressions DAX en instructions Transact-SQL, tel que le client [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
### <a name="dax"></a>DAX  
 Vous pouvez utiliser DAX pour créer des expressions et des formules dans tous les types de modèles tabulaires, que le modèle soit stocké sur SharePoint en tant que classeur Excel compatible PowerPivot ou sur une instance d'Analysis Services.  
  
 En outre, vous pouvez utiliser des expressions DAX dans le contexte d'une instruction de commande XMLA EXECUTE pour envoyer des requêtes à un modèle tabulaire déployé en mode DirectQuery.  
  
 Pour obtenir des exemples de requêtes sur un modèle tabulaire à l’aide de DAX, consultez [informations de référence sur la syntaxe de requête DAX] (/DAX/Dax-Syntax-Reference
  
### <a name="mdx"></a>MDX  
 Vous pouvez utiliser MDX pour créer des requêtes sur des modèles tabulaires qui utilisent le cache en mémoire comme méthode de requête par défaut (autrement dit, les modèles qui n'ont pas été déployés en mode DirectQuery). Bien que les clients tels que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] utilisent DAX pour créer des agrégations et pour interroger le modèle comme source de données, si vous êtes familiarisé avec MDX, il sera plus rapide de créer des exemples de requêtes dans MDX. Consultez [Génération de mesures dans une expression MDX](../multidimensional-models/mdx/mdx-building-measures.md).  
  
### <a name="csdl"></a>CSDL  
 Le langage CSDL (Conceptual Schéma Definition Language) n'est pas un langage de requête en soi, mais il peut être utilisé pour récupérer des informations sur le modèle et les métadonnées du modèle, qui peuvent être utilisés plus tard pour créer des rapports ou pour créer des requêtes sur le modèle.  
  
 Pour plus d’informations sur la façon dont le langage CSDL est utilisé dans les modèles tabulaires, consultez [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi).  
  
## <a name="programmatic-interfaces"></a>Interfaces de programmation  
 Les interfaces principales utilisées pour interagir avec des modèles tabulaires d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont les ensembles de lignes de schéma, XMLA, ainsi que les clients de requête et les outils de requête fournis par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
### <a name="data-and-metadata"></a>Données et métadonnées  
 Vous pouvez récupérer des données et des métadonnées des modèles tabulaires dans les applications managées utilisant ADOMD.NET. Pour obtenir des exemples d'applications qui créent et modifient des objets dans un modèle tabulaire, consultez les ressources suivantes :  
  
-   Exemple AMO de modèle tabulaire sur Codeplex  
  
-   [Utiliser des vues de gestion dynamique &#40;DMV&#41; pour surveiller Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
 Vous pouvez utiliser le fournisseur OLE DB pour Analysis Services 9.0 dans des applications clientes non managées afin de prendre en charge l'accès du fournisseur OLE DB aux modèles tabulaires. Une version mise à jour du fournisseur OLE DB pour Analysis Services est nécessaire pour activer l'accès au modèle tabulaire. Pour plus d’informations sur les fournisseurs utilisés avec les modèles tabulaires, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) .  
  
 Vous pouvez également récupérer les données directement à partir d'une instance d'Analysis Services en format XML. Vous pouvez récupérer le schéma du modèle tabulaire à l'aide de l'ensemble de lignes DISCOVER_CSDL_METADATA ou vous pouvez utiliser une commande EXECUTE ou DISCOVER avec des éléments ASSL, des objets ou des propriétés existants. Pour plus d’informations, consultez les ressources suivantes :  
  
-   [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
### <a name="manipulate-analysis-services-objects"></a>Manipulation des objets Analysis Services  
 Vous pouvez créer, modifier, supprimer, et traiter des modèles tabulaires et les objets qu'ils contiennent, notamment des tables, des colonnes, des perspectives, des mesures et des partitions, à l'aide des commandes XMLA ou en utilisant AMO. AMO et XMLA ont été mis à jour pour prendre en charge les propriétés supplémentaires utilisées dans les modèles tabulaires pour une création de rapports et une modélisation améliorées.  
  
 Pour obtenir des exemples sur la création de script à partir d'objets tabulaires en utilisant AMO et XMLA, consultez les ressources suivantes :  
  
-   Exemple AMO de modèle tabulaire sur Codeplex  
  
-   Exemples AdventureWorks sur CodePlex  
  
 Vous pouvez utiliser PowerShell pour gérer et surveiller des instances d'Analysis Services, ainsi que pour créer et surveiller la sécurité utilisée pour l'accès au modèle tabulaire. Pour plus d’informations, consultez [Analysis Services PowerShell](../analysis-services-powershell.md).  
  
### <a name="schema-rowsets"></a>Ensembles de lignes de schéma  
 Les applications clientes peuvent utiliser les ensembles de lignes de schéma pour examiner les métadonnées des modèles tabulaires et récupérer les informations de prise en charge et de surveillance du serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Dans cette version de SQL Server, de nouveaux ensembles de lignes de schéma ont été ajoutés et des ensembles de lignes de schéma existants ont été étendus pour prendre en charge des fonctionnalités relatives aux modèles tabulaires et pour améliorer la surveillance et l'analyse des performances sur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   [DISCOVER_CALC_DEPENDENCY, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset)  
  
     Nouvel ensemble de lignes de schéma pour suivre les dépendances entre les colonnes et les références d'un modèle tabulaire  
  
-   [DISCOVER_CSDL_METADATA, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)  
  
     Nouvel ensemble de lignes de schéma pour obtenir la représentation CSDL d'un modèle tabulaire  
  
-   [DISCOVER_XEVENT_TRACE_DEFINITION, ensemble de lignes](../dev-guide/discover-xevent-trace-definition-rowset.md)  
  
     Nouvel ensemble de lignes de schéma pour surveiller les événements étendus SQL Server. Pour plus d’informations, consultez [utiliser des événements étendus SQL Server &#40;XEvents&#41; pour analyser les Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md).  
  
-   [DISCOVER_TRACES, ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-traces-rowset)  
  
     La nouvelle colonne `Type` vous permet de filtrer les traces par catégorie. Pour plus d’informations, consultez [Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](../instances/create-profiler-traces-for-replay-analysis-services.md).  
  
-   [Ensemble de lignes MDSCHEMA_HIERARCHIES](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset)  
  
     La nouvelle énumération `STRUCTURE_TYPE` prend en charge l'identification des hiérarchies définies par l'utilisateur créées dans les modèles tabulaires. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](hierarchies-ssas-tabular.md).  
  
 Il n'y a aucune mise à jour apportée à OLE DB pour les ensembles de lignes de schéma d'exploration de données dans cette version.  
  
> [!WARNING]  
>  Vous ne pouvez pas utiliser les requêtes MDX ou DMX dans une base de données déployée en mode DirectQuery ; par conséquent, si vous devez exécuter une requête sur un modèle DirectQuery à l'aide des ensembles de lignes de schéma, vous devez utiliser XMLA, et non le DMV associé. Pour les DMV qui retournent des résultats pour le serveur dans son ensemble, tels que SELECT * from $system.DBSCHEMA_CATALOGS ou DISCOVER_TRACES, vous pouvez exécuter la requête dans le contenu d'une base de données déployée en mode mis en cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à une base de données model tabulaire &#40;SSAS&#41;](connect-to-a-tabular-model-database-ssas.md)   
 [Accès aux données PowerPivot](../power-pivot-sharepoint/power-pivot-data-access.md)   
 [Se connecter à Analysis Services](../instances/connect-to-analysis-services.md)  
  
  
