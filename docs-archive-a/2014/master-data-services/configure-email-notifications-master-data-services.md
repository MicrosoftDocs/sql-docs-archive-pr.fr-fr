---
title: Configurer des notifications par e-mail (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: baf60677435122af00f5ee5492e47bafaa45a3ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615195"
---
# <a name="configure-email-notifications-master-data-services"></a>Configurer des notifications par courrier électronique (Master Data Services)
  Configurez des e-mail de notification lorsque vous souhaitez que [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] envoie automatiquement des e-mails.  
  
### <a name="to-configure-notifications"></a>Pour configurer des notifications  
  
1.  Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], dans la page **Base de données** , sélectionnez votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Dans la section **Paramètres système** , cliquez sur **Créer un profil**.  
  
3.  Complétez tous les champs obligatoires. Pour plus d’informations, consultez [Boîte de dialogue Créer un compte et un profil de messagerie de base de données &#40;Gestionnaire de configuration des services de données de référence&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).  
  
4.  Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Après avoir configuré des notifications, vous ne pouvez pas utiliser le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour apporter des modifications. Vous devez apporter les modifications directement dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Objets de configuration de la messagerie de base de données](../relational-databases/database-mail/database-mail-configuration-objects.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Il existe des paramètres dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] qui affectent les notifications. Vous pouvez ajuster ces paramètres dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou directement dans la table Paramètres système dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;de notifications Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)   
 [Résolution des problèmes de notifications par courrier électronique (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
