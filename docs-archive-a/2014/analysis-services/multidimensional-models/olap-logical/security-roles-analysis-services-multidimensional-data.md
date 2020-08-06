---
title: Rôles de sécurité (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62abaab5a8f74dfee7d51962f2fb243dc6eb20a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705560"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>Rôles de sécurité (Analysis Services - Données multidimensionnelles)
  Les rôles sont utilisés dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour gérer la sécurité des [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objets et des données. En clair, un rôle associe les identificateurs de sécurité (SID) des utilisateurs et des groupes de Microsoft Windows qui disposent de droits et d'autorisations d'accès spécifiques, définis pour des objets gérés par une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Deux types de rôles sont fournis dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:  
  
-   le rôle du serveur, un rôle fixe qui fournit un accès administrateur à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)];  
  
-   les rôles de base de données, des rôles définis par les administrateurs pour contrôler l'accès des utilisateurs qui ne sont pas administrateurs aux objets et aux données.  
  
 La sécurité dans la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sécurité est gérée à l’aide de rôles et d’autorisations. Les rôles sont des groupes d'utilisateurs. Les utilisateurs, également appelés membres, peuvent être ajoutés ou supprimés des rôles. Les autorisations pour les objets sont spécifiées par les rôles et tous les membres dans un rôle peuvent utiliser les objets pour lesquels le rôle a des autorisations. Tous les membres dans un rôle ont des autorisations aux objets égales. Les autorisations sont particulières aux objets. Chaque objet a une collection d'autorisations incluant les autorisations accordées pour cet objet, différents jeux d'autorisations peuvent être accordés sur un objet. Chaque autorisation de la collection d'autorisations de l'objet se voit attribuer un rôle unique.  
  
## <a name="role-and-role-member-objects"></a>Rôle et objets membres du rôle  
 Un rôle est un objet conteneur d'une collection d'utilisateurs (membres). La définition du rôle établit l'appartenance des utilisateurs dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Parce que les autorisations sont assignées par rôle, un utilisateur doit être le membre d'un rôle avant d'avoir accès à tout objet.  
  
 Un objet <xref:Microsoft.AnalysisServices.Role> est composé des paramètres Name, Id et Members. Le paramètre Members est une collection de chaînes. Chaque membre contient le nom d'utilisateur sous la forme « domaine\nom d'utilisateur ». Le nom est une chaîne qui contient le nom du rôle. L'ID est une chaîne qui contient l'identificateur unique du rôle.  
  
### <a name="server-role"></a>Rôle serveur  
 Le rôle de serveur [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] définit l'accès d'administrateur des utilisateurs et des groupes Windows à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Les membres de ce rôle ont accès à toutes les bases de données et tous les objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sur une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]et ils peuvent effectuer les tâches suivantes :  
  
-   effectuer des fonctions d'administration de niveau serveur à l'aide de SQL Server Management Studio ou de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], notamment créer des bases de données et définir des propriétés de niveau serveur ;  
  
-   effectuer des fonctions d'administration par programme avec AMO (Analysis Management Objects) ;  
  
-   maintenir les rôles de base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ;  
  
-   démarrer des traces (à des fins autres que le traitement des événements, qui peut être effectué par un rôle de base de données ayant accès aux processus).  
  
 Chaque instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] a un rôle de serveur qui définit les utilisateurs pouvant l'administrer. Le nom et ID de ce rôle est Administrateurs et contrairement aux rôles de base de données, le rôle du serveur ne peut pas être supprimé et des autorisations ne peuvent pas être ajoutées ou supprimées. En d'autres termes, un utilisateur est ou n'est pas administrateur pour une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], selon qu'il ou elle est inclus dans le rôle de serveur de cette instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
### <a name="database-roles"></a>Rôles de base de données  
 Un rôle de base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] définit l'accès utilisateur aux objets et données d'une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Un rôle de base de données est créé comme un objet distinct dans une base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et s'applique uniquement à la base de données dans laquelle il est créé. Les utilisateurs et les groupes Windows sont inclus dans le rôle par un administrateur, qui définit également les autorisations à l'intérieur du rôle.  
  
 Les autorisations d'un rôle peuvent permettre aux membres d'accéder à la base de données et de l'administrer, y compris les objets et les données qu'elle contient. Chaque autorisation a un ou plusieurs droits d'accès qui lui sont associés, ce qui permet d'affiner le contrôle relatif à l'accès à un objet particulier de la base de données.  
  
## <a name="permission-objects"></a>Objets Permission  
 Les autorisations sont associées à un objet (cube, dimension et autres) pour un rôle particulier. Les autorisations spécifient les opérations que le membre d'un rôle peut effectuer sur un objet.  
  
 La classe <xref:Microsoft.AnalysisServices.Permission> est une classe abstraite. Par conséquent, vous devez utiliser les classes dérivées pour définir des autorisations sur les objets correspondants. Pour chaque objet, une classe d'autorisation dérivée est définie.  
  
