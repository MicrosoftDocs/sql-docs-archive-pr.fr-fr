---
title: Développement avec le langage de script Analysis Services (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb64c120e67d5b4ac12e7bd77f0e0c4e5736757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605805"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Développement avec le langage de script Analysis Services (ASSL)
  Le langage de script ASSL (Analysis Services Scripting Language) est une extension de XMLA qui ajoute un langage de définition d'objets et un langage de commande pour créer et gérer les structures des services Analysis Services directement sur le serveur. Vous pouvez utiliser ASSL dans l'application personnalisée pour communiquer avec Analysis Services sur le protocole XMLA. ASSL comprend deux parties :  
  
-   Un langage de définition de données (DDL), ou un langage de définition d'objets, qui définit et décrit une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ainsi que les bases de données et les objets de base de données que contient l'instance.  
  
-   Un langage de commande qui envoie des commandes d'action, telles que `Create`, `Alter` ou `Process`, à une instance d'Analysis Services. Ce langage de commande est abordé dans la [référence de&#41; XML for Analysis &#40;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).  
  
 Pour afficher l'ASSL qui décrit une solution multidimensionnelle dans [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], vous pouvez utiliser la commande Afficher le code au niveau du projet. Vous pouvez également créer ou modifier le script ASSL dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] à l'aide de l'éditeur de requête XMLA. Les scripts que vous créez peuvent être utilisés pour gérer des objets ou pour exécuter des commandes sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets ASSL et caractéristiques de l’objet](assl-objects-and-object-characteristics.md)   
 [Conventions XML ASSL](assl-xml-conventions.md)   
 [Sources de données et liaisons &#40;SSAS Multidimensionnel&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
