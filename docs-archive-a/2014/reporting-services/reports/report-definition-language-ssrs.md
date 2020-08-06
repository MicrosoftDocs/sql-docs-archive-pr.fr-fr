---
title: Langage de définition de rapport (SSRS, Report Definition Language) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Reporting Services, RDL
- Reporting Services, RDL
- RDL [Reporting Services], about Report Definition Language
- SSRS, RDL
- Report Definition Language, about Report Definition Language
- Report Definition Language
- RDL [Reporting Services]
- reports [Reporting Services], definitions
ms.assetid: b18b025e-f4bd-4744-8f86-0ac9fb967548
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dba006564da0d0554dc812f1a8752234d4249092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603831"
---
# <a name="report-definition-language-ssrs"></a>Langage de définition de rapport (SSRS, Report Definition Language)
  Report Definition Language (RDL) est une représentation XML d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] définition de rapport. Une définition de rapport contient les informations d'extraction de données et de mise en page d'un rapport. La spécification RDL est composée d’éléments XML qui sont conformes à une grammaire XML créée pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous pouvez ajouter vos propres fonctions personnalisées pour contrôler les valeurs, les styles et la mise en forme des éléments de rapport en accédant à des assemblys de code dans les fichiers de définition de rapport.  
  
 Le langage RDL favorise l'interopérabilité des produits commerciaux de création de rapports en définissant un schéma commun qui permet l'échange de définitions de rapport. Les protocoles ou les interfaces de programmation qui fonctionnent avec XML peuvent être utilisés avec le langage RDL. Les caractéristiques du langage RDL sont les suivantes :  
  
-   Schéma XML pour les définitions de rapport  
  
-   Format d'échange pour les entreprises et les fournisseurs tiers  
  
-   Schéma extensible et ouvert qui prend en charge des éléments personnalisés et des espaces de noms supplémentaires.  
  
