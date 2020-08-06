---
title: Ajouter une source à l’aide de l’Assistant source | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e850b7c-4b89-42ad-b0a6-d63ac7cc9568
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b58b10508765580e0cffe9bd62099f3e2d69863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604711"
---
# <a name="add-a-source-using-source-assistant"></a>Ajouter une source à l'aide de l'Assistant Source
  Cette rubrique présente les étapes à suivre pour ajouter une nouvelle source à l’aide de l’Assistant Source. En outre, elle répertorie les options disponibles dans la boîte de dialogue **Ajouter une nouvelle source** , qui s’affiche quand vous effectuez un glisser-déplacer de l’Assistant Source vers le concepteur SSIS.  
  
### <a name="to-use-source-assistant-to-add-a-source"></a>Pour utiliser l'Assistant Source afin d'ajouter une source  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auquel vous voulez ajouter un composant source.  
  
2.  Faites glisser le composant **Assistant Source** de la boîte à outils SSIS vers l'onglet **Flux de données** . Vous devez voir s'afficher la boîte de dialogue **Ajouter une nouvelle source** . La section suivante fournit des détails sur les options disponibles dans la boîte de dialogue.  
  
3.  Sélectionnez le type de la destination dans la liste **Types** .  
  
4.  Sélectionnez un gestionnaire de connexions existant dans la liste **Gestionnaires de connexions** ou sélectionnez **\<New>** pour en créer un.  
  
5.  Si vous sélectionnez un gestionnaire de connexions existant, cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une nouvelle destination** . Vous devez constater que la destination et les gestionnaires de connexions ont été ajoutés au flux de données.  
  
6.  Si vous cliquez sur **\<New>** pour créer un gestionnaire de connexions, vous devez voir s’afficher une boîte de dialogue **Gestionnaire de connexions**, qui vous permet de spécifier les paramètres de la connexion. Une fois que vous avez fini de créer le gestionnaire de connexions, vous constatez que la destination et le gestionnaire de connexions figurent dans le concepteur SSIS.  
  
  
