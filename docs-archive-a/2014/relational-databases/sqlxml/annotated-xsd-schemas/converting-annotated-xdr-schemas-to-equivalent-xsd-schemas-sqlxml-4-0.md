---
title: Conversion de schémas XDR annotés en schémas XSD équivalents (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: rothja
ms.author: jroth
ms.openlocfilehash: c36eb17aacb61a47fad0f389de9a3c216202827d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611682"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a>Conversion de schémas XDR annotés en schémas XSD équivalents (SQLXML 4.0)
  Le langage XSD (XML Schema Definition) est le successeur du langage de définition de schéma XDR (XML-Data Reduced). Avec l'introduction de la prise en charge du langage XSD dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, les nouveaux schémas annotés sont donc supposés être créés à l'aide de ce langage XSD. SQLXML 4.0 inclut un outil de conversion XDR vers XSD conçu pour vous aider à convertir vos schémas XDR annotés en schémas XSD équivalents.  
  
> [!IMPORTANT]  
>  Utilisez cet outil uniquement lorsque vous souhaitez convertir des schémas XDR annotés en XSD pour une utilisation avec SQLXML 4.0. Il ne s'agit pas d'un outil de conversion XDR vers XSD à usage général. Les schémas XSD convertis peuvent ne pas se comporter de la même façon que les schémas XDR d'origine en cas d'utilisation dans d'autres environnements.  
  
 Si le fichier XDR d'entrée spécifie l'encodage dans la déclaration XML, cela devient l'encodage du fichier de sortie XSD généré.  
  
 L'outil de conversion (Cvtschema.exe) est installé dans le dossier \Program Files\SQLXML 4.0\bin et exécuté à l'invite de commandes.  
  
 Voici la syntaxe générale :  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 Où :  
  
 XDRFileName  
 Est le nom du fichier XDR qui doit être converti en XSD. L'outil lit le fichier XDR d'entrée et crée un fichier de sortie XSD dans le répertoire de travail actif. Si le fichier d'entrée a une extension .xdr ou .xml, le fichier XSD de sortie est créé avec le même nom mais avec une extension .xsd. Si l'extension du fichier d'entrée n'est ni .xdr ni .xml (ou si elle est manquante), le fichier de sortie est créé avec le même nom et l'extension .xsd est ajoutée au nom de fichier d'entrée. Par exemple, si le nom de fichier XDR d'entrée est SampleFile.abc, le fichier XSD résultant est enregistré en tant que SampleFile.abc.xsd.  
  
 -y  
 (Facultatif) Remplace le fichier XSD existant par le fichier XSD généré par l'outil de conversion. Si l'indicateur n'est pas spécifié, l'outil vous invite à spécifier si vous souhaitez remplacer le fichier XSD existant et vous donne la possibilité de modifier le nom de fichier de sortie.  
  
 -w  
 (Facultatif) Retourne des avertissements récupérables générés durant le processus de conversion par l'outil. Par défaut, l'outil affiche les messages uniquement pour les erreurs irrécupérables.  
  
 -?  
 Retourne une liste des options que vous pouvez spécifier avec `cvtschema`, accompagnées d'une explication.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de types de données XSD à des types de données XPath &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)   
 [Annotations XSD &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
