---
title: Extension de la fonctionnalité OLAP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d64d1ac46e2571aa6f8065a8ea42e4cc43aa589e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614857"
---
# <a name="extending-olap-functionality"></a>Étendre les fonctionnalités OLAP
  En tant que programmeur, vous pouvez étendre Analysis Services en entrant des assemblys, des extensions personnalisées et des procédures stockées pour fournir les fonctionnalités que vous souhaitez utiliser et rediriger dans plusieurs applications de base de données. Les assemblys sont utilisés pour étendre les fonctionnalités de modèles multidimensionnels en ajoutant de nouvelles procédures et fonctions au langage MDX ou au moyen du complément de personnalisation.  
  
 Les procédures stockées peuvent être utilisées pour appeler des routines externes, ce qui simplifie le développement et l'implémentation de la base de données Analysis Services grâce au développement d'un code commun qui est stocké dans un seul emplacement. Les procédures stockées peuvent être utilisées pour ajouter à vos applications des fonctionnalités métier qui ne sont pas fournies par les fonctionnalités natives de MDX.  
  
 Les personnalisations sont des objets personnalisés que vous ajoutez à un cube pour fournir un comportement qui varie selon l'utilisateur. Les personnalisations ne sont pas des objets permanents dans le cube. Il s'agit d'objets que l'application cliente applique dynamiquement pendant la session de l'utilisateur. Voici quelques exemples : modifier la devise d'une valeur monétaire en fonction de la personne qui accède aux données en fournissant des indicateurs de performance clés individualisés, ou créer une liste ciblée de suggestions pour les clients standard qui achètent en ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extension d'OLAP par des personnalisations](extending-olap-through-personalizations.md)  
  
 [Extensions de personnalisation Analysis Services](analysis-services-personalization-extensions.md)  
  
 [Définition de procédures stockées](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
