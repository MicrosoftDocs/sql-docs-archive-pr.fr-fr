---
title: Créer des relations à base de termes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.kbtermsbased.f1
ms.assetid: 66db9277-d892-4dae-8a82-060fd3ba6949
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6b7424b962679af766efc10278def8947fc07b51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602333"
---
# <a name="create-term-based-relations"></a>Créer des relations à base de termes
  Cette rubrique décrit comment créer des relations à base de termes pour un domaine dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Une relation à base de termes (TBR) vous permet d'effectuer une correction sur un terme qui fait partie d'une valeur d'un domaine. Plusieurs valeurs qui sont identiques à l'exception de l'orthographe d'une partie commune peuvent ainsi être considérées comme synonymes identiques. Par exemple, vous pouvez installer une relation à base de termes qui remplace le terme « Inc. » par « Incorporated ». Le terme « Inc. » est modifié chaque fois qu’il apparaît dans le domaine. Les instances de « Contoso, Inc. » sont remplacées par « Contoso, Incorporated », et les deux valeurs sont considérées comme des synonymes exacts.  
  
 Pour utiliser les relations à base de termes, vous créez une liste de paires Valeur/Correct, telles que « Inc. » et « Incorporated », ou« Senior » et « Sr. ». L'utilisation d'une relation à base de termes vous permet de modifier un terme dans l'ensemble du domaine sans définir manuellement des valeurs de domaine en tant que synonymes. Vous pouvez spécifier qu'une valeur est corrigée même si la découverte des connaissances n'a pas découvert cette valeur précédemment. Si la transformation d'une relation à base de termes rend deux valeurs identiques, DQS crée une relation de synonyme entre elles (dans la découverte des connaissances) ou une relation de correction entre elles (dans la correction des données) ou une correspondance exacte (dans la correspondance).  
  
 La transformation de relations à base de termes et la transformation de symboles (où les caractères spéciaux sont remplacés par un espace ou la valeur null) sont toutes deux effectuées dans une étape de prétraitement avant analyse. Si l'analyse de domaine composite est demandée, elle sera effectuée avant les deux transformations, car l'analyse du séparateur requiert des symboles. D'autres opérations, telles que les règles de domaine et les modifications de valeurs de domaine, sont exécutées après les transformations. Pour qu'il y ait correspondance, les relations à base de termes sont appliquées aux données de la source avant l'activité correspondante, indépendamment du nettoyage.  
  
 **Relations à base de termes et gestion de domaine**  
  
 Lorsque vous appliquez une relation à base de termes dans la gestion de domaine, DQS applique les modifications aux processus de découverte des connaissances, de nettoyage ou de correspondance ; toutefois, DQS ne modifie pas la valeur de domaine elle-même pour se conformer à la relation à base de termes. En d'autres termes, si vous entrez et acceptez une relation à base de termes sous l'onglet **Relations à base de termes** de la page **Gestion de l'arborescence du domaine** , la modification ne sera pas répercutée dans l'onglet **Valeurs du domaine** de la même page. Cela vous permet de modifier la TBR par la suite.  
  
 **Relations à base de termes et nettoyage des données**  
  
 Lorsque vous appliquez une relation à base de termes dans un domaine, puis exécutez le processus de nettoyage de données, DQS applique les modifications lors du nettoyage, mais n'applique pas les modifications apportées aux termes dans la base de connaissances.  
  
-   Si une valeur modifiée par une relation à base de termes se trouve dans le domaine, mais n'est pas un synonyme, cela est affiché dans la colonne **Corriger vers** sous l'onglet **Corrigés** de la page **Gérer et afficher les résultats** , avec Raison défini sur Relation à base de termes.  
  
-   Si une valeur modifiée par une relation à base de termes n'est pas dans le domaine, et DQS trouve une valeur correspondante, la valeur est corrigée en conséquence et apparaît sous l'onglet Corrigés ou sous l'onglet Suggérés, selon le niveau de confiance. Si aucune correspondance n'est trouvée, la valeur apparaît sous Nouveau avec une correction TBR. La raison de cela est que même si vous corrigez la TBR, cela ne signifie pas que la valeur est correcte.  
  
-   Si une valeur modifiée par une relation à base de termes se trouve dans le domaine, mais la valeur est une erreur ou est non valide avec une correction existante, elle s'affiche sous l'onglet Corrigés avec sa correction et la raison Valeur de domaine.  
  
-   Si une valeur modifiée par une relation à base de termes se trouve dans le domaine, mais la valeur est une erreur ou est non valide sans correction existante, elle s'affiche sous l'onglet Non valide avec la raison Valeur de domaine.  
  
 **Relations à base de termes et découverte des connaissances**  
  
 Lorsque vous appliquez une relation à base de termes, puis exécutez le processus de découverte des connaissances, toutes les valeurs qui sont conformes à la TBR restent telles quelles et sont reconnues comme des valeurs correctes. Toute valeur qui est modifiée par une TBR est importée comme valeur correcte, et identifiée comme synonyme d'une valeur conforme à la TBR.  
  
 **Relations à base de termes et importation de valeurs de nettoyage dans un domaine**  
  
 Si vous importez des connaissances de qualité des données collectées pendant le processus de nettoyage dans un domaine, une valeur modifiée par une TBR sera importée comme valeur correcte.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Pour créer des relations à base de termes, vous devez avoir un domaine ouvert dans l'activité de gestion de l'arborescence du domaine.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour créer des relations à base de termes.  
  
