---
title: Actions de règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cdc4daca-3dff-46d8-b7f0-57f7826dd61a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5722eca9ed5c9fad7a4712b77366d34b8bab328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699990"
---
# <a name="business-rule-actions-master-data-services"></a>Actions de règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les actions de règle d'entreprise sont la conséquence de l'évaluation des conditions des règles d'entreprise. Si une condition est vraie (True), l'action est initiée.  
  
> [!NOTE]  
>  Pour les actions Valeur par défaut et Modifier la valeur, si la valeur générée dépasse la longueur maximale de l'attribut, la valeur générée est tronqué.  
  
## <a name="default-value-actions"></a>Actions Valeur par défaut  
 Les actions**Valeur par défaut** définissent la valeur par défaut d'un attribut spécifié. Les utilisateurs ayant l'autorisation adéquate peuvent modifier ces valeurs par défaut.  
  
|Nom de la valeur|Description|  
|----------------|-----------------|  
|**la valeur par défaut est**|L'attribut sélectionné **prend par défaut la valeur** d'un attribut spécifique, a une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**prend par défaut une valeur générée**|L'attribut sélectionné **prend par défaut une valeur générée** qui est déterminée par la saisie d'une valeur initiale et incrémentielle.<br /><br /> Cette action est valide pour les valeurs de texte et nombre.|  
|**prend par défaut une valeur concaténée**|L'attribut sélectionné **prend par défaut une valeur concaténée** qui est déterminée en spécifiant plusieurs attributs.<br /><br /> Cette action est valide pour les valeurs de texte et de lien.|  
  
## <a name="change-value-actions"></a>Actions Modifier la valeur  
 Les actions**Modifier la valeur** mettent à jour la valeur d'un attribut spécifié ou d'une valeur d'attribut. Les utilisateurs peuvent modifier ces valeurs uniquement si la nouvelle valeur a pour effet que l'action est vraie.  
  
|Nom de la valeur|Description|  
|----------------|-----------------|  
|**Égal à**|L'attribut sélectionné est modifié sur une valeur d'attribut définie, un autre attribut ou est vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**est égal à une valeur concaténée**|L'attribut sélectionné est modifié sur une valeur concaténée, qui est déterminée en spécifiant plusieurs attributs.<br /><br /> Cette action est valide pour les valeurs de texte et de lien.|  
  
## <a name="validation-actions"></a>Actions Validation  
 Lorsqu'elles ne retournent pas la valeur True, les actions**Validation** envoient un courrier électronique à un utilisateur ou un groupe spécifié. Pour valider une version, l'évaluation de toutes les actions de validation doit aboutir à vrai.  
  
 Les seules exceptions sont les actions **est obligatoire** et **n'est pas valide** . Ces actions doivent être combinées avec une action de valeur de modification, afin que les données puissent être validées et la version activée.  
  
|Nom de validation|Description|  
|---------------------|-----------------|  
|**est obligatoire**|L'attribut sélectionné **est requis**, ce qui signifie qu'il ne peut pas être null ou vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**n’est pas valide**|L'attribut sélectionné **n'est pas valide**.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**doit contenir le modèle**|L'attribut sélectionné **doit contenir le modèle** spécifié. Utilisez des expressions régulières .NET Framework pour spécifier le modèle.<br /><br /> Pour plus d'informations sur les expressions régulières, consultez [Éléments du langage des expressions régulières](https://go.microsoft.com/fwlink/?LinkId=164401) dans MSDN Library.<br /><br /> Cette action est valide pour les valeurs de texte et de lien.|  
|**doit être unique**|L'attribut sélectionné **doit être unique** indépendamment ou en association avec des attributs définis.<br /><br /> **Meilleure pratique :** associez cette action à une condition obligatoire pour garantir la validité des champs d'index dans les systèmes d'abonnement.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**doit avoir l'une des valeurs suivantes**|L'attribut sélectionné **doit avoir l'une des valeurs** spécifiées dans une liste.<br /><br /> Cette action est valide pour les valeurs de texte.|  
|**doit être supérieur à**|L'attribut sélectionné **doit être supérieur à** un attribut spécifique, une valeur d'attribut spécifique, ou être vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre et date.|  
|**doit être égal**|L'attribut sélectionné **doit être égal** à une valeur d'attribut définie, un autre attribut, ou être vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
|**doit être supérieur ou égal à**|L'attribut sélectionné **doit être supérieur ou égal à** un attribut spécifique, une valeur d'attribut spécifique, ou être vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre et date.|  
|**doit être inférieur à**|L'attribut sélectionné **doit être inférieur à** un attribut spécifique, une valeur d'attribut spécifique, ou être vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre et date.|  
|**doit être inférieur ou égal à**|L'attribut sélectionné **doit être inférieur ou égal à** un attribut spécifique, une valeur d'attribut spécifique, ou être vide.<br /><br /> Cette action est valide pour les valeurs de texte, nombre et date.|  
|**doit être compris entre**|L'attribut sélectionné **doit être compris entre** deux attributs ou valeurs d'attribut spécifiques.<br /><br /> Cette action est valide pour les valeurs de texte, nombre et date.|  
|**doit avoir une longueur minimale de**|L'attribut sélectionné **doit avoir une longueur minimale de** la valeur spécifiée.<br /><br /> Cette action est valide pour les valeurs de texte et de lien.|  
|**doit avoir une longueur maximale de**|L'attribut sélectionné **doit avoir une longueur maximale de** la valeur spécifiée.<br /><br /> Cette action est valide pour les valeurs de texte et de lien.|  
  
## <a name="external-action"></a>Action externe  
 Les actions**externes** interagissent avec les applications en dehors de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
|Nom de l'action|Description|  
|-----------------|-----------------|  
|**démarrer le flux de travail**|Initialise un flux de travail externe. Les données qui ont provoqué cette action sont transmises au flux de travail. Pour plus d'informations, consultez [Intégration de flux de travail SharePoint avec Master Data Services](https://msdn.microsoft.com/library/gg690195.aspx).<br /><br /> Cette action est valide pour les valeurs de texte, nombre, date et lien.|  
  
## <a name="see-also"></a>Voir aussi  
 [Conditions de règle d’entreprise &#40;Master Data Services&#41;](business-rule-conditions-master-data-services.md)   
 [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)  
  
  
