---
title: Activer et désactiver l’impression côté client pour Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611533"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Activer et désactiver l'impression côté client pour Reporting Services
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] contrôle ActiveX, **RSClientPrint**, permet l’impression côté client pour les rapports affichés dans un navigateur. Le contrôle affiche une boîte de dialogue d'impression personnalisée qui prend en charge des fonctionnalités communes à d'autres boîtes de dialogue d'impression. Les fonctionnalités incluent l'aperçu avant impression, les sélections de page pour spécifier des pages et des plages spécifiques, les marges des pages, et l'orientation. Bien que l'impression côté client soit activée par défaut, vous pouvez désactiver cette fonctionnalité pour l'empêcher d'être utilisée.  
  
> [!NOTE]  
>  Des autorisations d'administrateur sont nécessaires pour le téléchargement des contrôles ActiveX.  
  
## <a name="downloading-the-activex-control"></a>Téléchargement du contrôle ActiveX  
 Chaque utilisateur souhaitant utiliser la fonctionnalité d'impression doit télécharger et installer le contrôle ActiveX qui permet l'impression côté client. La première fois qu’un utilisateur clique sur l’icône de l' **imprimante** dans la barre d’outils rapport, le contrôle Microsoft ActiveX est téléchargé sur l’ordinateur. Une fois le contrôle téléchargé, la boîte de dialogue **Imprimer** s’affiche chaque fois que l’utilisateur clique sur l’icône de l' **imprimante** .  
  
 En fonction des paramètres du navigateur, l'installation du contrôle peut être demandée à l'utilisateur, être bloquée ou s'effectuer de manière transparente en arrière-plan.  
  
 Pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, les paramètres qui affectent le téléchargement et l’installation du contrôle ActiveX sont spécifiés via le nœud **contrôles ActiveX et plug-ins** de la page **paramètres de sécurité** de la zone de contenu Web. Les paramètres suivants déterminent si les utilisateurs peuvent télécharger et exécuter le contrôle d'impression, en fonction des spécifications de sécurité de la zone Web :  
  
-   Télécharger les contrôles ActiveX signés.  
  
-   Contrôles ActiveX reconnus sûrs pour l'écriture de scripts.  
  
-   Exécuter les contrôles ActiveX et les plug-ins.  
  
 Les utilisateurs qui souhaitent utiliser **RSClientPrint** pour effectuer une impression côté client doivent activer les éléments suivants :  
  
-   **Téléchargez les contrôles ActiveX signés** et **le contrôle ActiveX de script marqués comme sécurisés** pour l’écriture de scripts à des fins d’installation.  
  
-   **Exécuter les contrôles ActiveX et les plug-ins** pour les opérations d’impression en cours.  
  
 Le contrôle ActiveX **RSClientPrint** est signé, ce qui signifie qu’il contient un certificat numérique valide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="enabling-and-disabling-client-side-printing"></a>Activation et désactivation de l'impression côté client  
 Les administrateurs du serveur de rapports ont la possibilité de désactiver la fonctionnalité d’impression en affectant à la propriété système du serveur de rapports **EnableClientPrinting** la valeur `false` . Cela entraîne la désactivation de l'impression côté client pour tous les rapports gérés par ce serveur. Par défaut, **EnableClientPrinting** a la valeur `true` . Vous pouvez désactiver l'impression côté client de différentes façons :  
  
-   Pour un **serveur de rapports en mode natif**:  
  
    1.  Lancez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des privilèges d'administrateur.  
  
    2.  Connectez-vous à une instance de serveur de rapports dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    3.  Cliquez avec le bouton droit sur le nœud du serveur de rapports et sélectionnez **Propriétés**. Si l'option **Propriétés** est désactivée, vérifiez que vous avez lancé [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avec des privilèges d'administrateur.  
  
    4.  Sélectionnez **activer le téléchargement pour le contrôle d’impression du client ActiveX**.  
  
    5.  Cliquez sur **OK**.  
  
-   Pour un **serveur de rapports en mode SharePoint**:  
  
    1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gestion des applications**.  
  
    2.  Cliquez sur **Gérer les applications de service**.  
  
    3.  Cliquez sur le nom de votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et cliquez sur **Gérer** dans le ruban SharePoint.  
  
    4.  Cliquez sur **Paramètres système**.  
  
    5.  Sélectionnez **Activer l'impression cliente**. L'option **Activer l'impression cliente** se trouve en bas de la page.  
  
    6.  Cliquez sur **OK**.  
  
-   Écrire un script ou du code pour définir la propriété système du serveur de rapports **EnableClientPrinting** sur`false.`  
  
 L'exemple de script suivant illustre une approche possible en matière de désactivation de l'impression côté client. Compilez et exécutez le code [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] suivant afin d'affecter à la propriété **EnableClientPrinting** la valeur **False**. Une fois le code exécuté, redémarrez les services Internet (IIS).  
  
### <a name="sample-script"></a>Exemple de script  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
