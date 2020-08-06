---
title: Éditeur de transformation d’exportation de colonne (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603571"
---
# <a name="export-column-transformation-editor-columns-page"></a>Éditeur de transformation d'exportation de colonne (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de transformation d'exportation de colonne** pour spécifier les colonnes du flux de données à extraire dans des fichiers. Vous pouvez préciser si la transformation d'exportation de colonne ajoute des données à la fin d'un fichier ou écrase le fichier existant.  
  
 Pour en savoir plus sur la transformation d'exportation de colonne, consultez [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonne d'extraction**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant des données texte ou image. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Colonne du chemin d'accès**  
 Permet de sélectionner à partir de la liste d'entrée des colonnes contenant les chemins d'accès aux fichiers ainsi que les noms de fichiers. Toutes les lignes doivent avoir des définitions pour les options **Colonne d'extraction** et **Colonne du chemin d'accès**.  
  
 **Autoriser l'ajout**  
 Permet de préciser si la transformation ajoute ou non des données à la fin des fichiers existants. Par défaut, il s’agit de `false`.  
  
 **Forcer la troncation**  
 Permet de préciser si la transformation supprime le contenu des fichiers existants avant d'écrire des données. Par défaut, il s’agit de `false`.  
  
 **Écrire la marque d'ordre d'octet**  
 Indique s'il est nécessaire d'écrire une marque d'ordre d'octet (BOM, Byte-Order Mark) dans le fichier. Une BOM n'est inscrite que dans les cas où les données sont de type `DT_NTEXT` ou DT_WSTR et qu'elles ne sont pas ajoutées à la fin d'un fichier de données existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation d’exportation de colonne &#40;page Sortie d’erreur&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
