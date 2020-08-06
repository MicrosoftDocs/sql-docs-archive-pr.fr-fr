---
title: 'Leçon 13 : analyser dans Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600285"
---
# <a name="lesson-13-analyze-in-excel"></a>Leçon 13 : Analyser dans Excel
  Dans cette leçon, vous allez utiliser la fonction Analyser dans Excel dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour ouvrir Microsoft Excel, créer automatiquement une connexion de source de données à l'espace de travail du modèle et ajouter automatiquement un tableau croisé dynamique à la feuille de calcul. La fonctionnalité Analyser dans Excel est destinée à fournir un moyen simple et rapide de tester l’efficacité de la conception de votre modèle avant de déployer ce dernier. Vous n'allez exécuter aucune analyse de données dans cette leçon. L’objectif de cette leçon est de vous familiariser, en tant qu’auteur de modèle, avec les outils que vous pouvez utiliser pour tester la conception de votre modèle. Contrairement à la fonctionnalité Analyser dans Excel, qui est destinée aux auteurs de modèle, les utilisateurs finaux utilisent les applications de création de rapports clientes, par exemple Excel ou [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] , pour se connecter aux données du modèle déployé et les parcourir.  
  
 Pour pouvoir exécuter cette leçon, Excel doit être installé sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Pour en savoir plus, consultez [Analyser dans Excel &#40;SSAS Tabulaire&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).  
  
 Durée estimée pour suivre cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 11 : Créer des partitions](lesson-10-create-partitions.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Parcourir des données à l’aide des perspectives par défaut et Internet Sales  
 Dans ces premières tâches, vous pourrez parcourir votre modèle à l'aide de la perspective par défaut, qui inclut tous les objets de modèle, et de la perspective Internet Sales que vous avez créée dans la leçon 8 : créer des perspectives. La perspective Internet Sales exclut l'objet table Customer.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Pour parcourir des données à l’aide de la perspective par défaut  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel**, cliquez sur **OK**.  
  
     Excel s’ouvre avec un nouveau classeur. Une connexion de source de données est créée à l'aide du compte d'utilisateur actuel et la perspective par défaut est utilisée pour définir les champs visibles. Un tableau croisé dynamique est automatiquement ajouté à la feuille de calcul.  
  
3.  Dans Excel, dans la **liste de champs de tableau croisé dynamique**, Notez que les mesures **Date** et **Internet Sales** s’affichent, ainsi que les tables **client**, **Date**, **géographie**, **produit**, **catégorie de produit**, sous- **catégorie de produit**et **ventes sur Internet** avec toutes leurs colonnes respectives s’affichent.  
  
4.  Fermez Excel sans enregistrer le classeur.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Pour parcourir les données à l’aide de perspective Internet Sales  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel** , laissez **Utilisateur Windows actuel** sélectionné, puis dans la zone de liste déroulante **Perspective** , sélectionnez **Internet Sales**, puis cliquez sur **OK**. Excel s'ouvre.  
  
3.  Dans Excel, dans la **Liste de champs de tableau croisé dynamique**, notez que la table Customer est exclue de la liste de champs.  
  
## <a name="browse-using-roles"></a>Parcourir les données à l'aide de rôles  
 Les rôles font partie intégrante de n’importe quel modèle tabulaire. Sans disposer d'au moins un rôle auquel les utilisateurs sont ajoutés en tant que membres, ces derniers ne peuvent pas accéder aux données et les analyser à l'aide de votre modèle. La fonctionnalité Analyser dans Excel vous fournit un moyen de tester les rôles que vous avez définis.  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a>Pour parcourir les données à l'aide du rôle utilisateur Sales Manager  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel** , dans **Spécifier le nom d’utilisateur ou le rôle à utiliser pour se connecter au modèle**, sélectionnez **Rôle**, puis dans la zone de liste déroulante, sélectionnez **Internet Sales Manager**, puis cliquez sur **OK**.  
  
     Excel s’ouvre avec un nouveau classeur. Un tableau croisé dynamique est créé automatiquement. La liste des champs du tableau croisé dynamique inclut tous les champs de données disponibles dans votre nouveau modèle.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la [Leçon 14 : Déployer](lesson-13-deploy.md).  
  
  
