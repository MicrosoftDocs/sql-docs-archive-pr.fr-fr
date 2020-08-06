---
title: Gestionnaire de connexions OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611221"
---
# <a name="odata-connection-manager"></a>Gestionnaire de connexions OData
  Un gestionnaire de connexions OData permet à un package de se connecter à une source OData. Un composant source OData se connecte à une source OData à l'aide d'un gestionnaire de connexions OData et consomme les données du service. Consultez la [OData Source](../data-flow/odata-source.md)section qui traite des informations détaillées et des instructions d'installation de ces composants.  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a>Ajout d'un gestionnaire de connexions à un package SSIS  
 Vous pouvez ajouter un nouveau gestionnaire de connexions OData à un package SSIS de trois manières :  
  
-   Cliquez sur le bouton **Nouveau...** dans **Éditeur de source OData**.  
  
-   Cliquez avec le bouton droit sur le dossier **Gestionnaires de connexions** dans l' **Explorateur de solutions** et cliquez sur **Nouveau gestionnaire de connexions**. Sélectionnez **ODATA** pour **Type du gestionnaire de connexions**.  
  
-   Cliquez avec le bouton droit dans le volet **gestionnaires de connexions** au bas du concepteur de packages, puis sélectionnez **nouvelle connexion...**. Sélectionnez **ODATA** pour le **type de gestionnaire de connexions**.  
  
## <a name="connection-manager-authentication"></a>Authentification du gestionnaire de connexions  
 Le Gestionnaire de connexions OData prend en charge deux modes d'authentification.  
  
-   Authentification Windows  
  
-   Authentification de base (nom d'utilisateur/mot de passe)  
  
 Pour un accès anonyme, sélectionnez l'option Authentification Windows.  
  
### <a name="specifying-and-securing-credentials"></a>Spécification des informations d'identification  
 Si votre service OData requiert l'authentification de base, spécifiez un nom d'utilisateur et un mot de passe dans [OData Connection Manager Editor](../odata-connection-manager-editor.md). Les valeurs que vous entrez dans l'éditeur sont conservées dans le package. La valeur du mot de passe est chiffrée selon le niveau de protection du package.  
  
 Il y a plusieurs manières d'extérioriser/paramétrer les valeurs de nom d'utilisateur et de mot de passe. Les deux principales façons de procéder dans [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] sont en utilisant les paramètres, ou en définissant les propriétés du gestionnaire de connexions directement lorsque vous exécutez le package en utilisant SQL Server Management Studio.  
  
## <a name="odata-connection-manager-properties"></a>Propriétés du gestionnaire de connexions OData  
 Le tableau suivant répertorie certaines propriétés du gestionnaire de connexions OData que vous pouvez modifier.  
  
|||  
|-|-|  
|Propriété|Description|  
|Url|URL vers le document de service.|  
|UserName|Nom d'utilisateur à utiliser pour l'authentification de base.|  
|Mot de passe|Mot de passe à utiliser pour l'authentification de base.|  
|ConnectionString|Reflète d'autres propriétés du gestionnaire de connexions.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur du gestionnaire de connexions OData](../odata-connection-manager-editor.md)  
  
  
