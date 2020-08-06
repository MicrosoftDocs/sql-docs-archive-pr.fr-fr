---
title: Mettre en surbrillance les exceptions (outils d’analyse de table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707971"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>Mettre en surbrillance les exceptions (Outils d'analyse de table pour Excel)
  ![Bouton Mettre en surbrillance les exceptions sur le ruban](media/tat-highlightex.gif "Bouton Mettre en surbrillance les exceptions sur le ruban")  
  
 Parfois vos données peuvent contenir des valeurs particulières. Par exemple, pour le critère d'âge d'un propriétaire de bien immobilier, la valeur 5 ans peut être indiquée. Ces valeurs, *souvent appelées*valeurs hors norme, peuvent être erronées en raison d’une erreur d’entrée de données, ou peuvent indiquer des tendances inhabituelles. Dans les deux cas, les exceptions peuvent avoir une incidence sur la qualité de votre analyse. L’outil **mettre en surbrillance les exceptions** vous aide à trouver ces valeurs et à les examiner pour une action supplémentaire.  
  
 L’outil **mettre en surbrillance les exceptions** peut fonctionner avec l’intégralité de la plage de données dans une table de données Excel, ou vous ne pouvez sélectionner que quelques colonnes. Vous pouvez également définir un seuil qui contrôle la variabilité des données pour trouver un nombre d'exceptions plus ou moins important.  
  
 Une fois que l'outil a terminé son analyse, il crée une nouvelle feuille de calcul qui contient un rapport de synthèse indiquant le nombre d'observations aberrantes décelées dans chacune des colonnes analysées. L'outil met également en surbrillance les exceptions dans la table de données d'origine. Du fait que l'outil analyse des séquences globales, il peut signaler que la plupart des valeurs d'une ligne sont normales et mettre en surbrillance une seule cellule dans cette ligne. Dans l’exemple propriétaire ci-dessus, seule la colonne **Age** peut être mise en surbrillance.  
  
 Vous pouvez également modifier la valeur du **seuil d’exception** dans le **rapport de synthèse**. Cette valeur indique la probabilité qu'une cellule particulière contienne une valeur anormale. Par conséquent, si vous définissez la valeur, un nombre inférieur de valeurs sera mis en surbrillance en tant que valeurs hors norme. Inversement, lorsque vous diminuez la valeur, les cellules mises en surbrillance sont alors plus nombreuses.  
  
## <a name="using-the-highlight-exceptions-tool"></a>Utilisation de l'outil Mettre en surbrillance les exceptions  
  
1.  Ouvrez un tableau Excel, puis cliquez sur **mettre en surbrillance les exceptions**.  
  
2.  Spécifiez les colonnes à analyser.  
  
3.  Cliquez sur **Exécuter**.  
  
4.  Ouvrez la feuille de calcul intitulée valeurs hors norme \<table name> pour afficher un résumé des valeurs hors norme qui ont été trouvées.  
  
5.  Pour modifier le nombre de mises en surbrillance, cliquez sur les flèches vers le haut et vers le bas dans la ligne **seuil d’exception** du **rapport mettre en surbrillance les exceptions**.  
  
### <a name="requirements"></a>Spécifications  
 Vous pouvez inclure des colonnes qui ne contiennent pas des valeurs incorrectes si ces valeurs contiennent des informations pouvant être utiles pour la prédiction d'autres lignes. Cependant, vous devez désélectionner les colonnes susceptibles de contenir des valeurs manquantes ou nulles.  
  
 Dans la mesure où toutes les colonnes sélectionnées sont utilisées pour créer une séquence générale, vous devez éviter d'utiliser les colonnes d'entrée contenant des informations médiocres, telles que les suivantes :  
  
-   Colonnes qui contiennent des valeurs uniques telles que les ID.  
  
-   Colonnes qui contiennent un pourcentage élevé de valeurs incorrectes.  
  
-   Colonnes avec de nombreuses valeurs manquantes.  
  
     Il existe des cas où il est utile d'inclure des colonnes d'entrée ayant de nombreuses valeurs manquantes. Par exemple, si la valeur du champ adresse est toujours manquante lorsque le client achète par l'intermédiaire d'un détaillant, l'algorithme d'exploration de données peut utiliser ces informations pour identifier d'autres clients similaires. Vous devez déterminer au cas par cas si les données sont manquantes par omission ou car l'état Manquant est significatif.  
  
-   Colonnes qui ont peu de chances d'être utiles dans la création d'une séquence. Par exemple, une colonne qui a la même valeur dans chaque ligne n'ajoute pas d'informations pouvant être utiles dans la construction des séquences.  
  
## <a name="understanding-the-highlight-exceptions-report"></a>Présentation de l'outil Mettre en surbrillance les exceptions  
 Lorsque vous cliquez sur **exécuter**, l’outil effectue trois opérations :  
  
-   Il crée une structure d'exploration de données d'après les données actuelles de la table.  
  
-   Crée un nouveau modèle d'exploration de données en utilisant l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering).  
  
-   Il crée une requête de prédiction en fonction des séquences de données remarquables pour déterminer si des valeurs de la feuille de calcul sont improbables.  
  
 La valeur initiale pour le seuil d'exception est toujours de 75, ce qui signifie que l'algorithme a calculé qu'il y a 75 % de chance que les données en surbrillance soient fausses. L'outil définit automatiquement ce seuil pour l'analyse initiale, mais vous pouvez modifier la valeur dans le rapport.  
  
 L’outil **mettre en surbrillance les exceptions** met en surbrillance les cellules de la table de données d’origine suspectes. Une couleur sombre signifie que la ligne doit faire l'objet d'une attention particulière. Une couleur claire indique que la valeur d'une cellule spécifique a été identifiée comme étant suspecte. Si vous modifiez le seuil pour les exceptions, les valeurs en surbrillance changeront également.  
  
 Le diagramme de synthèse indique le nombre de cellules contenant des valeurs supérieures au seuil des exceptions dans chaque colonne.  
  
## <a name="related-tools"></a>Outils connexes  
 Lorsque vous nettoyez ou vérifiez des données en prévision de l'exploration de données, vous pouvez également tester les fonctionnalités d'exploration de données du Client d'exploration de données pour Excel. Ce complément fournit des outils avancés qui vous permettront de déceler les observations aberrantes, de réétiqueter les données ou d'afficher la distribution des données. Pour plus d’informations sur les outils d’exploration de données dans le client d’exploration de données pour Excel, consultez [exploration et nettoyage des données](exploring-and-cleaning-data.md).  
  
 L’outil **mettre en surbrillance les exceptions** utilise l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de clustering. Un modèle de clustering détecte les groupes de lignes qui partagent des caractéristiques communes. Le client d’exploration de données pour Excel fournit une fenêtre **Parcourir** qui utilise des graphiques et des profils caractéristiques pour vous permettre d’explorer les modèles d’exploration de données créés par le clustering. Pour plus d’informations sur la façon de parcourir le modèle de clustering créé par l’outil **mettre en surbrillance les exceptions** , consultez [Parcourir les modèles (client d’exploration de données pour Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).  
  
 Pour plus d'informations sur l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering, consultez la rubrique « Algorithme de gestion de clusters Microsoft » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)  
  
  
