---
title: Créer un rapport lié | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5e70c9ff8179ae05186685e21303693fc9aed7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611523"
---
# <a name="create-a-linked-report"></a>Créer un rapport lié
  Un rapport lié est un élément de serveur de rapports qui fournit un point d'accès à un rapport existant. Au niveau conceptuel, il est assimilable au raccourci d'un programme que vous utilisez pour exécuter une application ou ouvrir un fichier.

 Un rapport lié est issu d'un rapport existant et il reste fidèle à la définition de rapport d'origine. Il hérite toujours des propriétés de la source de données et de la mise en page du rapport d'origine. Toutes les autres propriétés et toutes les autres valeurs peuvent différer, notamment la sécurité, les paramètres, l'emplacement, les abonnements et les planifications.

 Vous créez un rapport lié lorsque vous voulez créer des versions supplémentaires d'un rapport existant. Ainsi, vous pouvez trouver pratique d'utiliser un rapport de ventes régional unique pour créer des rapports spécifiques aux régions pour tous vos secteurs de ventes.

 Bien que les rapports liés soient généralement basés sur des rapports paramétrés, il n'est pas obligatoire de recourir à des rapports paramétrés. Vous pouvez créer des rapports liés dès lors que vous souhaitez déployer un rapport existant avec des paramètres différents.

### <a name="to-create-a-linked-report"></a>Pour créer un rapport lié

1.  Dans le Gestionnaire de rapports, accédez au dossier qui contient le rapport à lier, puis ouvrez le menu d’options et cliquez sur **Créer un rapport lié**.

2.  Indiquez un nom pour le nouveau rapport lié. Tapez éventuellement une description.

3.  Pour sélectionner un autre dossier pour le rapport, cliquez sur **Modifier l’emplacement**. Cliquez ensuite sur le dossier à utiliser ou tapez son nom dans la zone **Emplacement** . [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Si vous ne sélectionnez aucun dossier, le rapport lié est créé dans le dossier actif (où est stocké le rapport sur lequel il est basé).

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Le rapport lié s’ouvre.

     L'icône d'un rapport lié est différente des autres éléments gérés par un serveur de rapports. L'icône ci-après indique un rapport lié :

     ![Icône Rapport lié](../media/hlp-16linked.gif "Icône Rapport lié")

## <a name="see-also"></a>Voir aussi
 [Ouvrez et fermez une &#40;de rapport Gestionnaire de rapports&#41;](../reports/open-and-close-a-report-report-manager.md) page [nouveau rapport lié &#40;gestionnaire de rapports](../new-linked-report-page-report-manager.md) [&#41;&#40;](../choose-item-location-page-report-manager.md) gestionnaire de rapports&#41;[SSRS](../reporting-services-concepts-ssrs.md) &#40;gestionnaire de rapports&#41;SSRS [en mode natif](../report-manager-ssrs-native-mode.md) Reporting Services de &#40;&#41;[de](../general-properties-page-reports-report-manager.md) gestionnaire de rapports.


