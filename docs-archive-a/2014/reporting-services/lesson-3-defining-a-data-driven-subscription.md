---
title: 'Leçon 3 : définition d’un abonnement piloté par les données | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710260"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a>Leçon 3 : Définition d'un abonnement piloté par les données
  Au cours de cette leçon, vous allez utiliser les pages d'abonnement piloté par les données pour vous connecter à une source de données d'abonnement, créer une requête qui extrait des données d'abonnement et mapper le jeu de résultats aux options de remise et de rapport.  
  
> [!NOTE]  
>  Avant de commencer, assurez-vous que le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent est en cours d'exécution. Sans ce service, vous ne pouvez pas enregistrer l'abonnement.  
  
 Cette leçon suppose que vous avez terminé les leçons 1 et 2, et que la source de données du rapport utilise des informations d'identification stockées.  Pour plus d’informations, consultez [Leçon 2 : Modification des propriétés d’une source de données de rapport](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)  
  
 Dans cette rubrique :  
  
-   [Démarrer l’Assistant abonnement piloté par les données](#bkmk_startwizard)  
  
-   [Étape 1 - Définir une description](#bkmk_definesubscription)  
  
-   [Étape 2 - Définir une connexion à la source de données d'abonnement](#bkmk_defineconnectiontosubscriber)  
  
-   [Étape 3 - Définir une requête qui extrait les données des abonnés](#bkmk_definequery)  
  
-   [Étape 4 - Définir des options de remise](#bkmk_set_deliveryoptions)  
  
-   [Étape 5 - Configurer une valeur de paramètre pour modifier le résultat du rapport](#bkmk_configure_parameter)  
  
-   [Étape 6 - Pour planifier un abonnement](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a>Démarrer l’Assistant abonnement piloté par les données  
  
1.  Dans le Gestionnaire de rapports, cliquez sur **Accueil**, puis naviguez jusqu'au dossier contenant le rapport **Sales Orders** .  
  
2.  Dans le menu contextuel du rapport, cliquez sur **Gérer**, puis sur l'onglet **Abonnements** .  
  
3.  Cliquez sur **Nouvel abonnement piloté par les données**. Si ce bouton n'apparaît pas, il se peut que vous n'ayez pas les autorisations relatives au Gestionnaire de contenu.  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a>Étape 1-définir une description  
  
1.  Tapez **Sales Order delivery** comme description.  
  
2.  Sélectionnez **Partage de fichiers Windows** pour **Spécifiez le mode de notification des destinataires**.  
  
3.  Sélectionnez **Spécifier pour cet abonnement uniquement**, puis cliquez sur **Suivant**.  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a>Étape 2-définir une connexion à la source de données de l’abonné  
  
1.  Sélectionnez **Microsoft SQL Server** comme type de source de données.  
  
2.  Dans Chaîne de connexion, tapez la chaîne de connexion suivante :  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  Les abonnés correspondent à la base de données que vous avez créée au cours de la leçon 1.  
  
3.  Cliquez sur **Informations d'identification stockées en sécurité dans le serveur de rapports**.  
  
4.  Dans les zones **Nom d'utilisateur** et **Mot de passe**, tapez le nom d'utilisateur et le mot de passe de votre domaine. Prenez en compte à la fois le domaine et le compte d'utilisateur au moment de définir le **Nom d'utilisateur**.  
  
    > [!NOTE]  
    >  Les informations d'identification utilisées pour la connexion à la source de données d'un abonné ne sont pas renvoyées à [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Si vous modifiez l'abonnement ultérieurement, vous devrez retaper le mot de passe utilisé pour la connexion à la source de données.  
  
5.  Sélectionnez l'option **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**, puis cliquez sur **Suivant**.  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a>Étape 3-définir une requête pour récupérer les données de l’abonné  
  
1.  Dans la zone de requête, tapez la requête suivante :  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  Spécifiez un délai d'expiration de 30 secondes.  
  
3.  Cliquez sur **Valider**, puis sur **Suivant**.  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a>Étape 4 : définir les options de remise  
  
1.  Pour **Nom de fichier**, sélectionnez **Obtenir la valeur de la base de données**. Sélectionnez le champ **Order**.  
  
2.  Pour **Chemin d'accès**, sélectionnez **Spécifier une valeur statique**. Dans Valeur de paramètre, tapez le nom d'un partage de fichiers public pour lequel vous disposez d'autorisations en écriture (par exemple, `\\mycomputer\public\myreports`).  
  
3.  Pour **Format du rendu**, sélectionnez **Obtenir la valeur de la base de données**. Sélectionnez **format**.  
  
4.  Pour **Mode écriture**, sélectionnez **Spécifier une valeur statique** , puis **Autoincrément**.  
  
5.  Pour **Extension de fichier**, sélectionnez **Spécifier une valeur statique** , puis **True**.  
  
6.  Pour **Nom d'utilisateur**, sélectionnez **Spécifier une valeur statique**. Tapez votre compte d'utilisateur de domaine Entrez-le au format suivant : `<domain>\<account>`. Le compte d'utilisateur a besoin d'autorisations sur le chemin d'accès que vous avez configuré dans les étapes précédentes.  
  
7.  Pour **Mot de passe**, sélectionnez **Spécifier une valeur statique**. Tapez votre mot de passe. Tapez le mot de passe avec prudence. L'Assistant ne valide pas le mot de passe.  
  
8.  Cliquez sur **Suivant**.  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a>Étape 5-configurer une valeur de paramètre pour une sortie de rapport très importante  
  
1.  Pour **OrderNumber**, sélectionnez **Obtenir la valeur de la base de données**. Dans Valeur, sélectionnez **Ordre**. Cliquez sur **Suivant**.  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a>Étape 6-pour planifier un abonnement  
  
1.  Cliquez sur **Suivant une planification créée pour cet abonnement**, puis sur **Suivant**.  
  
2.  Dans **Détails de la planification**, cliquez sur **Une fois**.  
  
3.  Spécifiez une heure de début quelques minutes avant l'heure actuelle.  
  
4.  Cliquez sur **Terminer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Lors de l'exécution de l'abonnement, quatre fichiers de rapport sont remis au partage de fichiers que vous avez défini, un pour chaque commande dans la source de données *Abonnés* . Chaque remise doit être unique en termes de données (les données doivent être propres à chaque commande), de format de rendu et de format de fichier. Vous pouvez ouvrir chaque rapport à partir du dossier partagé pour vérifier que chaque version est personnalisée en fonction des options d'abonnement que vous avez définies.  
  
 ![Liste de fichiers créés par l'abonnement](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "Liste de fichiers créés par l'abonnement")  
  
 La page des abonnements dans le Gestionnaire de rapports contiendra la date **Dernière exécution** et l' **État** de l'abonnement.  
  
> [!NOTE]  
>  Actualisez la page après l'exécution de l'abonnement pour consulter les informations mises à jour.  
  
 ![Résultats d'abonnement dans le Gestionnaire de rapports](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Résultats d'abonnement dans le Gestionnaire de rapports")  
  
 Cette étape est la dernière du didacticiel « Définition d'un abonnement piloté par les données ». Pour en savoir plus sur les autres [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] didacticiels, consultez [didacticiels de Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement piloté par les données &#40;didacticiel SSRS&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Créer, modifier et supprimer un abonnement piloté par les données](subscriptions/create-modify-and-delete-data-driven-subscriptions.md)   
 [Utiliser une source de données externe pour les données des abonnés &#40;abonnements pilotés par les données&#41;](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
