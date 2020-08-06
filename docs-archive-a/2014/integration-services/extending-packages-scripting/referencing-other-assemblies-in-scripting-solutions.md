---
title: Référencement d’autres assemblys dans les solutions de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685bbaa62da88e84cd848eb49dcf5bedb03d5390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602210"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>Référencement d'autres assemblys dans les solutions de script
  La bibliothèque de classes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit au développeur de scripts un ensemble d’outils performants permettant d’implémenter des fonctionnalités personnalisées dans des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. La tâche de script et le composant Script peuvent également utiliser des assemblys managés personnalisés.

> [!NOTE]
>  Pour permettre à vos packages d’utiliser les objets et méthodes d’un service web, utilisez la commande **Ajouter une référence web** disponible dans [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). Dans les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous deviez générer une classe proxy pour utiliser un service Web.

## <a name="using-a-managed-assembly"></a>Utilisation d'un assembly managé
 Pour que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] trouve un assembly managé au moment de la conception, vous devez effectuer les étapes suivantes :

1.  Stockez l'assembly managé dans un dossier sur votre ordinateur.

    > [!NOTE]
    >  Dans les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouviez uniquement ajouter une référence à un assembly managé qui était stocké dans le dossier %windir%\Microsoft.NET\Framework\vx.x.xxxxx ou le dossier %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies.

2.  Ajoutez une référence à l'assembly managé.

     Pour ajouter la référence, dans VSTA, dans la boîte de dialogue **Ajouter une référence**, sous l’onglet **Parcourir**, localisez et ajoutez l’assembly managé.

 Pour que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] recherche l'assembly managé au moment de l'exécution, vous devez procéder comme suit :

1.  Signez l'assembly managé avec un nom fort.

2.  Installez l'assembly dans le Global Assembly Cache sur l'ordinateur sur lequel le package est exécuté.

     Pour plus d’informations, consultez [Génération, déploiement et débogage d’objets personnalisés](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).

## <a name="using-the-microsoft-net-framework-class-library"></a>Utilisation de la bibliothèque de classes Microsoft .NET Framework
 La tâche de script et le composant Script peuvent tirer parti de tous les autres objets et fonctionnalités exposés par la bibliothèque de classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Par exemple, en utilisant [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez extraire des informations sur votre environnement et interagir avec l'ordinateur qui exécute le package.

 Cette liste décrit plusieurs classes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] figurant parmi les plus fréquemment utilisées :

-   `System.Data`Contient l’architecture ADO.NET.

-   `System.IO`Fournit une interface au système de fichiers et aux flux.

-   `System.Windows.Forms`Fournit la création de formulaire.

-   `System.Text.RegularExpressions`Fournit des classes pour l’utilisation d’expressions régulières.

-   `System.Environment`Retourne des informations sur l’ordinateur local, l’utilisateur actuel et les paramètres de l’ordinateur et de l’utilisateur.

-   `System.Net`Fournit des communications réseau.

-   `System.DirectoryServices`Expose Active Directory.

-   `System.Drawing`Fournit de nombreuses bibliothèques de manipulation d’images.

-   `System.Threading`Active la programmation multithread.

 Pour plus d'informations sur le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], consultez MSDN Library.

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Extension de packages avec des scripts](extending-packages-with-scripting.md)


