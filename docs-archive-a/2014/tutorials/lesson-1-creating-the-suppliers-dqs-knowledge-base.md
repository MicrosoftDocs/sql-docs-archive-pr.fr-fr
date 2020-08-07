---
title: 'Leçon 1 : création de la base de connaissances DQS des fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6928637bfe23b6b68fd89ec8b34139720ac13a2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703544"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a><span data-ttu-id="8e442-102">Leçon 1 : Création d’une base de connaissances DQS nommée Fournisseurs</span><span class="sxs-lookup"><span data-stu-id="8e442-102">Lesson 1: Creating the Suppliers DQS Knowledge Base</span></span>
  <span data-ttu-id="8e442-103">Dans cette leçon, vous allez créer une base de connaissances DQS nommée **Suppliers** avec les connaissances (métadonnées) relatives aux données des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="8e442-103">In this lesson, you create a DQS knowledge base named **Suppliers** with the knowledge (metadata) about supplier data.</span></span> <span data-ttu-id="8e442-104">Utilisez la base de connaissances pour effectuer les activités de nettoyage et de correspondance sur les données d'entrée des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="8e442-104">You use the knowledge base to perform the cleansing and matching activities on input supplier data.</span></span> <span data-ttu-id="8e442-105">L'activité de nettoyage identifie les données incorrectes ou non valides, les corrige, propose des corrections/suggestions, normalise les données, et les enrichit avec des informations.</span><span class="sxs-lookup"><span data-stu-id="8e442-105">The cleansing activity identifies incorrect/invalid data, corrects the incorrect data, proposes corrections/suggestions, standardizes the data, and enriches the data with more information.</span></span> <span data-ttu-id="8e442-106">L'activité de correspondance compare les données et identifie les enregistrements de données similaires (mais légèrement différents), et vous permet de supprimer les doublons.</span><span class="sxs-lookup"><span data-stu-id="8e442-106">The matching activity compares data and identifies similar records (but slightly different) in the data that helps you remove duplicates on the data.</span></span>  
  
 <span data-ttu-id="8e442-107">Vous pouvez utiliser des processus assistés par ordinateur et interactifs pour créer et gérer une base de connaissances.</span><span class="sxs-lookup"><span data-stu-id="8e442-107">You can use both interactive and computer-assisted processes to create, build, and manage a knowledge base.</span></span> <span data-ttu-id="8e442-108">Les connaissances contenues dans une base de connaissances sont conservées dans des domaines, chacun d'entre eux étant spécifique à un champ dans les données que vous souhaitez nettoyer et/ou mettre en correspondance.</span><span class="sxs-lookup"><span data-stu-id="8e442-108">Knowledge in a knowledge base is maintained in domains, each of which is specific to a data field in the data that you want to cleanse and/or match.</span></span>  
  
 <span data-ttu-id="8e442-109">Dans cette leçon, vous allez effectuer les tâches suivantes pour créer la base de connaissances **fournisseurs** :</span><span class="sxs-lookup"><span data-stu-id="8e442-109">In this lesson, you perform the following tasks to create the **Suppliers** knowledge base:</span></span>  
  
-   <span data-ttu-id="8e442-110">Créez une base de connaissances DQS nommée **Suppliers**.</span><span class="sxs-lookup"><span data-stu-id="8e442-110">Create a DQS knowledge base named **Suppliers**.</span></span> <span data-ttu-id="8e442-111">Vous pouvez créer une base de connaissances de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="8e442-111">You can create a knowledge base in several ways.</span></span> <span data-ttu-id="8e442-112">Vous pouvez créer une base de connaissances de toutes pièces ou à partir d'une base de connaissances existante, ou encore, vous pouvez importer un fichier DQS (.dqs) contenant une base de connaissances prégénérée et exportée, ou exécuter une activité de découverte de connaissances sur un échantillon de données.</span><span class="sxs-lookup"><span data-stu-id="8e442-112">You can build a knowledge base from scratch or build it based on an existing knowledge base or by importing a DQS file (.dqs) that contains a prebuilt and exported knowledge base, or by performing a knowledge discovery activity on sample data.</span></span> <span data-ttu-id="8e442-113">Dans ce didacticiel, vous allez créer une base de connaissances de toutes pièces.</span><span class="sxs-lookup"><span data-stu-id="8e442-113">In this tutorial, you create the knowledge base from scratch.</span></span>  
  
