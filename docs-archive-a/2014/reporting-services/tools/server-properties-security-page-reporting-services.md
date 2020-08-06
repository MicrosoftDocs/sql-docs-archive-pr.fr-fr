---
title: Propriétés du serveur (page Sécurité) - Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f709d42bf593b4933d9fc1fdc423c195967df382
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610966"
---
# <a name="server-properties-security-page---reporting-services"></a>Propriétés du serveur (page Sécurité) - Reporting Services
  Utilisez cette page pour désactiver des fonctionnalités qui peuvent nuire potentiellement à un serveur de rapports. La désactivation de ces fonctionnalités limitera certaines d'entre elles, mais peut améliorer la sécurité globale du serveur de rapports en atténuant des menaces spécifiques.  
  
 Pour ouvrir cette page, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance de serveur de rapports, cliquez avec le bouton droit sur le nom du serveur de rapports, puis sélectionnez **Propriétés**. Cliquez sur **Sécurité** pour ouvrir cette page.  
  
## <a name="options"></a>Options  
 **Activer la sécurité intégrée Windows pour les sources de données de rapport**  
 Spécifiez si une connexion à une source de données de rapport peut être établie à l'aide du jeton de sécurité Windows de l'utilisateur qui a demandé le rapport.  
  
 Si vous désactivez cette fonctionnalité, la fonctionnalité de sécurité intégrée Windows dans les pages de propriétés de la source de données de rapport ne sera pas disponible. Si les sources de données de rapport sont configurées pour la sécurité intégrée Windows et que vous désactivez par la suite cette fonctionnalité, le serveur de rapports mettra immédiatement à jour toutes les propriétés de connexion à la source de données pour demander des informations d'identification.  
  
 **Activer la génération d'états ad hoc**  
 Spécifiez si les utilisateurs peuvent effectuer des requêtes ad hoc à partir d'un rapport du Générateur de rapports, où les nouveaux rapports sont générés automatiquement lorsqu'un utilisateur clique sur des données d'intérêt.  
  
 La définition de cette option détermine si la propriété `EnableLoadReportDefinition` sur le serveur de rapports a la valeur `True` ou `False`. Si vous désactivez cette option, la propriété aura la valeur `False` et le serveur de rapports ne générera pas les rapports générés interactifs créés pendant l'exploration de données. Tous les appels à la méthode `LoadReportDefinition` seront bloqués.  
  
 La désactivation de cette option atténue la menace qu'un utilisateur malveillant lance une attaque par déni de service en surchargeant le serveur de rapports avec des demandes `LoadReportDefinition`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Se connecter à un serveur de rapports dans Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Spécifier les informations d’identification et de connexion pour les sources de données de rapport] (.. /Report-Data/Specify-Credential-and-Connection-information-for-Report-Data-sources.MD [serveur de rapports dans Management Studio aide (F1](report-server-in-management-studio-f1-help.md) )  
  
  
