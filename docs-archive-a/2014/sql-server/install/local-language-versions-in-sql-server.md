---
title: Versions linguistiques locales dans SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646ffaed1e4b709c2c26030379f0a7f223f221e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697396"
---
# <a name="local-language-versions-in-sql-server"></a>Versions linguistiques locales dans SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge toutes les langues prises en charge par les systèmes d'exploitation Windows.  
  
## <a name="cross-language-support"></a>Prise en charge de langues différentes  
  
-   La version anglaise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est prise en charge sur toutes les versions localisées des systèmes d'exploitation.  
  
-   Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont prises en charge sur les systèmes d'exploitation localisés dans la langue correspondante ou sur les versions anglaises des systèmes d'exploitation pris en charge grâce aux paramètres du Pack Windows d'interface utilisateur multilingue. Pour plus d'informations, voir [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).  
  
-   Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être mises à niveau uniquement vers des versions localisées dans la même langue et ne peuvent pas être mises à niveau vers la version anglaise.  
  
-   Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent également être installées côte à côte avec des instances en langue anglaise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="configure-operating-system-to-support-localized-versions"></a><a name="BK_ConfigureOS"></a> Configure Operating System to Support Localized Versions  
 Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont prises en charge dans les versions anglaises des systèmes d'exploitation pris en charge via l'utilisation des paramètres du Pack d'interface utilisateur multilingue de Windows (MUI, Multilingual User Interface).  
  
 Vous devez toutefois vérifier certains paramètres de système d'exploitation avant d'installer une version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur qui exécute un système d'exploitation en langue anglaise avec un paramétrage MUI non anglais. Vous devez vérifier que les paramètres de système d'exploitation suivants correspondent à la langue de la version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui va être installée.  
  
-   Le paramètre de l'interface utilisateur du système d'exploitation  
  
-   Les paramètres régionaux utilisateur du système d'exploitation  
  
-   Les paramètres régionaux système  
  
 Si les paramètres ne correspondent pas à la langue de la version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à installer, procédez comme suit pour définir correctement ces paramètres de système d'exploitation.  
  
> [!CAUTION]  
>  Les installations de différentes versions linguistiques d'instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le même ordinateur ne sont pas prises en charge.  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a>Pour modifier le paramètre de l'interface utilisateur du système d'exploitation  
  
1.  Si elle n'est pas déjà installée, installez l'interface utilisateur multilingue du système d'exploitation qui correspond à votre version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans le Panneau de configuration, ouvrez **Options régionales et linguistiques**.  
  
3.  Dans l'onglet **Langues** , pour **Langue utilisée dans les menus et les dialogues**, sélectionnez une valeur dans la liste.  
  
     Ce paramètre affecte la langue de l'interface utilisateur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]qui doit correspondre à votre version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Cliquez sur **Appliquer** pour confirmer la modification et sur **OK** pour fermer la fenêtre.  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a>Pour modifier les paramètres régionaux utilisateur du système d'exploitation  
  
1.  Si elle n'est pas déjà installée, installez l'interface utilisateur multilingue du système d'exploitation qui correspond à votre version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans le Panneau de configuration, ouvrez **Options régionales et linguistiques**.  
  
3.  Dans l'onglet **Options régionales** , pour **Sélectionner un élément pour afficher ses paramètres**, sélectionnez une valeur dans la liste.  
  
     Ce paramètre affecte la mise en forme des données propre à une culture spécifique.  
  
4.  Cliquez sur **Appliquer** pour confirmer la modification et sur **OK** pour fermer la fenêtre.  
  
#### <a name="to-change-the-system-locale-setting"></a>Pour modifier les paramètres régionaux système  
  
1.  Si elle n'est pas déjà installée, installez l'interface utilisateur multilingue du système d'exploitation qui correspond à votre version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Dans le Panneau de configuration, ouvrez **Options régionales et linguistiques**.  
  
3.  Sous l’onglet **Options avancées** , pour **Sélectionnez une langue qui corresponde à la version des programmes non Unicode que vous voulez utiliser**, sélectionnez une valeur dans la liste.  
  
     Ce paramètre permet au programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de choisir le meilleur classement par défaut pour votre installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Cliquez sur **Appliquer** pour confirmer la modification et sur **OK** pour fermer la fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)   
 [Installer SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)  
  
  
