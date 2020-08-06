---
title: Gestion par programmation des rôles de package (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707667"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Gestion par programmation des rôles de package (service SSIS)
  Lorsque vous utilisez des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par programme, vous pouvez identifier les rôles disponibles pouvant être appliqués aux packages, ou identifier ou définir les rôles appliqués à un package spécifique. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.

 Les rôles sont uniquement appliqués aux packages stockés dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**. Pour plus d’informations sur les rôles de package, consultez [Rôles Integration Services &#40;Service SSIS&#41;](../security/integration-services-roles-ssis-service.md).

 Toutes les méthodes décrites dans cette rubrique requièrent une référence à l'assembly `Microsoft.SqlServer.ManagedDTS`. Après avoir ajouté la référence dans un nouveau projet, importez l' <xref:Microsoft.SqlServer.Dts.Runtime> espace de noms à l’aide d’une `using` `Imports` instruction ou.

> [!IMPORTANT]
>  Les méthodes de la classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> qui permettent d’utiliser le magasin de packages SSIS prennent uniquement en charge « . », localhost ou le nom du serveur local. Vous ne pouvez pas utiliser « (local) ».

## <a name="determining-which-roles-are-available"></a>Identification des rôles disponibles
 Pour identifier les rôles disponibles pour les packages stockés sur un serveur particulier, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> de la classe <xref:Microsoft.SqlServer.Dts.Runtime.Application>.

## <a name="determining-which-roles-are-assigned"></a>Identification des rôles assignés
 Pour identifier les rôles déjà attribués à un package particulier, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Pour attribuer des rôles à un package, appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Rôles Integration Services &#40;Service SSIS&#41;](../security/integration-services-roles-ssis-service.md)


