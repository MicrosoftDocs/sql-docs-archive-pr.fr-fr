---
title: Modifier ou supprimer une attribution de rôle (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d67c5cdb7647d50008f72890e4ac3e3c7eed456e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700776"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a>Modifier ou supprimer une attribution de rôle (Gestionnaire de rapports)
  Une attribution de rôle mappe un compte d'utilisateur ou de groupe à une définition de rôle prédéfinie qui inclut les tâches pouvant être effectuées. Elle détermine les types d'opérations qu'un utilisateur peut effectuer sur un dossier, un rapport, un modèle ou tout autre type de contenu. Pour créer, modifier ou supprimer des attributions de rôles, vous devez utiliser le Gestionnaire de rapports. Après avoir créé une attribution de rôle pour un utilisateur ou un groupe particulier, vous pouvez la modifier ultérieurement en sélectionnant un autre rôle. Pour révoquer des autorisations d'accès à un serveur de rapports, vous pouvez supprimer une attribution de rôle du serveur de rapports.  
  
 Selon votre objectif, d'autres approches peuvent être plus appropriées. Par exemple, vous pouvez personnaliser ou créer une définition de rôle, ou modifier l'appartenance (membership) d'un compte de groupe dans Active Directory.  
  
 Par exemple, un groupe d'utilisateurs doit gérer entièrement son contenu, mais il ne doit pas disposer du jeu complet d'autorisations associé au Gestionnaire de contenu. Dans ce cas, vous pouvez créer une définition de rôle appelée Gestionnaire de contenu du service, qui inclut toutes les tâches du Gestionnaire de contenu à l’exception de la tâche **Définir des stratégies de sécurité pour les éléments**.  
  
 De même, si vous êtes un administrateur système ou réseau, et s'il est plus facile pour vous de gérer des comptes de groupes Active Directory plutôt que des attributions de rôles dans le Gestionnaire de rapports, vous pouvez réduire le temps de traitement lié à la gestion des attributions de rôles en créant une attribution de rôle unique pour un compte de groupe, puis en ajustant l'appartenance au groupe lorsque des utilisateurs n'ont plus besoin d'accéder aux rapports.  
  
 Si vous déterminez que la modification ou la suppression d'une attribution de rôle est la meilleure approche, n'oubliez pas de vérifier les attributions de rôles système et les attributions de rôles au niveau élément. Chaque type d'attribution de rôle est configuré via des pages distinctes dans le Gestionnaire de rapports.  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a>Pour modifier ou supprimer une attribution de rôle système  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Cliquez sur **Sécurité**. Toutes les attributions de rôles de niveau système définies actuellement pour le serveur ou le déploiement avec montée en puissance parallèle sont répertoriées par nom de compte.  
  
4.  Recherchez l'attribution de rôle à modifier ou à supprimer.  
  
5.  Pour ajouter ou supprimer le rôle d’un utilisateur ou d’un groupe particulier, cliquez sur **Modifier**.  
  
6.  Pour supprimer une attribution de rôle, cochez la case à côté du nom d’utilisateur ou de groupe, puis cliquez sur **Supprimer**.  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a>Pour modifier ou supprimer une attribution de rôle au niveau élément  
  
1.  Démarrez le **Gestionnaire de rapports** et recherchez l’élément pour lequel vous souhaitez modifier ou supprimer une attribution de rôle.  
  
2.  Pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Sécurité**.  
  
4.  Recherchez l'attribution de rôle à modifier ou à supprimer.  
  
5.  Pour ajouter ou supprimer le rôle d’un utilisateur ou d’un groupe particulier, cliquez sur **Modifier**.  
  
6.  Pour supprimer une attribution de rôle, cochez la case à côté du nom d’utilisateur ou de groupe, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 (create-and-manage-role-assignments.md)   
 [Attributions de rôles](role-assignments.md)   
 [Page Paramètres du site &#40;Gestionnaire de rapports&#41;](../site-settings-page-report-manager.md)   
 [Page Nouvelle attribution de rôle système : Modifier les attributions de rôles système &#40;Gestionnaire de rapports&#41;](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)  
  
  
