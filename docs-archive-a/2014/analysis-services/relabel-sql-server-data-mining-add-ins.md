---
title: Renommer (SQL Server les compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
ms.openlocfilehash: a625676f60e2da32e19b85a94002b51eeb9ac816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605740"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>Réétiqueter (Compléments d'exploration de données SQL Server)
  ![Icône Office 13 pour l'outil Réétiqueter](media/dm13-relabel.gif "Icône Office 13 pour l'outil Réétiqueter")

 Le client d'exploration de données pour Excel vous permet de créer de nouvelles étiquettes pour les données afin de faciliter la compréhension des résultats de l'analyse.

 Les raisons du réétiquetage incluent les suivantes :

-   Les données contiennent des résultats qui ont été codés, comme 1 pour Homme et 2 pour Femme.

-   Vous créez des compartiments de valeurs numériques et souhaitez affecter un nom descriptif aux plages.

-   Vous souhaitez simplifier les noms longs.

## <a name="using-the-relabel-wizard"></a>Utilisation de l'Assistant Réétiquetage

1.  Dans le ruban **Exploration de données** , cliquez sur **Nettoyer** , puis sélectionnez **Réétiqueter**.

2.  Sélectionnez la table ou la plage de données qui contiennent les données à corriger.

3.  Dans la page **Réétiqueter** de l'Assistant, sélectionnez une colonne, dans la liste déroulante, ou en cliquant sur la colonne dans le volet des **Échantillons de données** .

     Le volet **Échantillons de données** affiche environ 50 lignes de données, mais elles sont échantillonnées pour garantir que vous consultez une bonne répartition des valeurs.

     Cliquez sur l'en-tête de colonne **Nombre** pour trier par le nombre de chaque valeur.

     Vous pouvez également trier par **Étiquettes d'origine**, ce qui est pratique si vous souhaitez réétiqueter les valeurs les plus élevées ou les plus faibles en premier.

4.  Dans la page de données **Réétiqueter** de l'Assistant, examinez les valeurs dans la colonne **Étiquettes d'origine** , et décidez comment vous souhaitez les regrouper ou les modifier.

5.  Tapez une nouvelle valeur dans la ligne sous **Nouvelles étiquettes**. Vous pouvez également choisir une valeur dans la liste de valeurs existantes. À mesure que vous entrez des nouvelles valeurs, elles sont disponibles en vue de leur réutilisation.

6.  Une fois que vous avez entré suffisamment de lignes, cliquez sur **suivant**, puis dans la page **Sélectionner la destination** , choisissez l’emplacement où vous allez enregistrer les données réparties.

    -   **Ajouter en tant que nouvelle colonne dans la feuille de calcul active**

         Cliquez pour ajouter une nouvelle colonne au tableau qui contient les nouvelles valeurs.

    -   **Copier les données de la feuille comportant les modifications dans une nouvelle feuille de calcul**

         Cliquez pour créer une nouvelle feuille de calcul qui contient les données mises à jour.

    -   **Changer les données de place**

         Cliquez pour remplacer les données d'origine par les nouvelles valeurs.

## <a name="see-also"></a>Voir aussi
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)


