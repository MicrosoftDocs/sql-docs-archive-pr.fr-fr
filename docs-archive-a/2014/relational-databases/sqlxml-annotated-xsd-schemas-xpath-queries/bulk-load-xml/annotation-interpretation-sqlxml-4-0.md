---
title: Interprétation des annotations (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: rothja
ms.author: jroth
ms.openlocfilehash: c31d56f7dd577b4b5a5b582eb0e3b1db312109a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611709"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Interprétation d'annotation (SQLXML 4.0)
  Les rubriques de cette section décrivent comment le chargement en masse XML interprète les annotations dans le schéma XSD. Le comportement décrit ici s'applique également aux annotations dans le schéma XDR.  
  
> [!NOTE]  
>  Les informations fournies dans ces rubriques décrivent uniquement les annotations utilisées par le chargement en masse XML lors de son traitement. Pour obtenir la liste complète des annotations pour le schéma XSD prises en charge par SQLXML 4,0, consultez [utilisation des annotations dans les schémas xsd &#40;sqlxml 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Pour obtenir la liste des annotations prises en charge pour les schémas XDR, consultez [schémas XDR Annotés &#40;dépréciés dans SQLXML 4,0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [SQL : Relationship et la règle de classement des clés &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Décrit comment l'annotation `sql:relationship` est interprétée dans le chargement en masse XML.  
  
 [SQL : mappé &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-mapped.md)  
 Décrit comment l'annotation `sql:mapped` est interprétée dans le chargement en masse XML.  
  
 [SQL : Limit-Field et SQL : limit-value &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Décrit comment les annotations `sql:limit-field` et `sql:limit-value` sont interprétées dans le chargement en masse XML.  
  
 [SQL : overflow-field &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-overflow-field.md)  
 Décrit comment l'annotation `sql:overflow` est interprétée dans le chargement en masse XML.  
  
 [Autres annotations &#40;SQLXML 4,0&#41;](annotation-interpretation-other-annotations.md)  
 Décrit comment les annotations suivantes sont interprétées dans le chargement en masse XML :  `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.  
  
  
