---
title: Générer du code XML à partir d’ensembles de lignes avec FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf9feb4dab9ad1149ab433c9d9b4999c96c1cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710419"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a>Générer du code XML à partir d'ensembles de lignes avec FOR XML
  Vous pouvez générer une `xml` instance de type de données à partir d’un ensemble de lignes en utilisant for XML avec la nouvelle directive de **type** .  
  
 Le résultat peut être assigné à une `xml` colonne, une variable ou un paramètre de type de données. De plus, il est possible d'imbriquer des clauses FOR XML pour générer une structure hiérarchique. Les clauses FOR XML imbriquées sont plus faciles à écrire que la clause FOR XML EXPLICIT, mais elles ne s'avèrent pas aussi performantes pour les hiérarchies profondes. FOR XML introduit aussi un nouveau mode PATH qui spécifie le chemin de l'arborescence XML où apparaît la valeur d'une colonne.  
  
 La nouvelle directive **FOR XML TYPE** permet de créer, avec une syntaxe SQL, des vues XML en lecture seule des données relationnelles. La vue peut être interrogée par des instructions SQL et le langage XQuery intégré, comme le montre l'exemple suivant. Vous pouvez également faire référence à ces vues SQL dans les procédures stockées.  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a>Exemple : Vue SQL retournant un type de données XML généré  
 La définition de la vue SQL suivante crée une vue XML d'une colonne relationnelle, pk, et extrait les auteurs des livres d'une colonne XML :  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 La vue V contient une seule ligne avec une seule colonne columnxmlVal de type XML `.` . elle peut être interrogée comme une `xml` instance de type de données normale. Par exemple, la requête suivante renvoie l'auteur dont le prénom est « David » :  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 Les définitions de vue SQL s'apparentent un peu aux vues XML créées à l'aide des schémas annotés, bien qu'il y ait des différences de taille. La définition d'une vue SQL est en lecture seule et doit être manipulée avec le langage XQuery intégré. Les vues XML sont créées à l'aide d'un schéma annoté. De plus, la vue SQL matérialise le résultat XML avant l'application de l'expression XQuery tandis que les requêtes XPath sur les vues XML évaluent les requêtes SQL portant sur les tables sous-jacentes.  
  
## <a name="see-also"></a>Voir aussi  
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  
