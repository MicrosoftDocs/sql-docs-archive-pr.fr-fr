---
title: Application sqlservr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], sqlservr
- command prompt [SQL Server], pausing/resuming instance of SQL Server
- starting instance of SQL Server
- command prompt [SQL Server], continuing instance of SQL Server
- sqlservr utility
- pausing instance of SQL Server
- stopping instance of SQL Server
- resuming SQL Server
- command prompt [SQL Server], stopping instance of SQL Server
- command prompt [SQL Server], starting instance of SQL Server
- continuing instance of SQL Server
ms.assetid: 60e8ef0a-0851-41cf-a6d8-cca1e04cbcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48dcf9d22686aa87f267304fe844a1989fe4e24c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703575"
---
# <a name="sqlservr-application"></a>Application sqlservr
  L’application **sqlservr** démarre, arrête, suspend et poursuit une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir d’une invite de commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      sqlservr [-sinstance_name] [-c] [-dmaster_path] [-f]   
     [-eerror_log_path] [-lmaster_log_path] [-m]  
     [-n] [-Ttrace#] [-v] [-x] [-gnumber]  
```  
  
## <a name="arguments"></a>Arguments  
 **-s** _nom_instance_  
 Spécifie l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle établir une connexion. Si aucune instance nommée n’est spécifiée, **sqlservr** démarre l’instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vous devez utiliser l’application **sqlservr** dans le répertoire approprié de cette instance. Si vous utilisez l’instance par défaut, exécutez **sqlservr** depuis le répertoire \MSSQL\Binn. Si vous utilisez l’instance nommée, exécutez **sqlservr** depuis le répertoire \MSSQL$*nom_instance*\Binn.  
  
 **-c**  
 Indique qu'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est démarrée indépendamment du Gestionnaire de contrôle des services Windows. En cas de démarrage de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir d’une invite de commandes, cette option réduit le délai de démarrage de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Avec cette option, vous ne pouvez pas arrêter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en utilisant le Gestionnaire des services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou la commande **net stop** . De plus, si vous vous déconnectez de l’ordinateur, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est arrêté.  
  
 **-d** _chemin_master_  
 Indique le chemin complet du fichier de base de données **master** . Il n’y a pas d’espace entre **-d** et *chemin_master*. Si vous ne spécifiez pas cette option, les paramètres du Registre existant sont utilisés.  
  
 **-f**  
 Démarre une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec une configuration minimale. Cette option est utile lorsqu'une valeur de configuration définie (espace mémoire insuffisant, par exemple) a empêché le serveur de démarrer.  
  
 **-e** _error_log_path_  
 Indique le chemin d'accès complet au fichier journal des erreurs. S’il n’est pas spécifié, l’emplacement par défaut est *\<Drive>* : \Program Files\Microsoft SQL Server\Mssql\Log\Errorlog pour l’instance par défaut et *\<Drive>* : \Program Files\Microsoft SQL Server\MSSQL $*instance_name*\Log\Errorlog pour une instance nommée. Il n’existe aucun espace entre **-e** et *chemin_du_journal_des_erreurs*.  
  
 **-l** _master_log_path_  
 Indique le chemin complet du fichier journal des transactions de la base de données **master** . Il n’existe aucun espace entre **-l** et *chemin_du_journal_master*.  
  
 **-m**  
 Spécifie le démarrage d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en mode mono-utilisateur. Dans ce mode, un seul utilisateur peut se connecter au démarrage de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Le mécanisme CHECKPOINT (qui garantit le transfert régulier des transactions terminées du cache disque vers l'unité de bases de données) n'est pas lancé. Cette option est généralement utilisée en cas de problème au niveau de bases de données système requérant une réparation. Active l’option **sp_configure allow updates**. Par défaut, l'option **allow updates** est désactivée.  
  
 **-n**  
 Permet de démarrer une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si le paramètre **-s** n’est pas spécifié, l’instance par défaut tente de démarrer. Vous devez accéder au répertoire BINN de l’instance, dans l’invite de commandes, avant de démarrer **sqlservr.exe**. Par exemple, si Instance1 doit utiliser \mssql$Instance1 pour ses fichiers binaires, l’utilisateur doit être dans le répertoire \mssql$Instance1\binn pour démarrer **sqlservr.exe -s instance1**. Si vous démarrez une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec l’option **-n** , il est également recommandé d’utiliser l’option **-e** , sinon les événements [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne sont pas consignés.  
  
 **-T** _trace #_  
 Indique qu’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit être démarrée avec un indicateur de trace spécifique (*trace#* ) en vigueur. Les indicateurs de trace permettent de démarrer le serveur avec un comportement non standard. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
> [!IMPORTANT]  
>  Lorsque vous spécifiez un indicateur de trace, utilisez **-T** pour transmettre le numéro d’indicateur de trace. **accepte un t minuscule (** -t [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]), mais **-t** définit d’autres indicateurs de trace internes requis par les ingénieurs du support technique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **-v**  
 Affiche le numéro de version du serveur.  
  
 **-x**  
 Désactive le suivi des statistiques temps UC et taux d'accès au cache. Optimise les performances au maximum.  
  
 **g -** _mémoire_à_réserver_  
 Spécifie un nombre entier de mégaoctets (Mo) de mémoire que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] laisse disponible pour des allocations de mémoire à l'intérieur du processus de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , mais hors du pool de mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . La mémoire en dehors du pool de mémoire est la zone utilisée par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour le chargement d'éléments tels que les fichiers `.dll` des procédures stockées étendues, les fournisseurs OLE DB référencés par les requêtes distribuées et les objets automation référencés dans les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] . La valeur par défaut est 256 Mo.  
  
 Cette option peut faciliter l'ajustement de l'allocation de mémoire, mais uniquement lorsque la mémoire physique dépasse la limite configurée définie par le système d'exploitation sur la mémoire virtuelle disponible pour les applications. L'utilisation de cette option peut s'avérer appropriée avec des configurations de mémoire importantes, dans lesquelles les besoins en utilisation de la mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne sont pas standard et l'espace d'adressage virtuel du processus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est utilisé dans son intégralité. L'utilisation incorrecte de cette option peut mener à des situations dans lesquelles une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne démarre pas ou rencontre des erreurs lors de l'exécution.  
  
 Utilisez la valeur par défaut du paramètre **-g** , sauf si l’un des avertissements suivants figure dans le journal des erreurs de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
-   « Octets virtuels alloués ayant échoué : FAIL_VIRTUAL_RESERVE \<size> »  
  
-   « Octets virtuels alloués ayant échoué : FAIL_VIRTUAL_COMMIT \<size> »  
  
 Ces messages peuvent indiquer que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tente de libérer des parties du pool de la mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] afin de trouver de l'espace pour des éléments tels que les fichiers .dll de procédure stockée étendue ou des objets Automation. Dans ce cas, envisagez d’augmenter la quantité de mémoire réservée par le commutateur **-g**``.  
  
 L'utilisation d'une valeur inférieure à celle par défaut augmente la quantité de mémoire disponible dans le pool de mémoires tampons ou les piles de threads ; cela permet de profiter de l'amélioration des performances pour les charges de travail qui ont recours de manière intensive à la mémoire dans les systèmes qui n'utilisent pas de nombreuses procédures stockées étendues, requêtes distribuées ou objets Automation.  
  
## <a name="remarks"></a>Notes  
 Dans la plupart des cas, le programme sqlservr.exe est uniquement utilisé pour le dépannage ou pour une maintenance majeure. Lorsque [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est démarré à partir de l’invite de commandes avec sqlservr.exe, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne démarre pas en tant que service et vous ne pouvez donc pas arrêter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec des commandes **net** . Les utilisateurs peuvent se connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais les outils [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] montrent l'état du service et le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] indique correctement que le service est arrêté. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut se connecter au serveur, mais indique également que le service est arrêté.  
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité  
 Le paramètre **-h**  n’est pas pris en charge dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Ce paramètre a été utilisé dans les versions antérieures des instances 32 bits de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour réserver l'espace d'adressage de mémoire virtuelle pour les métadonnées d'ajout de mémoire à chaud lorsque AWE est activé. Pour plus d’informations, consultez [Fonctionnalités SQL Server supprimées dans SQL Server 2014](../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Options de démarrage du service moteur de base de données](../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  
