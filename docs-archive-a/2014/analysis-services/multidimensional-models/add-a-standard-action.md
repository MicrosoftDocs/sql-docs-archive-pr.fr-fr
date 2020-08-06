---
title: Ajouter une action standard | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ccb2928a-f75d-4acb-8ff8-fa80bb0935b2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27e11c4b52a8283ba7694b8bd337a5ee9c82eaca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87604205"
---
# <a name="add-a-standard-action"></a>Ajouter une action standard
  Vous ajoutez une action à une base de données à l'aide de la vue Actions du Concepteur de cube. Cette vue est accessible depuis [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Après avoir créé une action, elle devient disponible aux utilisateurs une fois que vous avez retraité le cube approprié. Pour plus d'informations, consultez [Processing Analysis Services Objects](processing-analysis-services-objects.md).  
  
### <a name="to-create-an-action"></a>Pour créer une action  
  
1.  Ouvrez le cube pour lequel vous souhaitez créer une action, puis cliquez sur l'onglet **Actions** .  
  
2.  Dans la barre d'outils, cliquez sur l'icône **Nouvelle action** , puis dans le volet d'expression, procédez comme suit :  
  
    -   Dans **Nom**, tapez le nom de l'action.  
  
    -   Dans la liste déroulante **Type de cible** , sélectionnez le type d’objet auquel vous souhaitez attacher l’action. L'objet que vous sélectionnez dans **Type de cible** détermine les objets qui sont disponibles, ainsi que le type de sélection que vous pouvez effectuer dans **Objet cible**. Le tableau suivant répertorie les sélections **Objet cible** valides pour chaque type de cible.  
  
        |Si vous sélectionnez le type de cible suivant|Effectuez la sélection suivante dans Objet cible|  
        |---------------------------------------------|---------------------------------------------------|  
        |Membres d'attribut|La seule sélection valide est une hiérarchie d'attributs unique. Le type de cible de l'action sera tous les membres de l'attribut, partout où ils apparaissent (autrement dit, l'action s'applique aux hiérarchies définies par l'utilisateur également).|  
        |Cellules|Toutes les cellules est la seule sélection disponible. Si vous choisissez **Cellules** comme type de cible, vous pouvez taper une expression dans **Condition** pour limiter les cellules auxquelles l'action est associée.|  
        |Cube|CURRENTCUBE est la seule sélection disponible. L'action est associée au cube actif.|  
        |Membres de dimension|Sélectionnez une seule dimension. L'action est associée à tous les membres de la dimension.|  
        |Hierarchy|Sélectionnez une hiérarchie unique. L'action sera associée à l'objet hiérarchie uniquement. Les hiérarchies d'attribut apparaissent dans la liste uniquement si leurs propriétés **AttributeHierarchyEnabled** et **AttributeHierarchyVisible** sont définies avec la valeur **True**.|  
        |Membres de hiérarchie|Sélectionnez une hiérarchie unique. L'action est associée à tous les membres de la hiérarchie sélectionnée. Les hiérarchies d'attribut apparaissent dans la liste uniquement si leurs propriétés **AttributeHierarchyEnabled** et **AttributeHierarchyVisible** sont définies avec la valeur **True**.|  
        |Level|Sélectionnez un niveau unique. L'action sera associée à l'objet niveau uniquement.|  
        |Membres de niveau|Sélectionnez un niveau unique. L'action est associée à tous les membres du niveau sélectionné.|  
  
    -   Dans **Objet cible**, cliquez sur la flèche à droite de la zone de texte, puis dans l'arborescence qui s'ouvre, cliquez sur l'objet auquel vous souhaitez attacher l'action, puis sur **OK**.  
  
    -   (Facultatif.) Dans **Condition**, créez une expression MDX pour limiter la cible de l'action. Vous pouvez taper l'expression manuellement ou vous pouvez faire glisser des éléments depuis les onglets **Métadonnées** et **Fonctions** .  
  
    -   Dans la liste déroulante **Type** , sélectionnez le type d’action que vous souhaitez créer. Le tableau suivant répertorie les types d'actions disponibles.  
  
        |Type|Description|  
        |----------|-----------------|  
        |Dataset|Récupère un dataset.|  
        |Propriétaire|Effectue une opération en utilisant une interface différente de celles répertoriées dans ce tableau.|  
        |Ensemble de lignes|Récupère un ensemble de lignes.|  
        |Instruction|Exécute une commande OLE DB.|  
        |URL|Affiche une page Web dynamique dans un navigateur Internet.|  
  
    -   Dans **Expression d'action**, créez une expression qui définit l'action. L'expression doit correspondre à une chaîne. Vous pouvez taper l'expression manuellement ou vous pouvez faire glisser des éléments depuis les onglets **Métadonnées** et **Fonctions** .  
  
3.  (Facultatif.) Développez **Propriétés supplémentaires**, puis effectuez l'une des opérations suivantes :  
  
    -   Dans la liste déroulante **Invocation** , spécifiez le mode d’appel de l’action. Le tableau suivant décrit les options disponibles pour l'appel d'une action.  
  
        |Option|Description|  
        |------------|-----------------|  
        |Interactive|L'action est générée par l'intervention de l'utilisateur.|  
        |Batch|L'action s'exécute en tant que traitement par lots.|  
        |À l'ouverture|L'action s'exécute lorsqu'un utilisateur ouvre le cube.|  
  
    -   Dans **Application**, tapez le nom de l'application associée à l'action. Par exemple, si vous créez une action qui amène un utilisateur vers un site Web spécifique, l'application associée à cette action doit être Microsoft Internet Explorer ou un autre navigateur Web.  
  
        > [!NOTE]  
        >   Les actions propriétaires ne sont pas retournées au serveur sauf si l'application cliente restreint explicitement l'ensemble de lignes du schéma afin de retourner uniquement les actions qui correspondent au nom spécifié dans **Application**.  
  
    -   Dans **contenu**de l’action, si vous utilisez le type d’URL, placez l’adresse Internet entre guillemets, par exemple, " http://www.adventure-works.com ".  
  
    -   Dans **Description**, tapez la description de l'action.  
  
    -   Dans **Légende**, tapez une légende ou une expression MDX qui correspond à une légende. Cette légende est affichée aux utilisateurs finaux lorsque l'action est initiée. Si vous n'indiquez pas de légende, le nom de l'action est utilisé à la place.  
  
    -   Dans la liste déroulante **La légende est MDX** , spécifiez si la légende est MDX. Ce champ indique au serveur s'il faut évaluer le contenu de **Légende** en tant qu'expression MDX.  
  
  