-   <span data-ttu-id="8e442-114">Créez des domaines dans la base de connaissances **fournisseurs** que vous utilisez pour nettoyer les données et faites correspondre les données pour identifier les doublons.</span><span class="sxs-lookup"><span data-stu-id="8e442-114">Create domains in the **Suppliers** knowledge base that you use for cleansing data, and matching data to identify duplicates.</span></span> <span data-ttu-id="8e442-115">Créez des domaines pour les champs de données que vous souhaitez utiliser pour nettoyer les données et les mettre en correspondance, mais pas pour tous les champs de données dans les données.</span><span class="sxs-lookup"><span data-stu-id="8e442-115">create domains for data fields that you want to use in cleansing and matching activities, not for all the data fields in the data.</span></span>  
  
-   <span data-ttu-id="8e442-116">Ajouter des valeurs à un domaine manuellement, importer des valeurs à partir d'un fichier Excel, effectuer une activité de découverte des connaissances sur un échantillon de données, ou importer des valeurs de projet depuis un projet de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="8e442-116">Add values to a domain by adding values manually, importing values from an excel file, by performing a knowledge discovery activity on sample data, and by importing project values from a cleansing project.</span></span> <span data-ttu-id="8e442-117">Vous pouvez également importer des valeurs de domaine en important un fichier DQS qui contient des propriétés et des valeurs de champ, cependant, cette procédure n'est pas décrite dans le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="8e442-117">You can also import domain values by importing a DQS file that contains domain properties and values, which you do not perform in the tutorial.</span></span>  
  
-   <span data-ttu-id="8e442-118">Définir les règles pour un domaine.</span><span class="sxs-lookup"><span data-stu-id="8e442-118">Set rules for a domain.</span></span> <span data-ttu-id="8e442-119">Une règle de domaine est une condition utilisée par DQS pour valider, corriger et normaliser les valeurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="8e442-119">A domain rule is a condition that is used by DQS to validate, correct, and standardize domain values.</span></span>  
  
-   <span data-ttu-id="8e442-120">Définir des relations à base de termes pour un domaine.</span><span class="sxs-lookup"><span data-stu-id="8e442-120">Set term-based relationships for a domain.</span></span> <span data-ttu-id="8e442-121">Une relation à base de termes vous permet d'effectuer une correction sur un terme qui fait partie d'une valeur dans un domaine.</span><span class="sxs-lookup"><span data-stu-id="8e442-121">A term-based relationship enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="8e442-122">Par exemple, dans la valeur **contoso Inc., Inc.** est un terme qui peut être défini comme incorporé.</span><span class="sxs-lookup"><span data-stu-id="8e442-122">For example, in the value **Contoso Inc., Inc.** is a term that can be defined as Incorporated.</span></span> <span data-ttu-id="8e442-123">Une telle approche permet de normaliser les données et d'identifier les doublons.</span><span class="sxs-lookup"><span data-stu-id="8e442-123">This helps in standardizing the data as well as in identifying duplicates.</span></span> <span data-ttu-id="8e442-124">Par exemple, **contoso Inc.** et **contoso Incorporated** peuvent être considérés comme des doublons.</span><span class="sxs-lookup"><span data-stu-id="8e442-124">For example, **Contoso Inc.** and **Contoso Incorporated** can be considered duplicates.</span></span>  
  
