---
title: Accès de navigation (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600107"
---
# <a name="navigational-access-master-data-services"></a>Accès de navigation (Master Data Services)
  L’accès de navigation s’applique à la sécurité de l’objet modèle, affectée sous l’onglet **Modèles** .  
  
 L’accès de navigation désigne l’accès aux niveaux supérieurs par rapport à ceux auxquels vous avez affecté une sécurité.  
  
 Dans cet exemple, les autorisations sont affectées à une entité, et donc l'accès de navigation est accordé au niveau du modèle.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entités**  
  
 Lorsque vous affectez une autorisation à une entité, ses membres feuilles ou ses membres consolidés, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres. Vous pouvez également lire le nom du modèle.  
  
 **Attributs**  
  
 Lorsque vous affectez une autorisation à un attribut, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres dans l'entité. Vous pouvez également lire le nom du modèle.  
  
 **Regroupements**  
  
 Lorsque vous affectez des autorisations aux collections, vous pouvez lire ou mettre à jour le nom, le code, la description et l'ID de propriétaire. Vous pouvez également lire le nom du modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
