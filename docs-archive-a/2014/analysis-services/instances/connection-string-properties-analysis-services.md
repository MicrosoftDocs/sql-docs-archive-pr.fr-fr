---
title: Propriétés de la chaîne de connexion (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 29a00a41-5b0d-44b2-8a86-1b16fe507768
author: minewiskan
ms.author: owend
ms.openlocfilehash: 304525ae8a3ff5c910916352ff354cde8c354d44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698819"
---
# <a name="connection-string-properties-analysis-services"></a>Propriétés des chaînes de connexion (Analysis Services)
  Cette rubrique documente les propriétés de chaîne de connexion que vous pouvez définir dans le concepteur ou les outils d'administration, ou voir dans les chaînes de connexion générées par les applications clientes qui se connectent aux données Analysis Services et interrogent ces dernières. Par conséquent, elle couvre uniquement un sous-ensemble des propriétés disponibles. La liste complète inclut de nombreuses propriétés de serveur et de base de données, vous permettant de personnaliser une connexion à une application spécifique, indépendamment de la façon dont l'instance ou la base de données est configurée sur le serveur.  
  
 Les développeurs qui créent des chaînes de connexion personnalisées dans un code d’application doivent consulter la documentation de l’API pour le client ADOMD.NET afin d’obtenir une liste plus détaillée : <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>  
  
 Les propriétés décrites dans cette rubrique sont utilisées par les bibliothèques clientes Analysis Services, ADOMD.NET, AMO et le fournisseur OLE DB pour Analysis Services. La majorité des propriétés de chaîne de connexion peut être utilisée avec les trois bibliothèques clientes. Les exceptions sont signalées dans la description.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Paramètres de connexion couramment utilisés](#bkmk_common)  
  
 [Authentification et sécurité](#bkmk_auth)  
  
 [Paramètres spéciaux](#bkmk_special)  
  
 [Réservé pour un usage ultérieur](#bkmk_reserved)  
  
 [Exemples de chaîne de connexion](#bkmk_examples)  
  
 [Formats de chaîne de connexion utilisés dans Analysis Services](#bkmk_supportedstrings)  
  
 [Chiffrement des chaînes de connexion](#bkmk_encrypt)  
  
> [!NOTE]  
>  Si, par inadvertance, vous définissez deux fois la même propriété, c'est la dernière figurant dans la chaîne de connexion qui est utilisée.  
  
 Pour plus d’informations sur la façon de spécifier une connexion Analysis Services dans des applications Microsoft existantes, voir [Connexion à partir d’applications clientes (Analysis Services)](connect-from-client-applications-analysis-services.md).  
  
##  <a name="connection-parameters-in-common-use"></a><a name="bkmk_common"></a> Paramètres de connexion couramment utilisés  
 Le tableau suivant décrit les propriétés couramment utilisées lors de la génération d'une chaîne de connexion.  
  
|Propriété|Description|Exemple|  
|--------------|-----------------|-------------|  
|`Data Source` ou `DataSource`|Spécifie l'instance du serveur. Cette propriété est obligatoire pour toutes les connexions. Les valeurs valides incluent le nom réseau ou l'adresse IP du serveur, local ou localhost pour les connexions locales, une adresse URL si le serveur est configuré pour l'accès HTTP ou HTTPS, ou le nom d'un fichier de cube local (.cub).|`Data source=AW-SRV01` pour l'instance et le port par défaut (TCP 2383).<br /><br /> `Data source=AW-SRV01$Finance:8081` pour une instance nommée ($Finance) et un port fixe.<br /><br /> `Data source=AW-SRV01.corp.Adventure-Works.com` pour un nom de domaine complet, avec le port et l'instance par défaut.<br /><br /> `Data source=172.16.254.1` pour une adresse IP du serveur, en ignorant la recherche de serveur DNS, utile pour résoudre des problèmes de connexion.|  
|`Initial Catalog` ou `Catalog`|Spécifie le nom de la base de données Analysis Services à laquelle se connecter. La base de données doit être déployée sur Analysis Services et vous devez avoir l'autorisation de vous y connecter. Cette propriété est facultative pour les connexions AMO, mais requise pour ADOMD.NET.|`Initial catalog=AdventureWorks2012`|  
|`Provider`|Les valeurs valides sont MSOLAP ou MSOLAP. \<version> , où \<version> est 3, 4 ou 5. Dans le système de fichiers, le nom du fournisseur de données est msolap110.dll pour la version SQL Server 2012, msolap100.dll pour SQL Server 2008 et SQL Server 2008 R2, et msolap90.dll pour SQL Server 2005.<br /><br /> La version actuelle est MSOLAP.5. Cette propriété est facultative. Par défaut, les bibliothèques clientes lisent la version actuelle du fournisseur OLE DB à partir du Registre. Il vous suffit de définir cette propriété à si vous avez besoin d'une version spécifique du fournisseur de données, par exemple pour vous connecter à une instance SQL Server 2008.<br /><br /> Les fournisseurs de données correspondent aux versions de SQL Server. Si votre organisation utilise la version actuelle et les versions antérieures d'Analysis Services, vous devrez probablement spécifier le fournisseur à utiliser dans les chaînes de connexion que vous créez manuellement. Vous devrez peut-être aussi télécharger et installer des versions spécifiques du fournisseur de données sur des ordinateurs qui n'ont pas la version dont vous avez besoin. Vous pouvez télécharger le fournisseur OLE DB à partir des pages SQL Server Feature Pack du Centre de téléchargement. Accédez à [Microsoft SQL Server 2012 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=296473) pour télécharger le fournisseur OLE DB d'Analysis Services pour SQL Server 2012.<br /><br /> MSOLAP.4 a été implémenté à la fois dans SQL Server 2008 et dans SQL Server 2008 R2. La version 2008 R2 prend en charge les classeurs PowerPivot et doit parfois être installée manuellement sur les serveurs SharePoint. Pour distinguer ces versions, vous devez vérifier le numéro de build dans les propriétés de fichier du fournisseur : accédez à Program files\Microsoft Analysis Services\AS OLEDB\10. Cliquez avec le bouton droit sur msolap110.dll, puis sélectionnez **Propriétés**. Cliquez sur **Details**. Consultez les informations de version du fichier. La version doit inclure 10,50.\<buildnumber> pour SQL Server 2008 R2. Pour plus d’informations, voir [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) et [Fournisseurs de données utilisés pour les connexions Analysis Services](data-providers-used-for-analysis-services-connections.md).<br /><br /> MSOLAP. 3 a été publié en SQL Server 2005.<br /><br /> MSOLAP. 4 a été publié dans SQL Server 2008 et SQL Server 2008 R2<br /><br /> MSOLAP. 5 a été publié en SQL Server 2012|`Provider=MSOLAP.3` est utilisé pour les connexions qui nécessitent la version SQL Server 2005 du fournisseur OLE DB pour Analysis Services.|  
|`Cube`|Nom du cube ou de la perspective. Une base de données peut contenir plusieurs cubes et perspectives. Lorsque plusieurs cibles sont possibles, indiquez le nom du cube ou de la perspective dans la chaîne de connexion.|`Cube=SalesPerspective` indique que vous pouvez utiliser la propriété de chaîne de connexion Cube pour spécifier le nom d’un cube ou le nom d’une perspective.|  
  
##  <a name="authentication-and-security"></a><a name="bkmk_auth"></a>Authentification et sécurité  
 Cette section présente les propriétés de chaîne de connexion relatives à l'authentification et au chiffrement. Analysis Services utilise l'authentification Windows uniquement, mais vous pouvez définir des propriétés sur la chaîne de connexion pour transmettre un nom d'utilisateur et un mot de passe spécifiques.  
  
 Les propriétés sont répertoriées par ordre alphabétique.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`EffectiveUserName`|À utiliser lorsque l'identité de l'utilisateur final doit être empruntée sur le serveur. Spécifiez le compte sous le format domaine\utilisateur. Pour utiliser cette propriété, l'appelant doit avoir des autorisations d'administration dans Analysis Services. Pour plus d'informations sur l'utilisation de cette propriété dans un classeur Excel à partir de SharePoint, consultez [Utiliser Analysis Services EffectiveUserName dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=311905). Pour obtenir une illustration de l'utilisation de cette propriété avec Reporting Services, consultez [Utilisation d'EffectiveUserName pour l'emprunt d'identité dans SSAS](https://www.artisconsulting.com/blogs/greggalloway/2010/4/1/using-effectiveusername-to-impersonate-in-ssas).<br /><br /> `EffectiveUserName` est utilisé dans une installation de PowerPivot pour SharePoint afin de recueillir des informations d'utilisation. L'identité de l'utilisateur est fournie au serveur afin que les événements ou les erreurs qui incluent l'identité de l'utilisateur puissent être stockés dans les fichiers journaux. Dans le cas de PowerPivot, elle n'est pas utilisée pour l'autorisation.|  
|**Chiffrer le mot de passe**|Spécifie si un mot de passe local doit être utilisé pour chiffrer les cubes locaux. Les valeurs valides sont True ou False. La valeur par défaut est False.|  
|`Encryption Password`|Le mot de passe utilisé pour déchiffrer un cube local chiffré. La valeur par défaut est vide. Cette valeur doit être explicitement définie par l'utilisateur.|  
|`Impersonation Level`|Indique le niveau d'emprunt d'identité que le serveur est autorisé à utiliser lorsqu'il emprunte l'identité du client. Les valeurs valides sont les suivantes :<br /><br /> **Anonyme**: le client est anonyme pour le serveur. Le processus serveur ne peut pas obtenir les informations sur le client et il n'est pas possible d'emprunter l'identité du client.<br /><br /> **Identifier**: le processus serveur peut récupérer l’identité du client. Le serveur peut emprunter l'identité du client à des fins d'autorisation, mais il ne peut pas accéder aux objets système en tant que client.<br /><br /> **Impersonate**: il s’agit de la valeur par défaut. L'identité du client peut être empruntée, mais uniquement lorsque la connexion est établie, et non à chaque appel.<br /><br /> **Délégué**: le processus serveur peut emprunter l’identité du contexte de sécurité du client tout en agissant pour le compte du client. Le processus serveur peut également faire des appels sortants à d'autres serveurs lorsqu'il agit de la part du client.|  
|`Integrated Security`|L'identité Windows de l'appelant est utilisée pour la connexion à Analysis Services. Les valeurs possibles sont SSPI et BASIC ou aucune valeur.<br /><br /> `Integrated Security`=`SSPI`est la valeur par défaut pour les connexions TCP, ce qui autorise l’authentification NTLM, Kerberos ou anonyme. La valeur par défaut pour les connexions HTTP est vide.<br /><br /> Lorsque vous utilisez `SSPI`, `ProtectionLevel` doit être défini sur l'une des valeurs suivantes : `Connect`, `PktIntegrity`, `PktPrivacy`.|  
|`Persist Encrypted`|Définissez cette propriété lorsque l'application cliente doit disposer de l'objet source de données pour conserver les informations d'authentification sensibles, telles qu'un mot de passe, sous forme chiffrée. Par défaut, les informations d'identification ne sont pas conservées.|  
|`Persist Security Info`|Les valeurs valides sont True et False. Lorsque la valeur est True, les informations de sécurité, telles que l'identité de l'utilisateur ou le mot de passe spécifié précédemment dans la chaîne de connexion, figurent dans la connexion une fois celle-ci établie. La valeur par défaut est False.|  
|`ProtectionLevel`|Détermine le niveau de sécurité utilisé lors de la connexion. Les valeurs autorisées sont :<br /><br /> `None`. Unauthenticated or anonymous connections. N'effectue aucune authentification sur les données envoyées au serveur.<br /><br /> `Connect`. Authenticated connections. Effectue une authentification uniquement lorsque le client établit une relation avec un serveur.<br /><br /> `PktIntegrity`. Encrypted connections. Vérifie que toutes les données sont reçues du client et qu'elles n'ont pas été modifiées en cours de route.<br /><br /> `PktPrivacy`. Signed encryption, pris en charge uniquement pour XMLA. Vérifie que toutes les données sont reçues du client, qu'elles n'ont pas changées en cours de route et protège la confidentialité des données en les chiffrant.<br /><br /> <br /><br /> Pour plus d'informations, consultez [Establishing Secure Connections in ADOMD.NET](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/connections-in-adomd-net-establishing-secure-connections)|  
|`Roles`|Spécifiez une liste séparée par des virgules des rôles prédéfinis pour la connexion à un serveur ou une base de données à l'aide des autorisations données à ce rôle. Si cette propriété est omise, tous les rôles sont utilisés, et les autorisations effectives correspondent à la combinaison de tous les rôles. Affectation d’une valeur vide à la propriété (par exemple, Roles = ' ') la connexion cliente n’a pas d’appartenance à un rôle.<br /><br /> Un administrateur utilisant cette propriété se connecte à l'aide des autorisations données par le rôle. Certaines commandes risquent d'échouer si le rôle ne fournit pas d'autorisations suffisantes.|  
|`SSPI`|Spécifie explicitement les packages de sécurité à utiliser pour l'authentification du client lorsque `Integrated Security` a la valeur `SSPI`. SSPI prend en charge plusieurs packages, mais cette propriété permet de spécifier un package particulier. Les valeurs valides sont Negotiate, Kerberos, NTLM et Anonymous User. Si propriété n'est pas définie, tous les packages sont disponibles pour la connexion.|  
|`Use Encryption for Data`|Chiffre les transmissions de données. Les valeurs possibles sont True et False.|  
|`User ID`=...;`Password`=|`User ID`et `Password` sont utilisés ensemble. Analysis Services emprunte l'identité de l'utilisateur spécifiée au moyen de ces informations d'identification. Sur une connexion Analysis Services, placer les informations d'identification sur la ligne de commande n'est permis que lorsque le serveur est configuré pour l'accès HTTP et que vous avez défini l'authentification de base au lieu de la sécurité intégrée dans le répertoire virtuel IIS.<br /><br /> Le nom d'utilisateur et le mot de passe doivent être des informations d'identification d'une identité Windows, c'est-à-dire un compte d'utilisateur de domaine ou local. Notez que `User ID` comporte un espace incorporé. D'autres alias pour cette propriété sont `UserName` (sans espace) et `UID`. L'alias pour `Password` est `PWD`.|  
  
##  <a name="special-purpose-parameters"></a><a name="bkmk_special"></a> Paramètres spéciaux  
 Cette section décrit les autres paramètres de chaîne de connexion. Ceux-ci sont utilisées pour garantir des comportements de connexion spécifiques requis par une application.  
  
 Les propriétés sont répertoriées par ordre alphabétique.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`Application Name`|Définit le nom de l'application associée à la connexion. Cette valeur peut être utile pour surveiller les événements de suivi, notamment lorsque vous disposez de plusieurs applications accédant aux mêmes bases de données. Par exemple, l’ajout de l’application name = 'test’à une chaîne de connexion entraîne l’affichage de’test’dans une trace de SQL Server Profiler, comme illustré dans la capture d’écran suivante :<br /><br /> ![SSAS_AppNameExcample](../media/ssas-appnameexcample.gif "SSAS_AppNameExcample")<br /><br /> Les alias pour cette propriété sont `sspropinitAppName`, `AppName`. Pour plus d'informations, consultez [Utiliser le paramètre de nom d'application lors de la connexion à SQL Server](https://www.connectionstrings.com/use-application-name-sql-server/).|  
|`AutoSyncPeriod`|Définit la fréquence (en millisecondes) de la synchronisation du cache client et serveur. ADOMD.NET facilite la mise en cache client pour les objets souvent utilisés avec une charge minimale de mémoire. Cela permet de réduire le nombre d'allers-retours au serveur. La valeur par défaut est 10 000 millisecondes (dix secondes). Si la valeur est Null ou 0, la synchronisation automatique est désactivée.|  
|`Character Encoding`|Définit la manière dont les caractères sont encodés dans la demande. Les valeurs valides sont Default ou UTF-8 (les deux sont équivalentes), et UTF-16|  
|`CompareCaseSensitiveStringFlags`|Ajuste les comparaisons de chaînes sensibles à la casse pour les paramètres régionaux spécifiés. Pour plus d'informations sur la définition de cette propriété, consultez [Propriété CompareCaseSensitiveStringFlags](https://msdn.microsoft.com/library/aa237459\(v=sql.80\).aspx).|  
|`Compression Level`|Si `TransportCompression` est XPRESS, vous pouvez définir le niveau de compression pour contrôler le degré de compression utilisé. Les valeurs valides sont comprises entre 0 et 9, 0 correspondant à une compression moindre et 9 à la compression la plus importante. Une compression élevée ralentit les performances. La valeur par défaut est 0.|  
|`Connect Timeout`|Détermine la durée maximale (en secondes) pendant laquelle le client tente une connexion avant d’expirer. Si une connexion échoue au cours de cette période, le client quitte la tentative de connexion et génère une erreur.|  
|`MDX Compatibility`|L'objectif de cette propriété est de garantir un ensemble cohérent de comportements MDX pour les applications qui génèrent des requêtes MDX. Excel, qui utilise des requêtes MDX pour remplir et calculer un tableau croisé dynamique connecté à Analysis Services, définit cette propriété sur 1 pour s'assurer que les membres d'espace réservé dans les hiérarchies déséquilibrées sont visibles dans un tableau croisé dynamique. Les valeurs valides sont 0, 1, 2.<br /><br /> 0 et 1 exposent les membres d'espace réservé, contrairement à la valeur 2. En l'absence de valeur, c'est 0 qui est utilisé.|  
|`MDX Missing Member Mode=Error`|Indique si les membres manquants sont ignorés dans les instructions MDX. Les valeurs valides sont Default, Error et Ignore. Default utilise une valeur définie par le serveur. Error génère une erreur lorsqu'un membre n'existe pas. Ignore spécifie que les valeurs manquantes doivent être ignorées.|  
|`Optimize Response`|Un masque de bits indiquant lesquelles des optimisations suivantes de réponse aux requêtes sont activées.<br /><br /> 0x01 : valeur par défaut. Utiliser NormalTupleSet <br />0x02 : à utiliser lorsque les segments sont vides|  
|`Packet Size`|Taille d'un paquet réseau (en octets), comprise entre 512 et 32 767. La taille des paquets réseau par défaut est 4 096.|  
|`Protocol Format`|Définit le format du code XML envoyé au serveur. Les valeurs valides sont Default, XML ou Binary. Le protocole est XMLA. Vous pouvez spécifier que XML soit envoyé sous forme compressée (il s'agit de la valeur par défaut), dans un fichier XML brut ou sous un format binaire. Le format binaire encode les attributs et les éléments XML, ce qui les rend plus petits. La compression est un format propriétaire qui réduit encore la taille des demandes et des réponses. La compression et les formats binaires sont utilisés pour accélérer les demandes et les réponses de transfert de données.<br /><br /> Vous devez utiliser une bibliothèque cliente sur la connexion si vous utilisez le format binaire ou le format compressé. Le fournisseur OLE DB peut mettre en forme les demandes et les réponses au format binaire ou compressé. AMO et ADOMD.NET mettent en forme les demandes sous forme de texte, mais acceptent des réponses au format binaire ou compressé.<br /><br /> Cette propriété de chaîne de connexion est équivalente aux paramètres de configuration de serveur `EnableBinaryXML` et `EnableCompression`.|  
|`Real Time Olap`|Définissez cette propriété pour ignorer la mise en cache, afin que toutes les partitions écoutent activement les notifications de requêtes. Par défaut, cette propriété n'est pas définie.|  
|`Safety Options`|Définit le niveau de sécurité pour les actions et les fonctions définies par l'utilisateur. Les valeurs valides sont 0, 1 et 2. Dans une connexion Excel, cette propriété correspond aux options de sécurité=2. Pour plus de détails sur cette option, voir <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.|  
|`SQLQueryMode`|Spécifie si les requêtes SQL incluent des calculs. Les valeurs valides sont Data, Calculated, IncludeEmpty. Data signifie qu'aucun calcul n'est autorisé. Calculated autorise les calculs. IncludeEmpty permet le renvoi de calculs et de lignes vides dans le résultat de la requête.|  
|`Timeout`|Spécifie la durée (en millisecondes) pendant laquelle la bibliothèque cliente attend la fin d'une commande avant de générer une erreur.|  
|`Transport Compression`|Définit la manière dont les communications client et serveur sont compressées, si la compression est définie via la propriété `Protocol Format`. Les valeurs valides sont Default, None, Compressed et `gzip`. Default indique l'absence de compression pour TCP ou `gzip` pour HTTP. None indique qu'aucune compression n'est utilisée. Compressed utilise la compression XPRESS (SQL Server 2008 et versions ultérieures). `gzip`est valide uniquement pour les connexions HTTP, où la requête HTTP comprend Accept-Encoding = gzip.|  
|`UseExistingFile`|Utilisé lors de la connexion à un cube local. Cette propriété spécifie si le cube local est remplacé. Les valeurs valides sont True ou False. Si la valeur True est définie, le fichier de cube doit exister. Le fichier existant sera la cible de la connexion. Si la valeur définie est False, le fichier de cube est remplacé.|  
|`VisualMode`|Définissez cette propriété pour contrôler la façon dont les membres sont agrégées lorsque la sécurité de dimension est appliquée.<br /><br /> Pour les données de cube que toute le monde est autorisé à afficher, l'agrégation de tous les membres est logique car toutes les valeurs qui contribuent au total sont visibles. Toutefois, si vous filtrez ou restreignez les dimensions en fonction de l'identité de l'utilisateur, afficher un total basé sur tous les membres (en combinant les valeurs restreintes et autorisées dans un seul total) risque d'être déroutant ou d'inclure plus d'informations que nécessaire.<br /><br /> Pour spécifier la façon dont les membres sont agrégés lorsque la sécurité de dimension est appliquée, vous pouvez définir cette propriété sur True afin d'utiliser uniquement les valeurs autorisées dans l'agrégation, ou False pour exclure les valeurs restreintes du total.<br /><br /> Si la chaîne de connexion est définie, cette valeur s'applique au niveau de cube ou de perspective. Dans un modèle, vous pouvez contrôler les valeurs totales affichées à un niveau plus granulaire.<br /><br /> Les valeurs valides sont 0, 1 et 2.<br /><br /> La valeur par défaut est 0. Actuellement, le comportement par défaut est équivalent à 2, où les agrégations contiennent des valeurs qui sont masquées de l'utilisateur.<br /><br /> 1 exclut les valeurs masquées du total. Il s'agit de la valeur par défaut pour Excel.<br /><br /> 2 inclut les valeurs masquées dans le total. Il s'agit de la valeur par défaut sur le serveur.<br /><br /> <br /><br /> Les alias pour cette propriété sont `Visual Total` ou `Default MDX Visual Mode`.|  
  
##  <a name="reserved-for-future-use"></a><a name="bkmk_reserved"></a>Réservé pour un usage ultérieur  
 Les propriétés suivantes sont autorisées sur une chaîne de connexion, mais ne sont pas opérationnelles dans les versions actuelle d'Analysis Services.  
  
-   utilisateur authentifié  
  
-   Mise en cache des informations d'authentification  
  
-   Mode de cache (l'utilisation de cette propriété a été étudiée avec les versions antérieures. Bien que son utilisation soit recommandée dans certains blogs, vous devez éviter de définir cette propriété sauf spécification contraire par le support technique de Microsoft).  
  
-   Stratégie de cache  
  
-   Rapport du cache  
  
-   Ratio2 du cache  
  
-   Limite dynamique de débogage  
  
-   Mode débogage  
  
-   Mode  
  
-   SQLCompatibility  
  
-   Utiliser le cache de formule  
  
##  <a name="example-connection-strings"></a><a name="bkmk_examples"></a>Exemples de chaînes de connexion  
 Cette section présente la chaîne de connexion que vous utiliserez très probablement lors de la configuration d’une connexion Analysis Services dans les applications couramment utilisées.  
  
 **Chaîne de connexion générique**  
  
 Vous pouvez utiliser une chaîne de connexion comme celle-ci si vous configurez une connexion depuis Reporting Services.  
  
 `Data source=<servername>; initial catalog=<databasename>`  
  
 **Chaîne de connexion dans Excel**  
  
 La chaîne de connexion ADOMD.NET par défaut dans Excel spécifie le fournisseur de données, le serveur, le nom de la base de données et la sécurité intégrée de Windows. Le niveau de compatibilité MDX est toujours défini sur 1. Bien que vous puissiez modifier la valeur de la session active, Excel rétablira la compatibilité MDX à 1 lors de la prochaine ouverture du fichier.  
  
 `Provider=MSOLAP.5;Integrated Security=SSPI;Persist Security Info=True;Initial Catalog=Adventure Works DW 2008R2;Data Source=AW-SRV01;MDX Compatibility=1;Safety Options=2;MDX Missing Member Mode=Error`  
  
 Pour plus d’informations, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) et [authentification de données pour Excel Services dans SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=296350).  
  
##  <a name="connection-string-formats-used-in-analysis-services"></a><a name="bkmk_supportedstrings"></a> Formats de chaîne de connexion utilisés dans Analysis Services  
 Cette section répertorie tous les formats de chaîne de connexion pris en charge par Analysis Services. À l'exception des connexions aux bases de données PowerPivot, vous pouvez spécifier ces chaînes de connexion dans les applications qui se connectent à Analysis Services.  
  
 **Connexions natives (ou directes) au serveur**  
  
 `Data Source=server[:port][\instance]`où « port » et « \Instance » sont facultatifs. Par exemple, la spécification de « Data source = Server1 » ouvre une connexion à l’instance par défaut (et le port par défaut 2383) sur un serveur nommé « server1 ».  
  
 « Data source = Server1 : PORT1 » ouvre une connexion à une instance Analysis Services s’exécutant sur le port « PORT1 » sur « Serveur1 ».  
  
 « Data source = server1\instance1 » ouvre une connexion à SQL Browser (sur son port par défaut 2382), résout le port de l’instance nommée « Instance1 », puis ouvre la connexion à ce port de Analysis Services.  
  
 « Data source = Server1 : port1\instance1 » ouvre une connexion à SQL Browser sur « PORT1 », résout le port de l’instance nommée « Instance1 », puis ouvre la connexion à ce Analysis Services port.  
  
 **Connexions de cube locales (fichiers .cub)**  
  
 `Data Source=<path>`, par exemple « Data source = c:\temp\a.CUB »  
  
 **Connexions HTTP(s) à msmdpump.dll**  
  
 `Data Source=<URL>`, où l'URL est l'adresse HTTP ou HTTPS dans le dossier virtuel IIS qui contient le fichier msmdpump.dll. Pour plus d’informations, consultez [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
 **Connexions HTTP aux classeurs PowerPivot (fichiers .xlsx, .xlsb ou .xlsm)**  
  
 `Data Source=<URL>`, où l'URL est le chemin d'accès SharePoint à un classeur PowerPivot publié dans une bibliothèque SharePoint. Par exemple, « Data source = <http://localhost/Shared> documents/Sales.xlsx ».  
  
 **Connexions HTTP(s) aux fichiers de connexion de modèle sémantique BI**  
  
 `Data Source=<URL>` où l'URL est le chemin d'accès SharePoint au fichier .bism. Par exemple, « Data source = <http://localhost/Shared> documents/Sales. BISM ».  
  
 **Connexions incorporées PowerPivot**  
  
 `Data Source=$Embedded$` où $embedded$ " est un moniker qui fait référence à un modèle de données PowerPivot incorporées dans le classeur. Cette chaîne de connexion est créée et gérée en interne. Ne la modifiez pas. Les chaînes de connexion incorporées sont résolues par le complément PowerPivot pour Excel sur les stations de travail clientes, ou par les instances PowerPivot pour SharePoint dans une batterie de serveurs SharePoint.  
  
 **Contexte de serveur local dans les procédures stockées Analysis Services**  
  
 `Data Source=*`, où * est résolu en instance locale.  
  
##  <a name="encrypting-connection-strings"></a><a name="bkmk_encrypt"></a> Chiffrement des chaînes de connexion  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] chiffre et stocke les chaînes de connexion qu’il utilise pour se connecter à chacune de ses sources de données. Si la connexion à une source de données nécessite un nom d'utilisateur et un mot de passe, vous pouvez demander à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de stocker le nom et le mot de passe avec la chaîne de connexion, ou lui indiquer de demander le nom et le mot de passe chaque fois qu'une connexion à la source de données est nécessaire. Si vous indiquez à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de vous demander les informations utilisateur, ceci implique que ces informations ne doivent pas être stockées et chiffrées. En revanche, si vous stockez ces informations dans la chaîne de connexion, ces informations doivent être chiffrées et protégées.  
  
 Pour chiffrer et protéger les informations de la chaîne de connexion, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l'API de protection des données. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise une clé de chiffrement distincte pour chiffrer les informations de la chaîne de connexion pour chaque base de données de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée cette clé quand vous créez une base de données et chiffe les informations de la chaîne de connexion en fonction du compte de démarrage [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Lors du démarrage de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , la clé chiffrée pour chaque base de données est lue, déchiffrée et stockée. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise ensuite la clé déchiffrée appropriée pour déchiffrer les informations de la chaîne de connexion à la source de données lorsque [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a besoin de se connecter à une source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8,0](configure-http-access-to-analysis-services-on-iis-8-0.md)   
 [Configurer Analysis Services pour la délégation Kerberos avec restriction](configure-analysis-services-for-kerberos-constrained-delegation.md)   
 [Fournisseurs de données utilisés pour les connexions Analysis Services](data-providers-used-for-analysis-services-connections.md)   
 [Se connecter à Analysis Services](connect-to-analysis-services.md)  
  
  
