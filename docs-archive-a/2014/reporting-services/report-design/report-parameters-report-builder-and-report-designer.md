---
title: Paramètres de rapport (Générateur de rapports et Concepteur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.subreportproperties.parameters.f1
- sql12.rtp.rptdesigner.reportparameters.general.f1
- "10091"
- "10073"
- "10070"
- sql12.rtp.rptdesigner.reportparameters.advanced.f1
ms.assetid: 58b96555-d876-4f61-bff8-db5764b9f5f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d8898a18e143c7954766b5a0bf9e7bb6d068eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605133"
---
# <a name="report-parameters-report-builder-and-report-designer"></a>Paramètres de rapport (Générateur de rapports et Concepteur de rapports)
  Cette rubrique décrit les utilisations courantes des paramètres de rapport SSRS, les propriétés pouvant être définies et bien d'autres paramètres. Les paramètres de rapport vous permettent de contrôler les données du rapport, d'interconnecter les rapports associés et de varier la présentation des rapports.  
  
[!INCLUDE[applies](../../includes/applies-md.md)]Mode SharePoint et mode natif
  
 Pour une démonstration de l’ajout d’un paramètre à rapport, consultez [Didacticiel : Ajout de paramètres à un rapport (SSRS)](https://technet.microsoft.com/library/aa337432\(v=SQL.105\).aspx)  

  
##  <a name="common-uses-for-parameters"></a><a name="bkmk_Common_Uses_for_Parameters"></a> Utilisations courantes des paramètres  
 Voici quelques-unes des utilisations les plus courantes des paramètres.  
  
 **Contrôler les données de rapport**  
  
-   Filtrez les données de rapport au niveau de la source de données en écrivant des requêtes de dataset qui comportent des variables.  
  
-   Filtrez les données à partir d'un dataset partagé. Lorsque vous ajoutez un dataset partagé à un rapport, vous ne pouvez pas modifier la requête. Dans le rapport, vous pouvez ajouter un filtre de dataset qui inclut une référence à un paramètre de rapport de votre création.  
  
-   Permettez aux utilisateurs de spécifier des valeurs pour personnaliser les données d'un rapport. Par exemple, fournissez deux paramètres pour la date de début et la date de fin des données de ventes.  
  
 **Connecter des rapports associés**  
  
-   Utilisez des paramètres pour associer des rapports principaux à des rapports d'extraction, des sous-rapports et des rapports liés. Lorsque vous concevez un ensemble de rapports, vous pouvez élaborer chaque rapport pour obtenir des réponses à certaines questions. Chaque rapport peut offrir une vue différente ou un niveau de détail différent pour des informations connexes. Pour fournir un ensemble de rapports reliés entre eux, créez des paramètres pour les données associées sur les rapports cibles.  
  
     Pour plus d’informations, consultez [Rapports d’extraction &#40;Générateur de rapports et SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md), [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](subreports-report-builder-and-ssrs.md) et [Créer un rapport lié](../reports/create-a-linked-report.md).  
  
-   Personnalisez des ensembles de paramètres pour plusieurs utilisateurs. Créez deux rapports liés basés sur un état des ventes sur le serveur de rapports. L'un des rapports liés utilise des valeurs de paramètres prédéfinies pour les commerciaux et l'autre rapport lié utilise des valeurs de paramètres prédéfinies pour les responsables commerciaux. Les deux rapports utilisent la même définition de rapport.  
  
 **Varier la présentation des rapports**  
  
-   Envoyez des commandes à un serveur de rapports via une demande d'URL, pour personnaliser l'affichage d'un rapport. Pour plus d’informations, consultez [Accès URL &#40;SSRS&#41;](../url-access-ssrs.md) et [Passer un paramètre de rapport dans une URL](../pass-a-report-parameter-within-a-url.md).  
  
-   Permettez aux utilisateurs de spécifier des valeurs pour contribuer à la personnalisation de l'apparence d'un rapport. Par exemple, fournissez un paramètre booléen pour indiquer s'il faut développer ou réduire tous les groupes de lignes imbriqués dans une table.  
  
-   Autorisez les utilisateurs à personnaliser les données et l'apparence des rapports en incluant des paramètres dans une expression.  
  
     Pour plus d’informations, consultez [Informations de référence sur la collection de paramètres &#40;Générateur de rapports et SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md).  
  
##  <a name="parameter-pane"></a><a name="UserInterface"></a>Volet des paramètres  
 Lorsque vous visualisez un rapport, la barre d'outils de la visionneuse de rapports affiche chaque paramètre de sorte que l'utilisateur puisse spécifier des valeurs de manière interactive. L’illustration suivante montre la zone de paramètres d’un rapport qui a des paramètres @StartDate , @EndDate , @Subcategory et @ShowAllRows .  
  
 ![rs_ParameterStory](../media/rs-parameterstory.gif "rs_ParameterStory")  
  
1.  **Volet Paramètres** : la barre d’outils de la visionneuse de rapports affiche une invite et une valeur par défaut pour chaque paramètre. La mise en forme des paramètres de la barre d'outils est effectuée automatiquement. L'ordre suivi est déterminé par l'ordre d'affichage des paramètres dans le volet des données de rapport.  
  
2.  ** @StartDate @EndDate paramètres et** le paramètre @StartDate est le type de données `DateTime` . L'invite de la date de début s'affiche en regard de la zone de texte. Pour modifier la date, tapez une nouvelle date dans la zone de texte ou utilisez le contrôle calendrier.  
  
     Le paramètre @EndDate apparaît en regard de @StartDate .  
  
3.  ** @Subcategory paramètre** le type de données du paramètre @Subcategory `Text` . Étant donné que @Subcategory contient une liste de valeurs disponibles, les valeurs valides s’affichent dans une liste déroulante. Vous devez choisir des valeurs dans cette liste. Étant donné que @Subcategory est à valeurs multiples, une option **Sélectionner tout** s’affiche pour vous permettre d’effacer tout et de sélectionner toutes les valeurs de la liste.  
  
4.  ** @ShowAllRows paramètre** le type de données du paramètre @ShowAllRows `Boolean` . Utilisez les cases d'option pour spécifier `True` ou `False`.  
  
5.  **Poignée Afficher ou masquer la zone de paramètres** : dans la barre d’outils de la visionneuse de rapports, cliquez sur cette flèche pour afficher ou masquer le volet Paramètres.  
  
6.  **Bouton Paramètres** Dans l'aperçu du Générateur de rapports, dans le Ruban, cliquez sur le bouton **Paramètres** pour afficher ou masquer le volet Paramètres.  
  
7.  **Bouton Afficher le rapport** Dans la barre d'outils de la visionneuse de rapports, cliquez sur **Afficher le rapport** pour exécuter le rapport après avoir entré des valeurs de paramètres. Si tous les paramètres possèdent des valeurs par défaut, le rapport s'exécute automatiquement au premier affichage.  
  
##  <a name="creating-parameters"></a><a name="bkmk_Create_Parameters"></a> Création de paramètres  
 Vous pouvez créer des paramètres de rapport de différentes façons :  
  
-   Ajoutez une requête de dataset qui contient des variables ou une procédure stockée de dataset qui contient des paramètres d'entrée. Un paramètre de dataset est créé pour chaque variable ou paramètre d'entrée, et un paramètre de rapport est créé pour chaque paramètre de dataset.  
  
     L'image suivante du Générateur de rapports montre une requête de dataset avec une variable (1), et le paramètre de dataset correspondant (2) et le paramètre de rapport (3).  
  
     ![Boîte de dialogue et volet de rapport de propriétés du dataset](../media/datasetquery-parameters.png "Boîte de dialogue et volet de rapport de propriétés du dataset")  
  
    > **REMARQUE !** Toutes les sources de données ne prennent pas en charge les paramètres.  
  
     Le dataset peut être incorporé ou partagé. Lorsque vous ajoutez un dataset partagé à un rapport, les paramètres de dataset marqués comme internes ne peuvent pas être substitués dans le rapport. Vous pouvez substituer les paramètres de dataset qui ne sont pas marqués comme internes.  
  
     Pour plus d'informations, consultez [Requête de dataset](#bkmk_Dataset_Parameters) dans cette rubrique.  
  
-   Créez manuellement un paramètre à partir du volet des données de rapport.  
  
     Vous pouvez configurer des paramètres de rapport afin qu'un utilisateur puisse entrer de manière interactive des valeurs dans le but de personnaliser le contenu ou l'apparence d'un rapport. Vous pouvez également configurer des paramètres de rapport afin qu'un utilisateur ne puisse pas modifier les valeurs préconfigurées.  
  

  > **REMARQUE !** Les paramètres sont gérés indépendamment sur le serveur ; par conséquent, si vous republiez un rapport principal avec de nouveaux paramètres, les paramètres existants du rapport ne sont pas remplacés.  
  
-   Ajoutez une partie de rapport qui contient des références à un paramètre ou à un dataset partagé contenant des variables.  
  
     Les parties de rapports sont stockées sur le serveur de rapports et sont à la disposition des autres utilisateurs qui souhaitent s'en servir dans leurs rapports. Les parties de rapports qui sont des paramètres ne peuvent pas être gérées à partir du serveur de rapports. Vous pouvez rechercher des paramètres dans la bibliothèque de parties de rapports et les configurer une fois que vous les avez ajoutés à votre rapport. Pour plus d’informations, consultez [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
     
   > **REMARQUE !** Les paramètres peuvent être publiés en tant que partie de rapport distincte pour les régions de données qui ont des datasets dépendants avec des paramètres. Bien que les paramètres apparaissent sous la forme d'une partie de rapport, vous ne pouvez pas ajouter directement un paramètre de partie de rapport à un rapport. À la place, ajoutez la partie de rapport pour que tous les paramètres de rapport nécessaires soient générés automatiquement à partir des requêtes de dataset qui sont contenues ou référencées par la partie de rapport. Pour plus d’informations sur les parties de rapport, consultez [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md) et [Parties de rapports dans le Concepteur de rapports &#40;SSRS&#41;](report-parts-in-report-designer-ssrs.md).  
  
### <a name="parameter-values"></a>Valeurs des paramètres  
 Utilisez les options suivantes pour sélectionner les valeurs de paramètre dans le rapport.  
  
-   Sélectionnez une valeur de paramètre dans la liste déroulante.  
  
-   Sélectionnez plusieurs valeurs de paramètre dans la liste déroulante.  
  
-   Sélectionnez une valeur dans la liste déroulante pour un paramètre, qui détermine les valeurs disponibles dans la liste déroulante pour un autre paramètre. Il s'agit de paramètres en cascade. Les paramètres en cascade vous permettent de filtrer successivement les valeurs de paramètres afin de passer de milliers de valeurs à un nombre plus gérable.  
  
     Pour plus d’informations, consultez [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).  
  
-   Exécutez le rapport sans sélectionner une valeur de paramètre, car une valeur par défaut est créée pour le paramètre.  
  
##  <a name="report-parameter-properties"></a><a name="bkmk_Report_Parameters"></a>Propriétés des paramètres de rapport  
 Vous pouvez modifier les propriétés de paramètre de rapport en utilisant la boîte de dialogue Propriétés du rapport. Le tableau suivant récapitule les propriétés que vous pouvez définir pour chaque paramètre :  
  
|Propriété|Description|  
|--------------|-----------------|  
|Nom|Tapez un nom de paramètre qui respecte la casse. Le nom doit commencer par une lettre et contenir des lettres, des chiffres, un trait de soulignement (_). Le nom ne peut pas contenir d'espace. Les noms des paramètres générés automatiquement correspondent au paramètre dans la requête du dataset. Par défaut, les paramètres créés manuellement sont similaires à ReportParameter1.|  
|Prompt|Texte qui apparaît en regard du paramètre dans la barre d'outils de la visionneuse de rapports.|  
|Type de données|Lorsque des valeurs disponibles sont définies pour un paramètre, l’utilisateur choisit des valeurs dans une liste déroulante, même si le type de données est `DateTime` . Un paramètre de rapport doit avoir l'un des types de données suivants :<br /><br /> `Boolean`. L'utilisateur sélectionne True ou False à l'aide d'une case d'option.<br /><br /> `DateTime`. L'utilisateur sélectionne une date à l'aide d'un contrôle calendrier.<br /><br /> **Entier**. L'utilisateur tape des valeurs dans une zone de texte.<br /><br /> Valeur **float**. L'utilisateur tape des valeurs dans une zone de texte.<br /><br /> `Text`. L'utilisateur tape des valeurs dans une zone de texte.<br /><br /> Pour plus d'informations sur les types de données de rapport, consultez [RDL Data Types](../reports/report-definition-language-ssrs.md#bkmk_RDL_Data_Types).|  
|Autoriser une valeur vide|Sélectionnez cette option si la valeur du paramètre peut être une chaîne ou une valeur vide.<br /><br /> Si vous spécifiez les valeurs valides d'un paramètre et si vous souhaitez qu'une valeur vide soit l'une des valeurs valides, vous devez l'inclure dans les valeurs que vous spécifiez. La sélection de cette option n'inclut pas automatiquement une valeur vide dans les valeurs disponibles.|  
|Autoriser les valeurs de type NULL|Sélectionnez cette option si la valeur du paramètre peut être Null.<br /><br /> Si vous spécifiez les valeurs valides d'un paramètre et si vous souhaitez qu'une valeur Null soit l'une des valeurs valides, vous devez l'inclure dans les valeurs que vous spécifiez. La sélection de cette option n'inclut pas automatiquement une valeur Null dans les valeurs disponibles.|  
|Autoriser les valeurs multiples|Fournissez les valeurs disponibles pour la création d'une liste déroulante dans laquelle vos utilisateurs peuvent effectuer des choix. Cela constitue une bonne méthode pour s'assurer que seules les valeurs valides sont envoyées dans la requête de dataset.<br /><br /> Sélectionnez cette option si la valeur pour le paramètre peut être plusieurs valeurs affichées dans une liste déroulante. Les valeurs NULL ne sont pas autorisées. Lorsque cette option est sélectionnée, les cases à cocher sont ajoutées à la liste de valeurs disponibles dans une liste déroulante de paramètre. Le haut de la liste comporte une case à cocher pour **Sélectionner tout**. Les utilisateurs peuvent activer les valeurs qu'ils souhaitent.<br /><br /> Si les données qui fournissent des valeurs changent rapidement, il est possible que la liste visible par l'utilisateur ne soit pas actualisée.|  
|Visible|Sélectionnez cette option pour afficher le paramètre de rapport en haut du rapport lorsqu'il est exécuté. Cette option permet aux utilisateurs de sélectionner des valeurs de paramètre au moment de l'exécution.|  
|Hidden|Sélectionnez cette option pour masquer le paramètre de rapport dans le rapport publié. Les valeurs de paramètre de rapport peuvent toujours être définies sur une URL de rapport, dans une définition d'abonnement ou sur le serveur de rapports.|  
|Interne|Sélectionnez cette option pour masquer le paramètre de rapport. Dans le rapport publié, le paramètre de rapport ne peut être affiché que dans la définition du rapport.|  
|Valeurs disponibles|Si vous avez spécifié les valeurs disponibles d'un paramètre, les valeurs valides s'affichent toujours sous forme de liste déroulante. Par exemple, si vous fournissez les valeurs disponibles d'un paramètre `DateTime`, une liste déroulante de dates s'affiche dans le volet des paramètres à la place d'un contrôle calendrier. Pour vous assurer qu'une liste de valeurs est cohérente parmi un rapport et des sous-rapports, vous pouvez définir une option sur la source de données afin d'utiliser une transaction unique pour toutes les requêtes des datasets associés à une source de données.<br /><br /> Note de sécurité dans un rapport qui inclut un paramètre de type de données, veillez à utiliser une liste de valeurs disponibles (également appelée liste de valeurs valides) et assurez-vous que l’utilisateur qui exécute le rapport dispose uniquement des autorisations nécessaires pour afficher les données du rapport. ** \* \* \* \* ** `Text` Pour plus d’informations, consultez [Sécurité &#40;Générateur de rapports&#41;](../report-builder/security-report-builder.md).|  
|Valeurs par défaut|Définissez les valeurs par défaut à partir d'une requête ou d'une liste statique.<br /><br /> Lorsque chaque paramètre a une valeur par défaut, le rapport s'exécute automatiquement au premier affichage.|  
|Avancé|Définissez l'attribut de définition de rapport `UsedInQuery`, valeur qui indique si ce paramètre affecte directement ou indirectement les données d'un rapport.<br /><br /> **Déterminer automatiquement le moment de l'actualisation**<br /> Choisissez cette option lorsque vous souhaitez que le processeur de rapports détermine un paramètre pour cette valeur. La valeur est `True` si le processeur de rapports détecte une requête de dataset avec une référence directe ou indirecte à ce paramètre ou si le rapport possède des sous-rapports.<br /><br /> **Toujours actualiser**<br /> Choisissez cette option lorsque le paramètre de rapport est utilisé directement ou indirectement dans une requête de dataset ou une expression de paramètre. Cette option affecte la valeur True à `UsedInQuery`.<br /><br /> **Ne jamais actualiser**<br /> Choisissez cette option quand le paramètre de rapport n'est pas utilisé directement ou indirectement dans une requête de dataset ou une expression de paramètre. Cette option affecte la valeur False à `UsedInQuery`.<br /><br /> ** \* \* Attention \* Utilisez \* ** **ne jamais actualiser** avec précaution. Sur le serveur de rapports, `UsedInQuery` permet de contrôler les options de cache pour les données de rapports et les rapports rendus, ainsi que les options de paramètres des rapports d'instantané. Si vous définissez l'option **Ne jamais actualiser** de manière incorrecte, vous risquez de provoquer la mise en cache incorrecte de rapports ou de données de rapports ou de provoquer la présence de données incohérentes dans un rapport d'instantané. Pour plus d’informations, consultez [Langage de définition de rapport &#40;SSRS, Report Definition Language&#41;](../reports/report-definition-language-ssrs.md).|  
  
##  <a name="dataset-query"></a><a name="bkmk_Dataset_Parameters"></a> Requête de dataset  
 Pour filtrer les données dans la requête de dataset, vous pouvez inclure une clause de restriction qui limite les données récupérées en spécifiant les valeurs à inclure ou exclure dans le jeu de résultats.  
  
 Utilisez le concepteur de requêtes pour la source de données pour générer plus facilement une requête paramétrable.  
  
-   Pour les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] , différentes sources de données prennent en charge différentes syntaxes pour les paramètres. La prise en charge comprend les paramètres identifiés dans la requête par position ou par nom. Pour plus d’informations, consultez les rubriques relatives aux types de sources de données externes spécifiques dans [Ajouter des données à un rapport &#40;générateur de rapports et SSRS&#41;](../report-data/report-datasets-ssrs.md). Dans le concepteur de requêtes relationnelles, vous devez sélectionner l'option de paramètre pour un filtre afin de créer une requête paramétrable. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes relationnelles &#40;Générateur de rapports&#41;](../report-data/relational-query-designer-user-interface-report-builder.md).  
  
-   Pour les requêtes basées sur une source de données multidimensionnelle telle que Microsoft SQL Server Analysis Services, SAP NetWeaver BI ou Hyperion Essbase, vous pouvez définir s'il faut créer un paramètre en fonction d'un filtre que vous spécifiez dans le concepteur de requêtes. Pour plus d’informations, consultez la rubrique relative au concepteur de requêtes dans [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../query-designers-report-builder.md) qui correspond à l’extension de données.  
  
##  <a name="parameter-management-for-a-published-report"></a><a name="bkmk_Manage_Parameters"></a> Gestion des paramètres pour un rapport publié  
 Lorsque vous concevez un rapport, les paramètres de rapport sont enregistrés dans la définition de rapport. Lorsque vous publiez un rapport, les paramètres de rapport sont enregistrés et gérés indépendamment de la définition de rapport.  
  
 Pour un rapport publié, vous pouvez utiliser les éléments suivants :  
  
-   **Propriétés du paramètre de rapport.** Modifiez des valeurs de paramètres du rapport directement sur le serveur de rapports, indépendamment de la définition de rapport.  
  
-   **Rapports mis en cache.** Pour permettre la création d’un plan de cache pour un rapport, chaque paramètre doit avoir une valeur par défaut. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md).  
  
-   **Datasets partagés mis en cache.** Pour permettre la création d’un plan de cache pour un jeu de données partagé, chaque paramètre doit avoir une valeur par défaut. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md).  
  
-   **Rapports liés.** Vous pouvez créer des rapports liés avec des valeurs de paramètres prédéfinies pour filtrer les données selon les différents publics. Pour plus d’informations, consultez [Créer un rapport lié](../reports/create-a-linked-report.md).  
  
-   **Abonnements aux rapports.** Vous pouvez spécifier des valeurs de paramètres pour filtrer les données et remettre des rapports par le biais d’abonnements. Pour plus d’informations, consultez [Abonnements et remise &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
-   **Accès URL.** Vous pouvez spécifier des valeurs de paramètres dans une URL pointant vers un rapport. Vous pouvez également exécuter des rapports et spécifier des valeurs de paramètres à l'aide de l'accès URL. Pour plus d’informations, consultez [Accès URL &#40;SSRS&#41;](../url-access-ssrs.md).  
  
 Les propriétés de paramètres que vous définissez pour un rapport publié sont généralement conservées si vous republiez la définition du rapport. Si la définition du rapport est republiée dans le même rapport, et si les noms des paramètres et les types de données restent les mêmes, vos valeurs de propriétés sont conservées. Si vous ajoutez ou supprimez des paramètres dans la définition de rapport, ou si vous modifiez le type de données ou le nom d'un paramètre existant, il peut être nécessaire de modifier les propriétés des paramètres dans le rapport publié.  
  
 Tous les paramètres ne peuvent pas être modifiés dans tous les cas. Si un paramètre de rapport obtient une valeur par défaut d'une requête de dataset, cette valeur ne peut pas être modifiée pour un rapport publié et ne peut pas être modifiée sur le serveur de rapports. La valeur utilisée au moment de l'exécution est déterminée lorsque la requête est lancée ou, dans le cas des paramètres basés sur une expression, lorsque celle-ci est évaluée.  
  
 Les options d'exécution de rapport peuvent affecter le mode de traitement des paramètres. Un rapport qui s'exécute en tant qu'instantané ne peut pas utiliser les paramètres dérivés d'une requête sauf si cette requête inclut des valeurs par défaut pour les paramètres.  
  
##  <a name="parameters-for-a-subscription"></a><a name="bkmk_Parameters_Subscription"></a> Paramètres d'un abonnement  
 Vous pouvez définir un abonnement pour un rapport à la demande ou un rapport d'instantané et spécifier les valeurs de paramètres à utiliser lors du traitement de l'abonnement.  
  
-   **Rapport à la demande.**  Pour un rapport à la demande, vous pouvez spécifier une valeur de paramètre différente de la valeur publiée pour chaque paramètre répertorié pour le rapport. Prenons l'exemple d'un rapport Service d'appel qui utilise un paramètre *Période* pour retourner les demandes du service client de la journée, de la semaine ou du mois en cours. Si la valeur par défaut du paramètre du rapport est égale à **aujourd’hui**, votre abonnement peut utiliser une valeur de paramètre différente (par exemple, **semaine** ou **mois**) pour produire un rapport contenant des chiffres hebdomadaires ou mensuels.  
  
-   **Instantané.**  Pour un instantané, votre abonnement doit utiliser les valeurs de paramètres définies pour l’instantané. Votre abonnement ne peut pas passer outre une valeur de paramètre définie pour un instantané. Supposons que vous vous abonniez à un rapport des ventes de la région Ouest s'exécutant en tant qu'instantané de rapport et que la valeur du paramètre régional de cet instantané soit définie sur **Ouest** . Dans ce cas, vous devez spécifier la valeur de paramètre **Ouest** dans l'abonnement que vous créez pour ce rapport. Pour signaler visuellement que le paramètre est ignoré, les champs de paramètres de la page d'abonnement sont définis en lecture seule.  
  
     Les options d'exécution de rapport peuvent affecter le mode de traitement des paramètres. Les rapports paramétrables exécutés comme instantanés de rapport utilisent les valeurs de paramètre définies pour l'instantané. Ces valeurs sont définies dans la page de propriétés des paramètres du rapport. Un rapport qui s'exécute en tant qu'instantané ne peut pas utiliser les paramètres dérivés d'une requête sauf si cette requête inclut des valeurs par défaut pour les paramètres.  
  
     Si une valeur de paramètre est modifiée dans l'instantané du rapport une fois l'abonnement défini, le serveur de rapports désactive l'abonnement. Cette désactivation est une façon de signaler que le rapport a été modifié. Pour activer l'abonnement, ouvrez-le, puis enregistrez-le.  
  
> [!NOTE]  
>  Les abonnements pilotés par les données peuvent utiliser des valeurs de paramètre obtenues à partir d'une source de données d'abonnés. Pour plus d’informations, consultez [Utiliser une source de données externe pour les données des abonnés &#40;abonnements pilotés par les données&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
 Pour plus d’informations, consultez [Abonnements et remise &#40;Reporting Services&#41;](../subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
##  <a name="parameters-and-securing-data"></a><a name="bkmk_Parameters_Security"></a> Paramètres et sécurisation des données  
 Soyez attentif lorsque vous distribuez des rapports paramétrables qui contiennent des informations confidentielles ou sensibles. Un utilisateur peut facilement remplacer un paramètre de rapport par une autre valeur, avec pour résultat une divulgation d'informations.  
  
 Pour sécuriser l'utilisation des paramètres des données personnelles ou des employés, vous pouvez sélectionner les données en fonction d'expressions qui comprennent le champ **UserID** de la collection Users. La collection Users permet d'obtenir l'identité de l'utilisateur qui exécute le rapport et d'utiliser cette identité pour extraire les données spécifiques à l'utilisateur.  
  
> [!IMPORTANT]  
>  Dans un rapport qui inclut un paramètre de type `String`, veillez à utiliser une liste de valeurs disponibles (également appelée liste de valeurs valides) et assurez-vous que l'utilisateur qui exécute le rapport dispose uniquement des autorisations nécessaires à l'affichage des données du rapport. Lorsque vous définissez un paramètre de type `String`, la zone de texte qui apparaît vous permet d'entrer n'importe quelle valeur. Une liste de valeurs disponibles limite les valeurs susceptibles d'être entrées. Si le paramètre de rapport est lié à un paramètre de dataset et que vous n'utilisez pas une liste de valeurs disponibles, l'utilisateur d'un rapport peut taper la syntaxe SQL dans la zone de texte, ce qui peut exposer le rapport et votre serveur au risque d'une attaque par injection SQL. Si l'utilisateur dispose d'autorisations suffisantes pour exécuter la nouvelle instruction SQL, cela risque de générer des résultats indésirables sur le serveur.  
>   
>  Si un paramètre de rapport n'est pas lié à un paramètre de dataset et les valeurs de paramètre sont incluses dans le rapport, l'utilisateur d'un rapport peut taper la syntaxe de l'expression ou une URL dans la valeur de paramètre et rendre le rapport au format Excel ou HTML. Si un autre utilisateur affiche ensuite le rapport et clique sur le contenu du paramètre de rendu, celui-ci peut exécuter accidentellement le lien ou le script malveillant.  
>   
>  Pour réduire le risque d'exécution accidentelle de scripts malveillants, ouvrez les rapports rendus uniquement à partir de sources approuvées. Pour plus d’informations sur la sécurisation des rapports, consultez [Sécurisation des rapports et des ressources](../security/secure-reports-and-resources.md).  
  
##  <a name="how-to-topics"></a><a name="bkmk_How_To_Topics"></a>Rubriques de procédures  
 Cette section répertorie les procédures qui vous indiquent pas à pas comment utiliser les paramètres et les filtres.  
  
-   [Ajouter, modifier ou supprimer un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Ajouter, modifier ou supprimer les valeurs disponibles d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)  
  
-   [Ajouter, modifier ou supprimer les valeurs par défaut d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md)  
  
-   [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
-   [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)  
  
-   [Ajouter un filtre à un dataset &#40;Générateur de rapports et SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
-   [Ajouter un sous-rapport et des paramètres &#40;Générateur de rapports et SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)  
  
-   [Rapport SSRS pour la procédure stockée paramétrable](https://www.c-sharpcorner.com/UploadFile/7d3362/ssrs-report-for-parameterize-stored-procedure/)  
  
## <a name="did-this-article-help-you-were-listening"></a>Cet article vous a-t-il été utile ? Nous sommes à l’écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous écoutons vos commentaires afin d’améliorer le contenu. Veuillez envoyer vos commentaires à[sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Report%20Parameters%20page)  
  
##  <a name="related-content"></a><a name="bkmk_Related_Topics"></a> Contenu associé  
 [Configuration de paramètres de rapport SSRS (quiz)](https://www.trenovision.com/quiz/sql-server-reporting-services-ssrs-quiz/)  
  
 [Didacticiel : Ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
 [Bursting the mysteries of InvalidReportParameterException in Reporting service](https://go.microsoft.com/fwlink/p/?LinkId=393118)  
  
 [Exemples de rapports (Générateur de rapports et SSRS)](https://go.microsoft.com/fwlink/?LinkId=198283)  
  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapports et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
 [Sécurité &#40;Générateur de rapports&#41;](../report-builder/security-report-builder.md)  
  
 [Tri interactif, Explorateurs de documents et liens &#40;Générateur de rapports et SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
 [Extraction, exploration, sous-rapports et régions de données imbriquées &#40;Générateur de rapports et SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
