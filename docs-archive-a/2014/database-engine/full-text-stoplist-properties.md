---
title: Propriétés de la STOPLIST de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87614787"
---
# <a name="full-text-stoplist-properties"></a>Propriétés de la liste de mots vides de texte intégral
  Utilisez cette boîte de dialogue pour ajouter ou supprimer des mots vides, supprimer tous les mots vides pour une langue spécifique ou effacer la liste de mots vides actuelle. Un mot vide est un mot utilisé couramment et inclus dans une liste de mots vides. Les mots vides répertoriés dans une liste de mots vides sont omis de l'indexation de texte intégral pour les tables qui utilisent la liste de mots vides. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md).  
  
 **Pour utiliser SQL Server Management Studio pour modifier des propriétés de liste de mots vides**  
  
-   [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Options  
 **Action**  
 Spécifie l'action que vous souhaitez effectuer.  
  
 **Ajouter un mot vide**  
 Ajouter un mot utilisé couramment à la liste de mots vides.  
  
 **Supprimer le mot vide**  
 Supprimer un mot vide de la liste de mots vides.  
  
 **Supprimer tous les mots vides**  
 Supprimer tous les mots vides pour une langue spécifique.  
  
 **Effacer la liste de mots vides**  
 Effacer la liste de mots vides en supprimant tous les mots vides pour toutes les langues.  
  
 **Mot vide**  
 Si vous avez sélectionné **Ajouter un mot vide** ou **Supprimer le mot vide**, entrez le mot vide dans le champ **Mot vide** . Tout nouveau mot vide doit être unique ; autrement dit, il ne doit pas déjà figurer dans la liste de mots vides correspondant à la langue sélectionnée.  
  
 **Langue de texte intégral**  
 Si vous avez sélectionné **Ajouter un mot vide**, **Supprimer le mot vide**ou **Supprimer tous les mots vides**, sélectionnez la langue des mots vides dans la zone de liste. Celle-ci répertorie toutes les langues de texte intégral prises en charge par l'instance de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sys. fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [sys. fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [Configurer et gérer mots vides et mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md)   
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CRÉER une STOPLIST de texte intégral &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
