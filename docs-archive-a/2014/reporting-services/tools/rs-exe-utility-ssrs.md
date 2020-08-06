---
title: Utilitaire RS.exe (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf21a1bf2453d2bd1f0644e31ca46f3f94e6884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704824"
---
# <a name="rsexe-utility-ssrs"></a>Utilitaire RS.exe (SSRS)
  L'utilitaire rs.exe traite le script que vous fournissez dans un fichier d'entrée. Utilisez cet utilitaire pour automatiser les tâches de déploiement et d'administration du serveur de rapports.  
  
> [!NOTE]  
>  Depuis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], l’utilitaire **rs** est pris en charge sur les serveurs de rapports configurés pour le mode intégré SharePoint ainsi que sur les serveurs configurés en mode natif. Les versions antérieures ne prenaient en charge que les configurations en mode natif.  
  
 **Dans cette rubrique :**  
  
-   [Emplacement du fichier](#bkmk_filelocation)  
  
-   [Arguments](#bkmk_arguments)  
  
-   [autorisations](#bkmk_permissions)  
  
-   [Exemples](#bkmk_examples)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> Emplacement du fichier  
 **RS.exe** se trouve à l’emplacement **\Program Files\Microsoft SQL Server\110\Tools\Binn**. Vous pouvez exécuter l'utilitaire à partir de n'importe quel dossier de votre système de fichiers.  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a> Arguments  
 **-?**  
 (Facultatif) Affiche la syntaxe des arguments de **rs** .  
  
 `-i`*input_file*  
 (Obligatoire) Spécifie le fichier .rss à exécuter. Cette valeur peut être un chemin d'accès relatif ou totalement défini au fichier .rss.  
  
 `-s`*ServerURL*  
 (Obligatoire) Spécifie les noms du serveur Web et du répertoire virtuel du serveur de rapports auxquels s'applique le fichier à exécuter. L'URL du serveur de rapports pourrait être par exemple `http://examplewebserver/reportserver`. Le préfixe http:// ou https:// placé au début du nom du serveur est facultatif. Si vous omettez le préfixe, l'environnement d'exécution de scripts du serveur de rapports tente en premier lieu d'utiliser https et, si cela ne fonctionne pas, il essaie avec http.  
  
 `-u`[*domaine* \\ ] *nom d’utilisateur*  
 (Facultatif) Spécifie un compte d'utilisateur utilisé pour se connecter au serveur de rapports. Si `-u` et `-p` sont absents, le compte d'utilisateur Windows actuel est utilisé.  
  
 `-p` *mot de passe*  
 (Obligatoire si `-u` est spécifié) Spécifie le mot de passe à utiliser avec l'argument `-u`. Cette valeur respecte la casse.  
  
 `-e`  
 (Facultatif) Spécifie le point de terminaison SOAP sur lequel le script devrait s'exécuter. Les valeurs suivantes sont valides :  
  
-   Mgmt2010  
  
-   Mgmt2006  
  
-   Mgmt2005  
  
-   Exec2005  
  
 Si une valeur n'est pas spécifiée, le point de terminaison Mgmt2005 est utilisé. Pour plus d'informations sur les points de terminaison SOAP, consultez [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).  
  
 `-l`*time_out*  
 Facultatif Spécifie le nombre de secondes qui s’écoulent avant l’expiration de la connexion au serveur. La valeur par défaut est 60 secondes. Si vous ne spécifiez pas de délai d'expiration, la valeur par défaut est utilisée. La valeur `0` indique que la connexion n'arrive jamais à expiration.  
  
 **-b**  
 (Facultatif) Spécifie que les commandes du fichier script s'exécutent dans un lot. En cas d'échec d'une commande, l'ensemble du lot est annulé. Certaines commandes ne peuvent pas être traitées par lot ; leur exécution se déroule normalement. Seules les exceptions générées qui ne sont pas gérées par le code du script entraînent une annulation. Si le script gère une exception et si l'exécution se poursuit normalement à partir de `Main`, le traitement est validé. Si vous omettez ce paramètre, les commandes s'exécutent sans créer de lot. Pour plus d’informations, voir [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).  
  
 `-v`*GlobalVar (*  
 (Facultatif) Spécifie les variables globales utilisées dans le script. Si le script utilise des variables globales, vous devez spécifier cet argument. La valeur que vous spécifiez doit être une valeur correcte définie dans le fichier .rss pour les variables globales. Vous devez spécifier une variable globale pour chaque argument **-v** .  
  
 L'argument `-v` est spécifié sur la ligne de commande et est utilisé pour configurer la valeur pour une variable globale définie dans votre script au moment de l'exécution. Par exemple, si votre script contient une variable nommée *parentFolder*, vous pouvez spécifier un nom pour ce dossier sur la ligne de commande :  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 Les variables globales sont créées avec les noms donnés et prennent les valeurs fournies. Par exemple, **-v a =**" `1` " **-v b =**" `2` " produit une variable nommée `a` avec une valeur de " `1` " et une variable **b** avec la valeur " `2` ".  
  
 Les variables globales sont accessibles à n'importe quelle fonction du script. Une barre oblique inverse et un guillemet (** \\ "**) sont interprétés comme des guillemets doubles. Les guillemets sont obligatoires uniquement si la chaîne contient un espace. Les noms de variables doivent être valides pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ; ils doivent commencer par un caractère alphabétique ou un trait de soulignement et contenir des caractères alphabétiques, des chiffres ou des traits de soulignement. Les mots réservés ne peuvent pas être utilisés en tant que noms de variables. Pour plus d’informations sur l’utilisation de variables globales, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **-t**  
 (Facultatif) Génère des messages d'erreur dans le journal des traces. Cet argument ne prend pas de valeur. Pour plus d’informations, consultez [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> Autorisations  
 Pour exécuter l'outil, vous devez avoir l'autorisation de vous connecter à l'instance du serveur de rapports sur laquelle s'exécute le script. Vous pouvez exécuter des scripts pour apporter des modifications à l'ordinateur local ou à un ordinateur distant. Pour apporter des modifications à un serveur de rapports installé sur un ordinateur distant, spécifiez l'ordinateur distant dans l'argument `-s`.  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> Exemples  
 L'exemple ci-dessous montre comment spécifier le fichier de script qui contient un script [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET et les méthodes du service Web que vous souhaitez exécuter.  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
  Pour obtenir un exemple détaillé, consultez [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Pour obtenir des exemples supplémentaires, consultez [Exécuter un fichier de script Reporting Services](run-a-reporting-services-script-file.md).  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer des scripts pour définir des propriétés système, publier des rapports, etc. Les scripts que vous créez peuvent inclure toutes les méthodes de l'API [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations sur les méthodes et les propriétés disponibles, consultez [Report Server Web Service](../report-server-web-service/report-server-web-service.md).  
  
 Le script doit être écrit en code [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET et stocké dans un fichier texte au format Unicode ou UTF-8, avec l’extension de nom de fichier .rss. Vous ne pouvez pas déboguer les scripts à l’aide de l’utilitaire **rs** . Pour déboguer un script, exécutez le code dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!TIP]  
>   Pour obtenir un exemple détaillé, consultez [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter un fichier de script Reporting Services](run-a-reporting-services-script-file.md)   
 [Script de déploiement et tâches administratives](script-deployment-and-administrative-tasks.md)   
 [Script avec l’utilitaire rs.exe et le service Web](script-with-the-rs-exe-utility-and-the-web-service.md)   
 [Utilitaires d’invite de commandes du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)  
  
  
