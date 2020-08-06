---
title: 'Étape 2 : Ajout et configuration du conteneur de boucles Foreach | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de5e8875c43edda618ccef4839c88c3b84a003cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87601567"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a>Étape 2 : Ajout et configuration du conteneur de boucles Foreach
  Dans cette tâche, vous allez activer la fonction qui permet d'effectuer des boucles dans un dossier de fichiers plats et d'appliquer la transformation de flux de données utilisée dans la leçon 1 à chacun de ces fichiers plats. Pour activer cette fonction, vous allez ajouter et configurer un conteneur de boucles Foreach dans le flux de contrôle.  
  
 Le conteneur de boucles Foreach que vous allez ajouter doit pouvoir se connecter à chaque fichier plat dans le dossier. Étant donné que tous les fichiers du dossier ont le même format, le conteneur de boucles Foreach peut utiliser le même Gestionnaire de connexions de fichiers plats pour se connecter à chacun de ces fichiers. Le Gestionnaire de connexions de fichiers plats que le conteneur va utiliser est le même que celui créé au cours de la leçon 1.  
  
 Pour l'instant, le Gestionnaire de connexions de fichiers plats créé au cours de la leçon 1 se connecte uniquement à un seul fichier plat spécifique. Pour que la connexion réitère et s'établisse à chaque fichier plat dans le dossier, vous devez configurer le conteneur de boucles Foreach et le Gestionnaire de connexions de fichiers plats comme suit :  
  
-   **Conteneur de boucles Foreach :** vous allez mapper la valeur énumérée du conteneur à une variable de package définie par l’utilisateur. Le conteneur va ensuite utiliser cette variable définie par l'utilisateur pour modifier dynamiquement la propriété `ConnectionString` du Gestionnaire de connexions de fichiers plats et répéter la connexion à chaque fichier plat dans le dossier.  
  
-   **Gestionnaire de connexions de fichiers plats :** Vous allez modifier le gestionnaire de connexions qui a été créé au cours de la leçon 1 en utilisant une variable définie par l’utilisateur pour remplir la propriété du gestionnaire de connexions `ConnectionString` .  
  
 Les procédures de cette tâche montrent comment créer et modifier le conteneur de boucles Foreach pour utiliser une variable de package définie par l'utilisateur et comment ajouter la tâche de flux de données à la boucle. Au cours de la tâche suivante, vous allez apprendre à modifier le Gestionnaire de connexions de fichiers plats pour qu'il utilise une variable définie par l'utilisateur.  
  
 Une fois ces modifications apportées au package et le package exécuté, le conteneur de boucles Foreach effectue une itération dans la collection de fichiers dans le dossier Sample Data. À chaque fois qu'un fichier répondant aux critères est trouvé, le conteneur de boucles Foreach renseigne la variable définie par l'utilisateur avec le nom du fichier, mappe cette variable sur la propriété `ConnectionString` du gestionnaire de connexions de fichiers plats SampleCurrencyData, puis exécute le flux de données par rapport à ce fichier. Par conséquent, à chaque itération de la boucle Foreach, la tâche de flux de données utilise un fichier plat différent.  
  
> [!NOTE]  
>  Étant donné que [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sépare le flux de contrôle du flux de données, les boucles que vous ajoutez au flux de contrôle ne nécessitent pas la modification du flux de données. Par conséquent, il n'est pas nécessaire de modifier le flux de données que vous avez créé au cours de la leçon 1.  
  
### <a name="to-add-a-foreach-loop-container"></a>Pour ajouter un conteneur de boucles Foreach  
  
1.  Dans **SQL Server Data Tools**, cliquez sur l’onglet **Flux de contrôle** .  
  
2.  Dans la **Boîte à outils SSIS**, développez **Conteneurs**, puis faites glisser un **conteneur de boucles Foreach** dans l’aire de conception de l’onglet **Flux de contrôle** .  
  
3.  Cliquez avec le bouton droit sur le **conteneur de boucles Foreach** que vous venez d’ajouter et sélectionnez **Modifier**.  
  
4.  Dans la boîte de dialogue **éditeur de boucle foreach** , dans la page **général** , pour **nom**, entrez `Foreach File in Folder` . Cliquez sur **OK**.  
  
5.  Cliquez avec le bouton droit sur le conteneur de boucles Foreach, cliquez sur **Propriétés**, et dans la fenêtre Propriétés, vérifiez que la `LocaleID` propriété est définie sur **anglais (États-Unis)**.  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>Pour configurer l'énumérateur pour le conteneur de boucles Foreach  
  
1.  Double-cliquez sur Foreach File in Folder pour rouvrir l’**Éditeur de boucle Foreach**.  
  
2.  Cliquez sur **Collection**.  
  
3.  Dans la page **Collection** , cliquez sur **Énumérateur Foreach File**.  
  
4.  Dans le groupe **Configuration de l’énumérateur** , cliquez sur **Parcourir**.  
  
5.  Dans la boîte de dialogue **Rechercher un dossier** , recherchez dans votre ordinateur le dossier qui contient les fichiers Currency_*.txt.  
  
     Ces exemples de données sont inclus dans les packages de leçons [!INCLUDE[ssIS](../includes/ssis-md.md)] . Pour télécharger ces exemples de données et les packages de leçons, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l’onglet **téléchargements** .  
  
    3.  Cliquez sur le lien hypertexte « https://msftisprodsamples.codeplex.com/downloads/get/578097 » SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip fichier.  
  
6.  Dans la zone **Fichiers**, tapez **Currency_\*.txt**.  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>Pour mapper l'énumérateur à une variable définie par l'utilisateur  
  
1.  Cliquez sur **Mappages de variables**.  
  
2.  Dans la page **mappage de variables** , dans la colonne **variable** , cliquez sur la cellule vide et sélectionnez **\<New Variable...>** .  
  
3.  Dans la boîte de dialogue **Ajouter une variable** , pour **nom**, tapez `varFileName` .  
  
    > [!IMPORTANT]  
    >  Les noms des variables tiennent compte de la casse.  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez à nouveau sur **OK** pour quitter la boîte de dialogue **Éditeur de boucle Foreach** .  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>Pour ajouter la tâche de flux de données à la boucle  
  
-   Faites glisser la tâche de workflow **extraire l’exemple de données monétaires** sur le conteneur de boucles Foreach maintenant renommé `Foreach File in Folder` .  
  
## <a name="next-lesson-task"></a>Tâche suivante de la leçon  
 [Étape 3 : Modification du Gestionnaire de connexions de fichiers plats](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un conteneur de boucles Foreach](control-flow/foreach-loop-container.md)   
 [Utiliser des variables dans des packages](use-variables-in-packages.md)  
  
