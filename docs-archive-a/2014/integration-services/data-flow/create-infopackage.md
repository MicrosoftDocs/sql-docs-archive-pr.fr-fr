---
title: Créer un Infopackage| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9cd4a848-409f-4681-a390-1c49a2aadbd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f6ddce4e97c0c21d9f77c432231d414770dbce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695928"
---
# <a name="create-infopackage"></a>Créer un InfoPackage
  Utilisez la boîte de dialogue **Créer un InfoPackage** pour créer un InfoPackage dans le système SAP Netweaver BW.  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoPackage** depuis la page **Gestionnaire de connexions** de **l’Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [Destination SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Créer un InfoPackage**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **Créer des objets SAP BW** , sélectionnez **InfoPackage**, puis cliquez sur **Créer**.  
  
## <a name="options"></a>Options  
 **InfoSource**  
 Entrez le nom de l'InfoSource sur lequel le nouvel InfoPackage doit être basé.  
  
 **Brève description**  
 Entrez une description pour le nouvel InfoPackage.  
  
 **Système source**  
 Sélectionnez le système source auquel le nouvel InfoPackage doit être associé.  
  
 **Attributs**  
 Indique que l'InfoPackage chargera les données d'attribut.  
  
 **Textes**  
 Indique que l'InfoPackage chargera les données de texte.  
  
 **Transaction**  
 Indique que l'InfoPackage chargera les données de transaction.  
  
 **Enregistrer et activer**  
 Enregistrez et activez le nouvel InfoPackage.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
