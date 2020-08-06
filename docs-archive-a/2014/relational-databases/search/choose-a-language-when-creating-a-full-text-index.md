---
title: Choisir une langue lors de la création d’un index de recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- full-text indexes [SQL Server], languages
- international considerations [full-text search]
- stemmers [full-text search]
- global considerations [full-text search]
- full-text search [SQL Server], international considerations
- languages [SQL Server], full-text indexes
- word breakers [full-text search]
ms.assetid: 670a5181-ab80-436a-be96-d9498fbe2c09
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b514820ad64cbf17df209cbda552e4c5182b75fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612746"
---
# <a name="choose-a-language-when-creating-a-full-text-index"></a><span data-ttu-id="91da0-102">Choisir une langue lors de la création d'un index de recherche en texte intégral</span><span class="sxs-lookup"><span data-stu-id="91da0-102">Choose a Language When Creating a Full-Text Index</span></span>
  <span data-ttu-id="91da0-103">Lorsque vous créez un index de recherche en texte intégral, vous devez spécifier une langue au niveau de la colonne pour la colonne indexée.</span><span class="sxs-lookup"><span data-stu-id="91da0-103">When creating a full-text index, you need to specify a column-level language for the indexed column.</span></span> <span data-ttu-id="91da0-104">L’ [analyseur lexical et les générateurs de formes dérivées](configure-and-manage-word-breakers-and-stemmers-for-search.md) de la langue spécifiée seront utilisés par les requêtes de texte intégral sur la colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-104">The [word breaker and stemmers](configure-and-manage-word-breakers-and-stemmers-for-search.md) of the specified language will be used by full-text queries on the column.</span></span> <span data-ttu-id="91da0-105">Plusieurs aspects doivent être pris en considération pour le choix de la langue d'une colonne lors de la création d'un index de texte intégral.</span><span class="sxs-lookup"><span data-stu-id="91da0-105">There are a couple of things to consider when choosing the column language when creating a full-text index.</span></span> <span data-ttu-id="91da0-106">Ces aspects sont liés à la façon dont les unités lexicales de votre texte sont créées et à la façon dont ce texte est ensuite indexé par le Moteur d'indexation et de recherche en texte intégral.</span><span class="sxs-lookup"><span data-stu-id="91da0-106">These considerations relate to how your text is tokenized and then indexed by Full-Text Engine.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91da0-107">Pour spécifier une langue au niveau de la colonne pour une colonne d’index de recherche en texte intégral, utilisez la clause LANGUAGE *language_term* lors de la spécification de la colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-107">To specify a column-level language for a column of full-text index, use the LANGUAGE *language_term* clause when specifying the column.</span></span> <span data-ttu-id="91da0-108">Pour plus d’informations, consultez [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) et [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="91da0-108">For more information, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) and [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
##  <a name="language-support-in-full-text-search"></a><a name="langsupp"></a> <span data-ttu-id="91da0-109">Prise en charge linguistique dans la recherche en texte intégral</span><span class="sxs-lookup"><span data-stu-id="91da0-109">Language Support in Full-Text Search</span></span>  
 <span data-ttu-id="91da0-110">Cette section fournit une introduction aux analyseurs lexicaux et aux générateur de formes dérivées et indique comment la recherche en texte intégral utilise le LCID de la langue de la colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-110">This section provides an introduction to word breakers and stemmers, and discusses how full-text search uses the LCID of the column-level language.</span></span>  
  
