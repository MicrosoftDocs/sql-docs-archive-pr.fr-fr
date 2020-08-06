---
title: SetEmailConfiguration, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19068d7d7fff8c31c455ef76e8d2c2caa26b743f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706063"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="88f0d-102">Méthode SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="88f0d-102">SetEmailConfiguration Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="88f0d-103">Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="88f0d-103">Configures the e-mail delivery extension used by the report server to send e-mail.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88f0d-104">Syntax</span></span>  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88f0d-105">Parameters</span></span>  
 <span data-ttu-id="88f0d-106">*SendUsingSMTPServer*</span><span class="sxs-lookup"><span data-stu-id="88f0d-106">*SendUsingSMTPServer*</span></span>  
 <span data-ttu-id="88f0d-107">Valeur booléenne indiquant si le serveur doit utiliser le serveur SMTP pour envoyer le courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="88f0d-107">A Boolean value indicating whether the server is to use the SMTP server to send email.</span></span> <span data-ttu-id="88f0d-108">Cette valeur peut uniquement être True.</span><span class="sxs-lookup"><span data-stu-id="88f0d-108">This value can only be set to true.</span></span> <span data-ttu-id="88f0d-109">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="88f0d-109">Default value is false.</span></span>  
  
 <span data-ttu-id="88f0d-110">*SMTPServer*</span><span class="sxs-lookup"><span data-stu-id="88f0d-110">*SMTPServer*</span></span>  
 <span data-ttu-id="88f0d-111">Chaîne contenant le nom ou l'adresse IP d'un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="88f0d-111">A string containing the name or IP address of an SMTP server.</span></span>  
  
 <span data-ttu-id="88f0d-112">*SenderEmailAddress*</span><span class="sxs-lookup"><span data-stu-id="88f0d-112">*SenderEmailAddress*</span></span>  
 <span data-ttu-id="88f0d-113">Adresse de messagerie utilisée dans le champ 'De :' pour les messages électroniques envoyés depuis le serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="88f0d-113">The e-mail address used in the 'From:' field for e-mails sent from the report server.</span></span>  
  
 <span data-ttu-id="88f0d-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="88f0d-114">*HRESULT*</span></span>  
 <span data-ttu-id="88f0d-115">[out] Valeur indiquant si l'appel a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="88f0d-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88f0d-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="88f0d-116">Return Value</span></span>  
 <span data-ttu-id="88f0d-117">Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué.</span><span class="sxs-lookup"><span data-stu-id="88f0d-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="88f0d-118">Une valeur 0 indique que l'appel de méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="88f0d-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="88f0d-119">Une valeur différente de zéro indique qu'une erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="88f0d-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88f0d-120">Notes</span><span class="sxs-lookup"><span data-stu-id="88f0d-120">Remarks</span></span>  
 <span data-ttu-id="88f0d-121">Lorsque le paramètre *SendUsingSMTPServer* a la valeur `true` , l’entrée **SendUsing** dans le fichier de configuration du serveur de rapports a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="88f0d-121">When the *SendUsingSMTPServer* parameter is set to `true`, the **SendUsing** entry in the report server configuration file is set to 1.</span></span> <span data-ttu-id="88f0d-122">Lorsque *SendUsingSMTPServer* a la valeur `false` , l’entrée **SendUsing** n’est pas configurée.</span><span class="sxs-lookup"><span data-stu-id="88f0d-122">When *SendUsingSMTPServer* is set to `false`, the **SendUsing** entry is not configured.</span></span>  
  
 <span data-ttu-id="88f0d-123">Avec cette méthode, les utilisateurs ne peuvent pas configurer l’entrée **SendUsing** dans le fichier de configuration du serveur de rapports à une autre valeur que 1.</span><span class="sxs-lookup"><span data-stu-id="88f0d-123">This method does not provide a way for users to set the **SendUsing** entry in the report server configuration file to a value other than 1.</span></span> <span data-ttu-id="88f0d-124">Pour configurer le serveur de rapports pour une fonctionnalité autre que le courrier SMTP, vous devez modifier le fichier de configuration manuellement.</span><span class="sxs-lookup"><span data-stu-id="88f0d-124">To configure the report server for anything other than SMTP mail, you must edit the configuration file manually.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f0d-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="88f0d-125">Requirements</span></span>  
 <span data-ttu-id="88f0d-126">**Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f0d-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f0d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88f0d-127">See Also</span></span>  
 [<span data-ttu-id="88f0d-128">Membres MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="88f0d-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  