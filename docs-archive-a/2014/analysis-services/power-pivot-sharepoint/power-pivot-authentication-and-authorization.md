---
title: Authentification et autorisation PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 48230cc0-4037-4f99-8360-dadf4bc169bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1cf777960b24d9c65c7e7f7d9651eeb48e0fe42b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696231"
---
# <a name="powerpivot-authentication-and-authorization"></a>Authentification et autorisation PowerPivot
  Un déploiement PowerPivot pour SharePoint qui s'exécute dans une batterie de serveurs SharePoint 2010 utilise le sous-système d'authentification et le modèle d'autorisation fournis par les serveurs SharePoint. L'infrastructure de sécurité SharePoint s'étend au contenu et aux opérations PowerPivot, car l'ensemble du contenu relatif à PowerPivot est stocké dans des bases de données de contenu SharePoint et l'ensemble des opérations relatives à PowerPivot est effectué par des services partagés PowerPivot de la batterie de serveurs. Les utilisateurs qui demandent un classeur contenant des données PowerPivot sont authentifiés à l'aide d'une identité d'utilisateur SharePoint basée sur leur identité d'utilisateur Windows. Les autorisations d'affichage sur le classeur déterminent si la demande est accordée ou refusée.  
  
 Étant donné que l'intégration à Excel Services est requise pour les analyses de données libre-service, vous devez, pour sécuriser un serveur PowerPivot, bien comprendre également la sécurité d'Excel Services. Lorsqu'un utilisateur interroge un tableau croisé dynamique qui présente une connexion de données à des données PowerPivot, Excel Services envoie une demande de connexion de données à un serveur PowerPivot de la batterie pour charger les données. Du fait de cette interaction entre les serveurs, il est indispensable que vous compreniez comment configurer des paramètres de sécurité pour les deux serveurs.  
  
 Cliquez sur les liens suivants pour accéder à des sections spécifiques de cette rubrique :  
  
 [Authentification Windows à l'aide de la spécification de connexion en mode classique](power-pivot-authentication-and-authorization.md#bkmk_auth)  
  
 [Opérations PowerPivot qui requièrent une autorisation d'utilisateur](#UserConnections)  
  
 [Autorisations SharePoint pour l'accès aux données PowerPivot](#Permissions)  
  
 [Considérations sur la sécurité Excel Services pour les classeurs PowerPivot](#excel)  
  
##  <a name="windows-authentication-using-classic-mode-sign-in-requirement"></a><a name="bkmk_auth"></a>Authentification Windows à l’aide de la spécification de connexion en mode classique  
 PowerPivot pour SharePoint prend en charge un ensemble réduit d'options d'authentification disponibles dans SharePoint. Parmi les options d'authentification disponibles, seule l'authentification Windows est prise en charge pour un déploiement de PowerPivot pour SharePoint. En outre, l'application Web via laquelle la connexion se produit doit être configurée pour le mode classique.  
  
 L'authentification Windows est requise car le moteur de données Analysis Services dans un déploiement PowerPivot pour SharePoint prend uniquement en charge l'authentification Windows. Excel Services établit les connexions à Analysis Services via le fournisseur OLE DB MSOLAP à l'aide d'une identité d'utilisateur Windows qui a été authentifiée via NTLM ou du protocole Kerberos.  
  
 La deuxième spécification, l'authentification en mode classique sur l'application Web, est nécessaire pour garantir l'opérabilité du service Web PowerPivot. Le service Web est un composant qui s'exécute sur un serveur Web frontal et fournit la redirection HTTP vers un serveur PowerPivot pour SharePoint dans la batterie. Tandis que le service Web prend en charge les revendications pour les communications de service-à-service, il ne les prend pas en charge pour les demandes de connexion de données qu'il achemine vers un service partagé PowerPivot dans la batterie. Les demandes de chargement de données PowerPivot sont prises en charge uniquement pour les connexions authentifiées émanant d'IIS à l'aide d'une identité Windows. La connexion en mode classique sur l'application Web permet une connexion réussie du service Web PowerPivot aux services partagés PowerPivot dans la batterie.  
  
 Bien que la connexion en mode classique ne soit pas requise pour le scénario d'accès aux données le plus courant (où les données PowerPivot sont extraites du même classeur Excel qui les restitue), n'essayez pas d'utiliser PowerPivot pour SharePoint avec les applications Web SharePoint configurées pour utiliser d'autres fournisseurs d'authentification. Cette action provoquera un échec de connexion chaque fois que les utilisateurs essaieront de se connecter aux classeurs PowerPivot en tant que source de données externe.  
  
 Sans connexion en mode classique, les types suivants de demandes traitées par le service Web PowerPivot échoueront :  
  
-   Toute demande de données PowerPivot provenant de l'extérieur de la batterie (par exemple, lorsque vous créez un rapport dans le Concepteur de rapports ou le Générateur de rapports, où la source de données est une URL SharePoint d'un classeur PowerPivot)  
  
-   Les demandes dans la batterie d'une application cliente ou d'un rapport qui utilise le classeur PowerPivot comme source de données externe (par exemple, lorsque vous créez un classeur dans l'application bureautique Excel, en utilisant comme source de données un deuxième classeur Excel publié contenant des données PowerPivot)  
  
### <a name="how-to-check-the-authentication-provider-for-your-application"></a>Comment vérifier le fournisseur d'authentification pour votre application  
 Lors de la création d'applications Web, veillez à sélectionner l'option **Authentification en mode classique** dans la page Créer une application Web.  
  
 Pour les applications Web existantes, utilisez les instructions suivantes pour vérifier si l'application Web est configurée pour utiliser l'authentification Windows.  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications Web**.  
  
2.  Sélectionnez l'application Web.  
  
3.  Cliquez sur **Fournisseurs d'authentification**.  
  
4.  Vérifiez que vous avez un fournisseur pour chaque zone et que la zone par défaut a la valeur Windows.  
  
##  <a name="powerpivot-operations-requiring-user-authorization"></a><a name="UserConnections"></a>Opérations PowerPivot nécessitant une autorisation de l’utilisateur  
 L'autorisation SharePoint est utilisée exclusivement pour tous les niveaux d'accès au traitement de données et de requêtes PowerPivot.  
  
 Le modèle d'autorisation basé sur les rôles Analysis Services n'est pas pris en charge. Il n'y a aucune autorisation basée sur les rôles pour des données PowerPivot au niveau de la cellule, de la ligne ou de la table. Vous ne pouvez pas sécuriser des parties différentes du classeur pour accorder ou refuser à des utilisateurs spécifiques l'accès à des données sensibles qu'il contient. Les données PowerPivot incorporées sont entièrement disponibles pour les utilisateurs disposant d'autorisations d'affichage sur le classeur Excel dans une bibliothèque SharePoint.  
  
 PowerPivot pour SharePoint emprunte l'identité d'un utilisateur SharePoint dans les cas suivants :  
  
-   Requêtes adressées à des tableaux croisés dynamiques ou graphiques croisés dynamiques qui ont des connexions de données à une base de données PowerPivot, où une application de service PowerPivot établit de la part d'un utilisateur des connexions à une instance spécifique du service partagé PowerPivot qui traite les données.  
  
-   Chargement de données PowerPivot à partir du cache ou d'une bibliothèque si les données ne sont pas disponibles autrement. Si une demande de connexion de données concerne des données PowerPivot qui ne sont pas encore chargées dans le système, l'instance [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] utilise l'identité de l'utilisateur SharePoint pour récupérer la source de données d'une bibliothèque de contenu et la charger en mémoire.  
  
-   Opérations d'actualisation des données qui enregistrent une copie mise à jour de la source de données dans le classeur d'une bibliothèque de contenu. Dans ce cas, un journal réel de l'opération est créé avec le nom d'utilisateur et le mot de passe récupérés d'une application cible dans le service Banque d'informations sécurisé. Les informations d'identification peuvent correspondre au compte d'actualisation des données PowerPivot sans assistance, mais aussi aux informations d'identification stockées avec la planification d'actualisation des données lors de sa création. Pour plus d’informations, consultez [configurer les informations d’identification stockées pour l’actualisation des données powerpivot &#40;PowerPivot pour SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) et [configurer le compte d’actualisation des données powerpivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
##  <a name="sharepoint-permissions-for-powerpivot-data-access"></a><a name="Permissions"></a>Autorisations SharePoint pour l’accès aux données PowerPivot  
 La publication, la gestion et la sécurisation d'un classeur PowerPivot ne sont prises en charge que via l'intégration SharePoint. Les serveurs SharePoint fournissent des sous-systèmes d'authentification et d'autorisation qui garantissent un accès légitime aux données. Il n'existe pas de scénarios pris en charge pour le déploiement sûr d'un classeur PowerPivot en dehors d'une batterie de serveurs SharePoint.  
  
 L'accès utilisateur aux données PowerPivot est en lecture seule sur le serveur via les autorisations d'affichage ou supérieures. Les autorisations de collaboration permettent d'ajouter et de modifier le fichier. Les modifications apportées aux données PowerPivot requièrent le téléchargement du classeur dans une application bureautique Excel pour laquelle PowerPivot pour Excel est installé. Les autorisations de collaboration sur le fichier déterminent si l'utilisateur peut télécharger le fichier localement, puis enregistrer les modifications dans SharePoint.  
  
 Ainsi, les niveaux d'autorisation Collaboration et Vue seule définissent le jeu d'autorisations réel pour l'accès utilisateur aux données PowerPivot. D'autres niveaux d'autorisation fonctionnent dans la mesure où ils présentent les mêmes autorisations que Collaboration et Vue seule (par exemple, puisque Lecture inclut les autorisations Vue seule, un utilisateur auquel ont été octroyées les autorisations Lecture a le même niveau d'accès qu'avec Vue seule).  
  
 Le tableau suivant résume les niveaux d'autorisation qui déterminent l'accès aux données PowerPivot et aux opérations de serveur :  
  
|Niveau d'autorisation|Autorise les tâches suivantes|  
|----------------------|------------------------|  
|Administrateur de batteries de serveurs ou de services|Installation, activation et configuration de services et d'applications.<br /><br /> Utilisation du tableau de bord de gestion PowerPivot et affichage des rapports d'administration.|  
|Contrôle total|Activation de l'intégration des la fonctionnalités PowerPivot au niveau de la collection de sites.<br /><br /> Création d'une Galerie PowerPivot.<br /><br /> Création d'une bibliothèque de flux de données.|  
|Collaboration|Ajout, modification, suppression et téléchargement de classeurs PowerPivot.<br /><br /> Configuration de l'actualisation des données.<br /><br /> Création de classeurs et rapports basés sur des classeurs PowerPivot sur un site SharePoint.<br /><br /> Création de documents de service de données dans une bibliothèque de flux de données|  
|Lire|Accédez aux classeurs PowerPivot en tant que source de données externe, où l’URL du classeur est explicitement entrée dans une boîte de dialogue de connexion (par exemple, dans l’Assistant de connexion de données d’Excel).|  
|Vue seule|Affichage de classeurs PowerPivot.<br /><br /> Affichage de l'historique d'actualisation des données.<br /><br /> Connexion d'un classeur local à un classeur PowerPivot sur un site SharePoint pour réutiliser ses données d'une autre façon.<br /><br /> Téléchargement d'un instantané du classeur. L'instantané est une copie statique des données, sans segments, filtres, formules ou connexions de données. Le contenu de l'instantané est similaire à la copie de valeurs de cellules de la fenêtre de navigateur.|  
  
##  <a name="excel-services-security-considerations-for-powerpivot-workbooks"></a><a name="excel"></a>Considérations sur la sécurité Excel Services pour les classeurs PowerPivot  
 Le traitement des requêtes côté serveur PowerPivot est étroitement lié à Excel Services. L'intégration de produit commence au niveau du document, du fait que les classeurs PowerPivot sont des fichiers de classeur Excel (.xlsx) qui contiennent ou référencent des données PowerPivot. Il n'existe pas d'extension de fichier distincte pour un classeur PowerPivot.  
  
 Lorsqu'un classeur PowerPivot est ouvert sur un site SharePoint, Excel Services lit la chaîne de connexion des données PowerPivot intégrée et transmet la requête au fournisseur OLE DB Analysis Services SQL Server local. Le fournisseur transmet ensuite les informations de connexion à un serveur PowerPivot de la batterie. Pour que les requêtes transitent de façon transparente entre les deux serveurs, Excel Services doit être configuré de façon à utiliser les paramètres requis par PowerPivot pour SharePoint.  
  
 Dans Excel Services, les paramètres de configuration de sécurité sont spécifiés sur des emplacements, des fournisseurs de données approuvés et des bibliothèques de connexions de données approuvés. Le tableau suivant décrit les paramètres qui activent ou améliorent l'accès aux données PowerPivot. Si un paramètre n'apparaît pas ici, c'est qu'il n'a aucun effet sur les connexions de serveur PowerPivot. Pour obtenir des instructions sur la façon de spécifier ces paramètres étape par étape, consultez la section « Activer Excel Services » dans [configuration initiale &#40;PowerPivot pour SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md).  
  
> [!NOTE]  
>  La plupart des paramètres relatifs à la sécurité s'appliquent à des emplacements approuvés. Si vous souhaitez conserver les valeurs par défaut ou utiliser des valeurs différentes pour des sites différents, vous pouvez créer un emplacement approuvé supplémentaire pour les sites qui contiennent les données PowerPivot, puis configurer les paramètres suivants uniquement pour ce site. Pour plus d'informations, consultez [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
|Domaine|Paramètre|Description|  
|----------|-------------|-----------------|  
|Application web|Fournisseur d'authentification Windows|PowerPivot convertit un jeton de revendications qu'il obtient d'Excel Services en une identité d'utilisateur Windows. Toutes les applications Web qui utilisent Excel Services comme ressource doivent être configurées pour utiliser le fournisseur d'authentification Windows.|  
|Emplacement approuvé|Type d'emplacement|Cette valeur doit être paramétrée sur **Microsoft SharePoint Foundation**. Les serveurs PowerPivot récupèrent une copie du fichier .xlsx et la chargent sur un serveur Analysis Services dans la batterie. Le serveur ne peut récupérer que des fichiers .xlsx d'une bibliothèque de contenu.|  
||Autoriser les données externes|Ce paramètre doit avoir la valeur **Bibliothèques de connexions de données approuvées et incorporées**. Les connexions de données PowerPivot sont incorporées au classeur. Si vous interdisez les connexions incorporées, les utilisateurs peuvent consulter le cache de tableau croisé dynamique, mais ils ne seront pas en mesure d'interagir avec les données PowerPivot.|  
||Avertir lors de l'actualisation|Cette valeur doit être désactivée si vous utilisez la Galerie PowerPivot pour stocker des classeurs et des rapports. La Galerie PowerPivot inclut une fonctionnalité d'aperçu des documents qui fonctionne mieux si les paramètres Actualisation à l'ouverture et Avertir lors de l'actualisation sont désactivés.|  
|Fournisseurs de données approuvés|MSOLAP.4<br /><br /> MSOLAP.5|MSOLAP.4 est inclus par défaut, mais l'accès aux données PowerPivot requiert que le fournisseur MSOLAP.4 soit la version SQL Server 2008 R2.<br /><br /> MSOLAP.5 est installé avec la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de PowerPivot pour SharePoint.<br /><br /> Ne supprimez pas ces fournisseurs de la liste des fournisseurs de données approuvés. Dans certains cas, vous devrez peut-être installer des copies supplémentaires de ce fournisseur sur d'autres serveurs SharePoint dans votre batterie de serveurs. Pour plus d’informations, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).|  
|Bibliothèques de connexions de données approuvées|facultatif.|Vous pouvez utiliser des fichiers Office Data Connection (.odc) dans les classeurs PowerPivot. Si vous utilisez des fichiers .odc pour fournir les informations de connexion aux classeurs PowerPivot locaux, vous pouvez ajouter les mêmes fichiers .odc à cette bibliothèque.|  
|Assembly de fonction défini par l'utilisateur|Non applicable.|PowerPivot pour SharePoint ignore les assemblys de fonction définis par l'utilisateur que vous générez pour Excel Services. Si vous comptez sur les assemblys définis par l'utilisateur pour un comportement spécifique, sachez que le traitement des requêtes PowerPivot n'utilise pas les fonctions définies par l'utilisateur que vous avez créées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des comptes de service PowerPivot](configure-power-pivot-service-accounts.md)   
 [Configurez le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)   
 [Créer un emplacement approuvé pour les sites PowerPivot dans l’administration centrale](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [Architecture de la sécurité PowerPivot](https://go.microsoft.com/fwlink/?linkID=220970)  
  
  