### <a name="introduction-to-word-breakers-and-stemmers"></a><span data-ttu-id="91da0-111">Introduction aux analyseurs lexicaux et aux générateurs de formes dérivées</span><span class="sxs-lookup"><span data-stu-id="91da0-111">Introduction to Word Breakers and Stemmers</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="91da0-112">et les versions ultérieures incluent une nouvelle famille complète d'analyseurs lexicaux et de générateurs de formes dérivées qui sont considérablement plus performants que ceux précédemment disponibles dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91da0-112">and later versions include a complete new family of word breakers and stemmers that are significantly better than the those previously available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91da0-113">Le Microsoft Natural Language Group (MS NLG) a implémenté et prend en charge ces nouveaux composants linguistiques.</span><span class="sxs-lookup"><span data-stu-id="91da0-113">The Microsoft Natural Language Group (MS NLG) implemented and supports these new linguistic components.</span></span>  
  
 <span data-ttu-id="91da0-114">Les avantages de ces nouveaux analyseurs lexicaux sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="91da0-114">The new word breakers provide the following benefits:</span></span>  
  
-   <span data-ttu-id="91da0-115">Robustesse</span><span class="sxs-lookup"><span data-stu-id="91da0-115">Robustness</span></span>  
  
     <span data-ttu-id="91da0-116">Les tests ont montré que les nouveaux analyseurs lexicaux sont fiables dans les environnements de requête de haute intensité.</span><span class="sxs-lookup"><span data-stu-id="91da0-116">Testing has shown that the new word breakers are robust in high-pressure query environments.</span></span>  
  
