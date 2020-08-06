---
title: Hiérarchies déséquilibrées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ragged hierarchies [Analysis Services]
ms.assetid: e40a5788-7ede-4b0f-93ab-46ca33d0cace
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02cbb24b7ae80facf0ddbb1495fccc8f848df377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707928"
---
# <a name="ragged-hierarchies"></a>Hiérarchies déséquilibrées
  Une hiérarchie déséquilibrée est une hiérarchie définie par l'utilisateur qui a un nombre de niveaux impair. Voici quelques exemples : un organigramme où un responsable hiérarchique a comme subordonnés directs des cadres du service et des non cadres, ou des hiérarchies avec des attributs Country-Region-City, où certaines villes n'ont pas d'état (State) ou de province (Province) parent, notamment Washington D.C., l’État de la Cité du Vatican ou New Dehli.  
  
 Pour la plupart des hiérarchies dans une dimension, chaque niveau a le même nombre de membres au-dessus de lui que tout autre membre au même niveau. Dans une hiérarchie déséquilibrée, en revanche, le membre parent logique d'au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. En pareil cas, la hiérarchie descend à des niveaux différents pour des chemins d'extraction différents. Dans une application cliente, cela peut rendre les chemins d'extraction inutilement compliqués.  
  
 Les applications clientes varient dans la manière de gérer une hiérarchie déséquilibrée. S'il existe des hiérarchies déséquilibrées dans votre modèle, vous devrez effectuer un travail supplémentaire pour obtenir le comportement de rendu attendu.  
  
 Dans un premier temps, vérifiez la façon dont l'application cliente gère le chemin d'extraction. Par exemple, Excel répète les noms parents en tant qu'espaces réservés pour les valeurs manquantes. Pour afficher ce comportement, créez un tableau croisé dynamique à l'aide de la dimension Sales Territory dans le modèle multidimensionnel Adventure Works. Dans un tableau croisé dynamique avec les attributs Group, Country et Region pour Sales Territory, vous constaterez que les pays pour lesquels il manque une valeur de région obtiennent un espace réservé, dans ce cas une répétition du parent au-dessus (le nom du pays). Ce comportement dérive de la propriété de chaîne de connexion MDX Compatibility=1 qui est fixe dans Excel. Si le client ne fournit pas naturellement les comportements d'extraction dont vous avez besoin, vous pouvez définir les propriétés du modèle pour modifier au moins certains de ces comportements.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Approches pour modifier la navigation d’exploration dans une hiérarchie déséquilibrée](#bkmk_approach)  
  
