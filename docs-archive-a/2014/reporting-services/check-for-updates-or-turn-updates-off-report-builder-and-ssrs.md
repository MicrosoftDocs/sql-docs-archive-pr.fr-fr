---
title: Rechercher les mises à jour ou désactiver les mises à jour (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 088d41e71d770f746367f2760cff8ff67b15623c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605246"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a>Vérifier la présence de mises à jour ou désactiver les mises à jour (Générateur de rapports et SSRS)
  Chaque fois que vous ouvrez un rapport, le Générateur de rapports vérifie si les instances publiées des parties de rapports de ce rapport ont été mises à jour sur le serveur de rapports ou site SharePoint intégré à un serveur de rapports. Il recherche également des modifications dans les éléments dépendants des parties de rapport, tels que le dataset et les paramètres. Si des parties de rapport ou leurs dépendances ont été mises à jour sur le site ou serveur, une barre d'informations dans votre rapport affiche le nombre de parties mises à jour. Vous pouvez choisir d'afficher et d'accepter ou de rejeter les mises à jour ou de faire disparaître la barre d'informations.  
  
 Vous pouvez également désactiver la barre d'informations, auquel cas vous ne serez plus informé en cas de modification des instances publiées des parties de rapport. Il s'agit d'un paramètre utilisateur ; il sera désactivé pour tous les rapports que vous ouvrez. Même si vous avez désactivé la barre d'informations, vous pouvez toujours rechercher des mises à jour.  
  
### <a name="to-turn-on-and-off-report-part-updates"></a>Pour activer et désactiver les mises à jour des parties de rapport  
  
1.  Cliquez sur le bouton Générateur de rapports, puis sur **options**.  
  
2.  Dans la boîte de dialogue **options** , sous l’onglet **ressources** , activez ou désactivez la case à cocher **afficher les mises à jour des parties de rapport dans mes rapports** .  
  
> [!NOTE]  
>  Il s'agit d'un paramètre utilisateur. Il sera désactivé pour tous les rapports que vous ouvrez.  
  
### <a name="to-check-for-updates"></a>Pour rechercher des mises à jour  
  
-   Cliquez avec le bouton droit sur l’aire de conception en dehors du rapport ou dans le corps du rapport, puis cliquez sur **Rechercher les mises à jour**.  
  
## <a name="see-also"></a>Voir aussi  
 [Parties de rapport &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Publier et republier des parties de rapports &#40;Générateur de rapports et SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md)   
 [Rechercher des parties de rapports et définir un dossier par défaut &#40;Générateur de rapports et SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)   
 [Résoudre les problèmes liés aux parties de rapports &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [Parties de rapports et datasets dans le Générateur de rapports](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
