---
title: Se connecter au serveur (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8821018c45fdd77c4b3b896afc47b8f5b425af88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707823"
---
# <a name="connect-to-server-integration-services"></a>Se connecter au serveur (Integration Services)
  Utilisez cette boîte de dialogue pour afficher ou spécifier des options de connexion à [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Type de serveur**  
 Lorsque vous inscrivez un serveur depuis l'Explorateur d'objets, sélectionnez le type de serveur pour vous connecter à : [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services. Le reste de la boîte de dialogue affiche uniquement les options s'appliquant au type de serveur sélectionné. Lorsque vous inscrivez un serveur à partir de Serveurs inscrits, la zone Type de serveur est en lecture seule et correspond au type de serveur affiché dans le composant Serveurs inscrits. Pour inscrire un autre type de serveur, sélectionnez [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services ou Integration Services dans la barre d'outils Serveurs inscrits avant de commencer l'inscription d'un nouveau serveur.  
  
 **Nom du serveur**  
 Sélectionnez le serveur auquel vous connecter. La dernière instance de serveur à laquelle une connexion a été établie est affichée par défaut.  
  
> [!NOTE]  
>  N’utilisez pas *\<servername>* \\ *\<instancename>* , car [!INCLUDE[ssIS](../includes/ssis-md.md)] ne prend pas en charge plusieurs instances sur un ordinateur.  
  
 **Authentification**  
 Seule l'authentification [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)]. Le mode d’authentification Windows permet à l’utilisateur de se connecter au moyen d’un compte d’utilisateur Windows.  
  
 **Nom d'utilisateur**  
 Cette option n'est pas disponible car seule l'authentification Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Mot de passe**  
 Cette option n'est pas disponible car seule l'authentification Windows est disponible pour [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
 **Connexion**  
 Cliquez sur cette option pour vous connecter au serveur sélectionné.  
  
 **Options**  
 Cliquez ici pour afficher des options supplémentaires de connexion au serveur, comme l'inscription d'un serveur et la mémorisation du mot de passe.  
  
  