-   <span data-ttu-id="8e442-125">Spécifier les synonymes dans les valeurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="8e442-125">Specify synonyms in domain values.</span></span> <span data-ttu-id="8e442-126">Vous pouvez définir deux valeurs ou plus comme étant des synonymes et configurer l'une d'entre elles comme valeur menante, pouvant remplacer les synonymes lors d'une activité de nettoyage, afin de normaliser les données.</span><span class="sxs-lookup"><span data-stu-id="8e442-126">You can set two or more values as synonyms and set one of them as a leading value, which replaces its synonym values during a cleansing activity to standardize the data.</span></span>  
  
-   <span data-ttu-id="8e442-127">Créer un domaine composite nommé Validation d'adresses incluant les domaines Adresse, Ville, État et Code postal.</span><span class="sxs-lookup"><span data-stu-id="8e442-127">Create a composite domain named Address Validation that comprises Address line, City, State, and Zip domains.</span></span> <span data-ttu-id="8e442-128">Un domaine composite est un domaine qui comprend un ou plusieurs domaines individuels.</span><span class="sxs-lookup"><span data-stu-id="8e442-128">A composite domain is a domain that consists of one or more single domains.</span></span> <span data-ttu-id="8e442-129">Il vous permet de créer une règle impliquant plusieurs domaines.</span><span class="sxs-lookup"><span data-stu-id="8e442-129">It lets you create a rule that involves multiple domains.</span></span> <span data-ttu-id="8e442-130">Par exemple, si vous avez défini une règle : si Ville est Los Angeles, État doit être CA (pour Californie), où Ville et État sont deux domaines différents.</span><span class="sxs-lookup"><span data-stu-id="8e442-130">For example, you can define a rule: if City is Los Angeles, State must be CA, where City and State are two separate domains.</span></span>  
  
-   <span data-ttu-id="8e442-131">Configurer et utiliser un service de données de référence.</span><span class="sxs-lookup"><span data-stu-id="8e442-131">Configure and use a reference data service.</span></span> <span data-ttu-id="8e442-132">Dans Data Quality Services (DQS), la fonctionnalité de service de données de référence vous permet de vous abonner à des fournisseurs de données de référence tiers, et nettoyer et enrichir facilement vos données métier en les validant par rapport à des données de grande qualité.</span><span class="sxs-lookup"><span data-stu-id="8e442-132">The Reference Data Service feature in Data Quality Services (DQS) enables you to subscribe to third-party reference data providers, and to cleanse and enrich your business data by validating it against their high-quality data.</span></span> <span data-ttu-id="8e442-133">Vous pouvez utiliser les services des meilleurs fournisseurs DQS à partir de DQS, afin de normaliser, corriger ou enrichir vos données pendant le processus de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="8e442-133">You can use services from leading DQS providers from within DQS to standardize, correct, or enrich your data during the cleansing process.</span></span> <span data-ttu-id="8e442-134">Dans ce didacticiel, vous allez apprendre à configurer votre environnement DQS pour utiliser un service de données de référence sur la place de marché Azure et utiliser le service associé au domaine composite validation d’adresse pour nettoyer les données d’adresse.</span><span class="sxs-lookup"><span data-stu-id="8e442-134">In this tutorial, you learn how to configure your DQS environment to use a reference data service on Azure Marketplace and use the service associated with the Address Validation composite domain to cleanse address data.</span></span>  
  
-   <span data-ttu-id="8e442-135">Publiez la base de connaissances afin qu'elle puisse être utilisée pour les activités de nettoyage et de correspondance.</span><span class="sxs-lookup"><span data-stu-id="8e442-135">Publish the knowledge base so that the knowledge base can be used in cleansing and matching activities.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="8e442-136">étape suivante</span><span class="sxs-lookup"><span data-stu-id="8e442-136">Next Step</span></span>  
 [<span data-ttu-id="8e442-137">Tâche 1 : Création d’une base de connaissances et de domaines</span><span class="sxs-lookup"><span data-stu-id="8e442-137">Task 1: Creating a Knowledge Base and Domains</span></span>](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  