-   [Définir HideMemberIf pour masquer les membres dans une hiérarchie normale](#bkmk_Hide)  
  
-   [Définir la compatibilité MDX pour déterminer le mode de représentation des espaces réservés dans les applications clientes](#bkmk_Mdx)  
  
##  <a name="approaches-for-modifying-drilldown-navigation-in-a-ragged-hierarchy"></a><a name="bkmk_approach"></a> Approches pour modifier la navigation d'exploration dans une hiérarchie déséquilibrée  
 La présence d'une hiérarchie déséquilibrée est un problème lorsque la navigation d'extraction ne retourne pas les valeurs attendues ou est perçue comme une utilisation maladroite. Pour résoudre les problèmes de navigation qui résultent de hiérarchies déséquilibrées, considérez ces options :  
  
-   Utilisez une hiérarchie régulière, mais définissez la propriété `HideMemberIf` sur chaque niveau afin de spécifier si un niveau manquant est visualisé par l'utilisateur. Lorsque vous définissez `HideMemberIf`, vous devez également définir `MDXCompatibility` dans la chaîne de connexion pour remplacer les comportements de navigation par défaut. Les instructions de définition de ces propriétés sont fournies dans cette rubrique.  
  
-   Créez une hiérarchie parent-enfant qui gère explicitement les membres de niveau. Pour une présentation de la technique, consultez [Hiérarchie déséquilibrée dans SSAS (billet de blog)](http://dwbi1.wordpress.com/2011/03/30/ragged-hierarchy-in-ssas/). Pour plus d’informations dans la documentation en ligne de, consultez [hiérarchie parent-enfant](parent-child-dimension.md). Les inconvénients liés à la création d'une hiérarchie parent-enfant résident dans le fait que vous ne pouvez en avoir qu'une seule par dimension, ce qui entraîne généralement une baisse des performances lors du calcul des agrégations pour les membres intermédiaires.  
  
 Si votre dimension contient plusieurs hiérarchies déséquilibrées, vous devez utiliser la première approche, en définissant `HideMemberIf`. Les développeurs BI qui ont une expérience pratique des hiérarchies déséquilibrées vont plus loin et recommandent d'apporter des modifications supplémentaires aux tables de données physiques, en créant des tables distinctes pour chaque niveau. Pour plus d’informations sur cette technique, consultez [le cube financier SSAS de Martin Mason-part 1a-divisible Hierarchies (blog)](http://martinmason.wordpress.com/2012/03/03/the-ssas-financial-cubepart-1aragged-hierarchies-cont/) .  
  
##  <a name="set-hidememberif-to-hide-members-in-a-regular-hierarchy"></a><a name="bkmk_Hide"></a> Définition de HideMemberIf pour masquer les membres dans une hiérarchie normale  
 Dans la table d'une dimension déséquilibrée, les membres manquants peuvent être représentés de différentes manières. Les espaces réservés des cellules de table peuvent être des valeurs NULL ou des chaînes vides, ou bien la même valeur que leurs parents. La représentation des espaces réservés est déterminée par l'état d'espace réservé de membres enfants, conformément à la propriété `HideMemberIf`, et par la propriété de chaîne de connexion `MDX Compatibility` pour l'application cliente.  
  
 Pour les applications clientes qui autorisent l'affichage de hiérarchies déséquilibrées, vous pouvez utiliser ces propriétés de façon à masquer les membres manquants.  
  
1.  Dans SSDT, double-cliquez sur une dimension pour l'ouvrir dans le Concepteur de dimensions. Le premier onglet, Structure de dimension, affiche les hiérarchies d'attribut dans le volet Hiérarchies.  
  
2.  Cliquez avec le bouton droit sur un membre de la hiérarchie et choisissez **Propriétés**. Définissez `HideMemberIf` sur l'une des valeurs décrites ci-dessous.  
  
    |Paramètre de HideMemberIf|Description|  
    |--------------------------|-----------------|  
    |`Never`|Les membres de ce niveau ne sont jamais masqués. Valeur par défaut.|  
    |**OnlyChildWithNoName**|Un membre de ce niveau est masqué quand il est le seul enfant de son parent et qu'il a pour nom la valeur NULL ou une chaîne vide.|  
    |**OnlyChildWithParentName**|Un membre de ce niveau est masqué quand il est le seul enfant de son parent et qu'il porte le même nom que son parent.|  
    |**NoName**|Un membre de ce niveau est masqué lorsque son nom est vide.|  
    |**ParentName**|Un membre de ce niveau est masqué quand son nom est identique à celui de son parent.|  
  
##  <a name="set-mdx-compatibility-to-determine-how-placeholders-are-represented-in-client-applications"></a><a name="bkmk_Mdx"></a>Définir la compatibilité MDX pour déterminer le mode de représentation des espaces réservés dans les applications clientes  
 Après avoir défini `HideMemberIf` sur un niveau hiérarchique, vous devez également définir la propriété `MDX Compatibility` dans la chaîne de connexion envoyée depuis l'application cliente. Le paramètre `MDX Compatibility` détermine si `HideMemberIf` est utilisé.  
  
|Paramètre de compatibilité MDX|Description|Usage|  
|-------------------------------|-----------------|-----------|  
|**1**|Afficher une valeur d'espace réservé.|Il s'agit de la valeur par défaut utilisée par Excel, SSDT et SSMS. Elle indique au serveur de retourner les valeurs d'espace réservé lors de l'exploration de niveaux vides dans une hiérarchie déséquilibrée. Si vous cliquez sur la valeur d'espace réservé, vous pouvez continuer à explorer le bas de la hiérarchie pour obtenir les nœuds enfants (feuille).<br /><br /> Excel détient la chaîne de connexion utilisée pour la connexion à Analysis Services et définit toujours `MDX Compatibility` sur 1 pour chaque nouvelle connexion. Ce comportement préserve la compatibilité descendante.|  
|**2**|Masquez une valeur d'espace réservé (valeur Null ou dupliquée du niveau parent), mais affichez d'autres niveaux et nœuds avec des valeurs pertinentes.|`MDX Compatibility`=2 est généralement considéré comme le paramètre privilégié pour les hiérarchies déséquilibrées. Un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et certaines applications clientes tierces peuvent rendre ce paramètre persistant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des hiérarchies définies par l’utilisateur](user-defined-hierarchies-create.md)   
 [Hiérarchies utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Hiérarchie parent-enfant](parent-child-dimension.md)   
 [Propriétés des chaînes de connexion &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/instances/connection-string-properties-analysis-services)  
  
  
