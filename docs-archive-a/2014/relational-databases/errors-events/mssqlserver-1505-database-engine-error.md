---
title: MSSQLSERVER_1505 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1505 (Database Engine error)
ms.assetid: ef4df75d-0f36-4c8b-b36c-e427f65f91ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c152404cf2d3710bbe98b29da7a96d86f58859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698279"
---
# <a name="mssqlserver_1505"></a>MSSQLSERVER_1505
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1505|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DUP_KEY|  
|Texte du message|L’instruction CREATE UNIQUE INDEX a été interrompue, car une clé dupliquée a été trouvée pour l’objet '%.\*ls' et l’index '%.\*ls'.  Valeur de clé dupliquée : %ls.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lorsque vous essayez de créer un index unique et que plusieurs lignes de la table contiennent la valeur dupliquée spécifiée. Un index unique est créé lorsque vous créez un index et spécifiez le mot clé UNIQUE ou lorsque vous créez une contrainte UNIQUE. La table ne peut pas contenir de lignes qui présentent des valeurs dupliquées dans les colonnes définies dans l'index ou la contrainte.  
  
 Considérez les données de la table **Employee** suivante :  
  
|LastName|FirstName|JobTitle|HireDate|  
|--------------|---------------|--------------|--------------|  
|Walters|Rob|Senior Tool Designer|2004-11-19|  
|Brown|Kevin|Marketing Assistant|NULL|  
|Brown|Jo|Design Engineer|NULL|  
|Walters|Rob|Tool Designer|2001-08-09|  
  
 Un index unique ne peut pas être créé sur les combinaisons de colonnes **LastName** ou **LastName** et **FirstName** en raison de la présence de valeurs dupliquées dans les lignes.  
  
 La possibilité de violation d’unicité dans la colonne **HireDate** est moins évidente. À des fins d'indexation, les valeurs NULL sont comparées sur un pied d'égalité. Il est par conséquent impossible de créer un index ou une contrainte unique lorsque les valeurs de clés sont des valeurs NULL dans plusieurs lignes. Sur la base des informations fournies ci-dessus, un index unique ne peut pas être créé sur les combinaisons de colonnes **HireDate** ou **LastName** et **HireDate**.  
  
 Le message d'erreur 1505 retourne la première ligne qui enfreint la contrainte d'unicité. La table peut contenir d'autres lignes dupliquées. Pour les trouver toutes, interrogez la table spécifiée et utilisez les clauses GROUP BY et HAVING pour signaler les lignes dupliquées. Par exemple, la requête suivante retourne les lignes de la table **Employee** qui présentent des noms (LastName) et prénoms (FirstName) en double.  
  
 Sélectionnez LastName, FirstName, Count ( \* ) dans dbo. Employee GROUP BY LastName, FirstName ayant Count ( \* ) > 1 ;  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réfléchissez aux solutions ci-dessous.  
  
-   Ajoutez ou supprimez des colonnes de la définition de l'index ou de la contrainte afin de créer un composite unique. Dans l’exemple précédent, l’ajout d’une colonne **MiddleName** à la définition de l’index ou de la contrainte pourrait résoudre le problème des valeurs dupliquées.  
  
-   Lors de la sélection des colonnes d'un index unique ou d'une contrainte unique, sélectionnez donc les colonnes qui n'acceptent pas par définition les valeurs NULL. La possibilité d'une violation d'unicité provoquée lorsque plusieurs lignes contiennent NULL dans les valeurs de clés est ainsi écartée.  
  
-   Lorsque les valeurs dupliquées sont issues d'erreurs de saisie des données, corrigez manuellement les données, puis créez l'index ou la contrainte. Pour plus d’informations sur la suppression de lignes en double d’une table, consultez l’article 139444 de la Base de connaissances : [Comment faire pour supprimer des lignes en double d’une table dans SQL Server](https://support.microsoft.com/kb/139444).  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [Créer des index uniques](../indexes/indexes.md)   
 [Créer des contraintes uniques](../tables/create-unique-constraints.md)  
  
  
