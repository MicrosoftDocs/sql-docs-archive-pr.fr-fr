---
title: Exécution du conseiller de mise à niveau (invite de commandes) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87600476"
---
# <a name="running-upgrade-advisor-command-prompt"></a>Exécution du Conseiller de mise à niveau (Invite de commandes)
  Utilisez l’utilitaire **UpgradeAdvisorWizardCmd** pour exécuter le conseiller de mise à niveau à partir de l’invite de commandes. Vous pouvez choisir de recevoir les résultats dans le format XML ou dans un fichier dont les valeurs sont séparées par des virgules.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a>Arguments  
 **-?**  
 Affiche la syntaxe de la commande.  
  
 **-CONFIGFILE nom de** _fichier_  
 Nom de chemin d’accès et nom de fichier d’un fichier XML qui contient les paramètres à utiliser lors de l’exécution de l’utilitaire **UpgradeAdvisorWizardCmd** .  
  
 *<server_info>*  
 Spécifie l'ordinateur et l'instance à analyser. Servez-vous de ces options si vous n'utilisez pas de fichier de configuration.  
  
 *<server_info>* peut être n’importe quelle combinaison des quatre arguments suivants :  
  
 **-** _SERVER_NAME_ serveur  
 Spécifie le nom de l'ordinateur à analyser. Il peut s'agir de l'ordinateur local , qui correspond à la valeur par défaut, ou d'un ordinateur distant.  
  
 **-Instance** _instance_name_  
 Spécifie le nom de l'instance à analyser. Il n’y a pas de valeur par défaut. Si vous ne spécifiez pas ce paramètre, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’est pas analysé. La valeur d'une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est MSSQLSERVER. Pour une instance nommée, utilisez le nom de l'instance.  
  
 **-ASInstance**  _AS_instance_name_  
 Spécifie le nom de l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à analyser. Il n’y a pas de valeur par défaut. Si vous ne spécifiez pas cette valeur, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n'est pas analysé. La valeur d'une instance par défaut d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est MSSQLServerOLAPService. Pour une instance nommée, utilisez le nom de l'instance.  
  
 **-RSInstance**  _RS_instance_name_  
 Spécifie le nom de l'instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à analyser. Il n’y a pas de valeur par défaut. Si vous ne spécifiez pas cette valeur, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas analysé. La valeur d'une instance par défaut de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est ReportServer. Pour une instance nommée, utilisez le nom de l'instance.  
  
 **-SqlUser** _login_id_  
 Si vous recourez à l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette valeur est le compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que le Conseiller de mise à niveau utilise pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous ne spécifiez pas de compte de connexion, l'authentification Windows permet de se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **-Sqlpassword** _mot de passe_  
 Si vous utilisez l’argument **-SQLUser** , utilisez cet argument pour spécifier le mot de passe de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion.  
  
 **-CSV**  
 Indique que les résultats doivent être fournis sous forme de valeurs séparées par des virgules dans un fichier .csv en plus du format XML standard. Les résultats sont écrits dans le dossier Mes documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports.  
  
## <a name="return-values"></a>Valeurs de retour  
 Le tableau suivant montre les valeurs retournées par **UpgradeAdvisorWizardCmd** .  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Analyse réussie, aucun problème de mise à niveau détecté.|  
|entier positif|Analyse réussie, problèmes de mise à niveau détectés.|  
|entier négatif|Échec de l'analyse.|  
  
## <a name="remarks"></a>Notes  
 Toutes les informations nécessaires à l'exécution de l'analyse, autres que les noms d'utilisateurs et les mots de passe pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], peuvent être fournies dans un fichier de configuration XML. Ce fichier de configuration XML est documenté dans le modèle. Si vous n'utilisez pas de fichier de configuration, vous pouvez analyser tous les composants installés dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de paramètres par défaut en spécifiant des noms d'ordinateurs et des noms d'instances. Consultez le tableau « Description des éléments » plus loin dans cette rubrique pour obtenir une description des paramètres du fichier de configuration par défaut.  
  
## <a name="configuration-file-template"></a>Modèle de fichier de configuration  
 Servez-vous du code XML suivant comme modèle pour créer vos propres fichiers de configuration. Vous pouvez modifier le modèle en fonction des besoins de votre organisation.  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a>Descriptions des éléments  
  