-   <span data-ttu-id="91da0-117">Sécurité</span><span class="sxs-lookup"><span data-stu-id="91da0-117">Security</span></span>  
  
     <span data-ttu-id="91da0-118">Les nouveaux analyseurs lexicaux sont activés par défaut dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] grâce aux améliorations de sécurité apportées aux composants linguistiques.</span><span class="sxs-lookup"><span data-stu-id="91da0-118">The new word breakers are enabled by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] thanks to security improvements in linguistic components.</span></span> <span data-ttu-id="91da0-119">Nous recommandons vivement que les composants externes tels que les analyseurs lexicaux et filtres soient signés afin d'améliorer la sécurité globale et la robustesse de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91da0-119">We highly recommend that external components such as word breakers and filters be signed  to improve the overall security and robustness of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91da0-120">Vous pouvez configurer le texte intégral pour vérifier que ces composants sont signés comme suit :</span><span class="sxs-lookup"><span data-stu-id="91da0-120">You can configure full-text to verify that these components are signed as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'verify_signature';  
    ```  
  
-   <span data-ttu-id="91da0-121">Qualité</span><span class="sxs-lookup"><span data-stu-id="91da0-121">Quality</span></span>  
  
     <span data-ttu-id="91da0-122">Les analyseurs lexicaux ont été repensés, et les tests ont montré que les nouveaux analyseurs lexicaux fournissent une qualité sémantique supérieure à celle des analyseurs lexicaux précédents.</span><span class="sxs-lookup"><span data-stu-id="91da0-122">Word breakers have been redesigned, and testing has shown that the new word breakers provide better semantic quality than previous word breakers.</span></span> <span data-ttu-id="91da0-123">Cela augmente l'exactitude de rappel.</span><span class="sxs-lookup"><span data-stu-id="91da0-123">This increases the recall accuracy.</span></span>  
  
-   <span data-ttu-id="91da0-124">Pour couvrir une longue liste de langues, les analyseurs lexicaux sont inclus d'office dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et sont activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="91da0-124">Coverage for a vast list of languages, word breakers are included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] out of the box and enabled by default .</span></span>  
  
 <span data-ttu-id="91da0-125">Pour obtenir la liste des langues pour lesquelles comprend un analyseur lexical et des générateurs de formes dérivées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , consultez [sys. Fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="91da0-125">For a list of the languages for which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] includes a word breaker and stemmers, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span>  
  

  
### <a name="how-full-text-search-uses-the-name-of-the-column-level-language"></a><span data-ttu-id="91da0-126">Comment la recherche en texte intégral utilise le nom de la langue de la colonne</span><span class="sxs-lookup"><span data-stu-id="91da0-126">How Full-Text Search Uses the Name of the Column-Level Language</span></span>  
 <span data-ttu-id="91da0-127">Lorsque vous créez un index de recherche en texte intégral, vous devez spécifier un nom de langue valide pour chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-127">When creating a full-text index, you need to specify a valid language name for each column.</span></span> <span data-ttu-id="91da0-128">Si un nom de langue est valide mais n’est pas retourné par l’affichage catalogue [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) , la recherche en texte intégral revient, le cas échéant, au nom de la langue disponible le plus proche de la même famille de langues.</span><span class="sxs-lookup"><span data-stu-id="91da0-128">If a language name is valid but not returned by the [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) catalog view, full-text search falls back to the closest available language name of the same language family, if any.</span></span> <span data-ttu-id="91da0-129">Sinon, la recherche en texte intégral revient à l'analyseur lexical neutre.</span><span class="sxs-lookup"><span data-stu-id="91da0-129">Otherwise, full-text search falls back to the Neutral word breaker.</span></span> <span data-ttu-id="91da0-130">Ce comportement de repli peut affecter l'exactitude de rappel.</span><span class="sxs-lookup"><span data-stu-id="91da0-130">This fall-back behavior might affect the recall accuracy.</span></span> <span data-ttu-id="91da0-131">Par conséquent, nous vous recommandons vivement de spécifier un nom de langue valide et disponible pour chaque colonne lors de la création d'un index de recherche en texte intégral.</span><span class="sxs-lookup"><span data-stu-id="91da0-131">Therefore we strongly recommend that you specify a valid and available language name for each column when creating a full-text index.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91da0-132">Le LCID est appliqué à tous les types de données pouvant faire l'objet d'une indexation de texte intégral (par exemple `char` ou `nchar`).</span><span class="sxs-lookup"><span data-stu-id="91da0-132">The LCID is used against all data types eligible for full-text indexing (such as `char` or `nchar`).</span></span> <span data-ttu-id="91da0-133">Si l'ordre de tri d'une colonne de type `char`, `varchar` ou `text` est défini à l'aide d'une langue différente de la langue identifiée par le LCID, ce dernier est néanmoins utilisé durant l'indexation de recherche en texte intégral et l'interrogation de ces colonnes.</span><span class="sxs-lookup"><span data-stu-id="91da0-133">If you have the sort order of a `char`, `varchar`, or `text` type column set to a language setting different from the language identified by the LCID, the LCID is used anyway during full-text indexing and querying of those columns.</span></span>  
  

  
##  <a name="word-breaking"></a><a name="breaking"></a> <span data-ttu-id="91da0-134">Analyse lexicale</span><span class="sxs-lookup"><span data-stu-id="91da0-134">Word Breaking</span></span>  
 <span data-ttu-id="91da0-135">Un analyseur lexical crée des jetons dans le texte indexé à partir des limites des mots, qui sont spécifiques aux langues.</span><span class="sxs-lookup"><span data-stu-id="91da0-135">A word breaker tokenizes the text being indexed on word boundaries, which are language specific.</span></span> <span data-ttu-id="91da0-136">Par conséquent, le comportement d'analyse lexicale diffère d'une langue à l'autre.</span><span class="sxs-lookup"><span data-stu-id="91da0-136">Therefore, word-breaking behavior differs among different languages.</span></span> <span data-ttu-id="91da0-137">Si vous utilisez une langue x indexer plusieurs langues {x, y et z}, une partie du comportement peut donner lieu à des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="91da0-137">If you use one language, x, to index a number of languages {x, y, and ,z}, some of the behavior might cause unexpected results.</span></span> <span data-ttu-id="91da0-138">Par exemple, un tiret (-) ou une virgule (,) peut être un élément d'analyseur lexical pouvant être rejeté dans une langue mais pas dans un autre.</span><span class="sxs-lookup"><span data-stu-id="91da0-138">For example, a dash (-) or a comma (,) might be a word-break element that will be thrown away in one language but not in another.</span></span> <span data-ttu-id="91da0-139">Un comportement de génération de formes dérivées rarement inattendu peut également se produire parce qu'un mot donné peut être dérivé différemment dans une autre langue.</span><span class="sxs-lookup"><span data-stu-id="91da0-139">Also rarely unexpected stemming behavior might occur because a given word might stem differently in different language.</span></span> <span data-ttu-id="91da0-140">Par exemple, en anglais, les limites des mots sont généralement fixées par des espaces blancs ou un signe de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="91da0-140">For example, in the English language, word boundaries are typically white space or some form of punctuation.</span></span> <span data-ttu-id="91da0-141">Dans d'autres langues, par exemple l'allemand, les mots ou les caractères peuvent être accolés.</span><span class="sxs-lookup"><span data-stu-id="91da0-141">In other languages, such as German, words or characters may be combined together.</span></span> <span data-ttu-id="91da0-142">Par conséquent, le choix de la langue d'une colonne doit être représentatif de la langue destinée à être stockée dans les lignes de cette colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-142">Therefore, the column-level language that you choose should represent the language that you expect will be stored in rows of that column.</span></span>  
  
### <a name="western-languages"></a><span data-ttu-id="91da0-143">Langues occidentales</span><span class="sxs-lookup"><span data-stu-id="91da0-143">Western Languages</span></span>  
 <span data-ttu-id="91da0-144">Pour la famille des langues occidentales, si vous êtes incertain quant aux langues qui seront stockées dans une colonne ou si vous pensez en stocker plusieurs, la solution de contournement générale est d'utiliser l'analyseur lexical pour la langue la plus complexe pouvant être stockée dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-144">For the Western family of languages, if you are unsure which languages will be stored in a column or you expect more than one to be stored, a general workaround is to use the word breaker for the most complex language that might be stored in the column.</span></span> <span data-ttu-id="91da0-145">Par exemple, vous pouvez vous attendre à stocker du contenu en anglais, en espagnol et en allemand dans une colonne unique.</span><span class="sxs-lookup"><span data-stu-id="91da0-145">For instance, you might expect to store English, Spanish and German content in a single column.</span></span> <span data-ttu-id="91da0-146">Ces trois langues occidentales possèdent des modes d'analyse lexicale très semblables, les modes allemands étant les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="91da0-146">These three Western languages possess very similar word-breaking patterns, with the German patterns being the most complex.</span></span> <span data-ttu-id="91da0-147">Par conséquent, un bon choix dans ce cas serait d'utiliser l'analyseur lexical allemand, qui doit être en mesure de traiter le texte anglais et espagnol correctement.</span><span class="sxs-lookup"><span data-stu-id="91da0-147">Therefore, a good choice is this case would be to use the German word breaker, which should be able to process English and Spanish text correctly.</span></span> <span data-ttu-id="91da0-148">Par contre, il se peut que l'analyseur lexical anglais ne puisse pas traiter parfaitement le texte allemand à cause des mots composés allemands.</span><span class="sxs-lookup"><span data-stu-id="91da0-148">In contrast, the English word breaker might not process German text perfectly because of the compound words of German.</span></span>  
  
 <span data-ttu-id="91da0-149">Notez que l'utilisation de l'analyseur lexical de la langue la plus complexe dans une famille de langues ne garantit pas l'indexation parfaite de chaque langue de la famille.</span><span class="sxs-lookup"><span data-stu-id="91da0-149">Note that using the word breaker of the most complex language in a language family does not guarantee perfect indexing of every language in the family.</span></span> <span data-ttu-id="91da0-150">Il peut y avoir des cas où l'analyseur lexical le plus complexe ne peut pas gérer correctement le texte écrit dans une autre langue.</span><span class="sxs-lookup"><span data-stu-id="91da0-150">Corner cases might exist in which the most complex word breaker cannot correctly handle text written in another language.</span></span>  
  

  
### <a name="non-western-languages"></a><span data-ttu-id="91da0-151">Langues non occidentales</span><span class="sxs-lookup"><span data-stu-id="91da0-151">Non Western Languages</span></span>  
 <span data-ttu-id="91da0-152">Pour les langues non occidentales (telles que chinois, japonais, hindi, etc.), la solution de contournement précitée ne fonctionne pas nécessairement, pour des raisons linguistiques.</span><span class="sxs-lookup"><span data-stu-id="91da0-152">For non Western languages (such as Chinese, Japanese, Hindi, and so forth) the above workaround does not necessarily work, for linguistic reasons.</span></span> <span data-ttu-id="91da0-153">Pour les langues non occidentales, considérez l'une des solutions de contournement suivantes :</span><span class="sxs-lookup"><span data-stu-id="91da0-153">For non Western languages, consider one of the following workarounds:</span></span>  
  
-   <span data-ttu-id="91da0-154">Pour les langues de familles différentes</span><span class="sxs-lookup"><span data-stu-id="91da0-154">For languages from different families</span></span>  
  
     <span data-ttu-id="91da0-155">Si une colonne peut contenir des langues complètement différentes, par exemple l'espagnol et le japonais, pensez à stocker le contenu de langues différentes dans des colonnes séparées.</span><span class="sxs-lookup"><span data-stu-id="91da0-155">If a column might contain dramatically different languages, for example, Spanish and Japanese, consider storing the content of different languages in separate columns.</span></span> <span data-ttu-id="91da0-156">Cela vous permettrait d'utiliser l'analyseur lexical spécifique à une langue pour chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-156">This would allow you to use the language-specific word breaker for each column.</span></span> <span data-ttu-id="91da0-157">Si vous choisissez cette solution et que vous ne connaissez pas la langue de la requête à l'heure de la requête, vous pouvez devoir lancer la requête par rapport aux deux colonnes afin de faire en sorte que la requête recherche la bonne ligne ou le bon document.</span><span class="sxs-lookup"><span data-stu-id="91da0-157">If you choose this solution and you don't know the query language at query time, you might need to issue the query against both columns to ensure that the query finds the right row or document.</span></span>  
  
-   <span data-ttu-id="91da0-158">Pour le contenu binaire (par exemple, les documents Microsoft Word)</span><span class="sxs-lookup"><span data-stu-id="91da0-158">For Binary content (such as Microsoft Word documents)</span></span>  
  
     <span data-ttu-id="91da0-159">Lorsque le contenu indexé est de type `binary`, le filtre de recherche en texte intégral qui traite le contenu textuel avant de l'envoyer à l'analyseur lexical peut respecter des balises de langue spécifiques existantes dans le fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="91da0-159">When the indexed content is of `binary` type, the full-text search filter that processes the textual content before sending it to the word breaker might honor specific language tags existing within the binary file.</span></span> <span data-ttu-id="91da0-160">Dans ce cas, au moment de l'indexation, le filtre émettra le bon LCID pour un document ou une section d'un document.</span><span class="sxs-lookup"><span data-stu-id="91da0-160">In this case, at indexing time, the filter will emit the right LCID for a document or section of a document.</span></span> <span data-ttu-id="91da0-161">Le moteur d'indexation et de recherche en texte intégral appellera ensuite l'analyseur lexical pour la langue correspondant à ce LCID.</span><span class="sxs-lookup"><span data-stu-id="91da0-161">The Full-Text Engine will then call the word breaker for the language with that LCID.</span></span> <span data-ttu-id="91da0-162">Toutefois, après avoir indexé un contenu multilingue, nous vous recommandons de vérifier que le contenu a été indexé correctement.</span><span class="sxs-lookup"><span data-stu-id="91da0-162">However, after indexing multi language content, we recommend that you verify that the content was correctly indexed.</span></span>  
  
-   <span data-ttu-id="91da0-163">Pour un contenu de texte brut</span><span class="sxs-lookup"><span data-stu-id="91da0-163">For plain text content</span></span>  
  
     <span data-ttu-id="91da0-164">Lorsque votre contenu est du texte brut, vous pouvez le convertir en type de données `xml` et ajouter les balises de langue qui indiquent la langue qui correspond à chaque document ou section de document spécifique.</span><span class="sxs-lookup"><span data-stu-id="91da0-164">When your content is plain text, you can convert it to the `xml` data type and add language tags that indicate the language corresponding to each specific document or document section.</span></span> <span data-ttu-id="91da0-165">Pour que cette option fonctionne toutefois, vous devez connaître la langue avant l'indexation de recherche en texte intégral.</span><span class="sxs-lookup"><span data-stu-id="91da0-165">For this to work, however, you need to know the language before full-text indexing.</span></span>  
  

  
##  <a name="stemming"></a><a name="stemming"></a> <span data-ttu-id="91da0-166">Recherche de radical</span><span class="sxs-lookup"><span data-stu-id="91da0-166">Stemming</span></span>  
 <span data-ttu-id="91da0-167">La recherche de radical est un autre point à prendre en considération lors du choix de la langue de votre colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-167">An additional consideration when choosing your column-level language is stemming.</span></span> <span data-ttu-id="91da0-168">La*recherche de radical* dans les requêtes de texte intégral se définit comme la recherche de toutes les formes fléchies d’un mot dans une langue particulière.</span><span class="sxs-lookup"><span data-stu-id="91da0-168">*Stemming* in full-text queries is the process of searching for all stemmed (inflectional) forms of a word in a particular language.</span></span> <span data-ttu-id="91da0-169">Lorsque vous utilisez un analyseur lexical générique pour traiter plusieurs langues, le processus de recherche de radical fonctionne uniquement pour la langue spécifiée pour la colonne, et non pour d'autres langues dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="91da0-169">When you use a generic word breaker to process several languages, the stemming process works only for the language specified for the column, not for other languages in the column.</span></span> <span data-ttu-id="91da0-170">Par exemple, les générateur de formes dérivées allemands ne fonctionnent pas pour l'anglais et l'espagnol (etc.).</span><span class="sxs-lookup"><span data-stu-id="91da0-170">For example, German stemmers do not work for English or Spanish (and so forth).</span></span> <span data-ttu-id="91da0-171">Cela peut affecter votre rappel, selon la langue que vous choisissez au moment de la requête.</span><span class="sxs-lookup"><span data-stu-id="91da0-171">This might affect your recall depending of which language you choose at query time.</span></span>  
  

  
##  <a name="effect-of-column-type-on-full-text-search"></a><a name="type"></a> <span data-ttu-id="91da0-172">Effet du type de colonne sur la recherche en texte intégral</span><span class="sxs-lookup"><span data-stu-id="91da0-172">Effect of Column Type on Full-Text Search</span></span>  
 <span data-ttu-id="91da0-173">Un autre point à prendre en considération dans le choix de la langue est lié au mode de représentation des données.</span><span class="sxs-lookup"><span data-stu-id="91da0-173">Another consideration in language choice is related to how the data is represented.</span></span> <span data-ttu-id="91da0-174">Pour les données non stockées dans une colonne `varbinary(max)`, aucun filtrage particulier n'est effectué.</span><span class="sxs-lookup"><span data-stu-id="91da0-174">For data that is not stored in `varbinary(max)` column, no special filtering is performed.</span></span> <span data-ttu-id="91da0-175">À la place, le texte est généralement traité tel quel par le composant de séparation des mots.</span><span class="sxs-lookup"><span data-stu-id="91da0-175">Rather, the text is generally passed through the word breaking component as-is.</span></span>  
  
 <span data-ttu-id="91da0-176">Les analyseurs lexicaux sont, aussi, principalement conçus pour traiter le texte écrit.</span><span class="sxs-lookup"><span data-stu-id="91da0-176">Also, word breakers are designed mainly to process written text.</span></span> <span data-ttu-id="91da0-177">Par conséquent, si votre texte contient un balisage quelconque (par exemple du code HTML), vous risquez de ne pas obtenir une précision linguistique importante durant l'indexation et la recherche.</span><span class="sxs-lookup"><span data-stu-id="91da0-177">So, if you have any type of markup (such as HTML) on your text, you may not get great linguistic accuracy during indexing and search.</span></span> <span data-ttu-id="91da0-178">Dans ce cas, vous avez deux possibilités : la méthode recommandée consiste simplement à stocker les données de texte dans la `varbinary(max)` colonne et à indiquer le type de document afin qu’elles puissent être filtrées.</span><span class="sxs-lookup"><span data-stu-id="91da0-178">In that case, you have two choices-the preferred method is simply to store the text data in `varbinary(max)` column, and to indicate its document type so it may be filtered.</span></span> <span data-ttu-id="91da0-179">Si ce choix ne vous convient pas, utilisez un analyseur lexical neutre et, si possible, ajoutez des données de balisage (par exemple « br » en langage HTML) à vos listes de mots parasites.</span><span class="sxs-lookup"><span data-stu-id="91da0-179">If this is not an option, you may consider using the neutral word breaker and, if possible, adding markup data (such as 'br' in HTML) to your noise word lists.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91da0-180">L'identification de la racine linguistique n'intervient pas lorsque vous spécifiez la langue neutre.</span><span class="sxs-lookup"><span data-stu-id="91da0-180">Language based stemming does not come into play when you specify the neutral language.</span></span>  
  

  
##  <a name="specifying-a-non-default-column-level-language-in-a-full-text-query"></a><a name="nondef"></a> <span data-ttu-id="91da0-181">Spécification d'une langue de colonne autre que la langue par défaut dans un requête de texte intégral</span><span class="sxs-lookup"><span data-stu-id="91da0-181">Specifying a Non-default Column-Level Language in a Full-Text Query</span></span>  
 <span data-ttu-id="91da0-182">Par défaut, dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la recherche en texte intégral analyse les termes de la requête en utilisant la langue spécifiée pour chaque colonne incluse dans la clause de texte intégral.</span><span class="sxs-lookup"><span data-stu-id="91da0-182">By default, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], full-text search will parse the query terms using the language specified for each column that is included in the full-text clause.</span></span> <span data-ttu-id="91da0-183">Pour remplacer ce comportement, spécifiez une langue autre que par défaut au moment de la requête.</span><span class="sxs-lookup"><span data-stu-id="91da0-183">To override this behavior, specify a nondefault language at query time.</span></span> <span data-ttu-id="91da0-184">Pour les langues prises en charge dont les ressources sont installées, la clause LANGUAGE *language_term* d’une requête [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)ou [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) est utilisée pour spécifier la langue utilisée pour l’analyse lexicale, la recherche de radical, le dictionnaire des synonymes et le traitement des mots vides des termes de la requête.</span><span class="sxs-lookup"><span data-stu-id="91da0-184">For supported languages whose resources are installed, the LANGUAGE *language_term* clause of a [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) query can be used to specify the language used for word breaking, stemming, thesaurus, and stopword processing of the query terms.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="91da0-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91da0-185">See Also</span></span>  
 <span data-ttu-id="91da0-186">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-186">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="91da0-187">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-187">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="91da0-188">[Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-188">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="91da0-189">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-189">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="91da0-190">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-190">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 <span data-ttu-id="91da0-191">[Configurer et gérer des filtres pour la recherche](configure-and-manage-filters-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="91da0-191">[Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md) </span></span>  
 <span data-ttu-id="91da0-192">[sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-192">[sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) </span></span>  
 <span data-ttu-id="91da0-193">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91da0-193">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span></span>  
 [<span data-ttu-id="91da0-194">Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche</span><span class="sxs-lookup"><span data-stu-id="91da0-194">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  