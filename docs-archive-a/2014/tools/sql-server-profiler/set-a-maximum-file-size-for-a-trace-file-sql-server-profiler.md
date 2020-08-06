---
title: Définir la taille maximale d’un fichier de trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa990c610f7aa8bf82690c8c201c6643eb712191
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704552"
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a>Définir la taille maximale d'un fichier de trace (SQL Server Profiler)
  Procédez comme suit pour définir la taille maximale d'un fichier de trace.  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a>Pour définir une taille maximale de fichier de trace  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** , tapez un nom pour la trace.  
  
3.  Dans la liste **Nom du modèle**, sélectionnez un modèle de trace.  
  
4.  Sélectionnez **Enregistrer dans le fichier**, puis spécifiez un fichier dans lequel stocker les informations de trace.  
  
5.  Dans la case à cocher **Définir la taille de fichier maximale** , spécifiez la taille de fichier maximale pour la trace. Quand la taille du fichier atteint ce maximum, les événements de la trace ne sont plus enregistrés. Si vous sélectionnez **Activer la substitution de fichier** (option par défaut), voici ce qu’il se produit :  
  
     L'option de substitution de fichier entraîne la fermeture par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du fichier actif et la création d'un nouveau fichier lorsque la taille de fichier maximale est atteinte. Le nouveau fichier possède le même nom que le fichier d'origine, mais un entier est ajouté au nom pour indiquer son numéro séquentiel. Par exemple, si le premier fichier de trace s'appelle nom_fichier_1.trc, le deuxième se nommera nom_fichier_2.trc. Si le nom attribué au nouveau fichier de substitution est celui d'un fichier existant, ce dernier est écrasé sauf s'il est en lecture seule. L’option de substitution de fichier est activée par défaut lors de l’enregistrement de données de trace dans un fichier.  
  
     Lorsque l’option de substitution de fichier est activée, la trace se poursuit jusqu'à ce qu'elle soit arrêtée par un autre moyen. Pour arrêter la trace lorsque la taille de fichier maximale est atteinte, vous devez désactiver l’option de substitution de fichier.  
  
    > [!NOTE]  
    >  Le système de fichiers FAT32 impose une limite maximale légèrement inférieure à 4 gigaoctets (Go) à la taille de fichier. Lorsque la taille du fichier de trace atteint ce maximum, la trace échoue et le message d'erreur « Espace disque insuffisant » s'affiche. Pour que des fichiers plus volumineux puissent être créés, vous devez opter pour le système de fichiers NTFS.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
