---
title: Services d’exploration de données et sources de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b26fd6e3-7d87-4f66-ab47-5303b51b87da
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4b86ff2603e58210a66e7b40401ff8da7c938b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612628"
---
# <a name="data-mining-services-and-data-sources"></a>Services d'exploration de données et sources de données
  L'exploration de données requiert une connexion à une instance de SQL Server Analysis Services. Les données d’un cube ne sont pas nécessaires pour l’exploration de données et l’utilisation de sources relationnelles est recommandée. Toutefois, l’exploration de données utilise des composants fournis par le moteur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Cette rubrique fournit les informations à connaître pour établir une connexion à une instance de SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] afin de créer, traiter, déployer ou interroger des modèles d’exploration de données.  
  
## <a name="data-mining-services"></a>Services d'exploration de données  
 Le composant serveur de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est l’application msmdsrv.exe, qui s’exécute habituellement en tant que service Windows. Cette application intègre des composants de sécurité, un composant d'écoute XMLA (XML for Analysis), un composant processeur de requêtes et de nombreux autres composants internes qui permettent d'effectuer les actions suivantes :  
  
-   Analyser des instructions reçues des clients  
  
-   Gérer des métadonnées  
  
-   Gérer des transactions  
  
-   Effectuer des calculs  
  
-   Stocker des données de dimension et de cellule  
  
-   Créer des agrégations  
  
-   Planifier des requêtes  
  
-   Mettre des objets en cache  
  
-   Gérer des ressources du serveur  
  
