---
title: Se connecter à un fichier Microsoft Excel (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79bb3d57470be8acbbb990dde71cf21b62b3cb2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602470"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>Connexion à un fichier Microsoft Excel (SSAS)
  Cette page de l' **Assistant Importation de table** vous permet de vous connecter à un fichier Microsoft Excel stocké sur l'ordinateur local. Pour accéder à l'Assistant [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans le menu **Modèle** , cliquez sur **Importer à partir de la source de données**.  
  
 Pour vous connecter à un fichier Excel, vous devez disposer du fournisseur ACE approprié, installé sur votre ordinateur. Pour plus d’informations, consultez [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Les informations d'identification de l'utilisateur actuel sont utilisées lors de la sélection d'un fichier dans cette page. Toutefois, l'importation ne réussira pas si l'utilisateur spécifié dans la page Informations d'emprunt d'identité n'a pas de privilèges suffisants pour lire le fichier sélectionné.  
  
## <a name="ui-element-list"></a>Liste d’éléments d’interface utilisateur  
 **Nom convivial de la connexion**  
 Tapez un nom unique pour cette connexion à la source de données. Ce champ est obligatoire.  
  
 **Chemin du fichier Excel**  
 Spécifiez le chemin d'accès complet du fichier Excel.  
  
 **Parcourir**  
 Accédez à un emplacement dans lequel un fichier Excel est disponible.  
  
 **Avancée**  
 Définissez des propriétés de connexion supplémentaires à l’aide de la boîte de dialogue **définir les propriétés avancées** .  
  
 **Utiliser la première ligne comme en-têtes de colonnes**  
 Spécifiez s'il convient d'utiliser la première ligne de données comme en-têtes de colonnes de la table de destination.  
  
 **Tester la connexion**  
 Essayez d'établir une connexion à la source de données à l'aide des paramètres actuels. Un message est affiché pour indiquer si la connexion a abouti.  
  
  
