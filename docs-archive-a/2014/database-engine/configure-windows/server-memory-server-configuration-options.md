---
title: Options de configuration de la mémoire du serveur | Microsoft Docs
ms.custom: ''
ms.date: 07/22/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Virtual Memory Manager
- max server memory option
- virtual memory [SQL Server]
- VMM
- server memory options [SQL Server]
- servers [SQL Server], memory
- buffer pools [SQL Server]
- min server memory option
- manual memory options [SQL Server]
- memory [SQL Server], servers
ms.assetid: 29ce373e-18f8-46ff-aea6-15bbb10fb9c2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a4bb354b78d25c6667e9ff67c6eda697a0369e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706739"
---
# <a name="server-memory-configuration-options"></a>Options de configuration de la mémoire du serveur
  Utilisez les deux options de mémoire du serveur, **min server memory** et **max server memory**, pour reconfigurer la quantité de mémoire (en mégaoctets) gérée par le Gestionnaire de mémoire de SQL Server pour un processus SQL Server utilisé par une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le paramètre par défaut de l'option **min server memory** est 0 et le paramètre par défaut de l'option **max server memory** est 2 147 483 647 Mo. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut modifier dynamiquement sa configuration mémoire en fonction des ressources système disponibles.  
  
> [!NOTE]  
> Si vous donnez à **max server memory** sa valeur minimale, vous allez gravement limiter les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , jusqu'à l'empêcher même de démarrer. Si vous ne pouvez plus démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] après avoir changé cette option, démarrez-le au moyen de l’option de démarrage **-f** et restaurez **max server memory** à sa valeur antérieure. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md).  
  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise dynamiquement la mémoire, il interroge régulièrement le système afin de déterminer la mémoire physique disponible. La conservation de cette mémoire libre empêche le système d'exploitation de paginer. S'il y a moins de mémoire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en libère pour le système d'exploitation. S’il y a plus de mémoire disponible, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut allouer davantage de mémoire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’ajoute de la mémoire que lorsque sa charge de travail en requiert davantage. Un serveur au repos n’augmente pas la taille de son espace d’adressage virtuel.  
  
 Pour une requête qui retourne la mémoire utilisée actuellement, consultez l'exemple B. L’option**max server memory** contrôle l’allocation de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , y compris le pool de mémoires tampons, la mémoire de compilation, tous les caches, les allocations de mémoire qe, la mémoire du gestionnaire de verrous et la mémoire clr (essentiellement les régisseurs de mémoires qui se trouvent dans **sys.dm_os_memory_clerks**). La mémoire pour les piles de threads, les segments de mémoire, les fournisseurs de serveurs liés autres que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que toute mémoire allouée par une DLL non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ne sont pas contrôlées par max server memory.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]utilise l’API de notification de mémoire **QueryMemoryResourceNotification** pour déterminer le moment où le gestionnaire de mémoire SQL Server peut allouer de la mémoire et libérer de la mémoire.  
  
 Il est recommandé de permettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'utiliser dynamiquement la mémoire ; cependant, vous pouvez configurer manuellement les options de mémoire et limiter la mémoire à laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accéder. Avant de définir la mémoire allouée à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], déterminez la valeur adaptée pour la mémoire : pour cela, vous devez soustraire de la mémoire physique totale la mémoire requise par le système d'exploitation et par toute autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , (ainsi que par d'autres systèmes si l'ordinateur n'est pas totalement dédié à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Cette différence représente la mémoire maximale que vous pouvez allouer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="setting-the-memory-options-manually"></a>Paramétrage manuel des options de mémoire  
Vous pouvez définir les options de serveur **min server memory** et **max server memory** pour couvrir une plage de valeurs de mémoire. Cette méthode est utile pour les administrateurs système ou de bases de données qui souhaitent configurer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en accord avec la mémoire exigée par d’autres applications ou d’autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s’exécutent sur le même hôte.

> [!NOTE]
> **min server memory** et **max server memory** sont des options avancées. Si vous utilisez la procédure stockée système **sp_configure** pour changer ces paramètres, vous ne pouvez les modifier que si l’option **show advanced options** a la valeur 1. Ces paramètres entrent immédiatement en vigueur, sans redémarrage du serveur.  
  
<a name="min_server_memory"></a> Utilisez **min_server_memory** pour garantir une quantité minimale de mémoire accessible au Gestionnaire de mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'alloue pas immédiatement la mémoire spécifiée dans **min server memory** au démarrage. Néanmoins, lorsque l’utilisation de la mémoire atteint cette valeur en raison de la charge client, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut libérer de la mémoire à moins que la valeur **min server memory** ne soit réduite. Par exemple, si plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent exister simultanément sur le même ordinateur hôte, définissez min_server_memory plutôt que max_server_memory afin de réserver de la mémoire pour une instance. La définition d’une valeur min_server_memory est essentielle dans un environnement virtualisé. Elle permet en effet de garantir que la sollicitation de la mémoire de l’hôte sous-jacent ne tente pas de libérer, dans le pool de tampons d’une machine virtuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] invitée, une quantité de mémoire supérieure à celle nécessaire pour obtenir des performances acceptables.
 
> [!NOTE]  
> Il n’est pas garanti que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alloue la mémoire spécifiée dans **min server memory**. Si la charge sur le serveur ne nécessite jamais d’allouer la mémoire spécifiée dans **min server memory**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute alors avec moins de mémoire.  
  
<a name="max_server_memory"></a> Utilisez **max_server_memory** pour que le système d’exploitation ne fasse pas l’objet d’une sollicitation de la mémoire préjudiciable. Pour définir la configuration de la mémoire maximale du serveur, surveillez la consommation globale du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de déterminer les besoins en mémoire. Pour obtenir des résultats plus précis pour une instance unique :
 -  Réservez 1 à 4 Go de la mémoire totale du système d’exploitation au système d’exploitation lui-même.
 -  Ensuite, soustrayez l’équivalent des allocations de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potentielles en dehors du contrôle **max server memory**, à savoir la **_taille de la pile <sup>1</sup> \*, le nombre maximal calculé de threads de worker <sup>2</sup> et le paramètre de démarrage -g <sup>3</sup>_** (ou 256 Mo par défaut si *-g* n’est pas défini). Il doit rester le paramètre max_server_memory pour une installation d’instance unique.
 
<sup>1</sup> Pour plus d’informations sur les tailles de piles de threads par architecture, consultez le [guide d’architecture de gestion de la mémoire](https://docs.microsoft.com/sql/relational-databases/memory-management-architecture-guide#stacksizes).

<sup>2</sup> Pour plus d’informations sur les threads de worker par défaut calculés pour un nombre donné d’UC avec affinité dans l’hôte actif, consultez la page [Configurer l’option de configuration du serveur max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md) dans la documentation.

<sup>3</sup> Pour plus d’informations sur le paramètre de démarrage *-g*, consultez la page [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md?view=sql-server-2014) dans la documentation. Aplicable uniquement à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 32 bits (de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] à [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).

|Type de système d'exploitation|Quantité de mémoire minimale autorisée pour **Max Server Memory**|  
|-------------|----------------------------------------------------------------|  
|32 bits|64 Mo|  
|64 bits|128 Mo| 

## <a name="how-to-configure-memory-options-using-sql-server-management-studio"></a>Comment configurer les options de mémoire à l'aide de SQL Server Management Studio  
 Utilisez les deux options de mémoire du serveur, **min server memory** et **max server memory**, pour reconfigurer la quantité de mémoire (en mégaoctets) gérée par le Gestionnaire de mémoire de SQL Server pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut modifier dynamiquement sa configuration mémoire en fonction des ressources système disponibles.  
  
### <a name="procedure-for-configuring-a-fixed-amount-of-memory"></a>Procédure de configuration d'une quantité de mémoire fixe  
 **Pour définir une quantité fixe de mémoire :**  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Sous **Options mémoire du serveur**, entrez les quantités souhaitées pour **Mémoire minimale du serveur** et **Mémoire maximale du serveur**.  
  
     Utilisez les paramètres par défaut pour autoriser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à modifier ses besoins de mémoire de façon dynamique en fonction des ressources système disponibles. La valeur par défaut de l’option **min Server Memory** est 0 et la valeur par défaut de l’option **max server memory** est de 2147483647 mégaoctets (Mo).  
  
## <a name="maximize-data-throughput-for-network-applications"></a>Obtenir le débit de données maximal pour les applications réseau  
 Pour optimiser l'utilisation de la mémoire système pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez limiter la quantité de mémoire utilisée par le système pour la mise en cache des fichiers. Pour limiter le cache du système de fichiers, veillez à désactiver **Maximiser le débit des données pour le partage de fichiers** . Vous pouvez spécifier le plus petit cache du système de fichiers en sélectionnant **Minimiser la mémoire utilisée** ou **Équilibrer**.  
  
#### <a name="to-check-the-current-setting-on-your-operating-system"></a>Pour connaître la configuration actuelle de votre système d'exploitation  
  
1.  Cliquez sur **Démarrer**, sur **Panneau de configuration**, double-cliquez sur **Connexions réseau**, puis sur **Connexion au réseau local**.  
  
2.  Sous l'onglet **Général** , cliquez sur **Propriétés**. Sélectionnez **Partage de fichiers et d'imprimantes pour les réseaux Microsoft**et cliquez sur **Propriétés**.  
  
3.  Si l'option **Maximiser le débit des données pour les applications réseau** est sélectionnée, choisissez une autre option et cliquez sur **OK**. Fermez ensuite les boîtes de dialogue restantes.  
  
## <a name="lock-pages-in-memory"></a>Verrouiller les pages en mémoire  
 Cette stratégie Windows détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque. Le verrouillage des pages en mémoire peut permettre de conserver sa réactivité au serveur lors de la pagination de la mémoire sur disque. L’option SQL Server **verrouiller les pages en mémoire** a la valeur on dans les instances 32 bits et 64 bits de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition et supérieure lorsque le compte avec les privilèges pour exécuter sqlservr.exe a reçu le droit d’utilisateur Windows « pages verrouillées en mémoire » (LPIM). Dans les versions antérieures de SQL Server, la définition de l'option de verrouillage des pages pour une instance 32 bits de SQL Server exige que le compte avec les privilèges nécessaires pour exécuter sqlservr.exe ait le droit d'utilisateur LPIM et que l'option de configuration « awe_enabled » ait la valeur ON.  
  
 Pour désactiver l’option **verrouiller les pages en mémoire** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , supprimez le droit d’utilisateur « pages verrouillées en mémoire » pour le compte de démarrage SQL Server.  
  
### <a name="to-disable-lock-pages-in-memory"></a>Pour désactiver Verrouiller les pages en mémoire  
 **Pour désactiver l’option verrouiller les pages en mémoire :**  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans la zone **ouvrir** , tapez `gpedit.msc` .  
  
     La boîte de dialogue **Stratégie de groupe** s'affiche.  
  
2.  Sur la console **Stratégie de groupe** , développez **Configuration de l'ordinateur**, puis **Paramètres Windows**.  
  
3.  Développez **Paramètres de sécurité**, puis **Stratégies locales**.  
  
4.  Sélectionnez le dossier **Attribution des droits utilisateur** .  
  
     Les stratégies s'affichent dans le volet Détails.  
  
5.  Dans le volet, double-cliquez sur **Verrouiller les pages en mémoire**.  
  
6.  Dans la boîte de dialogue **Paramètre de stratégie de sécurité locale** , sélectionnez le compte avec les privilèges nécessaires pour exécuter sqlservr.exe et cliquez sur **Supprimer**.  
  
## <a name="virtual-memory-manager"></a>Gestionnaire de mémoire virtuelle  
 Les systèmes d'exploitation 32 bits permettent d'accéder à un espace d'adressage virtuel de 4 Go. 2 Go de mémoire virtuelle sont alloués en privé à chaque processus et disponibles pour les applications. 2 Go sont réservés au système d'exploitation. Toutes les éditions des systèmes d'exploitation comportent un commutateur qui permet aux applications d'accéder à 3 Go d'espace d'adressage virtuel, ce qui limite la mémoire disponible pour le système d'exploitation à 1 Go. Pour plus d'informations sur l'utilisation de la configuration de la mémoire avec le commutateur, consultez la documentation Windows sur la technologie 4GT (4-gigabyte tuning). Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 32 bits s'exécute sur un système d'exploitation 64 bits, l'utilisateur a accès à l'intégralité des 4 Go pour son espace d'adressage virtuel.  
  
 Les zones d'espace d'adressage validées sont mappées à la mémoire physique disponible par le Gestionnaire de mémoire virtuelle Windows (VMM).  
  
 Pour plus d'informations sur la taille de mémoire physique prise en charge par les divers systèmes d'exploitation, consultez la documentation Windows « Limites de la mémoire selon les versions de Windows ».  
  
 Les systèmes de mémoire virtuelle autorisent le surengagement de la mémoire physique, de sorte que le rapport entre la mémoire virtuelle et la mémoire physique peut être supérieur à 1:1. Il est alors possible d'exécuter des programmes plus volumineux sur des ordinateurs offrant diverses configurations de la mémoire physique. Toutefois, dans la plupart des cas, l'utilisation d'une quantité de mémoire virtuelle nettement plus importante que les plages de travail moyennes combinées de tous les processus peut entraîner une détérioration des performances.  
  
 **min server memory** et **max server memory** sont des options avancées. Si vous utilisez la procédure stockée système **sp_configure** pour changer ces paramètres, vous ne pouvez les modifier que si l’option **show advanced options** a la valeur 1. Ces paramètres entrent immédiatement en vigueur, sans redémarrage du serveur.  
  
## <a name="running-multiple-instances-of-sql-server"></a>Exécution de plusieurs instances SQL Server  
 Lorsque vous exécutez plusieurs instances de [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous avez le choix entre trois approches pour gérer la mémoire :  
  
-   Choisir **max server memory** pour contrôler l'utilisation de la mémoire. Définir les valeurs maximales pour chaque instance, en veillant à ce que le total alloué ne soit pas supérieur à la mémoire physique totale de votre ordinateur. Il se peut que vous souhaitiez attribuer à chaque instance une mémoire proportionnelle à la charge ou à la taille de base de données prévue. Cette solution présente l'avantage qu'au démarrage des nouveaux processus ou des nouvelles instances, ils pourront accéder immédiatement à la mémoire libre. En revanche, cette solution présente l'inconvénient que, si toutes les instances ne sont pas en cours d'exécution, aucune d'entre elles ne pourra utiliser la mémoire libre restante.  
  
-   Choisir **min server memory** pour contrôler l'utilisation de la mémoire. Définissez les valeurs minimales pour chaque instance, de telle sorte que leur somme soit inférieure de 1 à 2 Go à la mémoire physique totale de votre machine. Une fois encore, vous pouvez établir ces valeurs minimales de façon proportionnelle à la charge prévue de cette instance. Cette solution présente l'avantage que si toutes les instances ne sont pas en cours d'exécution au même instant, celles qui le sont peuvent utiliser la mémoire libre restante. Elle est également utile quand un autre processus gourmand en mémoire est présent sur l'ordinateur, car elle garantit que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bénéficie au moins d'une quantité de mémoire acceptable. Le désagrément est que, lorsqu'une nouvelle instance (ou un autre processus) démarre, il se peut que les instances en cours d'exécution mettent un certain temps à libérer de la mémoire, notamment si elles doivent à cette fin réécrire les pages modifiées sur leurs bases de données.  
  
-   Ne rien faire (déconseillé). Les premières instances présentées avec une charge de travail tendent à allouer la totalité de la mémoire. Les instances inactives ou les instances ayant démarré ultérieurement peuvent finir par ne disposer que d'une quantité de mémoire minime. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'effectue aucune tentative pour équilibrer l'utilisation de la mémoire entre les instances. Cependant, toutes les instances répondent aux signaux de Windows Notification Memory pour ajuster la taille de leur occupation mémoire. Windows n'équilibre pas la mémoire entre les applications avec l'API Memory Notification. Il fournit simplement un commentaire global quant à la disponibilité de la mémoire sur le système.  
  
 Comme vous pouvez modifier ces paramètres sans redémarrer les instances, vous pouvez sans peine procéder à des essais pour trouver les valeurs qui conviennent le mieux à votre modèle d'utilisation.  
  
## <a name="providing-the-maximum-amount-of-memory-to-sql-server"></a>Apport de la quantité maximale de mémoire à SQL Server  
  
||32 bits|64 bits|  
|-|-------------|-------------|  
|Mémoire conventionnelle|Jusqu'à la limite d'espace d'adressage virtuel de processus dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> 2 Go<br /><br /> 3 Go avec le paramètre de démarrage **/3GB** *<br /><br /> 4 Go sur WOW64\*\*|Jusqu'à la limite d'espace d'adressage virtuel de processus dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> 8 To sur l'architecture x64|  
  
 ***/3GB** est un paramètre de démarrage du système d’exploitation. Pour plus d’informations, consultez [MSDN Library](https://go.microsoft.com/fwlink/?LinkID=10257&clcid=0x409).  
  
 * * WOW64 (Windows sur Windows 64) est un mode dans lequel 32 bits [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute sur un système d’exploitation 64 bits. Pour plus d’informations, consultez [MSDN Library](https://go.microsoft.com/fwlink/?LinkID=10257&clcid=0x409).  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-a"></a>Exemple A  
 L'exemple suivant affecte la valeur 4 Go à l'option `max server memory` .  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'max server memory', 4096;  
GO  
RECONFIGURE;  
GO  
```  
  
### <a name="example-b-determining-current-memory-allocation"></a>Exemple B. Détermination de l’allocation de mémoire actuelle  
 La requête suivante retourne des informations sur la mémoire allouée actuellement.  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
