---
title: Serveur de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db52b93b3d260ff58a151e7238bbbe065bc47bc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600800"
---
# <a name="oracle-publisher"></a>Serveur de publication Oracle
  Depuis [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet de publier des données à partir d’une base de données Oracle à l’aide de la réplication transactionnelle et d’instantané. Pour plus d’informations, consultez [Présentation de la publication Oracle](non-sql/oracle-publishing-overview.md).  
  
 Le serveur de publication Oracle doit utiliser un serveur de distribution distant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; cet Assistant doit être exécuté sur ce serveur après l'installation et le test du logiciel réseau Oracle nécessaire. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](non-sql/configure-an-oracle-publisher.md).  
  
> [!IMPORTANT]  
>  Si un autre administrateur a configuré la base de données Oracle en tant que serveur de publication, après avoir cliqué sur **Suivant** , le système vous demande d'entrer le mot de passe de la connexion de réplication utilisée en vue de vous connecter à la base de données Oracle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée ensuite un mappage entre votre nom d'accès et la connexion de serveur liée à la base de données Oracle. Vous ne devez pas entrer un mot de passe pour les connexions ultérieures à la base de données Oracle.  
  
## <a name="options"></a>Options  
 **Serveurs de publication Oracle**  
 Sélectionnez un serveur de publication Oracle dans la liste. Cette liste contient les serveurs de publication Oracle, qui ont été configurés au préalable pour utiliser le serveur, sur lequel s'exécute l'Assistant en tant que serveur de distribution. Si la liste est vide ou si le serveur de publication Oracle souhaité n'y figure pas, cliquez sur **Ajouter un serveur de publication Oracle**.  
  
 **Ajouter un serveur de publication Oracle**  
 Cliquez sur ce bouton pour ouvrir la boîte de dialogue **Propriétés du serveur de distribution** . Dans cette la boîte de dialogue, cliquez sur **Ajouter**, puis sur **Ajouter un serveur de publication Oracle**. Dans la boîte de dialogue **Se connecter au serveur** , spécifiez le nom du serveur Oracle ainsi que le nom de connexion et le mot de passe destinés au schéma de l'administrateur de réplication. Pour plus d’informations, consultez [Se connecter au serveur &#40;Oracle&#41;, Connexion](connect-to-server-oracle-login.md).  
  
> [!NOTE]  
>  Si le serveur, sur lequel s'exécute l'Assistant, n'a pas été configuré en tant que serveur de distribution, le système vous demande alors de le faire.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une publication à partir d’une base de données Oracle](publish/create-a-publication-from-an-oracle-database.md)   

  
  
