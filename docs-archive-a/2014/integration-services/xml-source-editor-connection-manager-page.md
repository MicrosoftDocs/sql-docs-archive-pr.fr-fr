---
title: Éditeur de source XML (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e40ca6ef2d8fbcd10b756a2ce15f33730c367d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614160"
---
# <a name="xml-source-editor-connection-manager-page"></a>Éditeur de source XML (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de l' **Éditeur de source XML** pour spécifier un fichier XML et le schéma XSD qui transforme les données XML.  
  
 Pour plus d'informations sur la source XML, consultez [XML Source](data-flow/xml-source.md).  
  
## <a name="static-options"></a>Options statiques  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Emplacement du fichier XML|Récupère des données dans un fichier XML.|  
|Fichier XML à partir d'une variable|Spécifiez le nom de fichier XML dans une variable.<br /><br /> **Informations connexes** : [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)|  
|Données XML à partir d'une variable|Récupère des données XML à partir d'une variable.|  
  
 **Utiliser le schéma inclus**  
 Indique si les données de la source XML contiennent le schéma XSD définissant et validant sa structure et ses données.  
  
 **Emplacement XSD**  
 Tapez le chemin et le nom de fichier du schéma XSD, ou recherchez le fichier en cliquant sur **Parcourir**.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , recherchez le fichier de schéma XSD.  
  
 **Créer XSD**  
 Utilisez la boîte de dialogue **Enregistrer sous** pour sélectionner l’emplacement du fichier de schéma XSD généré automatiquement. L'éditeur détermine le schéma en fonction de la structure des données XML.  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
### <a name="data-access-mode--xml-file-location"></a>Mode d'accès aux données = emplacement du fichier XML  
 **Emplacement XML**  
 Tapez le chemin et le nom du fichier de données XML, ou recherchez le fichier en cliquant sur **Parcourir**.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , recherchez le fichier de données XML.  
  
### <a name="data-access-mode--xml-file-from-variable"></a>Mode d'accès aux données = fichier XML à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable contenant le chemin d'accès et le nom du fichier XML.  
  
### <a name="data-access-mode--xml-data-from-variable"></a>Mode d'accès aux données = données XML à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient les données XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source XML &#40;page colonnes&#41;](../../2014/integration-services/xml-source-editor-columns-page.md)   
 [Éditeur de source XML &#40;page sortie d’erreur&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md)   
 [Extraire des données à l'aide de la source XML](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
