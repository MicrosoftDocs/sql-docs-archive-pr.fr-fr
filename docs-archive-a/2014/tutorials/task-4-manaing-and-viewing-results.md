---
title: 'Tâche 4 : gestion et affichage des résultats | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 34fc2a7821fc275a0a0787f703d61a74ea3ee000
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698982"
---
# <a name="task-4-manaing-and-viewing-results"></a>Tâche 4 : Gestion et affichage des résultats
  Dans cette tâche, vous allez examiner les résultats du nettoyage assisté par ordinateur, et vous allez également effectuer un nettoyage interactif des données du fournisseur. Pour plus d’informations, consultez [étape de nettoyage interactif](https://msdn.microsoft.com/library/hh213061.aspx#Interactive) .  
  
1.  Sélectionnez le domaine de **messagerie du contact** dans la liste des domaines.  
  
2.  Basculez vers l’onglet **non valide** dans le volet droit. Notez que deux adresses de messagerie manquent de caractère» à la fin. Ces deux e-mails qui ont été détectés comme étant non valides par la règle de domaine qui requiert que toutes les adresses de messagerie se terminent par ** \@ Adventure-Works.com** (avec’s'). DQS utilise la règle de domaine lors du nettoyage afin de déterminer si une adresse électronique est valide ou non. Cet onglet affiche les valeurs de domaine qui ont été marquées comme non valides dans la base de connaissances, ou celles qui ne respectent pas une règle de domaine. Dans ce cas, ces valeurs ne respectent pas la règle de domaine (validation de l'adresse électronique).  
  
3.  Dans la colonne **corriger vers** , tapez l’adresse de messagerie appropriée qui se termine par ** \@ Adventure-Works.com** (avec’s').  
  
     ![Corrections de la règle de validation du courrier électronique](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Corrections de la règle de validation du courrier électronique")  
  
4.  Cliquez sur **approuver** pour que les deux enregistrements approuvent les deux modifications. Lorsque vous approuvez, les enregistrements sont déplacés vers l’onglet **corrigé** . Au lieu d’approuver chaque élément séparément, vous pouvez approuver toutes les modifications à la fois à l’aide du bouton de la barre d’outils **approuver tous les termes** .  
  
5.  Basculez vers le **nouvel** onglet dans le volet droit. Les valeurs de cet onglet sont les valeurs pour lesquelles DQS ne dispose pas encore de suffisamment d'informations dans la base de connaissances pour déterminer si elles sont correctes. Par conséquent, il ne peut pas modifier ou suggérer des modifications aux valeurs de domaine.  
  
6.  Passez en revue les valeurs pour confirmer que tous les e-mails se terminent par ** \@ Adventure-Works.com** et cliquez sur **approuver tous les termes** dans la barre d’outils. Les valeurs approuvées de cet onglet sont déplacées vers l’onglet **correct** .  
  
7.  Sélectionnez le domaine **Country** dans la liste des domaines.  
  
8.  Basculez vers l’onglet **corrigé** dans le volet droit et remarquez que la valeur de l' **État des États-Unis** est automatiquement corrigée sur le **États-Unis** avec la valeur «» à la fin. Cette règle n’est pas une règle que vous avez définie pour le domaine **Country** , mais DQS est **83%** confiant que la valeur correcte est **États-Unis**. Le bouton **approuver** est automatiquement sélectionné pour tous les éléments **corrigés** . Vous pouvez substituer ce comportement et rejeter une modification.  
  
9. Notez que les **États-Unis** sont corrigés pour **États-Unis** , car il s’agit de synonymes et **États-Unis** est la valeur principale (préférée).  
  
     ![Corrections basées sur synonymes](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Corrections basées sur synonymes")  
  
10. Notez que le bouton **approuver** est déjà sélectionné pour ces valeurs corrigées. Il s'agit du comportement par défaut pour les valeurs corrigées. Vous pouvez refuser une modification et, dans ce cas, la valeur se déplace vers l’onglet **non valide** .  
  
11. Sélectionnez **nom du fournisseur** dans la liste des domaines.  
  
12. Basculez vers l’onglet **corrigé** dans le volet droit.  
  
     ![Noms corrigés des fournisseurs](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "Noms corrigés des fournisseurs")  
  
    1.  Notez qu' **un. Datum Corp.** est corrigé en **. Datum Corporation** et la **raison** est définie sur la **relation à base de termes. A. Datum Corporation** est une valeur de domaine connue pour DQS, car elle a été détectée pendant le processus de découverte des connaissances. Par conséquent, DQS est **assuré de 100%** de cette correction.  
  
    2.  Notez que le **storex de pays paresseux** est corrigé vers le **magasin de pays paresseux**, le **niveau de confiance** est défini sur **100%** et la **raison** est définie sur la **valeur de domaine**. Pendant le processus de découverte des connaissances, vous définissez le **storex paresseux** en tant qu’erreur avec le **magasin de pays paresseux** comme **Correction**. par conséquent, DQS est **assuré de 100%** en toute confiance.  
  
    3.  DQS n’est pas familiarisé avec les autres valeurs de la liste, mais il a trouvé les corrections pour ces valeurs à l’aide du **vérificateur d’orthographe** et propose les corrections appropriées. DQS n’est pas en confiance **100%** de ces corrections, mais le niveau de confiance est supérieur à 80%, qui est le niveau de seuil pour effectuer des corrections, de sorte que DQS propose les corrections.  
  
13. Notez que l' **approbation** est automatiquement activée pour toutes les valeurs. Vous pouvez remplacer la valeur corrigée ou refuser la modification, comme il convient. Par défaut, le bouton **approuver** est sélectionné pour toutes les valeurs sous l’onglet **corrigé** .  
  
14. Basculez vers le **nouvel** onglet.  
  
15. Notez que **Corp.** est résolu en **Corporation**, **Co.** est corrigé en **Company**, et **Inc.** est remplacé par **Incorporated**. Par exemple, **consolider Inc.** est corrigé pour **consolider** les **Co. Incorporated et consolidés** est corrigé en **société consolidée**, et **Frabrikam Corp.** est corrigé pour **Fabrikam Corporation**.  Vous pouvez voir que la **relation à base de termes** est mentionnée comme raison. Ces modifications sont suggérées à l'aide des relations à base de termes que vous avez définies pendant l'activité de gestion de domaine. Vous pouvez modifier les valeurs **correctes** manuellement ici.  
  
16. Faites défiler la liste pour voir **Hunxgry Coyote Store** avec une ligne ondulée rouge. Cliquez dessus avec le bouton droit, puis cliquez sur **Store Coyote suspendu** (sans « x »). La colonne **corriger vers** doit être renseignée automatiquement avec le **magasin Coyote**le plus gourmand. Vous pouvez également entrer manuellement une valeur dans la colonne Corriger vers.  
  
17. Cliquez sur **approuver tous les termes** dans la barre d’outils. Les valeurs de domaine avec la valeur **correcte pour** spécifiée se déplacent vers l’onglet **corrigé** et les nouvelles valeurs sans **correct pour** les valeurs sont déplacées vers l’onglet **correct** .  
  
18. Sélectionnez le domaine composite **validation d’adresse** dans la liste domaine.  
  
19. Dans le volet droit, basculez vers l’onglet **correct** . Vous devez voir les adresses qui sont correctes par le service de **vérification de l’adresse de données Melissa** sur la place de **marché Azure**.  
  
20. Basculez vers l’onglet **corrigé** .  
  
21. Notez que l' **État** de l’enregistrement dont la **ville** est **Los Angeles** est défini sur **ca** maintenant. Notez que, dans le champ **raison** , la **règle est corrigée par la règle « régional-State Rule »**.  
  
     ![Correction de la règle Ville-Département](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "Correction de la règle Ville-Département")  
  
22. Notez que la case d’option **approuver** est déjà sélectionnée pour cet élément dans la liste. Il s’agit du comportement par défaut des éléments de l’onglet **corrigé** .  
  
23. Basculez vers l’onglet **suggéré** . passez en revue les modifications suggérées par le service de **vérification des adresses de données Melissa** .  
  
24. **Cliquez sur approuver tous les termes** dans le bouton de la barre d’outils, puis cliquez sur **OK** dans la boîte de message de **confirmation** .  
  
     ![Bouton à la barre d'outils Approuver tous les termes](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "Bouton à la barre d'outils Approuver tous les termes")  
  
25. Cliquez sur **suivant** pour passer à la page **Exporter** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
