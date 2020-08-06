---
title: Convertir des données en un type de données différent à l’aide de la transformation de conversion de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 878741717c36c18e9a069c62e86be0148272239f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611195"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a>Convertir des données en un type différent à l'aide de la transformation de conversion de données
  Pour pouvoir ajouter et configurer une transformation de conversion de données, le package doit inclure au moins une tâche de flux de données et une source.  
  
### <a name="to-convert-data-to-a-different-data-type"></a>Pour convertir des données en un type différent  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** et, dans la **boîte à outils**, faites glisser la transformation de conversion de données sur l’aire de conception.  
  
4.  Connectez la transformation de conversion de données au flux de données en faisant glisser un connecteur à partir de la source ou de la transformation précédente vers la transformation de conversion de données.  
  
5.  Double-cliquez sur la transformation de conversion de données.  
  
6.  Dans la boîte de dialogue **Éditeur de transformation de conversion de données** , dans la table **Colonnes d’entrée disponibles** , cochez la case en regard des colonnes dont vous voulez convertir le type de données.  
  
    > [!NOTE]  
    >  Vous pouvez appliquer plusieurs conversions de données à une colonne d'entrée.  
  
7.  Si vous le souhaitez, modifiez les valeurs par défaut de la colonne **Alias de sortie** .  
  
8.  Dans la liste **Type de données** , sélectionnez le nouveau type de données de la colonne. Le type de données par défaut est celui de la colonne d'entrée.  
  
9. Si vous le souhaitez et selon le type de données sélectionné, mettez à jour les valeurs des colonnes **Longueur**, **Précision**, **Échelle**et **Page de codes** .  
  
10. Pour configurer la sortie d’erreur, cliquez sur **Configurer la sortie d’erreur**. Pour plus d’informations, consultez [Configurer une sortie d’erreur dans un composant de flux de données](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Data Conversion Transformation](data-conversion-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)   
 [Chemins Integration Services](../integration-services-paths.md)   
 [Types de données d’Integration Services](../integration-services-data-types.md)   
 [tâche de flux de données](../../control-flow/data-flow-task.md)  
  
  
