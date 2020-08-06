---
title: Scénarios de globalisation pour Analysis Services données multidimensionnelles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b243c83bae41f35f95f4f113661f924979cc6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602427"
---
# <a name="globalization-scenarios-for-analysis-services-multiidimensional"></a><span data-ttu-id="1a440-102">Scénarios de globalisation pour données multidimensionnelles Analysis Services</span><span class="sxs-lookup"><span data-stu-id="1a440-102">Globalization scenarios for Analysis Services Multiidimensional</span></span>
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="1a440-103">stocke et manipule les métadonnées et les données multilingues dans les modèles de données tabulaires et multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="1a440-103">stores and manipulates multilingual data and metadata in both tabular and multidimensional data models.</span></span> <span data-ttu-id="1a440-104">Le stockage des données est en Unicode (UTF-16), dans des jeux de caractères qui utilisent l'encodage Unicode.</span><span class="sxs-lookup"><span data-stu-id="1a440-104">Data storage is Unicode (UTF-16), in character sets that use Unicode encoding.</span></span> <span data-ttu-id="1a440-105">Si vous chargez des données ANSI dans un modèle de données, les caractères sont stockés à l'aide de points de code équivalents Unicode.</span><span class="sxs-lookup"><span data-stu-id="1a440-105">If you load ANSI data into a data model, characters are stored using Unicode equivalent code points.</span></span>  
  
 <span data-ttu-id="1a440-106">La prise en charge d'Unicode signifie qu' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peut stocker des données dans n'importe laquelle des langues prises en charge par les systèmes d'exploitation Windows clients et serveurs, ce qui autorise la lecture, l'écriture, le tri et la comparaison des données dans n'importe quel jeu de caractères utilisé sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="1a440-106">The implications of Unicode support means that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can store data in any of the languages supported by the Windows client and server operating systems, allowing read, write, sort, and comparison of data in any character set used on a Windows computer.</span></span> <span data-ttu-id="1a440-107">Les applications clientes BI consommant des données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent représenter les données dans la langue choisie par l'utilisateur, en supposant que les données existent dans cette langue dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="1a440-107">BI client applications consuming [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data can represent data in the user's language of choice, assuming the data exists in that language in the model.</span></span>  
  
 <span data-ttu-id="1a440-108">La prise en charge linguistique peut signifier différentes choses pour différentes personnes.</span><span class="sxs-lookup"><span data-stu-id="1a440-108">Language support can mean different things to different people.</span></span> <span data-ttu-id="1a440-109">La liste suivante répond à quelques questions courantes liées à la prise en charge des langues par Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="1a440-109">The following list addresses a few common questions related to how Analysis Services supports languages.</span></span>  
  
-   <span data-ttu-id="1a440-110">Les données, comme nous l'avons déjà dit, sont stockées dans n'importe quel jeu de caractères Unicode détecté sur un système d'exploitation client Windows.</span><span class="sxs-lookup"><span data-stu-id="1a440-110">Data, as already noted, is stored in any Unicode-encoded character set found on a Windows client operating system.</span></span>  
  