|Object|Classe|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 Les actions possibles activées par les autorisations sont répertoriées dans la liste :  
  
|Action|Valeurs|Explication|  
|------------|------------|-----------------|  
|Process|{`true`, `false`}<br /><br /> Valeur par défaut=`false`|Si `true`, les membres peuvent traiter l'objet et tout objet contenu dans l'objet.<br /><br /> Les autorisations de processus ne s'appliquent pas aux modèles d'exploration de données. Les autorisations <xref:Microsoft.AnalysisServices.MiningModel> sont toujours héritées de l'objet <xref:Microsoft.AnalysisServices.MiningStructure>.|  
|ReadDefinition|{`None`, `Basic`, `Allowed`}<br /><br /> Valeur par défaut=`None`|Spécifie si les membres peuvent lire les définitions de données (ASSL) associées à l'objet.<br /><br /> Si `Allowed`, les membres peuvent lire les définitions ASSL associées à l'objet.<br /><br /> `Basic` et `Allowed` sont hérités par les objets contenus dans l'objet. `Allowed` remplace `Basic` et `None`.<br /><br /> `Allowed` est requis pour DISCOVER_XML_METADATA sur un objet. `Basic` est requis pour créer des objets liés et des cubes locaux.|  
|Lire|{`None`, `Allowed`}<br /><br /> Valeur par défaut =`None` (sauf pour DimensionPermission, où la valeur par défaut est `Allowed`)|Spécifie si les membres ont l'accès en lecture aux ensembles de lignes et au contenu des données du schéma.<br /><br /> `Allowed`octroie l’accès en lecture à une base de données, ce qui vous permet de découvrir une base de données.<br /><br /> `Allowed` sur un cube, donne l'accès en lecture aux ensembles de lignes du schéma et l'accès au contenu du cube (sauf si contraint par <xref:Microsoft.AnalysisServices.CellPermission> et <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).<br /><br /> `Allowed` sur une dimension, accorde une autorisation de lecture sur tous les attributs dans la dimension (sauf si contraint par <xref:Microsoft.AnalysisServices.CubeDimensionPermission>). L'autorisation de lecture est utilisée uniquement pour l'héritage statique à l'objet <xref:Microsoft.AnalysisServices.CubeDimensionPermission>. `None` sur une dimension masque la dimension et donne uniquement l'accès au membre par défaut pour les attributs pouvant faire l'objet d'une agrégation ; une erreur est levée si la dimension contient un attribut ne pouvant pas faire l'objet d'une agrégation.<br /><br /> `Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningModelPermission> accorde des autorisations pour consulter des objets dans les ensembles de lignes de schéma et effectuer des jointures de prédiction.<br /><br /> **NoteAllowed** est requis pour lire ou écrire dans n’importe quel objet de la base de données.|  
|Write|{`None`, `Allowed`}<br /><br /> Valeur par défaut=`None`|Spécifie si les membres ont un accès en écriture aux données de l'objet parent.<br /><br /> L'accès s'applique aux sous-classes <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, et <xref:Microsoft.AnalysisServices.MiningModel>. Il ne s'applique pas aux sous-classes <xref:Microsoft.AnalysisServices.MiningStructure> de base de données, qui génèrent une erreur de validation.<br /><br /> `Allowed` sur un objet <xref:Microsoft.AnalysisServices.Dimension> accorde une autorisation d'écriture sur tous les attributs dans une dimension.<br /><br /> `Allowed` sur un objet <xref:Microsoft.AnalysisServices.Cube> accorde l'autorisation d'écriture sur les cellules du cube pour les partitions définies comme Type=writeback.<br /><br /> `Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningModel> accorde l'autorisation de modifier le contenu du modèle.<br /><br /> `Allowed` sur un objet <xref:Microsoft.AnalysisServices.MiningStructure> n'a aucune signification spécifique dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. **Remarque :**  Impossible d’affecter la valeur Write à `Allowed` , sauf si Read a également la valeur`Allowed`|  
|Remarque de l’administration **:** uniquement dans les autorisations de base de données|{`true`, `false`}<br /><br /> Valeur par défaut=`false`|Spécifie si les membres peuvent administrer une base de données.<br /><br /> `true` accorde aux membres l'accès à tous les objets dans une base de données.<br /><br /> Un membre peut avoir des autorisations d'administrateur pour une base de données spécifique, mais pas pour les autres.|  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisation de l’accès à des objets et des opérations &#40;Analysis Services&#41;](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  
