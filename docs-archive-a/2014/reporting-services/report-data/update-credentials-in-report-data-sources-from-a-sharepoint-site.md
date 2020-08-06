---
title: Mettre à jour les informations d’identification dans les sources de données de rapport à partir d’un site SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 923fee5656ed6032201fb4276fcca75be799e42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600559"
---
# <a name="update-credentials-in-report-data-sources-from-a-sharepoint-site"></a>Mettre à jour les informations d'identification dans les sources de données de rapport à partir d'un site SharePoint
  Cette rubrique explique comment mettre à jour les sources de données incorporées dans les rapports et les sources de données partagées enregistrées dans une bibliothèque de documents SharePoint.  
  
 Plusieurs de vos rapports peuvent inclure des sources de données ou utiliser des sources de données partagées configurées pour utiliser l'authentification Windows. Dans certaines circonstances, comme lors de la création d'alertes de données sur les rapports enregistrés dans une bibliothèque de documents SharePoint, vous devez mettre à jour les informations d'identification de la source de données avec les informations d'identification stockées, ou bien vous pouvez choisir de ne configurer aucune information d'identification.  
  
 Pour utiliser les informations d'identification stockées dans les rapports, vous pouvez décider de créer et utiliser un nouveau compte de connexion SQL Server. Pour plus d’informations, consultez [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md).  
  
### <a name="to-update-an-embedded-data-source-to-use-stored-credentials"></a>Pour mettre à jour une source de données incorporée et utiliser les informations d'identification stockées  
  
1.  Allez à la bibliothèque de documents SharePoint où vous avez enregistré le rapport.  
  
2.  Cliquez sur l’icône pour développer le menu déroulant sur le rapport, puis cliquez sur **Gérer les sources de données**.  
  
     La page de gestion des sources de données s'ouvre.  
  
3.  Dans la colonne **Nom** , cliquez sur la source de données.  
  
4.  Pour **Type de connexion** vérifiez que l’option **Source de données personnalisée** est sélectionnée.  
  
     Cette option indique que la source de données est incorporée dans le rapport.  
  
5.  Laissez les options **Type de source de données** et **Chaîne de connexion** comme elles sont, sauf si vous souhaitez que le rapport se connecte à un type de source de données, ou à un serveur ou magasin de données différent.  
  
6.  Pour **Informations d’identification**, sélectionnez **Informations d’identification stockées**. Cette option fonctionne uniquement si la source de données n'accepte pas les informations d'identification ou si vous transmettez les informations d'identification d'une autre façon.  
  
     L’option **Informations d’identification non requises** peut également être utilisée dans certains cas.  
  
     Pour certains types de sources de données, le compte d'exécution sans assistance doit être configuré sur le serveur de rapports. Pour plus d’informations, consultez la rubrique relative au type de source de données correspondant dans [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) et [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
7.  Tapez un nom d'utilisateur et un mot de passe.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le au format suivant : \<domain> \\<compte \> , puis sélectionnez **utiliser comme informations d’identification Windows lors de la connexion à la source de données**.  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, vous pouvez sélectionner **Définir le contexte d'exécution pour ce compte**.  
  
8.  Pour vérifier que la source de données peut se connecter à l’aide des informations d’identification mises à jour, cliquez sur **Tester la connexion**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-update-a-shared-data-source-to-use-stored-credentials"></a>Pour mettre à jour une source de données partagée et utiliser les informations d'identification stockées  
  
1.  Accédez à la bibliothèque de documents SharePoint où vous avez enregistré la source de données partagée.  
  
2.  Cliquez sur l’icône pour développer le menu déroulant sur la source de données partagée, puis cliquez sur **Modifier la définition de la source de données**.  
  
     La page de la source de données s'affiche.  
  
3.  Laissez les options **Type de source de données** et **Chaîne de connexion** comme elles sont, sauf si vous souhaitez que la source de données partagée se connecte à un type de source de données, ou à un serveur ou magasin de données différent.  
  
4.  Pour **Informations d’identification**, sélectionnez **Informations d’identification stockées**.  
  
     L’option **Informations d’identification non requises** peut également être utilisée dans certains cas. Cette option fonctionne uniquement si la source de données n'accepte pas les informations d'identification ou si vous transmettez les informations d'identification d'une autre façon.  
  
     Pour certains types de sources de données, le compte d'exécution sans assistance doit être configuré sur le serveur de rapports. Pour plus d’informations, consultez la rubrique relative au type de source de données correspondant dans [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) et [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
5.  Tapez un nom d'utilisateur et un mot de passe.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le au format suivant : \<domain> \\<compte \> , puis sélectionnez **utiliser comme informations d’identification Windows lors de la connexion à la source de données.**  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, vous pouvez sélectionner **Définir le contexte d'exécution pour ce compte**.  
  
6.  Pour vérifier que la source de données peut se connecter à l’aide des informations d’identification mises à jour, cliquez sur **Tester la connexion**.  
  
7.  Vérifiez que l'option Activer cette source de données est sélectionnée.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Télécharger des documents vers une bibliothèque SharePoint &#40;Reporting Services en mode SharePoint&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
  
