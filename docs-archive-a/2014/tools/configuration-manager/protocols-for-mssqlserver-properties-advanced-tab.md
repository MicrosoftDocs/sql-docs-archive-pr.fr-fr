---
title: Propriétés de Protocoles pour MSSQLSERVER (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1549b773df2fec7dbfece481daeb9228ec35cfd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87613247"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a><span data-ttu-id="7b264-102">Propriétés de Protocoles pour MSSQLSERVER (onglet Avancé)</span><span class="sxs-lookup"><span data-stu-id="7b264-102">Protocols for MSSQLSERVER Properties (Advanced Tab)</span></span>
  <span data-ttu-id="7b264-103">Utilisez l'onglet **Avancé** dans la boîte de dialogue **Propriétés de Protocoles pour MSSQLSERVER** pour configurer la **protection étendue de l'authentification** du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b264-103">Use the **Advanced** tab on the **Protocols for MSSQLSERVER Properties** dialog box to configure **Extended Protection for Authentication** for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="7b264-104">La**Protection étendue** est une fonctionnalité des composants réseau implémentée par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="7b264-104">**Extended Protection** is a feature of the network components implemented by the operating system.</span></span> <span data-ttu-id="7b264-105">La**protection étendue** est disponible dans Windows 7 et Windows Server 2008 R2 et est incluse dans les Service Packs pour les précédents systèmes d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="7b264-105">**Extended Protection** is available in Windows 7 and Windows Server 2008 R2, and is included in service packs for older operating systems.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7b264-106">est plus sécurisé lorsque les connexions sont établies à l'aide de la **protection étendue**.</span><span class="sxs-lookup"><span data-stu-id="7b264-106">is more secure when connections are made using **Extended Protection**.</span></span> <span data-ttu-id="7b264-107">Certains avantages de la **Protection étendue** requièrent de sélectionner l'option **Forcer le chiffrement** sous l'onglet **Indicateurs** .</span><span class="sxs-lookup"><span data-stu-id="7b264-107">Some benefits of **Extended Protection** require **Force Encryption** to be selected on the **Flags** tab.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b264-108">Windows n'active pas la **protection étendue** par défaut.</span><span class="sxs-lookup"><span data-stu-id="7b264-108">Windows does not enable **Extended Protection** by default.</span></span> <span data-ttu-id="7b264-109">Pour plus d’informations sur l’activation de la **protection étendue** dans Windows, consultez l’article [Protection étendue de l’authentification](https://go.microsoft.com/fwlink/?LinkId=178431)de la Base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="7b264-109">For information about how to enable **Extended Protection** in Windows, see the Knowledge Base article, [Extended Protection for Authentication](https://go.microsoft.com/fwlink/?LinkId=178431).</span></span>  
  
 <span data-ttu-id="7b264-110">Pour plus d’informations sur la configuration d’autres services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour obtenir une description complète de la **protection étendue**, consultez les informations plus récentes sur [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).</span><span class="sxs-lookup"><span data-stu-id="7b264-110">For more information about how to configure other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, and a complete description of **Extended Protection**, see more recent information on [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).</span></span>  
  
 <span data-ttu-id="7b264-111">La**protection étendue** est totalement prise en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b264-111">**Extended Protection** is fully supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="7b264-112">La prise en charge de la **protection étendue** pour d'autres fournisseurs du client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est actuellement pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="7b264-112">Support for **Extended Protection** for other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client providers is not currently supported.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b264-113">Options</span><span class="sxs-lookup"><span data-stu-id="7b264-113">Options</span></span>  
 <span data-ttu-id="7b264-114">**Protection étendue**</span><span class="sxs-lookup"><span data-stu-id="7b264-114">**Extended Protection**</span></span>  
 <span data-ttu-id="7b264-115">Il existe trois valeurs possibles :</span><span class="sxs-lookup"><span data-stu-id="7b264-115">There are three possible values:</span></span>  
  
-   <span data-ttu-id="7b264-116">Lorsque la valeur est **Off**, la **protection étendue** est désactivée.</span><span class="sxs-lookup"><span data-stu-id="7b264-116">When set to **Off**, **Extended Protection** is disabled.</span></span> <span data-ttu-id="7b264-117">L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] acceptera les connexions de tous les clients, qu'ils soient protégés ou non.</span><span class="sxs-lookup"><span data-stu-id="7b264-117">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will accept connections from any client regardless of whether the client is protected or not.</span></span> <span data-ttu-id="7b264-118">La valeur**Off** est compatible avec les anciens systèmes d'exploitation non corrigés, mais elle est moins sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b264-118">**Off** is compatible with older and unpatched operating systems, but is less secure.</span></span> <span data-ttu-id="7b264-119">Utilisez ce paramètre uniquement lorsque vous savez que les systèmes d'exploitation clients ne prennent pas en charge la Protection étendue.</span><span class="sxs-lookup"><span data-stu-id="7b264-119">Only use this setting when you know that the client operating systems do not support extended protection.</span></span>  
  
-   <span data-ttu-id="7b264-120">Lorsque la valeur est **Autorisée**, la **protection étendue** est requise pour les connexions à partir des systèmes d'exploitation qui prennent en charge la **protection étendue**.</span><span class="sxs-lookup"><span data-stu-id="7b264-120">When set to **Allowed**, **Extended Protection** is required for connections from operating systems that support **Extended Protection**.</span></span> <span data-ttu-id="7b264-121">Les connexions provenant d'applications clientes non protégées qui s'exécutent sur des systèmes d'exploitation clients protégés sont rejetées.</span><span class="sxs-lookup"><span data-stu-id="7b264-121">Connections from unprotected client applications that are running on protected client operating systems are rejected.</span></span> <span data-ttu-id="7b264-122">La**Protection étendue** est ignorée pour les connexions provenant de systèmes d'exploitation non protégés.</span><span class="sxs-lookup"><span data-stu-id="7b264-122">**Extended Protection** is ignored for connections from unprotected operating systems.</span></span> <span data-ttu-id="7b264-123">Ce paramètre offre une meilleure protection que la valeur **Off**, mais ce n'est pas la configuration la plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="7b264-123">This setting is more secure than **Off**, but is not the most secure setting.</span></span> <span data-ttu-id="7b264-124">Utilisez ce paramètre dans des environnements mixtes, dans lesquels certains systèmes d'exploitation ou applications prennent en charge la **protection étendue** et d'autres non.</span><span class="sxs-lookup"><span data-stu-id="7b264-124">Use this setting in mixed environments, where some operating systems or applications support **Extended Protection** and some do not.</span></span>  
  
-   <span data-ttu-id="7b264-125">Lorsque la valeur est **Requis**, seules les connexions provenant d'applications protégées sur des systèmes d'exploitation protégés sont acceptées.</span><span class="sxs-lookup"><span data-stu-id="7b264-125">When set to **Required**, only connections from protected applications on protected operating systems are accepted.</span></span> <span data-ttu-id="7b264-126">Ce paramètre est le plus sécurisé des trois options mais les connexions provenant de systèmes d'exploitation qui ne prennent pas en charge la **Protection étendue** ne pourront pas se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b264-126">This setting is the most secure of the three options but connections from operating systems that do not support **Extended Protection** will not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7b264-127">**SPN NTLM acceptés**</span><span class="sxs-lookup"><span data-stu-id="7b264-127">**Accepted NTLM SPNs**</span></span>  
 <span data-ttu-id="7b264-128">Lorsque l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est identifiée par plusieurs noms principaux de service (SPN) NTLM, répertoriez-les ici sous la forme d'une série de chaînes séparées par des points-virgules.</span><span class="sxs-lookup"><span data-stu-id="7b264-128">When the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is identified by more than one NTLM service principal name (SPN), list the SPNs here as a series of strings separated by semicolons.</span></span> <span data-ttu-id="7b264-129">Par exemple, la valeur **MSSQLSvc/NomHôte1.Contoso.com;MSSQLSvc/NomHôte2.Contoso.com**indique que les clients qui essaient de se connecter aux noms principaux de service (SPN) **MSSQLSvc/HÔTE1.Contoso.com** et **MSSQLSvc/HÔTE2.Contoso.com** sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7b264-129">For example, the value **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com**, indicates that clients attempting to connect to SPNs named **MSSQLSvc/HOST1.Contoso.com** and **MSSQLSvc/HOST2.Contoso.com** are allowed.</span></span> <span data-ttu-id="7b264-130">La variable a une longueur maximale de 2048 caractères.</span><span class="sxs-lookup"><span data-stu-id="7b264-130">The variable has a maximum length of 2048 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b264-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b264-131">See Also</span></span>  
 [<span data-ttu-id="7b264-132">Protection étendue de l'authentification avec Reporting Services</span><span class="sxs-lookup"><span data-stu-id="7b264-132">Extended Protection for Authentication with Reporting Services</span></span>](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)  
  
  