##  <a name="create-term-based-relations"></a><a name="Create"></a>Créer des relations à base de termes  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez ou créez une base de connaissances. Sélectionnez **Gestion de l'arborescence du domaine** comme activité, puis cliquez sur **Ouvrir** ou **Créer**. Pour plus d’informations, consultez [Créer une base de connaissances](../../2014/data-quality-services/create-a-knowledge-base.md) ou [Ouvrir une base de connaissances](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
    > [!NOTE]  
    >  La gestion de domaine est exécutée dans une page du client Data Quality Service qui contient cinq onglets pour les opérations distinctes de gestion de domaine. Ce n'est pas un processus piloté par l'Assistant ; toute opération de gestion peut être exécutée séparément.  
  
3.  Dans **Liste des domaines** de la page **Gestion de l'arborescence du domaine** , sélectionnez le domaine pour lequel vous souhaitez créer une règle de domaine, ou créez un nouveau domaine. Si vous devez créer un domaine, consultez [Créer un domaine](../../2014/data-quality-services/create-a-domain.md).  
  
4.  Cliquez sur l'onglet **Relations à base de termes** .  
  
5.  Créez les relations à base de termes comme suit :  
  
    1.  Cliquez sur **Ajouter une nouvelle relation** pour ajouter une ligne à la table Relations.  
  
    2.  Dans la colonne **Valeur** de la ligne ajoutée, entrez un terme que vous voulez modifier chaque fois qu'il apparaît dans une valeur du domaine sélectionné.  
  
        > [!NOTE]  
        >  Vous obtiendrez une erreur si le terme existe comme valeur complète dans le domaine ou si elle existe déjà comme valeur de correction dans le domaine.  
  
    3.  Dans la colonne **Corriger vers** , entrez le terme dans lequel vous voulez modifier le terme de la colonne **Valeur** .  
  
    4.  Cliquez sur **Ajoutez de nouvelles relations** à nouveau pour ajouter une autre relation à base de termes.  
  
    5.  Cliquez sur **Supprimer les relations sélectionnées** pour supprimer une ou plusieurs lignes sélectionnées de la table Relations. Vous pouvez sélectionner plusieurs lignes en appuyant sur le bouton Ctrl et en cliquant sur une ligne non sélectionnée.  
  
    6.  Recherchez une valeur dans la table Relations en entrant un ou plusieurs chiffres dans la zone de texte **Rechercher** . Les correspondances exactes pour la chaîne sont mises en surbrillance. Utilisez les flèches haut et bas pour vous déplacer vers différentes instances de la chaîne dans la table.  
  
    7.  **Vérificateur d'orthographe**: si une valeur dans la colonne **Valeur** ou **Corriger vers** comporte un trait de soulignement ondulé rouge, le vérificateur d'orthographe suggère une correction pour la valeur. Cliquez avec le bouton droit sur la valeur comportant un trait de soulignement, puis sélectionnez l'une des valeurs proposées par le vérificateur d'orthographe. Ou bien, vous pouvez cliquer sur **Ajouter** dans le menu contextuel pour utiliser la valeur d'origine. Pour plus d'informations, consultez [Utiliser le vérificateur d'orthographe DQS](../../2014/data-quality-services/use-the-dqs-speller.md) et [Définir les propriétés du domaine](../../2014/data-quality-services/set-domain-properties.md).  
  
        > [!NOTE]  
        >  Pour utiliser le vérificateur d'orthographe, vous pouvez l'activer dans la page **Propriétés du domaine** ou, s'il est désactivé, dans la page **Propriétés du domaine** , vous pouvez cliquer sur l'icône **Activer/désactiver le vérificateur d'orthographe** dans la page **Relations à base de termes** pour l'activer sur cette page.  
  
6.  Cliquez sur **Appliquer les modifications** pour appliquer les relations à base de termes au domaine.  
  
7.  Cliquez sur **Terminer** pour terminer l'activité de gestion de l'arborescence du domaine, comme décrit dans [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).  
  
##  <a name="follow-up-after-creating-term-based-relations"></a><a name="FollowUp"></a> Suivi : Après la création de relations à base de termes  
 Après avoir créé les relations à base de termes, vous pouvez effectuer d'autres tâches de gestion des domaines sur le domaine, effectuer une découverte des connaissances pour ajouter des connaissances au domaine ou ajouter une stratégie de correspondance au domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../../2014/data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../../2014/data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../../2014/data-quality-services/create-a-matching-policy.md).  
  
  
