---
title: Rendu des données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a458fdf9-fb2a-4fee-9fbd-b38f36e91753
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc2757d308529c8b5a03e206a827fce7028edbfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704899"
---
# <a name="rendering-data-report-builder-and-ssrs"></a>Rendu des données (Générateur de rapports et SSRS)
  Lorsque vous utilisez des convertisseurs de mise en page, tels que HTML, MHTML, Word, Excel, PDF ou Image, les données et leur organisation restent inchangées. Lorsque vous effectuez une exportation à l'aide d'un format de convertisseur de données, comme CSV ou XML, aucun élément de présentation visuelle n'est rendu. Lors du rendu du rapport, les formats CSV et XML appliquent certaines règles au corps du rapport et à son contenu. Ces règles déterminent la façon dont les données sont rendues dans ces formats.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Vous pouvez utiliser des convertisseurs de données pour les opérations suivantes :  
  
-   Importation dans une base de données. Le format CSV est un format commun que de nombreuses applications de base de données peuvent facilement importer, notamment SQL Server et Microsoft Access.  
  
-   Importation dans Excel. Utilisez le convertisseur CSV pour exporter vos données vers Excel sans présentation visuelle. Une fois que les données sont dans Excel, vous pouvez tirer parti des outils Excel standard tels que les graphiques, les formules et les tableaux croisés dynamiques.  
  
-   Transformations XSLT. Une transformation XSLT peut être appliquée à la sortie du convertisseur XML. Cette transformation côté serveur est une technique puissante pour transformer vos données en quasiment tous les formats.  
  
-   Échange de données/EDI. Un processus externe peut demander un rendu CSV ou XML d'un rapport et utiliser ces données.  
  
 Les formats des convertisseurs de données et les convertisseurs de mise en page sont contrôlés par un ensemble différent de propriétés. Vous trouverez ci-dessous une liste de propriétés définies dans le volet **Propriétés** qui ne s'appliquent qu'aux convertisseurs de données :  
  
-   La propriété DataElementOutput contrôle si un élément spécifique est présent ou non dans les données pendant l’exportation.  
  
-   La propriété DataElementName contrôle le nom de l’élément de données. Dans le format CSV, cela contrôle le nom de l'en-tête de colonne CSV. Dans le format XML, cela devient le nom de l'élément XML ou de l'attribut de l'élément.  
  
-   La propriété DataElementStyle contrôle, dans le format XML, si l’élément de rapport est ou non rendu sous la forme d’un élément ou d’un attribut.  
  
 L'option d'exportation CSV enregistre les données du rapport sous la forme de fichiers texte bruts aux valeurs délimitées par des virgules, sans aucune mise en forme. Par défaut, le fichier utilise une virgule (,) pour délimiter les champs et les lignes, mais ce paramètre peut être configuré à l'aide des paramètres d'informations de périphérique. Le fichier obtenu peut être ouvert dans un tableur comme Office SharePoint Server ou être utilisé comme format d'importation pour d'autres programmes. Le fichier .csv s'ouvre dans un éditeur de texte, tel que le Bloc-notes. Si vous y accédez par une URL, le fichier .csv retourne un type MIME **texte/csv**. Les fichiers utilisent le codage MIME version 1.0. Pour plus d’informations sur le rendu de votre rapport dans le type de fichier CSV, consultez [Exportation vers un fichier CSV &#40;Générateur de rapports et SSRS&#41;](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
 L'option d'exportation des données d'un rapport en tant que fichier XML enregistre le rapport sous la forme d'un fichier XML. Le schéma XML du rapport est spécifique au rapport. Les informations de mise en page du rapport ne sont pas enregistrées par l'option d'exportation XML. La sortie XML générée par cette option peut être importée dans une base de données, utilisée en tant que message de données XML ou envoyée à une application personnalisée. Pour plus d’informations sur le rendu de votre rapport dans le type de fichier XML, consultez [Exportation au format XML &#40;Générateur de rapports et SSRS&#41;](../report-builder/exporting-to-xml-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)   
 [Fonctionnalités interactives des différentes extensions de rendu de rapport &#40;Générateur de rapports et SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendu des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md)   
 [Répertorie &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Paramètres d’informations de périphérique Reporting Services](https://go.microsoft.com/fwlink/?LinkId=102515)  
  
  
