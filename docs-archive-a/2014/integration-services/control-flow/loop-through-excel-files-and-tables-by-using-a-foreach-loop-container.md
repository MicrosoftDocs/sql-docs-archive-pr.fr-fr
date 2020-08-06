---
title: Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: a5393c1a-cc37-491a-a260-7aad84dbff68
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51de779b6869d80245302741035e6169aa750c83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604073"
---
# <a name="loop-through-excel-files-and-tables-by-using-a-foreach-loop-container"></a>Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach
  Les procédures de cette rubrique expliquent comment effectuer une boucle dans les classeurs Excel d'un dossier, ou dans les tableaux d'un classeur Excel, à l'aide du conteneur de boucles Foreach et de l'énumérateur approprié.  
  
### <a name="to-loop-through-excel-files-by-using-the-foreach-file-enumerator"></a>Pour effectuer une boucle dans des fichiers Excel à l'aide de l'énumérateur Foreach File  
  
1.  Créez une variable de chaîne qui recevra le chemin d'accès et le nom de fichier Excel actuel à chaque itération de la boucle. Pour éviter des problèmes de validation, assignez un chemin d'accès Excel et un nom de fichier valides comme valeur initiale de la variable. (L'exemple d'expression présenté ultérieurement dans cette procédure utilise le nom de variable `ExcelFile`.)  
  
2.  En option, créez une autre variable de chaîne qui contiendra la valeur de l'argument Propriétés étendues de la chaîne de connexion Excel. Cet argument contient une série de valeurs qui spécifient la version d'Excel et déterminent si la première ligne contient les noms de colonnes, et si le mode d'importation est utilisé. (L'exemple d'expression présenté ultérieurement dans cette procédure utilise le nom de variable `ExtProperties`, avec une valeur initiale «`Excel 8.0;HDR=Yes`».)  
  
     Si vous n'utilisez pas une variable pour l'argument de propriétés étendues, vous devez l'ajouter manuellement à l'expression qui contient la chaîne de connexion.  
  
3.  Ajoutez un conteneur de boucles Foreach à l’onglet **Flow Control** . Pour plus d’informations sur la configuration du conteneur de boucles Foreach, consultez [configurer un conteneur de boucles Foreach](foreach-loop-container.md).  
  
4.  Dans la page **Collection** de **l’Éditeur de boucle Foreach**, sélectionnez l’énumérateur Foreach File, spécifiez le dossier contenant les classeurs Excel, puis spécifiez le filtre de fichiers (généralement *.xls).  
  
5.  Dans la page **Mappage de variables** , mappez l’index 0 à une variable de chaîne définie par l’utilisateur qui recevra le chemin et le nom de fichier Excel actuels à chaque itération de la boucle. L'exemple d'expression présenté plus loin dans cette procédure utilise le nom de variable `ExcelFile`.  
  
6.  Fermez **l’Éditeur de boucle Foreach**.  
  
7.  Ajoutez un gestionnaire de connexions Excel au package, comme décrit dans la rubrique [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../add-delete-or-share-a-connection-manager-in-a-package.md). Pour éviter toute erreur de validation, sélectionnez un fichier de classeur Excel pour la connexion.  
  
    > [!IMPORTANT]  
    >  Pour éviter des erreurs de validation à mesure que vous configurez des tâches et des composants de flux de données qui utilisent ce gestionnaire de connexions Excel, sélectionnez un classeur Excel existant dans **l’Éditeur du gestionnaire de connexions Excel**. Le gestionnaire de connexions n'utilise pas ce classeur au moment de l'exécution après que vous ayez configuré une expression pour la propriété `ConnectionString` comme décrit dans la procédure suivante. Après avoir créé et configuré le package, vous pouvez supprimer la valeur de la propriété `ConnectionString` dans la fenêtre Propriétés. Néanmoins, si vous supprimez cette valeur, la propriété de chaîne de connexion du gestionnaire de connexions Excel n'est plus valide tant que la boucle Foreach n'est pas exécutée. Vous devez donc définir la propriété `DelayValidation` à `True` dans les tâches où le gestionnaire de connexions est utilisé, ou bien dans le package, pour éviter des erreurs de validation.  
    >   
    >  Vous devez également utiliser la valeur par défaut `False` pour la propriété `RetainSameConnection` du gestionnaire de connexions Excel. Si vous remplacez cette valeur par `True`, chaque itération de la boucle continue d'ouvrir le premier classeur Excel.  
  
