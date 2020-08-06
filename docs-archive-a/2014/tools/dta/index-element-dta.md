---
title: Index, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Index element (DTA)
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 110dcd8ef5f554bdf1c59ab9a15984ec8ca97c65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703632"
---
# <a name="index-element-dta"></a>Index, élément (Assistant Paramétrage de base de données)
  Contient les informations sur un index que vous souhaitez créer ou supprimer pour une configuration spécifiée par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut d'index|Type de données|Description|  
|---------------------|---------------|-----------------|  
|`Clustered`|`boolean`|facultatif. Spécifie un index cluster. Défini sur « true » ou « false », par exemple :<br /><br /> `<Index Clustered="true">`<br /><br /> Par défaut, cet attribut est défini sur « false ».|  
|`Unique`|`boolean`|facultatif. Spécifie un index unique Défini sur « true » ou « false », par exemple :<br /><br /> `<Index Unique="true">`<br /><br /> Par défaut, cet attribut est défini sur « false ».|  
|`Online`|`boolean`|facultatif. Spécifie un index qui peut effectuer des opérations alors que le serveur est connecté, ce qui nécessite de l'espace disque temporaire. Défini sur « true » ou « false », par exemple :<br /><br /> `<Index Online="true">`<br /><br /> Par défaut, cet attribut est défini sur « false ».<br /><br /> Pour plus d'informations, consultez [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).|  
|`IndexSizeInMB`|`double`|facultatif. Spécifie la taille maximale, en mégaoctets, de l'index, par exemple :<br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> Aucun paramètre par défaut.|  
|`NumberOfRows`|`integer`|facultatif. Simule différentes tailles d'index, ce qui simule différentes tailles de tables, par exemple :<br /><br /> `<Index NumberOfRows="3000">`<br /><br /> Aucun paramètre par défaut.|  
|`QUOTED_IDENTIFIER`|`boolean`|facultatif. Force [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à suivre les règles ISO concernant les guillemets délimitant les identificateurs et les chaînes littérales. Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).|  
|`ARITHABORT`|`boolean`|facultatif. Entraîne l'arrêt d'une requête lorsqu'un dépassement de capacité ou une division par zéro se produit durant son exécution. Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index ARITHABORT [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).|  
|`CONCAT_NULL_YIELDS_`<br /><br /> `NULL`|`boolean`|facultatif. Détermine si les résultats de concaténation sont considérés comme des valeurs NULL ou des chaînes vides. Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).|  
|`ANSI_NULLS`|`boolean`|facultatif. Spécifie le comportement conforme à la norme ISO pour les opérateurs de comparaison égal à (=) et différent de (<>), lorsqu'ils sont utilisés avec des valeurs Null. Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).|  
|`ANSI_PADDING`|`boolean`|facultatif. Contrôle la façon dont une colonne stocke des valeurs plus courtes que sa taille définie Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).|  
|`ANSI_WARNINGS`|`boolean`|facultatif. Spécifie le comportement conforme à la norme ISO pour plusieurs conditions d'erreur : Cet attribut doit être activé si l'index se trouve sur une colonne calculée ou une vue. Par exemple, la syntaxe suivante active cet attribut :<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).|  
|`NUMERIC_ROUNDABORT`|`boolean`|facultatif. Spécifie le niveau de gravité de l'erreur générée lorsqu'un arrondi effectué dans une expression entraîne une perte de précision. Cet attribut doit être désactivé si l'index se trouve sur une colonne calculée ou une vue.<br /><br /> La syntaxe suivante active cet attribut :<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Par défaut, cet attribut est désactivé.<br /><br /> Pour plus d’informations, consultez [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois pour chaque élément `Create` ou `Drop` si aucune autre structure PDS n'est spécifiée avec les éléments `Statistics` ou `Heap`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Create, élément &#40;Assistant Paramétrage de base de données&#41;](create-element-dta.md)<br /><br /> `Drop`Appartient. Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.|  
|**Éléments enfants**|[Name, élément pour les index &#40;Assistant Paramétrage de base de données&#41;](name-element-for-index-dta.md)<br /><br /> [Column, élément pour les index &#40;Assistant Paramétrage de base de données&#41;](column-element-for-index-dta.md)<br /><br /> `PartitionScheme`Appartient. Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.<br /><br /> `PartitionColumn`Appartient. Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.<br /><br /> [Filegroup, élément pour les index &#40;Assistant Paramétrage de base de données&#41;](filegroup-element-for-index-dta.md)<br /><br /> `NumberOfReferences`Appartient. Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.<br /><br /> `PercentUsage`Appartient. Pour plus d'informations, voir le schéma de l'Assistant Paramétrage du moteur de base de données.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