-   <span data-ttu-id="1a440-111">Les métadonnées, telles que les noms d'objets, les identificateurs et les descriptions, peuvent également être dans n'importe quel(le) langue et script Unicode.</span><span class="sxs-lookup"><span data-stu-id="1a440-111">Metadata, such as object names, identifiers, and descriptions, can also be in any Unicode language and script.</span></span> <span data-ttu-id="1a440-112">Cela est vrai même quand les outils et l'environnement sont dans une autre langue.</span><span class="sxs-lookup"><span data-stu-id="1a440-112">This is true even when the tools and environment are in another language.</span></span> <span data-ttu-id="1a440-113">Par exemple, dans un environnement de développement qui utilise la langue anglaise et un classement Latin dans toute la pile, vous pouvez inclure dans votre modèle un objet dont le nom contient des caractères cyrilliques.</span><span class="sxs-lookup"><span data-stu-id="1a440-113">For example, in a development environment that uses English language and a Latin collation throughout the stack, you can include in your model an object that uses Cyrillic characters in its name.</span></span>  
  
     <span data-ttu-id="1a440-114">Pour les modèles multidimensionnels uniquement, les légendes et les membres d'attributs peuvent être exprimés comme des traductions.</span><span class="sxs-lookup"><span data-stu-id="1a440-114">For multidimensional models only, captions and attribute members can be expressed as translations.</span></span> <span data-ttu-id="1a440-115">Vous pouvez définir une ou plusieurs traductions, puis utiliser un identificateur de paramètres régionaux pour déterminer la traduction retournée au client.</span><span class="sxs-lookup"><span data-stu-id="1a440-115">You can define one or more translations, and then use a locale identifier to determine which translation is returned to the client.</span></span> <span data-ttu-id="1a440-116">Pour plus d'informations, consultez [Fonctionnalités](#bkmk_features) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="1a440-116">See [Features](#bkmk_features) below for more details.</span></span>  
  
-   <span data-ttu-id="1a440-117">Les messages d'erreur, d'avertissement et d'information retournés par le moteur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (msmdsrv) sont traduits dans les 43 langues prises en charge par Office et Office 365.</span><span class="sxs-lookup"><span data-stu-id="1a440-117">Error, warning, and informational messages returned from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] engine (msmdsrv) are localized into the 43 languages supported by Office and Office 365.</span></span> <span data-ttu-id="1a440-118">Aucune configuration n'est requise pour obtenir les messages dans une langue spécifique.</span><span class="sxs-lookup"><span data-stu-id="1a440-118">No configuration is required to get messages in a specific language.</span></span> <span data-ttu-id="1a440-119">Les paramètres régionaux de l'application cliente déterminent quelles chaînes sont retournées.</span><span class="sxs-lookup"><span data-stu-id="1a440-119">The locale of the client application determines which strings are returned.</span></span>  
  
-   <span data-ttu-id="1a440-120">Le fichier de configuration (msmdsrv.ini) et PowerShell AMO sont en anglais uniquement.</span><span class="sxs-lookup"><span data-stu-id="1a440-120">Configuration file (msmdsrv.ini) and AMO PowerShell are in English only.</span></span>  
  
-   <span data-ttu-id="1a440-121">Les fichiers journaux contiendront un mélange de messages localisés et en anglais, en supposant que vous avez installé un module linguistique sur le serveur Windows qui exécute Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="1a440-121">Log files will contain a mix of English and localized messages, assuming you have installed a language pack on the Windows server that Analysis Services runs on.</span></span>  
  
-   <span data-ttu-id="1a440-122">La documentation et les outils, tels que [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], sont traduits dans les langues suivantes : allemand, chinois simplifié, chinois traditionnel, coréen, espagnol, français, italien, japonais, portugais (brésilien) et russe.</span><span class="sxs-lookup"><span data-stu-id="1a440-122">Documentation and tools, such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], are translated into these languages: Chinese Simplified, Chinese Traditional, French, German, Italian, Japanese, Korean, Portuguese (Brazil), Russian, and Spanish.</span></span> <span data-ttu-id="1a440-123">Pour utiliser une version des outils spécifique à une langue, installez une version de SQL Server spécifique à une langue (par exemple, installez la version allemande de SQL Server pour obtenir Management Studio en allemand) ou exécutez le programme d'installation autonome dans la langue cible pour [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a440-123">To use a language-specific version of the tools, install a language-specific version of SQL Server (for example, install the German version of SQL Server to get Management Studio in German) or run the standalone setup in the target language for [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].</span></span>  
  
 <span data-ttu-id="1a440-124">Analysis Services vous permet de définir la langue, le classement et les traductions indépendamment dans toute la hiérarchie d'objets.</span><span class="sxs-lookup"><span data-stu-id="1a440-124">Analysis Services lets you set language, collation, and translations independently throughout the object hierarchy.</span></span>  
  
 <span data-ttu-id="1a440-125">Voici quelques-uns des scénarios possibles grâce aux langues, aux classements et aux traductions :</span><span class="sxs-lookup"><span data-stu-id="1a440-125">Scenarios enabled through language, collations, and translations include:</span></span>  
  
-   <span data-ttu-id="1a440-126">Un modèle de données fournit plusieurs légendes traduites pour que les noms et les valeurs des champs apparaissent dans la langue choisie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1a440-126">One data model provides multiple translated captions so that field names and values appear in the user's language of choice.</span></span> <span data-ttu-id="1a440-127">Pour les entreprises qui opèrent dans des pays bilingues comme le Canada, la Belgique ou la Suisse, la prise en charge de plusieurs langues dans les applications clientes et de serveur est une exigence de codage ordinaire.</span><span class="sxs-lookup"><span data-stu-id="1a440-127">For companies operating in bi-lingual countries such as Canada, Belgium, or Switzerland, supporting multiple languages across client and server applications is a standard coding requirement.</span></span> <span data-ttu-id="1a440-128">Ce scénario est possible grâce aux traductions et aux conversions monétaires.</span><span class="sxs-lookup"><span data-stu-id="1a440-128">This scenario is enabled through translations and currency conversions.</span></span> <span data-ttu-id="1a440-129">Voir [Fonctionnalités](#bkmk_features) ci-dessous pour plus d'informations et pour obtenir des liens.</span><span class="sxs-lookup"><span data-stu-id="1a440-129">See [Features](#bkmk_features) below for details and links.</span></span>  
  