|Tag|Définition|Occurrence|  
|---------|----------------|----------------|  
|`Configuration`|Élément parent du fichier de configuration du Conseiller de mise à niveau.|Obligatoire une fois par fichier de configuration.|  
|`Server`|Nom du serveur à analyser.|Facultatif une fois par fichier de configuration. La valeur par défaut est l'ordinateur local.|  
|`Instance`|Nom de l' [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance à analyser.|Facultatif une fois par fichier de configuration. La valeur par défaut est l'instance par défaut.<br /><br /> Requis une fois par fichier de configuration, si un élément [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou `IntegrationServices` est présent sur le serveur.|  
|`Components`|Contient des éléments qui spécifient les composants à analyser.|Obligatoire une fois par fichier de configuration.|  
|`SQLServer`|Contient les paramètres d’analyse d’une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .|Facultatif une fois par fichier de configuration. S'il n'est pas spécifié, les bases de données [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne sont pas analysées.|  
|`Databases` de l'élément `SQLServer`|Contient une liste de bases de données à analyser.|Facultatif une fois par `SQLServer` élément. Si cet élément n'est pas présent, toutes les bases de données de l'instance sont analysées.|  
|`Database` de l'élément `SQLServer`|Spécifie le nom d'une base de données à analyser.|Obligatoire une ou plusieurs fois si l'élément `Databases` est présent. Si un élément `Database` contient la valeur "*", toutes les bases de données de l'instance sont analysées. Il n’y a pas de valeur par défaut.|  
|`TraceFiles`|Contient une liste de fichiers de trace à analyser.|Facultatif une fois par `SQLServer` élément.|  
|`TraceFile`|Spécifie le chemin d'accès et le nom d'un fichier de trace à analyser.|Obligatoire une ou plusieurs fois si l'élément `TraceFiles` est présent. Il n’y a pas de valeur par défaut.|  
|`BatchFiles`|Contient une liste de fichiers de commandes à analyser.|Facultatif une fois par `SQLServer` élément.|  
|`BatchFile`|Spécifie un fichier de commandes à analyser. Peut concerner plusieurs fichiers.|Obligatoire une ou plusieurs fois si l'élément `BatchFiles` est présent. Il n’y a pas de valeur par défaut.|  
|`BatchSeparator`|Spécifie le délimiteur de lot utilisé dans les fichiers de commandes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Facultatif une fois par `SQLServer` élément. La valeur par défaut est GO.|  
|`AnalysisServices`|Contient les paramètres d'analyse d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|Facultatif une fois par fichier de configuration. S'il n'est pas spécifié, les bases de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne sont pas analysées.|  
|`ASInstance`|Spécifie le nom d’une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|Obligatoire une fois par élément `AnalysisServices`. Il n’y a pas de valeur par défaut.|  
|`Databases` de l'élément `Analysis Services`|Contient une liste de bases de données à analyser.|Facultatif une fois par `AnalysisServices` élément. Si cet élément n'est pas présent, toutes les bases de données de l'instance sont analysées.|  
|`Database` de l'élément `AnalysisServices`|Spécifie le nom d'une base de données à analyser.|Obligatoire une ou plusieurs fois si l'élément `Databases` est présent. Si un élément `Database` contient la valeur "*", toutes les bases de données de l'instance sont analysées. Il n’y a pas de valeur par défaut.|  
|`ReportingServices`|Spécifie d'exécuter l'analyse sur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Facultatif une fois par fichier de configuration. S'il n'est pas spécifié, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est pas analysé.|  
|`RSInstance`|Spécifie le nom d’une instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Obligatoire une fois par élément `ReportingServices`. Il n’y a pas de valeur par défaut.|  
|`IntegrationServices`|Contient les paramètres d'analyse d'[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Facultatif une fois par fichier de configuration. S'il n'est pas spécifié, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est pas analysé.|  
|`PackagePath`|Spécifie le chemin d'accès d'un jeu de packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|Facultatif une fois par `IntegrationServices` élément. Si cet élément n’est pas présent, l’analyse se produit sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance et aucun package stocké de manière externe n’est analysé. Il n’y a pas de valeur par défaut.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a>R. Exécuter le Conseiller de mise à niveau à l'aide d'un fichier de configuration  
 L'exemple suivant indique comment exécuter le Conseiller de mise à niveau à partir de l'invite de commandes en utilisant un fichier de configuration qui spécifie les éléments à analyser. Cet exemple utilise l'authentification Windows pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a>B. Exécuter le Conseiller de mise à niveau à l'aide des paramètres de configuration par défaut  
 L'exemple suivant indique comment exécuter le Conseiller de mise à niveau à partir de l'invite de commandes en utilisant des paramètres de configuration par défaut et l'authentification Windows.  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a>C. Exécuter le Conseiller de mise à niveau à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 L'exemple suivant indique comment exécuter le Conseiller de mise à niveau à partir de l'invite de commandes en utilisant un fichier de configuration. Cet exemple spécifie un nom d'utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de mise à niveau](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Utilisation du conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Exécution du conseiller de mise à niveau &#40;de l’interface utilisateur&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
