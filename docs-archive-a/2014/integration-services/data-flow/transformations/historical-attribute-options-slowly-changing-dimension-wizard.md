---
title: Options des attributs d’historique (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613063"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Options des attributs d'historique (Assistant Dimension à variation lente)
  Utilisez la boîte de dialogue **Options des attributs d'historique** pour afficher les attributs d'historique par dates de début et de fin ou pour enregistrer les attributs d'historique dans une colonne créée spécialement à cet effet.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Utiliser une seule colonne pour afficher les enregistrements actifs et expirés**  
 Si vous choisissez d'utiliser une seule colonne pour enregistrer l'état des attributs d'historique, les options suivantes sont disponibles :  
  
|Option|Description|  
|------------|-----------------|  
|**Colonne d'indicateur d'enregistrement actif**|Sélectionnez une colonne dans laquelle indiquer l'enregistrement actif.|  
|**Valeur si actif**|Utilisez soit **True** soit **Current** pour indiquer que l'enregistrement est actif.|  
|**Valeur d'expiration**|Utilisez soit **False** soit **Expired** pour indiquer que l'enregistrement est une valeur historique.|  
  
 **Utiliser les dates de début et de fin pour identifier les enregistrements actifs et expirés**  
 La table de dimension pour cette option doit comprendre une colonne de date. Si vous choisissez d'afficher les attributs d'historique par dates de début et de fin, les options suivantes sont disponibles.  
  
|Option|Description|  
|------------|-----------------|  
|**Colonne de date de début**|Sélectionnez la colonne de la table de dimension qui doit contenir la date de début.|  
|**Colonne de date de fin**|Sélectionnez la colonne de la table de dimension qui doit contenir la date de fin.|  
|**Variable de définition des valeurs de date**|Sélectionnez une variable de date dans la liste.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
