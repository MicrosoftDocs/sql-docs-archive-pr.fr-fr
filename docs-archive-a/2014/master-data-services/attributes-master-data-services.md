---
title: Attributs (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5a6fb01b47658f39e14c599ae88aa7ad3d29c69a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613004"
---
# <a name="attributes-master-data-services"></a>Attributs (Master Data Services)
  Les attributs sont des objets contenus dans des entités [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Les valeurs d'attribut décrivent les membres de l'entité. Un attribut peut être utilisé pour décrire un membre feuille, un membre consolidé ou une collection.  
  
## <a name="how-attributes-relate-to-other-model-objects"></a>Relations entre les attributs et les autres objets de modèle  
 Vous pouvez considérer un attribut comme une colonne dans une table d'entités. Une valeur d'attribut est la valeur utilisée pour décrire un membre spécifique.  
  
 ![Entité Master Data Services représentée en tant que table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Entité Master Data Services représentée en tant que table")  
  
 Lorsque vous créez une entité qui contient de nombreux attributs, vous pouvez les organiser en groupes d'attributs. Pour plus d’informations, consultez [Groupes d’attributs &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).  
  
## <a name="required-attributes"></a>Attributs requis  
 Lorsque vous créez une entité, les attributs Name et Code sont créés automatiquement. L'attribut Code requiert une valeur et doit être unique dans l'entité. Vous ne pouvez pas supprimer les attributs Name et Code.  
  
## <a name="attribute-types"></a>Types d’attributs  
 Il existe trois types d'attributs :  
  
-   Les attributs de forme libre qui acceptent comme entrées de forme libre du texte, des nombres, des dates et des liens.  
  
-   Les attributs basés sur un domaine, remplis par les entités. Pour plus d’informations, consultez [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).  
  
-   Les attributs de fichier qui permettent de stocker des fichiers, des documents ou des images. Les attributs de fichier qui contribuent à la cohérence de vos données en requérant que les fichiers aient une extension spécifique. Les attributs de fichier ne peuvent pas empêcher un utilisateur malveillant de télécharger un fichier d'un type différent.  
  
### <a name="numeric-free-form-attributes"></a>Attributs numériques de forme libre  
 Les attributs numériques de forme libre nécessitent une gestion spéciale, car leurs valeurs sont limitées au type **SqlDouble** .  
  
 Par défaut, une valeur décimale **SqlDouble** est caractérisée par une précision à 15 chiffres, bien qu’un maximum de 17 chiffres soit maintenu en interne. La précision d'un nombre à virgule flottante a plusieurs conséquences :  
  
-   Deux nombres à virgule flottante qui apparaissent égaux pour une précision particulière peuvent ne pas l'être parce que leurs chiffres de droite sont différents.  
  
-   Une opération mathématique ou de comparaison qui utilise un nombre à virgule flottante peut ne pas donner le même résultat si un nombre décimal est utilisé parce que le nombre à virgule flottante peut ne pas se rapprocher exactement du nombre décimal.  
  
-   Il peut arriver qu’une valeur n’effectue pas *d’aller-retour* si un nombre à virgule flottante est utilisé. Une valeur est dite d'aller-retour lorsqu'une opération convertit un nombre à virgule flottante d'origine sous une autre forme, lorsque l'opération inverse retransforme la forme convertie en un nombre à virgule flottante et lorsque le dernier chiffre du nombre à virgule flottante est égal au chiffre du nombre à virgule flottante d'origine. L'aller-retour peut échouer parce qu'un ou plusieurs chiffres de droite sont perdus ou ont changé au cours d'une conversion.  
  
## <a name="attribute-examples"></a>Exemples d'attributs  
 Dans l'exemple suivant, l'entité comporte les attributs suivants : Name, Code, Subcategory, StandardCost, ListPrice et FilePhoto. Ces attributs décrivent les membres. Chaque membre est représenté par une ligne unique de valeurs d'attribut.  
  
 ![Table de l'entité Bike Product](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Table de l'entité Bike Product")  
  
 Dans l'exemple suivant, l'entité Product contient :  
  
-   Les attributs de forme libre Name, Code, StandardCost et ListPrice.  
  
-   L'attribut basé sur un domaine Subcategory.  
  
-   L'attribut de fichier FilePhoto.  
  
 Subcategory est une entité utilisée comme un attribut basé sur un domaine de Product. Category est une entité utilisée comme un attribut basé sur un domaine de Subcategory. Comme l'entité Product, les entités Category et Subcategory contiennent chacune les attributs par défaut Name et Code.  
  
 ![Arborescence de l'entité Product](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Arborescence de l'entité Product")  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer un attribut de texte de forme libre.|[Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|Créer un attribut numérique de forme libre.|[Créer un attribut numérique &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|Créer un attribut de lien de forme libre.|[Créer un attribut de lien &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|Créer un attribut de fichier.|[Créer un attribut de fichier &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|Créer un attribut basé sur un domaine.|[Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Modifier le nom d'un attribut existant.|[Modifier le nom d’un attribut &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)|  
|Ajouter des attributs existants à un groupe de suivi des modifications.|[Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Supprimer un attribut existant.|[Supprimer un attribut &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|Modifier l'ordre des attributs.|[Changer l'ordre des attributs](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Attributs basés sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [Groupes d’attributs &#40;Master Data Services&#41;](attribute-groups-master-data-services.md)  
  
-   [Membres &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
-   [Autorisations de feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [Autorisations consolidées &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