8.  Sélectionnez le nouveau gestionnaire de connexions Excel, cliquez sur la propriété **Expressions** dans la fenêtre Propriétés, puis cliquez sur les points de suspension.  
  
9. Dans l' **éditeur d’expressions**de la propriété, sélectionnez la `ConnectionString` propriété, puis cliquez sur les points de suspension.  
  
10. Dans le Générateur d'expressions, entrez l'expression suivante :  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=\"" + @[User::ExtProperties] + "\""  
    ```  
  
     L’utilisation du caractère d’échappement «\\» permet d’isoler les guillemets internes requis autour de la valeur de l’argument de propriétés étendues (ExtProperties).  
  
     L'argument de propriétés étendues n'est pas facultatif. Si vous n'utilisez pas une variable pour contenir sa valeur, vous devez l'ajouter manuellement à l'expression, comme dans l'exemple suivant pour un fichier Excel 2003 :  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=Excel 8.0"  
    ```  
  
11. Dans le conteneur de boucles Foreach, créez des tâches qui utilisent le gestionnaire de connexions Excel pour effectuer les mêmes opérations sur chaque classeur Excel correspondant à l'emplacement et au modèle des fichiers spécifiés.  
  
### <a name="to-loop-through-excel-tables-by-using-the-foreach-adonet-schema-rowset-enumerator"></a>Pour effectuer une boucle dans des tableaux Excel à l'aide de l'énumérateur d'ensemble de lignes du schéma ADO.NET Foreach  
  
1.  Créez un gestionnaire de connexions ADO.NET qui utilise le fournisseur OLE DB pour Microsoft Jet afin d'établir une connexion à un classeur Excel. Dans la page Tout de la boîte de dialogue **Gestionnaire de connexions** , veillez à entrer Excel 8.0 comme valeur de la propriété Extended Properties. Pour plus d’informations, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../add-delete-or-share-a-connection-manager-in-a-package.md).  
  
2.  Créez une variable de chaîne qui recevra le nom du tableau actuel à chaque itération de la boucle.  
  
3.  Ajoutez un conteneur de boucles Foreach à l’onglet **Flow Control** . Pour plus d’informations sur la configuration du conteneur de boucles Foreach, consultez [configurer un conteneur de boucles Foreach](foreach-loop-container.md).  
  
4.  Dans la page **Collection** de **l’Éditeur de boucle Foreach**, sélectionnez l’énumérateur d’ensemble de lignes du schéma ADO.NET Foreach.  
  
5.  En guise de valeur pour **Connexion**, sélectionnez le gestionnaire de connexions ADO.NET que vous avez créé.  
  
6.  En guise de valeur pour **Schéma**, sélectionnez Tables.  
  
    > [!NOTE]  
    >  La liste des tableaux d'un classeur Excel comprend à la fois les feuilles de calcul (affectées du suffixe $) et les plages nommées. Si vous devez filtrer la liste uniquement à partir des feuilles de calcul ou des plages nommées, vous pouvez être amené à écrire du code personnalisé dans une tâche de script. Pour plus d’informations, consultez [Utilisation de fichiers Excel avec la tâche de script](script-task.md).  
  
7.  Dans la page **Mappage de variables** , mappez Index 2 avec la variable de chaîne créée précédemment pour inclure le nom du tableau actuel.  
  
8.  Fermez **l’Éditeur de boucle Foreach**.  
  
9. Dans le conteneur de boucles Foreach, créez des tâches qui utilisent le gestionnaire de connexions Excel pour effectuer les mêmes opérations sur chaque tableau Excel du classeur spécifié. Si vous utilisez une tâche de script dans le but d’examiner le nom de tableau énuméré ou pour utiliser chaque tableau, pensez à ajouter la variable chaîne à la propriété ReadOnlyVariables de la tâche de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données à partir d’Excel ou exporter des données vers Excel avec SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md) [configurer un conteneur de boucles Foreach](foreach-loop-container.md)   
 [Ajouter ou modifier une expression de propriété](../expressions/add-or-change-a-property-expression.md)   
 [Gestionnaire de connexions Excel](../connection-manager/excel-connection-manager.md)   
 [Source Excel](../data-flow/excel-source.md)   
 [Destination Excel](../data-flow/excel-destination.md)   
 [Utilisation de fichiers Excel avec la tâche de script](script-task.md)  
  
  
