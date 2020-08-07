---
title: Planifier l’actualisation des données et les sources de données qui ne prennent pas en charge l’authentification Windows (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605769"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a>Actualisation planifiée des données et sources de données qui ne prennent pas en charge l'authentification Windows (PowerPivot pour SharePoint)
  Cette rubrique décrit un flux de travail d’actualisation planifiée des données PowerPivot pour SharePoint qui peut utiliser des sources de données qui **NE PRENNENT PAS EN CHARGE** l’authentification Windows. Par exemple, des sources de données Oracle ou IDM DB2. Les illustrations et les étapes figurant dans cette rubrique font référence à des sources de données Oracle, mais le même flux de travail s'applique aux autres sources de données.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 &#124; SharePoint 2013.|  
  
 **Présentation :** créer deux applications cibles Banque d'informations sécurisées. Configurez la première application cible (PowerPivotDataRefresh) en vue d'utiliser les informations d'identification Windows. Configurez la deuxième application cible avec les informations d'identification d'une source de données qui ne prend pas en charge l'authentification Windows, une base de données Oracle par exemple. La deuxième application cible utilise également la première application cible pour le compte d'actualisation des données sans assistance.  
  
 ![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")  
  
-   **(1) PowerPivotDatarefresh :** ID d’application cible de la Banque d’informations sécurisées qui est défini avec l’authentification Windows.  
  
-   **(2) OracleAuthentication :** ID d’application cible de la Banque d’informations sécurisées qui est défini avec les informations d’identification Oracle.  
  
-   **(3)** l’application de service PowerPivot est configurée pour utiliser l’application cible « PowerPivotDataRefresh » pour le **compte d’actualisation des données sans assistance**.  
  
-   **(4)** Le classeur PowerPivot utilise des données Oracle. Les paramètres d’actualisation du classeur spécifient que la connexion de source de données utilise l’application cible **(2)** pour les informations d’identification.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Présence d'une application de service PowerPivot.  
  
-   Présence d'une application du service Banque d'informations sécurisées.  
  
-   Présence d'un classeur Excel avec un modèle de données PowerPivot.  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a>Pour créer un ID d'application cible qui utilise l'authentification Windows  
  
1.  Dans l’administration centrale de SharePoint, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur le nom de votre application de service Banque d'informations sécurisées.  
  
3.  Sur la page **Gérer** , cliquez sur **Nouveau**. ![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")  
  
4.  Sur la page **Créer une nouvelle application cible du magasin sécurisé** , configurez les valeurs suivantes :  
  
    -   **ID de l'application cible :** PowerPivotDataRefresh.  
  
    -   **Nom complet :** PowerPivotDataRefresh.  
  
    -   **Adresse de messagerie du contact :** ?  
  
    -   **Type d'application cible :** Groupe.  
  
    -   **URL de la page de l'application cible :** aucune.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur la page Informations d'identification, ne changez pas les deux noms de champ par défaut, ainsi que les types de champ pour **Nom d'utilisateur Windows** et **Mot de passe Windows**.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Sur la page **Paramètres d'appartenance** , ajoutez au moins un **administrateur d'application cible** , puis ajoutez des membres qui ont besoin d'accéder à l'application cible.  
  
9. Cliquez sur **OK**.  
  
10. Le nouvel ID d'application cible est ajouté à la liste. Sélectionnez l’ID de l’application cible, puis cliquez sur **définir les informations d’identification**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").  
  
11. Tapez le Nom d'utilisateur Windows et le Mot de passe Windows, puis cliquez sur **OK**.  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a>Pour créer un ID d'application cible qui utilise les informations d'identification Oracle  
  
1.  Dans l’administration centrale de SharePoint, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur le nom de votre application de service Banque d'informations sécurisées.  
  
3.  Dans la page **gérer** , cliquez sur **nouveau**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").  
  
4.  Sur la page **Créer une nouvelle application cible du magasin sécurisé** , configurez les valeurs suivantes :  
  
    -   **ID de l'application cible :** OracleAuthentication.  
  
    -   **Nom complet :** OracleAuthentication.  
  
    -   **Adresse de messagerie du contact :** ?  
  
    -   **Type d'application cible :** Groupe.  
  
    -   **URL de la page de l'application cible :** aucune.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **informations d’identification** , remplacez le nom du premier champ par `Oracle User ID` , puis remplacez le **type de champ** par `User Name` .  
  
     Remplacez le deuxième nom de champ par `Oracle Password` et le **type de champ** par `Password` .  
  
7.  Cliquez sur **Suivant**.  
  
8.  Sur la page **Paramètres d'appartenance** , ajoutez au moins un **administrateur d'application cible** , puis ajoutez des membres qui ont besoin d'accéder à l'application cible.  
  
9. Cliquez sur **OK**.  
  
10. Le nouvel ID d'application cible est ajouté à la liste. Sélectionnez l’ID de l’application cible, puis cliquez sur **définir les informations d’identification**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").  
  
11. Tapez l'ID d'utilisateur Oracle, ainsi que le mot de passe Oracle, puis cliquez sur **OK**.  
  
 Pour plus d’informations, consultez la section « pour créer une application cible pour l’authentification SQL Server » dans utiliser la Banque d’informations [sécurisées avec l’authentification SQL Server (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) ( https://technet.microsoft.com/library/gg298949.aspx) .  
  
## <a name="to-configure-the-powerpivot-service-application"></a>Pour configurer l'application de service PowerPivot  
  
1.  Dans l'administration centrale de SharePoint, cliquez sur Gérer les applications de service.  
  
2.  Cliquez sur le nom de votre application de service PowerPivot, par exemple « application de service PowerPivot par défaut ».  
  
3.  Cliquez sur **Configurer les paramètres d'application de service** dans la section Actions.  
  
4.  Dans la section **actualisation des données** , définissez le compte d’actualisation des **données PowerPivot sans assistance**sur `PowerPivotDataRefresh` , puis cliquez sur **OK**.  
  
     ![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")  
  
## <a name="to-configure-the-workbook"></a>Pour configurer le classeur  
  
1.  Accédez à votre classeur dans la Galerie PowerPivot, puis cliquez sur **gérer l’actualisation des données**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").  
  
2.  Si la page **Historique d'actualisation des données** s'affiche, cliquez sur **Configurer la planification**.  
  
3.  Cliquez sur **Activer**.  
  
4.  Cliquez sur **Aussi actualiser dès que possible**.  
  
5.  Dans la section **Informations d'identification** , cliquez sur **Utilisez le compte d'actualisation des données configuré par l'administrateur**.  
  
6.  Désactivez la case **Toutes les sources de données**.  
  
7.  Sélectionnez **Actualiser** pour la source de données qui utilise les données Oracle. Le nom de la source de données peut être modifié dans Microsoft Excel dans le menu **Données**, **Connexions**, **Propriétés** .  
  
8.  Sous votre source de données, sélectionnez **Utiliser la planification par défaut**.  
  
9. Sélectionnez **Connectez-vous à l'aide des informations d'identification enregistrées dans le service Banque d'informations sécurisé (SSS) pour la connexion à la source de données. Entrez l’ID utilisé pour consulter les informations d’identification dans la zone Identification SSS**.  
  
10. Dans la zone **ID :** , tapez `OracleAuthentication` .  
  
11. Cliquez sur **OK**.  
  
     Si un message d'erreur semblable au suivant s'affiche : `The provided Secure Store target application is either incorrectly configured or does not exist`.  
  
     Les deux solutions courantes sont les suivantes :  
  
    -   Vérifiez que l'ID d'application cible est correct.  
  
    -   Vérifiez que vous définissez les informations d'identification pour l'application cible.  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a>Pour vérifier l'actualisation des données avec la nouvelle authentification  
 Lorsque vous cliquez sur **OK**, la page **Historique d'actualisation** s'affiche. Après quelques minutes, vous devez voir apparaître un nouvel élément dans l'historique d'actualisation du fait que vous avez sélectionné **Aussi actualiser dès que possible**dans les étapes précédentes. La valeur par défaut du travail du minuteur **Travail du minuteur d’actualisation des données PowerPivot** est de 1 minute. Si aucun nouvel élément n'apparaît dans l'historique d'actualisation, patientez quelques minutes, puis actualisez votre navigateur. Si le problème persiste, vérifiez la valeur actuelle du travail du minuteur.  
  
## <a name="more-information"></a>Informations complémentaires  
  
-   [Configurer le service Banque d'informations sécurisé dans SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).  
  
-   Consultez la section « actualisation planifiée des données » de la rubrique [actualisation des données PowerPivot avec SharePoint 2013 et SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).  
  
  
