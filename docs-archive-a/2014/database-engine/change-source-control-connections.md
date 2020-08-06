---
title: Modifier les connexions du contrôle de code source | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 077a09cdca0c0aff777184f04467ca39592690aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611323"
---
# <a name="change-source-control-connections"></a>Modifier les connexions du contrôle de code source
  La première fois que vous ouvrez ou ajoutez une solution au contrôle de code source, le fournisseur de contrôle de code source crée une association entre le dossier racine du répertoire de la solution locale et le dossier de serveur correspondant.  
  
 Le dossier racine (appelé également racine unique) réside sur le client. Il s'agit du dossier dans lequel se trouvent tous les fichiers référencés par une solution ou un projet. Pour trouver la dernière version d'une solution, son historique et ses informations d'état, recherchez le dossier de serveur qui réside sur le serveur du contrôle de code source. Dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, les dossiers de serveur sont appelés projets.  
  
 Dans de nombreux cas, vous devez détacher ou déconnecter une solution de son dossier de serveur. Par exemple, si l'ordinateur sur lequel votre fournisseur de contrôle de code source réside n'est pas disponible, vous pouvez alors vous connecter à un ordinateur de réserve, reconnecter votre solution à un dossier de serveur sauvegardé et reprendre le travail normalement. En cas de dédoublement d'un projet de contrôle de code source, vous pouvez également être amené à vous connecter au dossier de serveur dans lequel la nouvelle version de projet réside.  
  
 Utilisez l'interface utilisateur du fournisseur de contrôle de code source pour modifier le dossier de serveur auquel une solution est liée. Vous pouvez ouvrir l'interface utilisateur du contrôle de code source à partir de l'environnement [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>Pour ouvrir l'interface utilisateur du contrôle de code source à partir de l'environnement Studio  
  
1.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Démarrer Microsoft Visual SourceSafe**.  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base sur le contrôle de code source](../../2014/database-engine/source-control-basics.md)   
 [Définir les options de contrôle de code source](../../2014/database-engine/set-source-control-options.md)   
 [Exclure des fichiers du contrôle de code source](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