##  <a name="rdl-specifications"></a><a name="bkmk_RDL_Specifications"></a>Spécifications RDL  
 Pour télécharger les spécifications des versions de schéma spécifiques, consultez [Report Definition Language Specification](https://go.microsoft.com/fwlink/?linkid=116865)[Spécification RDL (Report Definition Language)].  
  
##  <a name="rdl-xml-schema-definition"></a><a name="bkmk_RDL_XML_Schema_Definition"></a>Définition de schéma XML RDL  
 Un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fichier de Report Definition Language (RDL) est validé à l’aide d’un fichier XSD (XML Schema Definition). Le schéma définit les règles indiquant où des éléments RDL peuvent se trouver dans un fichier .rdl. Un élément inclut son type de données et sa cardinalité, c’est-à-dire le nombre d’occurrences autorisées. Un élément peut être simple ou complexe. Un élément simple n'a pas d'éléments enfants ni d'attributs. Un élément complexe a des enfants et éventuellement des attributs.  
  
 Par exemple, le schéma inclut l'élément RDL `ReportParameters`, qui est le type complexe `ReportParametersType`. Par convention, un type complexe d'un élément correspond au nom de l'élément suivi du mot `Type`. Un élément `ReportParameters` peut être contenu par l'élément `Report` (type complexe) et peut contenir des éléments `ReportParameter`. Un type `ReportParameterType` est un type simple qui ne peut avoir d'autres valeurs que les valeurs suivantes : `Boolean`, `DateTime`, `Integer`, `Float` et `String`. Pour plus d’informations sur les types de données de schéma XML, consultez [XML Schema Part 2: Datatypes Second Edition](https://go.microsoft.com/fwlink/?linkid=4871)(Schéma XML - Partie 2 : Types de données - Deuxième édition).  
  
 Le XSD RDL est disponible dans le fichier ReportDefinition.xsd, situé dans le dossier Extras sur le CD-ROM du produit. Il est également disponible sur le serveur de rapports via l’URL suivante : http://servername/reportserver/reportdefinition.xsd.  
  
##  <a name="creating-rdl"></a><a name="bkmk_Creating_RDL"></a>Création de RDL  
 Compte tenu du caractère ouvert et extensible du langage RDL, il est possible de créer divers outils et applications qui génèrent le langage RDL selon son schéma XML.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit plusieurs outils pour créer les fichiers RDL. Pour plus d’informations, consultez [Outils de Reporting Services](../tools/reporting-services-tools.md).  
  
 L’une des méthodes les plus simples pour générer le langage RDL à partir d’une application consiste à utiliser les [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes de l’espace de noms et de l' <xref:System.Xml> <xref:System.Linq> espace de noms. Une classe en particulier, la classe **XmlTextWriter** , peut être utilisée pour l’écriture du langage RDL. Cette classe **XmlTextWriter**vous permet de générer intégralement une définition de rapport complète dans une application [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Les développeurs peuvent également étendre le langage RDL en ajoutant des éléments de rapport personnalisés avec des propriétés personnalisées. Pour plus d’informations sur la classe **XmlTextWriter** et l’espace de noms <xref:System.Xml>, consultez le Guide du développeur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Pour plus d'informations sur LINQ (Language-Integrated Query), recherchez les termes « LINQ to XML » sur MSDN.  
  
 L'extension de fichier standard pour les fichiers de définition de rapport est .rdl. Vous pouvez également développer des fichiers de définition de rapport client, lesquels portent l'extension .rdlc. Le type MIME pour les deux extensions est text/xml. Pour plus d’informations sur les rapports, consultez [Rapports Reporting Services &#40;SSRS&#41;](reporting-services-reports-ssrs.md).  
  
##  <a name="rdl-types"></a><a name="bkmk_RDL_Types"></a>Types RDL  
 La table suivante répertorie les types utilisés dans des éléments et des attributs RDL.  
  
|Type|Description|  
|----------|-----------------|  
|`Binary`|Propriété dotée d'une valeur binaire encodée en base 64.|  
|`Boolean`|Propriété de l'objet ayant pour valeur `true` ou `false`. Sauf indication contraire, la valeur d'un objet Boolean omis facultatif est `False`.|  
|`Date`|Propriété dotée d'une valeur date ou date/heure entièrement spécifiée au format de date ISO8601 : AAAA-MM-JJ[THH:MM[:SS[.S]]]|  
|`Enum`|Propriété dont la valeur est le texte d'une chaîne, qui doit appartenir à une liste de valeurs désignées.|  
|`Float`|Propriété dotée d'une valeur flottante (Float). Une virgule (,) est utilisée comme séparateur décimal facultatif.|  
|`Integer`|Propriété dotée d'une valeur entière (int32).|  
|`Language`|Propriété dont la valeur est le texte d'une chaîne, qui contient un code de langue et de culture, tel que « en-us » pour l'anglais (États-Unis). La valeur doit être une langue spécifique ou une langue neutre pour laquelle une langue par défaut est définie dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .|  
|`Name`|Propriété dont la valeur est le texte d'une chaîne. Les noms doivent être uniques dans l'espace de noms de l'élément. S'il n'est pas spécifié, l'espace de noms d'un élément est l'objet conteneur le plus profond doté d'un nom.|  
|`NormalizedString`|Propriété dont la valeur est le texte d'une chaîne, qui a été normalisée.|  
|`Size`|Un élément de taille doit contenir un nombre (avec une virgule comme séparateur décimal facultatif). Le nombre doit être suivi d'un indicateur pour une unité de longueur CSS ; par exemple, cm, mm, in, pt ou pc. Un espace entre le nombre et l'indicateur est facultatif. Pour plus d’informations sur les indicateurs de taille, consultez [CSS Length Units Reference](https://www.w3schools.com/CSSref/css_units.asp)(Guide de référence des unités de longueur CSS).<br /><br /> Dans RDL, la valeur maximale pour `Size` est de 160 po. La taille minimale est 0 po.|  
|`String`|Propriété dont la valeur est le texte d'une chaîne.|  
|`UnsignedInt`|Propriété dotée d'une valeur entière non signée (uint32).|  
|`Variant`|Une propriété dotée d'un type XML simple.|  
  
##  <a name="rdl-data-types"></a><a name="bkmk_RDL_Data_Types"></a>Types de données RDL  
 L'énumération DataType définit le type de données d'un attribut, d'une expression ou d'un paramètre dans RDL. Le tableau suivant illustre les types de données CLR (common langage runtime (CLR)) correspondent aux types de données RDL.  
  
|**Type CLR**|**Type de données correspondant**|  
|-----------------------|---------------------------------|  
|Boolean|Boolean|  
|DateTime, DateTimeOffset|DateTime|  
|Int16, Int32, UInt16, Byte, SByte|Integer|  
|Single, Double|Float|  
|String, Char, GUID, Timespan|String|  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher la version du schéma de définition de rapport &#40;SSRS&#41;](find-the-report-definition-schema-version-ssrs.md)   
 [Utilisation d’assemblys personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Éléments de rapport personnalisés](../custom-report-items/custom-report-items.md)  
  
  
