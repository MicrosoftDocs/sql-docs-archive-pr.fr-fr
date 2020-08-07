---
title: Boîte de dialogue Propriétés de la fenêtre d’affichage de la carte, Centre et zoom | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603304"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a>Boîte de dialogue Propriétés du point de vue de la carte, Centrer et zoomer
  Sélectionnez **Centrer et zoomer** dans la boîte de dialogue **Propriétés de la fenêtre d'affichage de la carte** pour définir le centre d'affichage et le facteur de zoom d'une carte. Après avoir spécifié une source de données cartographiques et les limites de la carte que vous souhaitez inclure dans votre rapport, vous pouvez spécifier le centre d'affichage et le facteur de zoom pour contrôler encore davantage l'affichage de la carte. Les options disponibles varient en fonction de la méthode utilisée pour spécifier le centre et les valeurs de zoom. Cliquez sur le bouton **Expression** (*fx*) pour modifier une expression qui définit la valeur de l'option.  
  
## <a name="options"></a>Options  
 **Définir un centre d'affichage et un niveau de zoom**  
 Choisissez cette option pour spécifier des valeurs personnalisées pour le centre d'affichage et le niveau de zoom.  
  
 **Centrer la carte pour afficher une couche**  
 Choisissez cette option pour spécifier une couche et centrer automatiquement la vue sur ses données. Par exemple, centrez la vue sur LineLayer1.  
  
 **Centrer la carte pour afficher un élément de carte incorporé**  
 Choisissez cette option pour centrer la vue sur un élément cartographique spécifique lié aux données. Les données spatiales doivent être en relation avec des données analytiques pour spécifier cette option.  
  
 Par exemple, centrez la vue sur l'élément cartographique où le nom du champ de correspondance est [City] et la valeur de correspondance est « Seattle ».  
  
 **Centrer la carte pour afficher tous les éléments de carte liés aux données**  
 Choisissez cette option pour centrer la vue sur tous les éléments cartographiques de la couche. Les données spatiales doivent être en relation avec des données analytiques pour spécifier cette option.  
  
 Par exemple, centrez la vue sur la couche à bulles de polygones qui affiche des villes et des tailles de bulle différentes en fonction de la population. Seules les villes munies d'une valeur correspondante de population seront incluses lors du calcul du centre de la fenêtre de carte.  
  
 **Options de centre et de zoom**  
 Sélectionnez une option pour spécifier le centre d'affichage et le niveau de zoom.  
  
 **Centre d'affichage (X) %**  
 Coordonnée horizontale. La valeur par défaut, 50 %, centre la vue à mi-chemin entre les valeurs horizontales minimale et maximale.  
  
 **Centre d'affichage (Y) %**  
 Coordonnée verticale. La valeur par défaut, 50 %, centre la vue à mi-chemin entre les valeurs verticales minimale et maximale.  
  
 **Niveau de zoom (%)**  
 Facteur de zoom. La valeur par défaut, 100 %, n'indique aucun agrandissement.  
  
 **Centrer l'affichage sur cette couche**  
 Spécifiez le nom de la couche.  
  
 **Centrer l'affichage sur l'élément de carte correspondant à cette condition**  
 Le champ en lecture seule affiché est utilisé pour faire correspondre les données cartographiques et les données analytiques. Spécifiez la valeur avec laquelle les données doivent correspondre. La vue est centrée automatiquement sur cet élément cartographique. Par exemple, NAME = TEXAS. Par défaut, le type de données pour la condition est Chaîne et la correspondance respecte la casse.  
  
 Pour faire correspondre avec un champ qui a un type de données différent, vous devez écrire une expression qui prend la valeur de ce type de données. Par exemple, si le champ de correspondance est un code postal de 5 chiffres stocké comme nombre entier, pour spécifier le code postal 98053, vous devrez utiliser l'expression =98053.  
  
## <a name="see-also"></a>Voir aussi  
 [Cartes &#40;Générateur de rapports et SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
