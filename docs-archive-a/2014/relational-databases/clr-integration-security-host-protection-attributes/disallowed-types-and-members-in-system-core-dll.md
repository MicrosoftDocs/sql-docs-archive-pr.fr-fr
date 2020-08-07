---
title: Types et membres interdits dans System.Core.dll | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: dcd24cd6-f4ab-42cc-9786-a1604e8a4b4e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8699afa19bf32365f5c5dede5cb918f8a67e2ab1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87611832"
---
# <a name="disallowed-types-and-members-in-systemcoredll"></a><span data-ttu-id="5fe52-102">Types et membres interdits dans System.Core.dll</span><span class="sxs-lookup"><span data-stu-id="5fe52-102">Disallowed Types and Members in System.Core.dll</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5fe52-103">la programmation CLR (Common Language Integration) interdit l’utilisation d’un type ou d’un membre ayant un `HostProtectionAttribute` qui spécifie une `System.Security.Permissions.HostProtectionResource` énumération avec la valeur `ExternalProcessMgmt` , `ExternalThreading` ,, `MayLeakOnAbort` `SecurityInfrastructure` , `SelfAffectingProcessMgmnt` , `SelfAffectingThreading` , **SharedState**, `Synchronization` ou `UI` .</span><span class="sxs-lookup"><span data-stu-id="5fe52-103">common language integration (CLR) programming disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="5fe52-104">Le tableau suivant répertorie les membres et les types des assemblys System.Core.dll dont les valeurs d'attribut de protection de l'hôte (HPA) sont interdites.</span><span class="sxs-lookup"><span data-stu-id="5fe52-104">The following table lists the members and types of the System.Core.dll assemblies whose Host Protection Attribute (HPA) values are disallowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fe52-105">Cette liste a été générée à partir des assemblys pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5fe52-105">This list was generated from the supported assemblies.</span></span> <span data-ttu-id="5fe52-106">Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../clr-integration/database-objects/supported-net-framework-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="5fe52-106">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
|<span data-ttu-id="5fe52-107">Type ou membre</span><span class="sxs-lookup"><span data-stu-id="5fe52-107">Type or Member</span></span>|<span data-ttu-id="5fe52-108">Valeur(s) HPA</span><span class="sxs-lookup"><span data-stu-id="5fe52-108">HPA Value(s)</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="5fe52-109">System.Diagnostics.Eventing.EventDescriptor</span><span class="sxs-lookup"><span data-stu-id="5fe52-109">System.Diagnostics.Eventing.EventDescriptor</span></span>|<span data-ttu-id="5fe52-110">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-110">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-111">System.Diagnostics.Eventing.EventProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-111">System.Diagnostics.Eventing.EventProvider</span></span>|<span data-ttu-id="5fe52-112">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-112">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-113">System.Diagnostics.Eventing.EventProviderTraceListener</span><span class="sxs-lookup"><span data-stu-id="5fe52-113">System.Diagnostics.Eventing.EventProviderTraceListener</span></span>|<span data-ttu-id="5fe52-114">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-114">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-115">System.Management.Instrumentation.ManagementEntityAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-115">System.Management.Instrumentation.ManagementEntityAttribute</span></span>|<span data-ttu-id="5fe52-116">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-116">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-117">System.Management.Instrumentation.WmiConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-117">System.Management.Instrumentation.WmiConfigurationAttribute</span></span>|<span data-ttu-id="5fe52-118">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-118">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-119">System.Management.Instrumentation.ManagementMemberAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-119">System.Management.Instrumentation.ManagementMemberAttribute</span></span>|<span data-ttu-id="5fe52-120">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-120">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-121">System.Management.Instrumentation.ManagementNewInstanceAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-121">System.Management.Instrumentation.ManagementNewInstanceAttribute</span></span>|<span data-ttu-id="5fe52-122">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-122">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-123">System.Management.Instrumentation.ManagementBindAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-123">System.Management.Instrumentation.ManagementBindAttribute</span></span>|<span data-ttu-id="5fe52-124">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-124">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-125">System.Management.Instrumentation.ManagementCreateAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-125">System.Management.Instrumentation.ManagementCreateAttribute</span></span>|<span data-ttu-id="5fe52-126">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-126">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-127">System.Management.Instrumentation.ManagementRemoveAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-127">System.Management.Instrumentation.ManagementRemoveAttribute</span></span>|<span data-ttu-id="5fe52-128">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-128">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-129">System.Management.Instrumentation.ManagementEnumeratorAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-129">System.Management.Instrumentation.ManagementEnumeratorAttribute</span></span>|<span data-ttu-id="5fe52-130">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-130">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-131">System.Management.Instrumentation.ManagementProbeAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-131">System.Management.Instrumentation.ManagementProbeAttribute</span></span>|<span data-ttu-id="5fe52-132">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-132">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-133">System.Management.Instrumentation.ManagementTaskAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-133">System.Management.Instrumentation.ManagementTaskAttribute</span></span>|<span data-ttu-id="5fe52-134">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-134">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-135">System.Management.Instrumentation.ManagementKeyAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-135">System.Management.Instrumentation.ManagementKeyAttribute</span></span>|<span data-ttu-id="5fe52-136">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-136">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-137">System.Management.Instrumentation.ManagementReferenceAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-137">System.Management.Instrumentation.ManagementReferenceAttribute</span></span>|<span data-ttu-id="5fe52-138">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-138">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-139">System.Management.Instrumentation.ManagementConfigurationAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-139">System.Management.Instrumentation.ManagementConfigurationAttribute</span></span>|<span data-ttu-id="5fe52-140">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-140">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-141">System.Management.Instrumentation.ManagementCommitAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-141">System.Management.Instrumentation.ManagementCommitAttribute</span></span>|<span data-ttu-id="5fe52-142">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-142">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-143">System.Management.Instrumentation.ManagementNameAttribute</span><span class="sxs-lookup"><span data-stu-id="5fe52-143">System.Management.Instrumentation.ManagementNameAttribute</span></span>|<span data-ttu-id="5fe52-144">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-144">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-145">System.Management.Instrumentation.InstrumentationBaseException</span><span class="sxs-lookup"><span data-stu-id="5fe52-145">System.Management.Instrumentation.InstrumentationBaseException</span></span>|<span data-ttu-id="5fe52-146">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-146">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-147">System.Management.Instrumentation.InstrumentationException</span><span class="sxs-lookup"><span data-stu-id="5fe52-147">System.Management.Instrumentation.InstrumentationException</span></span>|<span data-ttu-id="5fe52-148">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-148">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-149">System.Management.Instrumentation.InstanceNotFoundException</span><span class="sxs-lookup"><span data-stu-id="5fe52-149">System.Management.Instrumentation.InstanceNotFoundException</span></span>|<span data-ttu-id="5fe52-150">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-150">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-151">System.Diagnostics.Eventing.Reader.EventBookmark</span><span class="sxs-lookup"><span data-stu-id="5fe52-151">System.Diagnostics.Eventing.Reader.EventBookmark</span></span>|<span data-ttu-id="5fe52-152">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-152">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-153">System.Diagnostics.Eventing.Reader.EventLogConfiguration</span><span class="sxs-lookup"><span data-stu-id="5fe52-153">System.Diagnostics.Eventing.Reader.EventLogConfiguration</span></span>|<span data-ttu-id="5fe52-154">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-154">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-155">System.Diagnostics.Eventing.Reader.EventLogLink</span><span class="sxs-lookup"><span data-stu-id="5fe52-155">System.Diagnostics.Eventing.Reader.EventLogLink</span></span>|<span data-ttu-id="5fe52-156">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-156">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-157">System.Diagnostics.Eventing.Reader.EventLogStatus</span><span class="sxs-lookup"><span data-stu-id="5fe52-157">System.Diagnostics.Eventing.Reader.EventLogStatus</span></span>|<span data-ttu-id="5fe52-158">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-158">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-159">System.Diagnostics.Eventing.Reader.EventProperty</span><span class="sxs-lookup"><span data-stu-id="5fe52-159">System.Diagnostics.Eventing.Reader.EventProperty</span></span>|<span data-ttu-id="5fe52-160">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-160">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-161">System.Diagnostics.Eventing.Reader.EventLogPropertySelector</span><span class="sxs-lookup"><span data-stu-id="5fe52-161">System.Diagnostics.Eventing.Reader.EventLogPropertySelector</span></span>|<span data-ttu-id="5fe52-162">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-162">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-163">System.Diagnostics.Eventing.Reader.EventRecord</span><span class="sxs-lookup"><span data-stu-id="5fe52-163">System.Diagnostics.Eventing.Reader.EventRecord</span></span>|<span data-ttu-id="5fe52-164">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-164">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-165">System.Diagnostics.Eventing.Reader.EventKeyword</span><span class="sxs-lookup"><span data-stu-id="5fe52-165">System.Diagnostics.Eventing.Reader.EventKeyword</span></span>|<span data-ttu-id="5fe52-166">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-166">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-167">System.Diagnostics.Eventing.Reader.EventLevel</span><span class="sxs-lookup"><span data-stu-id="5fe52-167">System.Diagnostics.Eventing.Reader.EventLevel</span></span>|<span data-ttu-id="5fe52-168">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-168">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-169">System.Diagnostics.Eventing.Reader.EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="5fe52-169">System.Diagnostics.Eventing.Reader.EventLogRecord</span></span>|<span data-ttu-id="5fe52-170">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-170">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-171">System.Diagnostics.Eventing.Reader.EventLogReader</span><span class="sxs-lookup"><span data-stu-id="5fe52-171">System.Diagnostics.Eventing.Reader.EventLogReader</span></span>|<span data-ttu-id="5fe52-172">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-172">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-173">System.Diagnostics.Eventing.Reader.EventLogWatcher</span><span class="sxs-lookup"><span data-stu-id="5fe52-173">System.Diagnostics.Eventing.Reader.EventLogWatcher</span></span>|<span data-ttu-id="5fe52-174">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-174">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-175">System.Diagnostics.Eventing.Reader.EventRecordWrittenEventArgs</span><span class="sxs-lookup"><span data-stu-id="5fe52-175">System.Diagnostics.Eventing.Reader.EventRecordWrittenEventArgs</span></span>|<span data-ttu-id="5fe52-176">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-176">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-177">System.Diagnostics.Eventing.Reader.EventLogSession</span><span class="sxs-lookup"><span data-stu-id="5fe52-177">System.Diagnostics.Eventing.Reader.EventLogSession</span></span>|<span data-ttu-id="5fe52-178">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-178">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-179">System.Diagnostics.Eventing.Reader.EventMetadata</span><span class="sxs-lookup"><span data-stu-id="5fe52-179">System.Diagnostics.Eventing.Reader.EventMetadata</span></span>|<span data-ttu-id="5fe52-180">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-180">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-181">System.Diagnostics.Eventing.Reader.EventOpcode</span><span class="sxs-lookup"><span data-stu-id="5fe52-181">System.Diagnostics.Eventing.Reader.EventOpcode</span></span>|<span data-ttu-id="5fe52-182">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-182">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-183">System.Diagnostics.Eventing.Reader.EventTask</span><span class="sxs-lookup"><span data-stu-id="5fe52-183">System.Diagnostics.Eventing.Reader.EventTask</span></span>|<span data-ttu-id="5fe52-184">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-184">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-185">System.Diagnostics.Eventing.Reader.EventLogException</span><span class="sxs-lookup"><span data-stu-id="5fe52-185">System.Diagnostics.Eventing.Reader.EventLogException</span></span>|<span data-ttu-id="5fe52-186">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-186">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-187">System.Diagnostics.Eventing.Reader.EventLogNotFoundException</span><span class="sxs-lookup"><span data-stu-id="5fe52-187">System.Diagnostics.Eventing.Reader.EventLogNotFoundException</span></span>|<span data-ttu-id="5fe52-188">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-188">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-189">System.Diagnostics.Eventing.Reader.EventLogReadingException</span><span class="sxs-lookup"><span data-stu-id="5fe52-189">System.Diagnostics.Eventing.Reader.EventLogReadingException</span></span>|<span data-ttu-id="5fe52-190">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-190">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-191">System.Diagnostics.Eventing.Reader.EventLogProviderDisabledException</span><span class="sxs-lookup"><span data-stu-id="5fe52-191">System.Diagnostics.Eventing.Reader.EventLogProviderDisabledException</span></span>|<span data-ttu-id="5fe52-192">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-192">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-193">System.Diagnostics.Eventing.Reader.EventLogInvalidDataException</span><span class="sxs-lookup"><span data-stu-id="5fe52-193">System.Diagnostics.Eventing.Reader.EventLogInvalidDataException</span></span>|<span data-ttu-id="5fe52-194">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-194">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-195">System.Diagnostics.Eventing.Reader.EventLogInformation</span><span class="sxs-lookup"><span data-stu-id="5fe52-195">System.Diagnostics.Eventing.Reader.EventLogInformation</span></span>|<span data-ttu-id="5fe52-196">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-196">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-197">System.Diagnostics.Eventing.Reader.ProviderMetadata</span><span class="sxs-lookup"><span data-stu-id="5fe52-197">System.Diagnostics.Eventing.Reader.ProviderMetadata</span></span>|<span data-ttu-id="5fe52-198">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-198">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-199">Microsoft.Win32.SafeHandles.SafeNCryptHandle</span><span class="sxs-lookup"><span data-stu-id="5fe52-199">Microsoft.Win32.SafeHandles.SafeNCryptHandle</span></span>|<span data-ttu-id="5fe52-200">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-200">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-201">Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle</span><span class="sxs-lookup"><span data-stu-id="5fe52-201">Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle</span></span>|<span data-ttu-id="5fe52-202">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-202">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-203">Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle</span><span class="sxs-lookup"><span data-stu-id="5fe52-203">Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle</span></span>|<span data-ttu-id="5fe52-204">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-204">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-205">Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle</span><span class="sxs-lookup"><span data-stu-id="5fe52-205">Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle</span></span>|<span data-ttu-id="5fe52-206">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-206">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-207">System.Security.Cryptography.Aes</span><span class="sxs-lookup"><span data-stu-id="5fe52-207">System.Security.Cryptography.Aes</span></span>|<span data-ttu-id="5fe52-208">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-208">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-209">System.Security.Cryptography.AesCryptoServiceProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-209">System.Security.Cryptography.AesCryptoServiceProvider</span></span>|<span data-ttu-id="5fe52-210">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-210">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-211">System.Security.Cryptography.AesManaged</span><span class="sxs-lookup"><span data-stu-id="5fe52-211">System.Security.Cryptography.AesManaged</span></span>|<span data-ttu-id="5fe52-212">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-212">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-213">System.Security.Cryptography.CngAlgorithm</span><span class="sxs-lookup"><span data-stu-id="5fe52-213">System.Security.Cryptography.CngAlgorithm</span></span>|<span data-ttu-id="5fe52-214">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-214">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-215">System.Security.Cryptography.CngAlgorithmGroup</span><span class="sxs-lookup"><span data-stu-id="5fe52-215">System.Security.Cryptography.CngAlgorithmGroup</span></span>|<span data-ttu-id="5fe52-216">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-216">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-217">System.Security.Cryptography.CngKey</span><span class="sxs-lookup"><span data-stu-id="5fe52-217">System.Security.Cryptography.CngKey</span></span>|<span data-ttu-id="5fe52-218">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-218">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-219">System.Security.Cryptography.CngKeyBlobFormat</span><span class="sxs-lookup"><span data-stu-id="5fe52-219">System.Security.Cryptography.CngKeyBlobFormat</span></span>|<span data-ttu-id="5fe52-220">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-220">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-221">System.Security.Cryptography.CngKeyCreationParameters</span><span class="sxs-lookup"><span data-stu-id="5fe52-221">System.Security.Cryptography.CngKeyCreationParameters</span></span>|<span data-ttu-id="5fe52-222">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-222">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-223">System.Security.Cryptography.CngProperty</span><span class="sxs-lookup"><span data-stu-id="5fe52-223">System.Security.Cryptography.CngProperty</span></span>|<span data-ttu-id="5fe52-224">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-224">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-225">System.Security.Cryptography.CngPropertyCollection</span><span class="sxs-lookup"><span data-stu-id="5fe52-225">System.Security.Cryptography.CngPropertyCollection</span></span>|<span data-ttu-id="5fe52-226">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-226">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-227">System.Security.Cryptography.CngProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-227">System.Security.Cryptography.CngProvider</span></span>|<span data-ttu-id="5fe52-228">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-228">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-229">System.Security.Cryptography.CngUIPolicy</span><span class="sxs-lookup"><span data-stu-id="5fe52-229">System.Security.Cryptography.CngUIPolicy</span></span>|<span data-ttu-id="5fe52-230">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-230">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-231">System.Security.Cryptography.ECDiffieHellman</span><span class="sxs-lookup"><span data-stu-id="5fe52-231">System.Security.Cryptography.ECDiffieHellman</span></span>|<span data-ttu-id="5fe52-232">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-232">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-233">System.Security.Cryptography.ECDiffieHellmanPublicKey</span><span class="sxs-lookup"><span data-stu-id="5fe52-233">System.Security.Cryptography.ECDiffieHellmanPublicKey</span></span>|<span data-ttu-id="5fe52-234">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-234">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-235">System.Security.Cryptography.ECDiffieHellmanCng</span><span class="sxs-lookup"><span data-stu-id="5fe52-235">System.Security.Cryptography.ECDiffieHellmanCng</span></span>|<span data-ttu-id="5fe52-236">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-236">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-237">System.Security.Cryptography.ECDiffieHellmanCngPublicKey</span><span class="sxs-lookup"><span data-stu-id="5fe52-237">System.Security.Cryptography.ECDiffieHellmanCngPublicKey</span></span>|<span data-ttu-id="5fe52-238">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-238">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-239">System.Security.Cryptography.ECDsa</span><span class="sxs-lookup"><span data-stu-id="5fe52-239">System.Security.Cryptography.ECDsa</span></span>|<span data-ttu-id="5fe52-240">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-240">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-241">System.Security.Cryptography.ECDsaCng</span><span class="sxs-lookup"><span data-stu-id="5fe52-241">System.Security.Cryptography.ECDsaCng</span></span>|<span data-ttu-id="5fe52-242">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-242">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-243">System.Security.Cryptography.ManifestSignatureInformation</span><span class="sxs-lookup"><span data-stu-id="5fe52-243">System.Security.Cryptography.ManifestSignatureInformation</span></span>|<span data-ttu-id="5fe52-244">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-244">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-245">System.Security.Cryptography.ManifestSignatureInformationCollection</span><span class="sxs-lookup"><span data-stu-id="5fe52-245">System.Security.Cryptography.ManifestSignatureInformationCollection</span></span>|<span data-ttu-id="5fe52-246">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-246">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-247">System.Security.Cryptography.MD5Cng</span><span class="sxs-lookup"><span data-stu-id="5fe52-247">System.Security.Cryptography.MD5Cng</span></span>|<span data-ttu-id="5fe52-248">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-248">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-249">System.Security.Cryptography.SHA1Cng</span><span class="sxs-lookup"><span data-stu-id="5fe52-249">System.Security.Cryptography.SHA1Cng</span></span>|<span data-ttu-id="5fe52-250">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-250">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-251">System.Security.Cryptography.SHA256Cng</span><span class="sxs-lookup"><span data-stu-id="5fe52-251">System.Security.Cryptography.SHA256Cng</span></span>|<span data-ttu-id="5fe52-252">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-252">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-253">System.Security.Cryptography.SHA256CryptoServiceProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-253">System.Security.Cryptography.SHA256CryptoServiceProvider</span></span>|<span data-ttu-id="5fe52-254">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-254">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-255">System.Security.Cryptography.SHA384Cng</span><span class="sxs-lookup"><span data-stu-id="5fe52-255">System.Security.Cryptography.SHA384Cng</span></span>|<span data-ttu-id="5fe52-256">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-256">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-257">System.Security.Cryptography.SHA384CryptoServiceProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-257">System.Security.Cryptography.SHA384CryptoServiceProvider</span></span>|<span data-ttu-id="5fe52-258">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-258">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-259">System.Security.Cryptography.SHA512Cng</span><span class="sxs-lookup"><span data-stu-id="5fe52-259">System.Security.Cryptography.SHA512Cng</span></span>|<span data-ttu-id="5fe52-260">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-260">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-261">System.Security.Cryptography.SHA512CryptoServiceProvider</span><span class="sxs-lookup"><span data-stu-id="5fe52-261">System.Security.Cryptography.SHA512CryptoServiceProvider</span></span>|<span data-ttu-id="5fe52-262">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-262">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-263">System.Security.Cryptography.StrongNameSignatureInformation</span><span class="sxs-lookup"><span data-stu-id="5fe52-263">System.Security.Cryptography.StrongNameSignatureInformation</span></span>|<span data-ttu-id="5fe52-264">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-264">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-265">System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation</span><span class="sxs-lookup"><span data-stu-id="5fe52-265">System.Security.Cryptography.X509Certificates.AuthenticodeSignatureInformation</span></span>|<span data-ttu-id="5fe52-266">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-266">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-267">System.Security.Cryptography.X509Certificates.TimestampInformation</span><span class="sxs-lookup"><span data-stu-id="5fe52-267">System.Security.Cryptography.X509Certificates.TimestampInformation</span></span>|<span data-ttu-id="5fe52-268">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-268">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-269">Microsoft.Win32.SafeHandles.SafePipeHandle</span><span class="sxs-lookup"><span data-stu-id="5fe52-269">Microsoft.Win32.SafeHandles.SafePipeHandle</span></span>|<span data-ttu-id="5fe52-270">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-270">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-271">System.TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="5fe52-271">System.TimeZoneInfo</span></span>|<span data-ttu-id="5fe52-272">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-272">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-273">System.TimeZoneNotFoundException</span><span class="sxs-lookup"><span data-stu-id="5fe52-273">System.TimeZoneNotFoundException</span></span>|<span data-ttu-id="5fe52-274">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-274">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-275">System.InvalidTimeZoneException</span><span class="sxs-lookup"><span data-stu-id="5fe52-275">System.InvalidTimeZoneException</span></span>|<span data-ttu-id="5fe52-276">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-276">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-277">System.Diagnostics.EventSchemaTraceListener</span><span class="sxs-lookup"><span data-stu-id="5fe52-277">System.Diagnostics.EventSchemaTraceListener</span></span>|<span data-ttu-id="5fe52-278">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-278">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-279">System.Diagnostics.UnescapedXmlDiagnosticData</span><span class="sxs-lookup"><span data-stu-id="5fe52-279">System.Diagnostics.UnescapedXmlDiagnosticData</span></span>|<span data-ttu-id="5fe52-280">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-280">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-281">System.Diagnostics.PerformanceData.CounterData</span><span class="sxs-lookup"><span data-stu-id="5fe52-281">System.Diagnostics.PerformanceData.CounterData</span></span>|<span data-ttu-id="5fe52-282">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-282">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-283">System.Diagnostics.PerformanceData.CounterSetInstanceCounterDataSet</span><span class="sxs-lookup"><span data-stu-id="5fe52-283">System.Diagnostics.PerformanceData.CounterSetInstanceCounterDataSet</span></span>|<span data-ttu-id="5fe52-284">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-284">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-285">System.Diagnostics.PerformanceData.CounterSet</span><span class="sxs-lookup"><span data-stu-id="5fe52-285">System.Diagnostics.PerformanceData.CounterSet</span></span>|<span data-ttu-id="5fe52-286">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-286">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-287">System.Diagnostics.PerformanceData.CounterSetInstance</span><span class="sxs-lookup"><span data-stu-id="5fe52-287">System.Diagnostics.PerformanceData.CounterSetInstance</span></span>|<span data-ttu-id="5fe52-288">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-288">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-289">System.Collections.Generic.HashSet\`1</span><span class="sxs-lookup"><span data-stu-id="5fe52-289">System.Collections.Generic.HashSet\`1</span></span>|<span data-ttu-id="5fe52-290">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-290">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-291">System.IO.Pipes.PipeStream</span><span class="sxs-lookup"><span data-stu-id="5fe52-291">System.IO.Pipes.PipeStream</span></span>|<span data-ttu-id="5fe52-292">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-292">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-293">System.IO.Pipes.AnonymousPipeServerStream</span><span class="sxs-lookup"><span data-stu-id="5fe52-293">System.IO.Pipes.AnonymousPipeServerStream</span></span>|<span data-ttu-id="5fe52-294">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-294">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-295">System.IO.Pipes.AnonymousPipeClientStream</span><span class="sxs-lookup"><span data-stu-id="5fe52-295">System.IO.Pipes.AnonymousPipeClientStream</span></span>|<span data-ttu-id="5fe52-296">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-296">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-297">System.IO.Pipes.NamedPipeServerStream</span><span class="sxs-lookup"><span data-stu-id="5fe52-297">System.IO.Pipes.NamedPipeServerStream</span></span>|<span data-ttu-id="5fe52-298">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-298">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-299">System.IO.Pipes.NamedPipeClientStream</span><span class="sxs-lookup"><span data-stu-id="5fe52-299">System.IO.Pipes.NamedPipeClientStream</span></span>|<span data-ttu-id="5fe52-300">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-300">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-301">System.IO.Pipes.PipeAccessRule</span><span class="sxs-lookup"><span data-stu-id="5fe52-301">System.IO.Pipes.PipeAccessRule</span></span>|<span data-ttu-id="5fe52-302">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-302">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-303">System.IO.Pipes.PipeAuditRule</span><span class="sxs-lookup"><span data-stu-id="5fe52-303">System.IO.Pipes.PipeAuditRule</span></span>|<span data-ttu-id="5fe52-304">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-304">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-305">System.IO.Pipes.PipeSecurity</span><span class="sxs-lookup"><span data-stu-id="5fe52-305">System.IO.Pipes.PipeSecurity</span></span>|<span data-ttu-id="5fe52-306">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-306">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-307">System.Threading.LockRecursionException</span><span class="sxs-lookup"><span data-stu-id="5fe52-307">System.Threading.LockRecursionException</span></span>|<span data-ttu-id="5fe52-308">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-308">MayLeakOnAbort</span></span>|  
|<span data-ttu-id="5fe52-309">System.Threading.ReaderWriterLockSlim</span><span class="sxs-lookup"><span data-stu-id="5fe52-309">System.Threading.ReaderWriterLockSlim</span></span>|<span data-ttu-id="5fe52-310">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="5fe52-310">MayLeakOnAbort</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fe52-311">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fe52-311">See Also</span></span>  
 <span data-ttu-id="5fe52-312">[Attributs de protection de l’hôte et programmation de l’intégration du CLR](host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="5fe52-312">[Host Protection Attributes and CLR Integration Programming](host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 <span data-ttu-id="5fe52-313">[Types et membres interdits dans Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span><span class="sxs-lookup"><span data-stu-id="5fe52-313">[Disallowed Types and Members in Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span></span>  
 <span data-ttu-id="5fe52-314">[Types et membres interdits dans mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span><span class="sxs-lookup"><span data-stu-id="5fe52-314">[Disallowed Types and Members in mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span></span>  
 <span data-ttu-id="5fe52-315">[Types et membres interdits dans System.dll](disallowed-types-and-members-in-system-dll.md) </span><span class="sxs-lookup"><span data-stu-id="5fe52-315">[Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md) </span></span>  
 [<span data-ttu-id="5fe52-316">Types et membres non autorisés dans System.Data.dll</span><span class="sxs-lookup"><span data-stu-id="5fe52-316">Disallowed Types and Members in System.Data.dll</span></span>](disallowed-types-and-members-in-system-data-dll.md)  
  
  