-   <span data-ttu-id="1a440-130">Les environnements de développement et de production sont géolocalisés dans différents pays.</span><span class="sxs-lookup"><span data-stu-id="1a440-130">Development and production environments are geo-located in different countries.</span></span> <span data-ttu-id="1a440-131">Il est de plus en plus courant de développer une solution dans un pays, puis de la déployer dans un autre.</span><span class="sxs-lookup"><span data-stu-id="1a440-131">It's increasingly common to develop a solution in one country and then deploy it another.</span></span> <span data-ttu-id="1a440-132">Savoir comment définir les propriétés de langue et de classement est essentiel si vous êtes chargé de la préparation d'une solution développée dans une langue et devant être déployée sur un serveur qui utilise un module linguistique différent.</span><span class="sxs-lookup"><span data-stu-id="1a440-132">Knowing how to set language and collation properties is essential if you are tasked with preparing a solution developed in one language, for deployment on a server that uses a different language pack.</span></span> <span data-ttu-id="1a440-133">Définir ces propriétés vous permet de remplacer les valeurs par défaut héritées du système hôte d'origine.</span><span class="sxs-lookup"><span data-stu-id="1a440-133">Setting these properties allows you to override the inherited defaults that you get from the original host system.</span></span> <span data-ttu-id="1a440-134">Pour plus d’informations, consultez la section [Langues et classements &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) .</span><span class="sxs-lookup"><span data-stu-id="1a440-134">See [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) for details about setting properties.</span></span>  
  
