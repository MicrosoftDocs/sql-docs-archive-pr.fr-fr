---
title: Leçon 2. Créer une stratégie sur un conteneur et générer une clé de signature d’accès partagé (SAP) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab209f08d53b25a4791ef675e6fb6b78cab115f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707528"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Leçon 2. Créer une stratégie sur le conteneur et générer une clé de signature d'accès partagé
  Dans cette leçon, vous allez apprendre comment créer une stratégie sur le conteneur d'objets blob et générer une clé SAS.  
  
 Une stratégie d'accès stockée fournit un niveau de contrôle supplémentaire sur des signatures d'accès partagé côté serveur. Une signature d'accès partagé est un URI qui octroie des droits d'accès restreints aux conteneurs, aux objets blob, aux files d'attente et aux tables. Si vous utilisez cette nouvelle amélioration, vous devez créer une stratégie sur un conteneur avec des droits en lecture, en écriture et en création de liste.  
  
 Créez une stratégie et une signature d'accès partagé en utilisant une des méthodes suivantes :  
  
-   Opérations de l’API REST Azure : [créer un conteneur](https://msdn.microsoft.com/library/azure/dd179468.aspx), définir une liste de contrôle d' [accès de conteneur](https://msdn.microsoft.com/library/azure/dd179391.aspx)et récupérer un [ACL de conteneur](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Méthode CloudBlobContainer. GetSharedAccessSignature](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) dans le kit de développement logiciel (SDK) Azure.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Un outil de l’Explorateur Azure tiers, tel que [Explorateur stockage Azure](https://azurestorageexplorer.codeplex.com/).  
  
 **Leçon suivante :**  
  
 [Leçon 3 : Créer des informations d'identification SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
