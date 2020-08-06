---
title: 'Tâche 5 : création d’un attribut basé sur un domaine à partir d’Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b866478150fb4c06a3c4ea1ee6c227527f963219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700493"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Tâche 5 : Création d’un attribut basé sur un domaine à partir d’Excel
  Dans cette tâche, vous convertissez l’attribut **State** de l’entité **Supplier** en tant qu' **attribut basé sur un domaine**. Une fois que vous avez configuré l’attribut d’État comme étant basé sur un domaine et que vous l’avez publié sur MDS, une nouvelle entité nommée **État** est créée sur le serveur MDS avec toutes les valeurs de la colonne et l’attribut **État** de l’entité **fournisseur** est rempli avec les valeurs de l’entité **État** . À présent, le modèle **fournisseurs** doit avoir deux entités : **fournisseur** et **État** où l’attribut **État** de l’entité **fournisseur** est un attribut basé sur un domaine qui dépend de l’entité **État** .  
  
1.  Basculez vers la fenêtre **Excel** avec **nettoyage et mis en correspondance Suppliers.xlsx** ouvrir.  
  
2.  Cliquez sur le bouton **Actualiser** du ruban pour accéder aux dernières mises à jour de MDS. Vous devez voir les deux autres enregistrements si vous avez effectué la **tâche facultative 4**.  
  
3.  Cliquez sur **État** du nom de colonne (cellule **I1**) dans la **ligne d’en-tête**.  
  
     ![Excel - Bouton Propriétés d'attributs](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - Bouton Propriétés d'attributs")  
  
4.  Cliquez sur Propriétés de l' **attribut** dans le ruban.  
  
5.  Dans la boîte de dialogue Propriétés de l' **attribut** , sélectionnez **liste restreinte (basée sur un domaine)** pour le **type d’attribut**.  
  
6.  Tapez **State** pour le **nouveau nom d’entité** , puis cliquez sur **OK**.  
  
     ![Excel - Boîte de dialogue Propriétés d'attributs](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Boîte de dialogue Propriétés d'attributs")  
  
7.  Désormais, dans Excel, vous devriez voir une **flèche vers le bas** lorsque vous cliquez sur une valeur dans la colonne **État** . Modifiez la valeur à l'aide de la liste déroulante, le cas échéant.  
  
     ![Excel - Liste déroulante des États](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - Liste déroulante des États")  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 6 : Tâche 6 : Vérification que l’attribut basé sur un domaine est créé à l’aide de Master Data Manager](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