##  <a name="features-for-building-a-globalized-multidimensional-solution"></a><a name="bkmk_features"></a><span data-ttu-id="1a440-135">Fonctionnalités de création d’une solution multidimensionnelle globalisée</span><span class="sxs-lookup"><span data-stu-id="1a440-135">Features for building a globalized multidimensional solution</span></span>  
 [!INCLUDE[applies](../includes/applies-md.md)] <span data-ttu-id="1a440-136">Modèles de données multidimensionnels uniquement</span><span class="sxs-lookup"><span data-stu-id="1a440-136">Multidimensional data models only</span></span>  
  
 <span data-ttu-id="1a440-137">Au niveau du client, les applications globalisées qui consomment ou manipulent des données multidimensionnelles [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent utiliser les fonctionnalités multilingues et multiculturelles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="1a440-137">At the client level, globalized applications that consume or manipulate [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional data can use the multilingual and multicultural features in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="1a440-138">Les [traductions &#40;Analysis Services&#41;](translations-analysis-services.md) sont utilisées pour incorporer plusieurs légendes pour un seul objet, où chaque chaîne traduite peut exister avec d’autres traductions.</span><span class="sxs-lookup"><span data-stu-id="1a440-138">[Translations &#40;Analysis Services&#41;](translations-analysis-services.md) are used to embed multiple captions for a single object, where each translated string can exist alongside other translations.</span></span> <span data-ttu-id="1a440-139">Vous pouvez utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir les traductions pour la légende, la description et les types de comptes pour des cubes, des mesures, des dimensions et des attributs.</span><span class="sxs-lookup"><span data-stu-id="1a440-139">You can use the [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define the translations for the caption, description, and account types for cubes and measures, dimension and attributes.</span></span> <span data-ttu-id="1a440-140">Vous pouvez récupérer des données et des métadonnées à partir d'objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur lesquels des traductions ont été définies automatiquement en fournissant un identificateur local lors de la connexion à une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a440-140">You can retrieve data and metadata from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects on which translations have been defined automatically by providing a locale identifier when connecting to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="1a440-141">Pour apprendre à utiliser cette fonctionnalité, consultez la [leçon 9 : définition de perspectives et de traductions](lesson-9-defining-perspectives-and-translations.md) du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a440-141">A lesson on how to use this feature can be found in [Lesson 9: Defining Perspectives and Translations](lesson-9-defining-perspectives-and-translations.md) of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tutorial.</span></span>  
  
-   <span data-ttu-id="1a440-142">Les [conversions monétaires &#40;Analysis Services&#41;](currency-conversions-analysis-services.md) est par le biais de scripts MDX spécialisés qui convertissent les mesures contenant des données monétaires.</span><span class="sxs-lookup"><span data-stu-id="1a440-142">[Currency Conversions &#40;Analysis Services&#41;](currency-conversions-analysis-services.md) is through specialized MDX scripts that convert measures containing currency data.</span></span> <span data-ttu-id="1a440-143">Vous pouvez utiliser l'Assistant Business Intelligence de [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] pour générer un script MDX qui utilise une combinaison de données et de métadonnées issues de dimensions, d'attributs et de groupes de mesures pour convertir des mesures contenant des données monétaires.</span><span class="sxs-lookup"><span data-stu-id="1a440-143">You can use the Business Intelligence Wizard in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] to generate an MDX script that uses a combination of data and metadata from dimensions, attributes, and measure groups to convert measures containing currency data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a440-144">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1a440-144">In This Section</span></span>  
  
|<span data-ttu-id="1a440-145">Rubrique</span><span class="sxs-lookup"><span data-stu-id="1a440-145">Topic</span></span>|<span data-ttu-id="1a440-146">Description</span><span class="sxs-lookup"><span data-stu-id="1a440-146">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1a440-147">Langues et classements &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1a440-147">Languages and Collations &#40;Analysis Services&#41;</span></span>](languages-and-collations-analysis-services.md)|<span data-ttu-id="1a440-148">Spécifiez la langue par défaut et le classement Windows pour une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a440-148">Specify default language and Windows collation for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="1a440-149">Vos choix affectent les données et les métadonnées gérées par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a440-149">Your choices affect data and metadata managed by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="1a440-150">Traductions &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1a440-150">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)|<span data-ttu-id="1a440-151">Définissez des traductions pour une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et des objets contenus dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="1a440-151">Define translations for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and objects contained by the database.</span></span> <span data-ttu-id="1a440-152">Cette rubrique explique comment [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] résout les demandes de données et de métadonnées traduites envoyées par les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="1a440-152">This topic explains how [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] resolves requests for translated data and metadata from client applications.</span></span>|  
|[<span data-ttu-id="1a440-153">Conversions monétaires &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1a440-153">Currency Conversions &#40;Analysis Services&#41;</span></span>](currency-conversions-analysis-services.md)|<span data-ttu-id="1a440-154">Définissez une conversion monétaire à l'aide de l'Assistant Business Intelligence.</span><span class="sxs-lookup"><span data-stu-id="1a440-154">Define a currency conversion using the Business Intelligence Wizard.</span></span>|  
|[<span data-ttu-id="1a440-155">Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1a440-155">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](globalization-tips-and-best-practices-analysis-services.md)|<span data-ttu-id="1a440-156">Passe en revue plusieurs pratiques de conception et de codage qui peuvent vous aider à éviter les problèmes liés aux données multilingues.</span><span class="sxs-lookup"><span data-stu-id="1a440-156">Reviews several design and coding practices that can help you avoid problems related to multi-language data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a440-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a440-157">See Also</span></span>  
 <span data-ttu-id="1a440-158">[Internationalisation pour les applications Windows](/windows/desktop/Intl/international-support) </span><span class="sxs-lookup"><span data-stu-id="1a440-158">[Internationalization for Windows Applications](/windows/desktop/Intl/international-support) </span></span>  
 <span data-ttu-id="1a440-159">[Documentation de la globalisation Microsoft](/globalization/) </span><span class="sxs-lookup"><span data-stu-id="1a440-159">[Microsoft Globalization Documentation](/globalization/) </span></span>  
 <span data-ttu-id="1a440-160">[Écriture d’applications du Windows Store avec la conception adaptative basée sur les paramètres régionaux](https://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/) </span><span class="sxs-lookup"><span data-stu-id="1a440-160">[Writing Windows Store apps with locale-based adaptive design](https://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/) </span></span>  
 [<span data-ttu-id="1a440-161">Développement d'applications Windows universelles avec C# et XAML</span><span class="sxs-lookup"><span data-stu-id="1a440-161">Developing Universal Windows Apps with C# and XAML</span></span>](https://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  