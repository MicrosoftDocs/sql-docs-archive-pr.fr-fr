---
title: Type de connexion de liste SharePoint (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2c4adf2f-e9c4-4fae-bd3c-97fe64436caf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dbe50adbf8d4daa7b616dad7f40d185a4c923d77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603258"
---
# <a name="sharepoint-list-connection-type-ssrs"></a>Type de connexion de liste SharePoint (SSRS)
  Pour inclure des données d'une liste Microsoft SharePoint dans votre rapport, vous devez ajouter ou créer un dataset basé sur une source de données de rapport de type Liste Microsoft SharePoint. Il s'agit d'un type de source de données intégré basé sur l'extension de données Liste SharePoint Microsoft SQL Server Reporting Services. Utilisez ce type de source de données pour vous connecter à et récupérer des données de liste des sites [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], [!INCLUDE[SPS2010](../../includes/sps2010-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 et [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007.  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions pas à pas, consultez [Ajouter et vérifier une connexion de données ou une source de données &#40;générateur de rapports et des&#41;SSRS ](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a>Chaîne de connexion  
 La chaîne de connexion à une liste SharePoint est l'URL pointant vers le site ou sous-site SharePoint, par exemple `http://MySharePointWeb/MySharePointSite` ou `http://MySharePointWeb/MySharePointSite/Subsite`.  
  
 Le concepteur de requêtes affiche automatiquement les listes SharePoint pour lesquelles vous disposez d'autorisations d'accès suffisantes.  
  
 Pour obtenir d’autres exemples sur les chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="credentials"></a><a name="Credentials"></a>Informations d’identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports. Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports. Les types d'informations d'identification qui peuvent être utilisés avec cette extension de données dépendent de la configuration de la technologie SharePoint pour la liste SharePoint que vous utilisez comme source de données.  
  
 Les tableaux suivants décrivent le comportement de récupération des informations d'identification pour l'extension de liste SharePoint lors de la connexion à une liste SharePoint locale de batteries de serveurs et à une liste SharePoint distante.  
  
 Le**tableau 1** dresse la liste des rapports déployés sur un site Windows SharePoint hérité. Un site Windows hérité prend en charge uniquement l'authentification Kerberos, NTLM et à base de formulaires (FBA). Le**tableau 2** dresse la liste des rapports déployés sur un site SharePoint basé sur les revendications.  
  
 **Table 1**  
  
||Informations d'identification prises en charge|Mode d'authentification Windows classique|<sup>3</sup> authentification par revendications|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|Liste SharePoint locale de batteries de serveurs|Jeton utilisateur pour l'authentification Windows (intégrée) ou SharePoint|Oui|Oui|  
||Stockage, invite, aucun (avec les informations d'identification Windows<sup>1</sup>)|Oui|Non|  
|Liste SharePoint distante|Jeton utilisateur pour l'authentification Windows (intégrée) ou SharePoint|Oui|Non <sup>2</sup>|  
||Stockage, invite, aucun (avec les informations d'identification Windows<sup>1</sup>)|Oui|Non <sup>2</sup>|  
  
 **Tableau 2**  
  
||Informations d'identification prises en charge|Mode d'authentification Windows classique|<sup>3</sup> authentification par revendications|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|Liste SharePoint locale de batteries de serveurs|Jeton utilisateur pour l'authentification Windows (intégrée) ou SharePoint|Oui|Oui|  
||Stockage, invite, aucun (avec les informations d'identification Windows<sup>1</sup>)|Non|Non|  
|Liste SharePoint distante|Jeton utilisateur pour l'authentification Windows (intégrée) ou SharePoint|Oui|Non <sup>2</sup>|  
||Stockage, invite, aucun (avec les informations d'identification Windows<sup>1</sup>)|Non|Non <sup>2</sup>|  
  
 <sup>1</sup> les informations d’identification stockées et de confirmation avec des informations d’identification non-Windows ne sont pas prises en charge.  
  
 <sup>2</sup> l’authentification basée sur les formulaires et l’authentification basée sur les revendications ne sont pas prises en charge pour les listes SharePoint distantes.  
  
 <sup>3</sup> authentification Windows, authentification basée sur des formulaires (FBA), jetons SAML (Secure Application Markup Language), autres fournisseurs d’identité ou combinaison de plusieurs fournisseurs d’authentification mentionnés ci-dessus.  
  
 **Authentification Windows**  
 Pour une technologie SharePoint configurée pour être utilisée avec un serveur de rapports en mode Compte approuvé, cette option n’est pas prise en charge. Cela s'applique uniquement aux versions antérieures à SQL Server 2012 Reporting Services.  
  
 Pour une technologie SharePoint configurée pour être utilisée avec un serveur de rapports en mode intégré Windows, cette option s'applique à la fois à l'utilisateur Windows actuel et à l'utilisateur SharePoint actuel.  
  
 Pour une technologie SharePoint configurée pour être utilisée sans serveur de rapports (mode local), cette option n'est pas prise en charge. Pour plus d’informations sur le mode local, consultez rapports en mode [local et rapports en mode connecté dans la visionneuse de rapports &#40;Reporting Services en mode SharePoint&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
 **Informations d'identification non requises (ne pas utiliser d'informations d'identification) :**  
 Pour utiliser cette option, vous devez avoir configuré le compte d'exécution sans assistance sur le serveur de rapports. Pour plus d’informations, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
 Pour plus d'informations sur la prise en charge de l'authentification par revendications dans la pile Microsoft BI, consultez [Utilisation de l'authentification par revendications dans la pile Microsoft BI](https://social.technet.microsoft.com/wiki/contents/articles/15274.using-claims-authentication-across-the-microsoft-bi-stack.aspx).  
  
 Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md), [spécifier les informations d’identification dans générateur de rapports](../specify-credentials-in-report-builder.md)et les sources de [données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
##  <a name="queries"></a><a name="Query"></a>Adressée  
 Pour concevoir une requête, créez un dataset selon la source de données, puis ouvrez le concepteur de requêtes associé. Pour plus d’informations, consultez [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
 Le concepteur de requêtes graphique de liste SharePoint affiche quatre volets :  
  
 **Listes SharePoint**  Affiche la liste de toutes les listes SharePoint sur le site pour cette source de données. Sélectionnez une liste, puis sélectionnez les champs que vous souhaitez dans votre requête. Les noms des champs dans ce volet sont les noms conviviaux SharePoint, également appelés noms complets. Pointez sur un élément pour afficher les propriétés suivantes dans l'info-bulle :  
  
-   **Nom** Nom unique du champ.  
  
-   **Identificateur** Identificateur unique du champ.  
  
-   **Type de champ** Type de données du champ.  
  
-   **Caché** Indique si le champ s'affiche dans l'affichage des listes SharePoint.  
  
 La sélection de champs dans plusieurs listes n'est pas prise en charge. Vous pouvez créer un dataset pour chaque liste et sélectionner des champs dans chaque dataset. Si les listes ont un champ en commun, vous pouvez utiliser la fonction de recherche dans une région de données de tableau matriciel liée à l'un des deux dataset pour extraire une valeur de l'autre dataset qui n'est pas lié à la région de données. Pour plus d’informations, consultez [Fonction de recherche &#40;Générateur de rapports et SSRS&#41;](../report-design/report-builder-functions-lookup-function.md).  
  
-   **Champs sélectionnés**  Affiche les champs que vous avez sélectionnés. Les noms des champs dans ce volet sont des noms conviviaux qu'un utilisateur SharePoint a spécifiés. Lorsque vous fermez le concepteur de requêtes, vous voyez ces noms dans la collection de champs de dataset dans le volet des données de rapport. La relation entre les noms uniques et les noms conviviaux est disponible dans la page [Boîte de dialogue Propriétés du dataset, Champs &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-fields-report-builder.md).  
  
-   **Filtres appliqués**  Limite les données retournées à partir de la liste SharePoint, avant que les données ne soient retournées vers le rapport. Sélectionnez le nom de champ, l'opérateur et la valeur à utiliser pour limiter les données récupérées dans la liste. Les opérateurs varient selon le type de données de la valeur que vous sélectionnez.  
  
     Vous ne pouvez pas modifier l'ordre de tri ni spécifier des groupes dans le concepteur de requêtes graphique. Pour ce faire, définissez des expressions de tri sur le dataset du rapport et des expressions de groupe sur les régions de données dans le rapport. Les paramètres de requête ne sont pas pris en charge. Pour filtrer des données dans le rapport, utilisez des filtres de rapport ou paramètres de rapport que vous créez. Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) et [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
-   **Résultats de la requête**  Affiche des lignes exemples qui sont retournées lors de l'exécution de la requête. Si les valeurs de liste SharePoint changent fréquemment sur le site SharePoint, les valeurs que vous voyez dans le volet des résultats de la requête peuvent différer de celles que vous voyez dans le rapport.  
  
-   **Champs sélectionnés**  Affiche les champs que vous avez sélectionnés. Les noms des champs dans ce volet sont des noms conviviaux qu'un utilisateur SharePoint a spécifiés. Lorsque vous fermez le concepteur de requêtes, vous voyez ces noms dans la collection de champs de dataset dans le volet des données de rapport. La relation entre les noms uniques et les noms conviviaux est disponible dans la page [Boîte de dialogue Propriétés du dataset, Champs &#40;Générateur de rapports&#41;](../dataset-properties-dialog-box-fields-report-builder.md).  
  
-   **Filtres appliqués**  Limite les données retournées à partir de la liste SharePoint, avant que les données ne soient retournées vers le rapport. Sélectionnez le nom de champ, l'opérateur et la valeur à utiliser pour limiter les données récupérées dans la liste. Les opérateurs varient selon le type de données de la valeur que vous sélectionnez.  
  
     Vous ne pouvez pas modifier l'ordre de tri ni spécifier des groupes dans le concepteur de requêtes graphique. Pour ce faire, définissez des expressions de tri sur le dataset du rapport et des expressions de groupe sur les régions de données dans le rapport. Les paramètres de requête ne sont pas pris en charge. Pour filtrer des données dans le rapport, utilisez des filtres de rapport ou paramètres de rapport que vous créez. Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) et [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
-   **Résultats de la requête**  Affiche des lignes exemples qui sont retournées lors de l'exécution de la requête. Si les valeurs de liste SharePoint changent fréquemment sur le site SharePoint, les valeurs que vous voyez dans le volet des résultats de la requête peuvent différer de celles que vous voyez dans le rapport.  
  
 Pour plus d’informations, consultez [Concepteur de requêtes de liste SharePoint &#40;Générateur de rapports&#41;](sharepoint-list-query-designer-report-builder.md).  
  
### <a name="query-text"></a>Texte de la requête  
 Pour afficher la requête générée par le concepteur de requêtes graphique, basculez vers le concepteur de requêtes textuel. Dans ce mode, vous pouvez voir le code XML qui est créé par le concepteur de requêtes graphique. Le code XML inclut des éléments pour le nom de liste, la collection de champs et le filtre.  
  
#### <a name="example-1-specified-fields-for-a-list"></a>Exemple 1. Champs spécifiés pour une liste  
 L'exemple suivant illustre une requête SharePoint bien formée :  
  
```  
<RSSharePointList>  
<listName>MyList</listName>  
<viewFields>  
  <FieldRef Name="Field1"/>  
  <FieldRef Name="Field4"/>  
</viewFields>  
<Query>  
  <Where>  
    <And>  
      <Gt>  
        <FieldRef Name="Field1"/>  
        <Value Type="Integer">1</Value>  
      </Gt>  
      <IsNotNull>  
        <FieldRef Name="Field2"/>  
        <Value Type="string"/>  
      </IsNotNull>   
    </And>  
  </Where>  
</Query>  
</RSSharePointList>  
```  
  
 Vous pouvez modifier cet affichage de la requête tant qu'elle se présente sous la forme de texte XML bien formé.  
  
#### <a name="example-2-all-fields-for-a-list"></a>Exemple 2. Tous les champs pour une liste  
 Vous pouvez également spécifier uniquement le nom d'une liste, et tous les champs, notamment les champs masqués, sont retournés. L'exemple suivant récupère tous les champs dans une liste nommée Tasks :  
  
```  
<RSSharePointList>  
<listName>Tasks</listName>  
</RSSharePointList>  
```  
  
 Tous les champs de la liste Tasks sont retournés dans les résultats de la requête.  
  
##  <a name="parameters"></a><a name="Parameters"></a> Paramètres  
 Les paramètres ne sont pas pris en charge par cette extension de données.  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Rubriques de procédures  
 Cette section contient des instructions pas à pas sur l'utilisation des connexions de données, des sources de données et des datasets.  
  
 [Ajouter et vérifier une connexion de données ou une source de données &#40;Générateur de rapports et SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Ajouter un filtre à un dataset &#40;Générateur de rapports et SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a>Sections connexes  
 Ces sections de la documentation fournissent des informations de fond d'ordre conceptuel sur les données de rapport, ainsi que des informations sur les procédures de définition, de personnalisation et d'utilisation des parties d'un rapport qui sont liées aux données.  
  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)  
 Fournit une vue d'ensemble de l'accès aux données pour votre rapport.  
  
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Fournit des informations sur les connexions de données et les sources de données.  
  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Fournit des informations sur les datasets incorporés et partagés.  
  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Fournit des informations sur la collection de champs de dataset générée par la requête.  
  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) dans la section [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentation en ligne](https://go.microsoft.com/fwlink/?linkid=121312) de .  
 Fournit des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et de Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier les données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