### <a name="xmla-listener"></a>Écouteur XMLA  
 Le composant écouteur XMLA gère toutes les communications XMLA entre [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et ses clients. Le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Port` paramètre de configuration dans le fichier msmdsrv.ini peut être utilisé pour spécifier un port sur lequel une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance écoute. La valeur 0 dans ce fichier indique qu' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] écoute sur le port par défaut. Sauf spécification contraire, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise par défaut les ports TCP suivants :  
  
|Port|Description|  
|----------|-----------------|  
|2383|Instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|2382|Redirecteur pour d’autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|Affectation dynamique au démarrage du serveur|Instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
  
 Pour plus d’informations sur le contrôle des ports utilisés par ce service, consultez [Configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
## <a name="connecting-to-data-sources"></a>Connexion à des sources de données  
 Chaque fois que vous créez ou mettez à jour une structure ou un modèle d'exploration de données, vous utilisez des données qui sont définies par une source de données. La source de données ne contient pas les données, lesquelles peuvent être des classeurs Excel, des fichiers texte et des bases de données SQL Server ; elle définit uniquement les informations de connexion.  Une vue de source de données (DSV) sert de couche d'abstraction au-dessus de cette source, modifiant ou mappant les données obtenues de la source.  
  
 La description des exigences de connexion pour chacune de ces sources dépasse l'objet de cette rubrique. Pour plus d'informations, consultez la documentation du fournisseur. Toutefois, vous devez en général garder à l'esprit les spécifications suivantes d'Analysis Services lorsque vous communiquer avec des fournisseurs :  
  
-   Étant donné que l'exploration de données est un service fourni par un serveur, l'accès à la source de données doit être accordé à l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  Il existe deux aspects à prendre en compte : l'emplacement et l'identité.  
  
     Pour**l’emplacement** , cela signifie que si vous créez un modèle avec des données stockées uniquement sur votre ordinateur, puis que vous déployez ce modèle sur un serveur, le traitement du modèle échouera, car la source de données sera introuvable. Pour résoudre ce problème, vous devrez peut-être transférer les données vers la même instance de SQL Server que celle où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est en cours d'exécution, ou déplacer les fichiers vers un emplacement partagé.  
  
     Pour**l’identité** , cela signifie que les services sur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] doivent pouvoir ouvrir le fichier de données ou la source de données avec les informations d’identification appropriées. Par exemple, quand vous avez créé le modèle, vous avez peut-être eu des autorisations illimitées pour afficher les données, mais l'utilisateur qui traite et met à jour les modèles sur le serveur peut avoir un accès limité ou aucun accès aux données, ce qui peut entraîner l'échec du traitement ou affecter le contenu d'un modèle. Le compte utilisé pour se connecter à la source de données distante doit au moins disposer d'autorisations en lecture sur les données.  
  
-   Lorsque vous déplacez un modèle, les mêmes exigences s'appliquent : vous devez configurer l'accès approprié à l'emplacement de l'ancienne source de données, copier les sources de données ou configurer une nouvelle source de données. De plus, vous devez transférer les connexions et les rôles, ou configurer des autorisations pour permettre le traitement et la mise à jour des objets d'exploration de données dans le nouvel emplacement.  
  
## <a name="configuring-permissions-and-server-properties"></a>Configuration d'autorisations et de propriétés de serveur  
 L'exploration de données requiert des autorisations supplémentaires sur une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . La plupart des propriétés d’exploration de données peuvent être définies dans la [boîte de dialogue Propriétés de Analysis Server &#40;Analysis Services&#41;](../analysis-server-properties-dialog-box-analysis-services.md).  
  
 Pour plus d’informations sur les propriétés que vous pouvez configurer, consultez [configurer les propriétés du serveur dans Analysis Services](../server-properties/server-properties-in-analysis-services.md).  
  
 Les propriétés de serveur suivantes concernent plus particulièrement l'exploration de données :  
  
-   `AllowAdHocOpenRowsetQueries`Contrôle l’accès ad hoc aux fournisseurs OLE DB, qui sont chargés directement dans l’espace mémoire du serveur.  
  
    > [!IMPORTANT]  
    >  Pour améliorer la sécurité, il est recommandé d'attribuer la valeur `false` à cette propriété. La valeur par défaut est `false`. Cependant, même si cette propriété est affectée de la valeur `false`, les utilisateurs peuvent continuer à créer des requêtes singleton et utiliser la fonction OPENQUERY sur les sources de données autorisées.  
  
-   **AllowedProvidersInOpenRowset** Spécifie le fournisseur, si l’accès ad hoc est activé. Vous pouvez spécifier plusieurs fournisseurs, en entrant une liste séparée par des virgules de ProgID.  
  
-   **MaxConcurrentPredictionQueries** Contrôle la charge sur le serveur causée par les prédictions. La valeur par défaut 0 autorise les requêtes illimitées pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise et un maximum de cinq requêtes simultanées pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard. Les requêtes qui dépassent la limite sont sérialisées et peuvent expirer.  
  
 Le serveur fournit des propriétés supplémentaires qui contrôlent les algorithmes d'exploration de données disponibles, y compris toutes les restrictions appliquées aux algorithmes, ainsi que les valeurs par défaut de tous les services d'exploration de données. Toutefois, il n'existe pas de paramètre permettant de contrôler spécifiquement l'accès aux procédures stockées de l'exploration de données. Pour plus d’informations, consultez [Propriétés de l’exploration de données](../server-properties/data-mining-properties.md).  
  
 Vous pouvez également définir des propriétés qui vous permettent de régler le serveur et contrôler la sécurité pour l'utilisation des clients. Pour plus d’informations, consultez [Propriétés de fonctionnalité](../server-properties/feature-properties.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur la prise en charge des algorithmes de plug-in par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) ( https://go.microsoft.com/fwlink/?linkid=232473) .  
  
## <a name="programmatic-access-to-data-mining-objects"></a>Accès par programmation aux objets d'exploration de données  
 Vous pouvez utiliser les modèles d'objet suivants pour créer une connexion à une base de données Analysis Services et utiliser des objets d'exploration de données :  
  
 **ADO** Utilise OLE DB pour se connecter à un serveur Analysis Services. Lorsque vous utilisez ADO, le client est limité aux requêtes sur un ensemble de lignes de schéma et aux instructions DMX.  
  
 **ADO.NET** Interagit avec les fournisseurs SQL Server plus efficacement qu’avec d’autres fournisseurs. Utilise des adaptateurs de données pour stocker des ensembles de lignes dynamiques. Utilise l'objet Dataset, qui est un cache des données de serveur stockées sous forme de tables de données et pouvant être mises à jour ou enregistrées au format XML.  
  
 **ADOMD.NET** Fournisseur de données managées qui est optimisé pour l’exploration de données et OLAP. ADOMD.NET est plus rapide et plus économe en mémoire qu'ADO.NET. ADOMD.NET vous permet également d'extraire des métadonnées relatives à des objets serveur. Recommandé pour les applications clientes, sauf lorsque .NET n'est pas disponible.  
  
 **Serveur ADOMD** Modèle objet permettant d’accéder aux objets Analysis Services directement sur le serveur. Destiné aux procédures stockées Analysis Services ; et non à l'usage des clients  
  
 **AMO** Interface de gestion d’Analysis Services qui remplace DSO (Decision Support Objects). Certaines opérations, telles que l'itération d'objets, requièrent des autorisations plus élevées lorsque AMO est utilisé à la place d'autres interfaces. Cela est dû au fait qu'AMO accède directement aux métadonnées, alors qu'ADOMD.NET et les autres interfaces accèdent uniquement aux schémas de base de données.  
  
### <a name="browse-and-query-access-to-servers"></a>Navigation et accès par requête à des serveurs  
 Vous pouvez effectuer tous les types de prédictions à l'aide d'une instance d'Analysis Services en mode OLAP/Exploration de données, avec les restrictions suivantes :  
  
-   Si vous utilisez Server ADOMD, vous pouvez accéder au serveur à l'aide de DMX sans établir de connexion. Vous pouvez ensuite copier les résultats directement dans une table de données. Toutefois, vous ne pouvez pas utiliser Server ADOMD avec des instances distantes; vous pouvez interroger uniquement le serveur local.  
  
-   ADO.NET ne prend pas en charge les paramètres nommés pour l'exploration de données. Vous devez utiliser ADOMD.NET.  
  
-   ADOMD.NET vous permet de traiter une table entière à utiliser comme paramètre ; par conséquent, vous pouvez utiliser les données sur le client, ou les données qui ne sont pas disponibles pour le serveur. Vous pouvez également utiliser des tables spécifiques comme entrée pour les prédictions.  
  
### <a name="using-data-mining-stored-procedures"></a>Utilisation des procédures stockées de l'exploration de données  
 Les procédures stockées sont habituellement employées pour encapsuler des requêtes en vue de leur réutilisation. Le client peut utiliser CALL pour exécuter des procédures stockées, y compris des procédures stockées système [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si la procédure retourne un dataset, le client reçoit un dataset ou datatable avec une table imbriquée contenant les lignes. Par exemple, si vous créez une requête sur le contenu d'un modèle, la requête retourne tout le modèle. Pour éviter de récupérer trop de lignes, vous pouvez écrire des procédures stockées en utilisant le modèle objet ADOMD+.  
  
 Pour écrire une procédure stockée de serveur, vous devez référencer l'espace de noms Microsoft.AnalysisServices.AdomdServer. Pour plus d’informations sur la création et l’utilisation des procédures stockées, consultez [Fonctions définies par l’utilisateur et procédures stockées](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures).  
  
> [!NOTE]  
>  Les procédures stockées ne peuvent pas être utilisées pour modifier la sécurité sur des objets serveur de données. Lorsque vous exécutez une procédure stockée, le contexte actuel de l'utilisateur est utilisé pour déterminer l'accès à tous les objets de serveur. Par conséquent, les utilisateurs doivent disposer des autorisations appropriées sur tous les objets de base de données auxquels ils accèdent.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture physique &#40;Analysis Services-données multidimensionnelles&#41;](../multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)   
 [Architecture physique &#40;Analysis Services d’exploration de données&#41;](physical-architecture-analysis-services-data-mining.md)   
 [Gestion des solutions et des objets d'exploration de données](management-of-data-mining-solutions-and-objects.md)  
  
  
