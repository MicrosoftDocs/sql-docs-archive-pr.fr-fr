---
title: Installation d’un cluster de basculement SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c0e75a7c-85c5-423c-a218-77247bf071aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d11b892bc3ae3dccfbab5bef01feca325056945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605037"
---
# <a name="sql-server-failover-cluster-installation"></a>Installation d'un cluster de basculement SQL Server
  Pour installer un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vous devez créer et configurer une instance de cluster de basculement en exécutant le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="installing-a-failover-cluster"></a>Installation d'un cluster de basculement  
 Pour installer un cluster de basculement, vous devez utiliser un compte de domaine avec des droits d'administrateur local pour vous connecter en tant que service et pour agir dans le cadre du système d'exploitation sur tous les nœuds du cluster de basculement. Pour installer un cluster de basculement à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , procédez comme suit :  
  
1.  Pour installer, configurer et gérer un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , utilisez le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    -   Identifiez les informations dont vous aurez besoin pour créer votre instance de cluster de basculement (par exemple, une ressource disque de cluster, des adresses IP et un nom réseau) et les nœuds disponibles pour le basculement. Pour plus d'informations :  
  
        -   [Avant l'installation du clustering de basculement](before-installing-failover-clustering.md)  
  
        -   [Considérations sur la sécurité pour une installation SQL Server](../../install/security-considerations-for-a-sql-server-installation.md)  
  
    -   Les étapes de configuration doivent se dérouler avant l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; pour cela, utilisez l'Administrateur de cluster Windows. Vous avez besoin d'un groupe WSFC pour chaque instance de cluster de basculement que vous souhaitez configurer.  
  
    -   Vous devez vous assurer que votre système satisfait la configuration minimale requise. Pour plus d’informations sur la configuration requise pour un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , consultez [Avant l’installation du clustering de basculement](before-installing-failover-clustering.md).  
  
2.  Ajoutez ou retirez des nœuds d'une configuration de cluster de basculement sans aucune incidence sur les autres nœuds du cluster. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
    -   Tous les nœuds d'un cluster de basculement doivent être de la même plateforme (32 bits ou 64 bits) et exécuter le même système d'exploitation et la même version. En outre, les éditions 64 bits de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent être installées sur un matériel 64 bits utilisant les versions 64 bits des systèmes d'exploitation Windows. Il n'existe pas de prise en charge WOW64 pour le clustering de basculement dans cette version.  
  
3.  Spécifiez plusieurs adresses IP pour chaque instance de cluster de basculement. Vous pouvez spécifier plusieurs adresses IP pour chaque sous-réseau. Si les adresses IP sont toutes sur le même sous-réseau, le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] définit la dépendance sur AND. Si vous mettez des nœuds en cluster sur plusieurs sous-réseaux, le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] définit la dépendance sur OR.  
  
## <a name="ssnoversion-failover-cluster-installation-options"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Options d’installation d’un cluster de basculement  
  
##### <a name="option-1-integrated-installation-with-add-node"></a>Option 1 : installation intégrée avec ajout de nœud  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comprend deux étapes :  
  
1.  Créez et configurez une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à un seul nœud. Une fois la configuration du nœud réussie, vous disposez d'une instance de cluster de basculement entièrement fonctionnelle. Celle-ci n'offre pas une haute disponibilité pour l'instant, car il n'y a qu'un seul nœud dans le cluster de basculement.  
  
2.  Sur chaque nœud à ajouter au cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , exécutez le programme d'installation en utilisant la fonctionnalité d'ajout de nœud pour ajouter le nœud correspondant.  
  
##### <a name="option-2-advancedenterprise-installation"></a>Option 2 : installation avancée/entreprise  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] L’installation avancée/entreprise d’un cluster de basculement comprend deux étapes :  
  
1.  Sur chaque nœud devant faire partie du cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , exécutez le programme d'installation en utilisant la fonctionnalité de préparation de cluster de basculement. Cette étape prépare les nœuds pour le clustering ; toutefois, aucune instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'est opérationnelle à la fin de cette étape.  
  
2.  Une fois les nœuds préparés pour le clustering, lancez le programme d'installation sur le nœud propriétaire du disque partagé en utilisant la fonctionnalité de création de cluster de basculement. Cette étape permet de configurer et de rendre opérationnelle l'instance de cluster de basculement. À la fin de cette étape, vous disposez d'une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] opérationnelle.  
  
    > [!NOTE]  
    >  Les deux options d'installation permettent d'effectuer une installation de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à plusieurs nœuds. Quelle que soit l'option d'installation choisie, la fonctionnalité d'ajout de nœud peut être utilisée pour ajouter des nœuds supplémentaires après qu'un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a été créé.  
  
    > [!IMPORTANT]  
    >  La lettre de lecteur du système d'exploitation pour les emplacements d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit correspondre sur tous les nœuds ajoutés au cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="ip-address-configuration-during-setup"></a>Configuration d'adresse IP pendant l'installation  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Le programme d'installation vous permet de définir ou de modifier les paramètres de dépendance de ressource IP pendant les actions suivantes :  
  
-   Installation intégrée – [Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   CompleteFailoverCluster (installation avancée) – [Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   Ajouter un nœud – [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   Supprimer un nœud – [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
 **Remarque** Les adresses IP IPV6 sont prises en charge.  Si vous configurez à la fois IPV4 et IPV6, les adresses sont traitées comme des sous-réseaux différents, et IPV6 devrait être mis en ligne en premier.  
  
##### <a name="ssnoversion-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Cluster de basculement de sous-réseaux multiples  
 Vous pouvez définir des dépendances OR lorsque les nœuds du cluster se trouvent sur des sous-réseaux différents. Toutefois, chaque nœud du cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit être un propriétaire possible d'au moins une d'adresse IP spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Avant l’installation du clustering de basculement](before-installing-failover-clustering.md)   
 [Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](create-a-new-sql-server-failover-cluster-setup.md)   
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Mettre à niveau un cluster de basculement SQL Server](../windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
