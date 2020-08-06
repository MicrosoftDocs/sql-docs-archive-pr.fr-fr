---
title: Utilitaire RS.exe (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704832"
---
# <a name="rsconfig-utility-ssrs"></a>Utilitaire rsconfig (SSRS)
  L’utilitaire **rsconfig.exe** chiffre et stocke des valeurs de connexion et de compte dans le fichier RSReportServer.config. Les valeurs chiffrées incluent les informations de connexion à la base de données du serveur de rapports et les valeurs de compte utilisées pour le traitement des rapports sans assistance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Facultatif/obligatoire|Définition|  
|----------|------------------------|----------------|  
|**-?**|facultatif.|Affiche la syntaxe des arguments de Rsconfig.exe.|  
|`-c`|Obligatoire si l'argument `-e` n'est pas utilisé.|Spécifie la chaîne de connexion, les informations d'identification et les valeurs de source de données utilisées pour connecter un serveur de rapports à la base de données du serveur de rapports.<br /><br /> Cet argument ne prend pas de valeur. Cependant, des arguments supplémentaires doivent être spécifiés avec lui pour fournir l'ensemble des valeurs de connexion requises.<br /><br /> Les arguments que vous pouvez spécifier avec `-c` include `-m` , **-s**, `-i` , `-d` , `-a` ,, `-u` `-p` et `-t` .|  
|`-e`|Obligatoire si l'argument `-c` n'est pas utilisé.|Spécifie le compte d'exécution de rapport sans assistance.<br /><br /> Cet argument ne prend pas de valeur. Cependant, vous devez inclure des arguments supplémentaires sur la ligne de commande pour spécifier les valeurs qui sont chiffrées dans le fichier de configuration.<br /><br /> Les arguments que vous pouvez spécifier avec `-e` incluent `-u` et `-p`. Vous pouvez également définir `-t`.|  
|`-m`  *nomd’ordinateur*|Obligatoire si vous configurez une instance distante du serveur de rapports.|Spécifie le nom de l'ordinateur qui héberge le serveur de rapports. Si cet argument est omis, la valeur par défaut est `localhost`.|  
|**-s**  *servername*|Obligatoire.|Spécifie l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports.|  
|`-i`  *InstanceName*|Obligatoire si vous utilisez des instances nommées.|Si vous utilisez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommée pour héberger la base de données du serveur de rapports, cette valeur spécifie l'instance nommée.|  
|`-d`  *DatabaseName*|Obligatoire.|Spécifie le nom de la base de données du serveur de rapports.|  
|`-a`  *authmethod*|Obligatoire.|Détermine la méthode d'authentification utilisée par le serveur de rapports pour la connexion à la base de données du serveur de rapports. Les valeurs valides sont `Windows` ou `SQL` (cet argument ne respecte pas la casse).<br /><br /> `Windows` spécifie que le serveur de rapports utilise l'authentification Windows.<br /><br /> `SQL` spécifie que le serveur de rapports utilise l'authentification SQL Server.|  
|`-u`  *[domaine \\ ] nom d’utilisateur*|Obligatoire avec `-e` Facultatif avec `-c`.|Spécifie un compte d'utilisateur pour la connexion à la base de données du serveur de rapports ou pour le compte sans assistance.<br /><br /> Pour **rsconfig -e**, cet argument est obligatoire. Il doit s’agir d’un compte d’utilisateur de domaine.<br /><br /> Pour **rsconfig-c** et `-a SQL` , cet argument doit spécifier une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.<br /><br /> Pour **rsconfig-c** et `-a Windows` , cet argument peut spécifier un utilisateur de domaine, un compte intégré ou des informations d’identification de compte de service. Si vous spécifiez un compte de domaine, spécifiez *domain* et *username* sous la forme *domaine\nom_utilisateur*. Si vous utilisez un compte prédéfini, cet argument est facultatif. Si vous souhaitez utiliser des informations d'identification de compte de service, omettez cet argument.|  
|`-p`  *mot de passe*|Obligatoire si `-u` est spécifié.|Définit le mot de passe à utiliser avec l'argument *username* . Vous pouvez affecter une valeur vide à cet argument si le compte n'exige pas de mot de passe. Cette valeur respecte la casse pour les comptes de domaine.|  
|`-t`|facultatif.|Envoie des messages d'erreur au journal de suivi. Cet argument ne prend pas de valeur. Pour plus d’informations, consultez [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).|  
  
## <a name="permissions"></a>Autorisations  
 Vous devez être un administrateur local sur l'ordinateur hébergeant le serveur de rapports que vous configurez.  
  
## <a name="file-location"></a>Emplacement du fichier  
 Rsconfig.exe se trouve dans le dossier **\Program Files\Microsoft SQL Server\110\Tools\Binn**. Vous pouvez exécuter l'utilitaire à partir de n'importe quel dossier de votre système de fichiers.  
  
## <a name="remarks"></a>Notes  
 Rsconfig.exe possède deux finalités :  
  
-   Modifier les informations de connexion qu'un serveur de rapports utilise pour la connexion à une base de données de serveur de rapports.  
  
-   Configurer un compte spécial que le serveur de rapports utilise pour la connexion à un serveur de base de données distant lorsque d'autres informations d'identification ne sont pas disponibles.  
  
 Vous pouvez exécuter l’utilitaire**rsconfig** sur une instance locale ou distante de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous ne pouvez pas employer l’utilitaire **rsconfig** pour déchiffrer et afficher des valeurs déjà définies.  
  
 Avant de pouvoir exécuter cet utilitaire, Windows Management Instrumentation (WMI) doit être installé sur l'ordinateur que vous configurez.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent diverses manières d’utiliser **rsconfig**.  
  
#### <a name="specifying-a-domain-user-account"></a>Utilisation d'un compte d'utilisateur de domaine  
 Cet exemple illustre la configuration d'un serveur de rapports pour utiliser un compte d'utilisateur de domaine lors de la connexion à une base de données de serveur de rapports local.  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a>Spécification d'un compte d'utilisateur de base de données SQL Server  
 Cet exemple illustre la configuration d'un serveur de rapports afin d'utiliser une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour se connecter à une base de données du serveur de rapports distante.  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a>Spécification d'un compte prédéfini  
 Cet exemple illustre la configuration d'un serveur de rapports pour utiliser un compte prédéfini lors de la connexion à une base de données de serveur de rapports local. Notez que `-u` n'est pas utilisé. Voici quelques exemples de valeurs de comptes intégrés prises en charge : NT AUTHORITY\SYSTEM pour système local et NT AUTHORITY\NETWORKSERVICE pour service réseau ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] uniquement).  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a>Spécification d'un compte de service  
 Cet exemple illustre la configuration d'un serveur de rapports pour l'utilisation du compte du service Windows Report Server et le compte du service Web lors de la connexion à une base de données de serveur de rapports local. Notez que `-u` n'est pas utilisé et qu'aucune information de compte n'est spécifiée. Lorsque vous éliminez des valeurs de compte à partir de la commande, l’utilitaire **rsconfig** emploie une sécurité intégrée et le compte de service sous lequel chaque service s’exécute.  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a>Spécification du compte sans assistance sur un serveur local  
 Cet exemple montre comment configurer le compte utilisé pour l'exécution d'un rapport sans assistance pour les rapports qui ne passent pas d'informations d'identification à la source de données externe. Le compte doit être un compte de domaine Windows. Vous ne pouvez pas spécifier une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le nom d'utilisateur et le mot de passe. Le compte est configuré sur une instance locale du serveur de rapports. Les messages d'erreur sont capturés dans les journaux de suivi dans le dossier ReportingServices\LogFiles.  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a>Spécification du compte sans assistance sur un serveur distant  
 Cet exemple illustre la configuration du compte sur une instance distante du serveur de rapports de même version que Rsconfig.exe (par exemple, le serveur de rapports et Rsconfig.exe sont tous deux de version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2). Les informations des messages d'erreur sont capturées dans les journaux de suivi sur le serveur distant.  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Configurer le compte d’exécution sans assistance &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Serveur de rapports Reporting Services &#40;mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md)   
 [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Fichiers de configuration de Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Utilitaires de ligne de commande du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)   
 [Fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
