---
title: Modifier les fichiers archivés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701627"
---
# <a name="edit-checked-in-files"></a>Modifier des fichiers archivés
  Vous devez généralement extraire les fichiers sous contrôle de code source avant de pouvoir les modifier. Toutefois, vous pouvez configurer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] de sorte que vous puissiez modifier les fichiers que vous n’avez pas extraits. Dans ce cas, vos modifications sont conservées en mémoire jusqu’à ce que vous enregistriez les fichiers. Vous êtes ensuite invité à extraire le fichier à partir du contrôle de code source.  
  
 Si vous travaillez en équipe, il n'est pas recommandé d'autoriser la modification des fichiers archivés, sauf si votre fournisseur de contrôle de code source prend en charge l'extraction à la fois de la version locale et de la version serveur. La plupart des fournisseurs ne prennent pas en charge les extractions de versions locales. Si votre fournisseur ne prend pas en charge les extractions de versions locales et que vous modifiez un fichier archivé, vous devez fusionner manuellement les versions en mémoire et sur le serveur pour pouvoir archiver le fichier. Les fusions automatiques et assistées par le fournisseur ne sont pas prises en charge dans cette situation.  
  
### <a name="to-edit-checked-in-files"></a>Pour modifier des fichiers archivés  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez le dossier **Contrôle de code source**, puis cliquez sur **Environnement**.  
  
3.  Cliquez sur **Permettre la modification des éléments archivés**, puis sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les archivages](../../2014/database-engine/manage-checkins.md)   
 [Gérer les extractions](../../2014/database-engine/manage-checkouts.md)  
  
  
