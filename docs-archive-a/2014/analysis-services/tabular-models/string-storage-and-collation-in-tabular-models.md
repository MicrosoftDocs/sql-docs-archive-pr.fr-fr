---
title: Stockage et classement des chaînes dans les modèles tabulaires | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8516f0ad-32ee-4688-a304-e705143642ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3aad4cf16c39897bc0796f4fb161eaf39abdb5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706788"
---
# <a name="string-storage-and-collation-in-tabular-models"></a><span data-ttu-id="6ba2e-102">Stockage de chaîne et classement dans les modèles tabulaires</span><span class="sxs-lookup"><span data-stu-id="6ba2e-102">String Storage and Collation in Tabular Models</span></span>
  <span data-ttu-id="6ba2e-103">Les chaînes (valeurs texte) sont stockées dans un format fortement compressé dans les modèles tabulaires ; en raison de cette compression, vous pouvez obtenir des résultats inattendus lorsque vous récupérez des chaînes entières ou partielles.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-103">Strings (text values) are stored in a highly compressed format in tabular models; because of this compression, you can get unexpected results when you retrieve entire or partial strings.</span></span> <span data-ttu-id="6ba2e-104">En outre, comme les paramètres régionaux et les classements de chaîne sont hérités hiérarchiquement de l'objet parent le plus proche, si le langage de chaîne n'est pas défini explicitement, les paramètres régionaux et le classement du parent peuvent affecter la façon dont chaque chaîne est stockée et si la chaîne doit être unique ou combinée avec des chaînes semblables tel que le défini le classement parent.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-104">Also, because string locale and collations are inherited hierarchically from the closest parent object, if the string language is not explicitly defined, the locale and collation of the parent can affect how each string is stored and whether the string is unique or conflated with similar strings as defined by the parent collation.</span></span>  
  
 <span data-ttu-id="6ba2e-105">Cette rubrique décrit le mécanisme par lequel les chaînes sont compressées et stockées, et fournit des exemples d'utilisation du classement et du langage qui affectent les résultats des formules de texte dans les modèles tabulaires.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-105">This topic describes the mechanism by which strings are compressed and stored, and provides examples of how collation and language affect the results of text formulas in tabular models.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="6ba2e-106">Stockage</span><span class="sxs-lookup"><span data-stu-id="6ba2e-106">Storage</span></span>  
 <span data-ttu-id="6ba2e-107">Dans les modèles tabulaires toutes les données sont fortement compressées de façon à ce qu'elles tiennent en mémoire.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-107">In tabular models all data is highly compressed to better fit in memory.</span></span> <span data-ttu-id="6ba2e-108">Par conséquent, toutes les chaînes qui peuvent être considérées comme des chaînes lexicales équivalentes sont stockées une seule fois.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-108">As a consequence, all strings that can be considered lexically equivalent are stored only once.</span></span> <span data-ttu-id="6ba2e-109">La première instance de la chaîne est utilisée comme la représentation canonique et par la suite chaque chaîne équivalente est indexée à la même valeur compressée que la première occurrence.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-109">The first instance of the string is used as the canonical representation and thereafter each equivalent string is indexed to the same compressed value as the first occurrence.</span></span>  
  
 <span data-ttu-id="6ba2e-110">La question clé est la suivante : qu'est-ce qui constitue une chaîne lexicale équivalente ?</span><span class="sxs-lookup"><span data-stu-id="6ba2e-110">The key question is: what constitutes a lexically equivalent string?</span></span> <span data-ttu-id="6ba2e-111">Deux chaînes sont considérées comme des chaînes lexicales équivalentes si elles peuvent être considérées comme même mot.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-111">Two strings are considered lexically equivalent if they can be considered as the same word.</span></span> <span data-ttu-id="6ba2e-112">Par exemple, lorsque vous recherchez le mot **violon** dans un dictionnaire, vous pouvez trouver l'entrée **Violon** ou **violon**, en fonction de la stratégie éditoriale du dictionnaire, mais en général vous considérez les deux mots comme équivalents, et vous ignorez la mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-112">For example, in English when you search for the word **violin** in a dictionary, you might find the entry **Violin** or **violin**, depending on the editorial policy of the dictionary, but generally you consider both words equivalent, and disregard the difference in capitalization.</span></span> <span data-ttu-id="6ba2e-113">Dans un modèle tabulaire, le facteur qui détermine si deux chaînes sont des chaînes lexicales équivalentes n'est pas une stratégie éditoriale ou une préférence de l'utilisateur, mais les paramètres régionaux et l'ordre de classement affectés à la colonne.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-113">In a tabular model, the factor that determines whether two strings are lexically equivalent is not editorial policy or even user preference, but the locale and collation order assigned to the column.</span></span>  
  
 <span data-ttu-id="6ba2e-114">Par conséquent, le choix en faveur de la gestion des majuscules et des minuscules de la même façon ou non dépend du classement et des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-114">Therefore, the decision of whether uppercase and lowercase letters should be handled as the same or different depends on the collation and locale.</span></span> <span data-ttu-id="6ba2e-115">Pour tout mot particulier dans ces paramètres régionaux, la première occurrence du mot trouvée dans une colonne particulière sert par conséquent de représentation canonique de ce mot et cette chaîne est stockée au format non compressé.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-115">For any particular word within that locale, the first occurrence of the word that is found within a particular column therefore serves as the canonical representation of that word and that string is stored in uncompressed format.</span></span>  <span data-ttu-id="6ba2e-116">Toutes les autres chaînes sont testées sur la première occurrence, et si elles correspondent au test d'équivalence, elles sont affectées à la valeur compressée de la première occurrence.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-116">All other strings are tested against the first occurrence, and if they match the equivalence test, they are assigned to the compressed value of the first occurrence.</span></span> <span data-ttu-id="6ba2e-117">Ultérieurement, lorsque les valeurs compressées sont récupérées, elles sont représentées à l'aide de la valeur non compressée de la première occurrence de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-117">Later, when the compressed values are retrieved they are represented using the uncompressed value of the first occurrence of the string.</span></span>  
  
 <span data-ttu-id="6ba2e-118">Un exemple permettra de mieux comprendre le fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-118">An example will help to clarify how this works.</span></span> <span data-ttu-id="6ba2e-119">La colonne suivante « Classification - anglais » a été extraite d'une table qui contient des informations sur les plantes et les arbres.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-119">The following column "Classification - English" was extracted from a table that contains information about plants and trees.</span></span> <span data-ttu-id="6ba2e-120">Pour chaque plante (les noms des plantes ne sont pas affichés ici) la colonne de classification affiche la catégorie générale de la plante.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-120">For each plant (the names of the plants are not shown here) the classification column shows the general category of plant.</span></span>  
  
|<span data-ttu-id="6ba2e-121">Classification - anglais</span><span class="sxs-lookup"><span data-stu-id="6ba2e-121">Classification - English</span></span>|  
|-------------------------------|  
|<span data-ttu-id="6ba2e-122">trEE</span><span class="sxs-lookup"><span data-stu-id="6ba2e-122">trEE</span></span>|  
|<span data-ttu-id="6ba2e-123">PlAnT</span><span class="sxs-lookup"><span data-stu-id="6ba2e-123">PlAnT</span></span>|  
|<span data-ttu-id="6ba2e-124">trEE</span><span class="sxs-lookup"><span data-stu-id="6ba2e-124">TREE</span></span>|  
|<span data-ttu-id="6ba2e-125">PlAnT</span><span class="sxs-lookup"><span data-stu-id="6ba2e-125">PLANT</span></span>|  
|<span data-ttu-id="6ba2e-126">Plant</span><span class="sxs-lookup"><span data-stu-id="6ba2e-126">Plant</span></span>|  
|<span data-ttu-id="6ba2e-127">Arborescence</span><span class="sxs-lookup"><span data-stu-id="6ba2e-127">Tree</span></span>|  
|<span data-ttu-id="6ba2e-128">PlAnT</span><span class="sxs-lookup"><span data-stu-id="6ba2e-128">plant</span></span>|  
|<span data-ttu-id="6ba2e-129">trEE</span><span class="sxs-lookup"><span data-stu-id="6ba2e-129">tReE</span></span>|  
|<span data-ttu-id="6ba2e-130">tree</span><span class="sxs-lookup"><span data-stu-id="6ba2e-130">tree</span></span>|  
|<span data-ttu-id="6ba2e-131">PlAnT</span><span class="sxs-lookup"><span data-stu-id="6ba2e-131">pLaNt</span></span>|  
|<span data-ttu-id="6ba2e-132">trEE</span><span class="sxs-lookup"><span data-stu-id="6ba2e-132">tREE</span></span>|  
  
 <span data-ttu-id="6ba2e-133">Les données peuvent être issues de nombreuses sources, et par conséquent la casse et l'utilisation des accents sont incohérentes, et la base de données relationnelle a stocké ces différences en l'état.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-133">Perhaps the data came from many different sources, and so the casing and use of accents was inconsistent, and the relational database stored those differences as is.</span></span> <span data-ttu-id="6ba2e-134">Mais en général les valeurs sont **Plant** ou **Tree**, uniquement avec une casse différente.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-134">But in general the values are either **Plant** or **Tree**, just with different casing.</span></span>  
  
 <span data-ttu-id="6ba2e-135">Lorsque ces valeurs sont chargées dans un modèle tabulaire qui utilise le classement et l’ordre de tri par défaut pour l’anglais (États-Unis), la casse n’est pas importante, donc seules deux valeurs sont stockées pour la colonne entière :</span><span class="sxs-lookup"><span data-stu-id="6ba2e-135">When these values are loaded into a tabular model that uses the default collation and sorting order for English (United States), case is not important, so only two values would be stored for the entire column:</span></span>  
  
|<span data-ttu-id="6ba2e-136">Classification - anglais</span><span class="sxs-lookup"><span data-stu-id="6ba2e-136">Classification - English</span></span>|  
|-------------------------------|  
|<span data-ttu-id="6ba2e-137">trEE</span><span class="sxs-lookup"><span data-stu-id="6ba2e-137">trEE</span></span>|  
|<span data-ttu-id="6ba2e-138">PlAnT</span><span class="sxs-lookup"><span data-stu-id="6ba2e-138">PlAnT</span></span>|  
  
 <span data-ttu-id="6ba2e-139">Si vous utilisez la colonne, **classification-anglais**, dans votre modèle, où vous affichez la classification des plantes, vous ne verrez pas les valeurs d’origine, avec leurs différentes utilisations des majuscules et des minuscules, mais uniquement la première instance.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-139">If you use the column, **Classification - English**, in your model, wherever you display plant classification you will see not the original values, with their various uses of upper and lower case, but only the first instance.</span></span> <span data-ttu-id="6ba2e-140">En effet, toutes les variantes de majuscules et minuscules de **tree** sont considérées comme équivalentes dans ce classement et ces paramètres régionaux ; par conséquent, une seule chaîne a été conservée et la première instance de cette chaîne qui est rencontrée par le système est celle qui est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-140">The reason is that all the uppercase and lowercase variants of **tree** are considered equivalent in this collation and locale; therefore, only one string was preserved and the first instance of that string that is encountered by the system is the one that is saved.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6ba2e-141">Vous pouvez décider de définir la première chaîne à stocker, en fonction de ce que vous considérez correct, mais cette opération peut être très difficile à effectuer.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-141">You might decide that you want to define which string will be the first to store, according to what you consider correct, but this could be very hard to so.</span></span> <span data-ttu-id="6ba2e-142">Il n'existe aucun moyen simple de déterminer à l'avance quelle ligne doit être traitée en premier par le moteur, étant donné que toutes les valeurs sont considérées comme identiques.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-142">There is no simple way to determine in advance which row should be processed first by the engine, given that all values are considered to be the same.</span></span> <span data-ttu-id="6ba2e-143">Au lieu de cela, si vous devez définir la valeur standard, vous devez nettoyer toutes vos chaînes avant de charger le modèle.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-143">Instead, if you need to set the standard value, you should cleanse all your strings before loading the model.</span></span>  
  
## <a name="locale-and-collation-order"></a><span data-ttu-id="6ba2e-144">Ordre des paramètres régionaux et de classement</span><span class="sxs-lookup"><span data-stu-id="6ba2e-144">Locale and Collation Order</span></span>  
 <span data-ttu-id="6ba2e-145">Lors de la comparaison de chaînes (valeurs texte), ce qui définit l'équivalence est normalement l'aspect culturel de la façon dont ces chaînes sont interprétées.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-145">When comparing strings (text values), what defines equivalence is normally the cultural aspect of how such strings are interpreted.</span></span> <span data-ttu-id="6ba2e-146">Dans certaines cultures un accent ou la mise en majuscules d'un caractère peut changer complètement la signification de la chaîne ; par conséquent, généralement ces différences sont prises en compte pour déterminer l'équivalence dans n'importe quelle langue ou région spécifique.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-146">In some cultures an accent or the capitalization of a character can completely change the meaning of the string; therefore, typically such differences are considered when determining equivalency for any particular language or region.</span></span>  
  
 <span data-ttu-id="6ba2e-147">Généralement, lorsque vous utilisez votre ordinateur elle est déjà configurée pour correspondre à vos propres attentes culturelles et comportement linguistique, et les opérations de chaîne, telles que le tri et la comparaison des valeurs texte se comportent de la façon attendue.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-147">Usually, when you use your computer it is already configured to match your own cultural expectations and linguistic behavior, and string operations such as sorting and comparing text values behaves as you would expect.</span></span> <span data-ttu-id="6ba2e-148">Les paramètres qui contrôlent le comportement spécifique à une langue sont définis par les **paramètres régionaux** dans Windows.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-148">The settings that control language-specific behavior are defined through the **Locale and Regional** settings in Windows.</span></span> <span data-ttu-id="6ba2e-149">Les applications lisent ces paramètres et modifient leur comportement en conséquence.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-149">Applications read those settings and change their behavior accordingly.</span></span> <span data-ttu-id="6ba2e-150">Dans certains cas, une application peut avoir une fonctionnalité qui vous permet de modifier le comportement culturel de l'application ou la façon dont les chaînes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-150">In some cases, an application might have a feature that allows you to change the cultural behavior of the application or the way in which strings are compared.</span></span>  
  
 <span data-ttu-id="6ba2e-151">Lorsque vous créez une base de données model tabulaire, par défaut la base de données hérite ces paramètres culturels et linguistiques sous la forme d'un identificateur de langue et d'un classement.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-151">When you are creating a tabular model database, by default the database inherits these cultural and linguistic settings in the form of a language identifier and collation.</span></span>  
  
-   <span data-ttu-id="6ba2e-152">L'identificateur de langue définit le jeu de caractères que vous voulez utiliser pour vos chaînes en fonction de la culture.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-152">The language identifier defines the character set you want to use for your strings according to your culture.</span></span>  
  
-   <span data-ttu-id="6ba2e-153">Le classement définit l'ordre des caractères et leur équivalence.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-153">The collation defines the ordering of the characters and their equivalence.</span></span>  
  
 <span data-ttu-id="6ba2e-154">Il est important de noter qu'un identificateur de langue identifie non seulement une langue mais, également le pays ou la zone où la langue est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-154">It is important to note that a language identifier not only identifies a language but, also the country or region where the language is used.</span></span> <span data-ttu-id="6ba2e-155">Chaque identificateur de langue a également une spécification de classement par défaut.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-155">Each language identifier also has a default collation specification.</span></span> <span data-ttu-id="6ba2e-156">Pour plus d'informations sur les identificateurs de langue, consultez [ID de paramètres régionaux assignés par Microsoft](https://msdn.microsoft.com/goglobal/bb964664.aspx).</span><span class="sxs-lookup"><span data-stu-id="6ba2e-156">For more information about language identifiers, see [Locale IDs Assigned by Microsoft](https://msdn.microsoft.com/goglobal/bb964664.aspx).</span></span> <span data-ttu-id="6ba2e-157">Vous pouvez utiliser la colonne LCID Dec pour obtenir l'ID correct en insérant manuellement une valeur.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-157">You can use the LCID Dec column to get the correct ID when manually inserting a value.</span></span> <span data-ttu-id="6ba2e-158">Pour plus d’informations sur le concept SQL des classements, consultez [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations).</span><span class="sxs-lookup"><span data-stu-id="6ba2e-158">For more information about the SQL concept of collations, see [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations).</span></span> <span data-ttu-id="6ba2e-159">Pour plus d’informations sur les indicateurs de classement et les styles de comparaison pour les noms de classements Windows, consultez [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="6ba2e-159">For information about the collation designators and the comparison styles for Windows collation names, see [Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql).</span></span> <span data-ttu-id="6ba2e-160">La rubrique [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) mappe les noms de classements Windows aux noms utilisés pour SQL.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-160">The topic, [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql), maps the Windows collation names to the names used for SQL.</span></span>  
  
 <span data-ttu-id="6ba2e-161">Une fois que votre base de données model tabulaire a été créée, tous les nouveaux objets du modèle héritent des attributs de langue et de classement des attributs de la base de données.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-161">Once your tabular model database has been created, all new objects in the model will inherit the language and collation attributes from the database attributes.</span></span> <span data-ttu-id="6ba2e-162">Cela est vrai pour tous les objets.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-162">This is true for all objects.</span></span> <span data-ttu-id="6ba2e-163">Le chemin d'accès d'héritage commence à l'objet, examine le parent pour trouver tous les attributs de langue et de classement à hériter, et si aucun attribut n'est trouvé, continue vers le haut et recherche les attributs de langue et de classement au niveau de la base de données.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-163">The inheritance path begins at the object, looks at the parent for any language and collation attributes to inherit, and if none are found, continues to the top and finds the language and collation attributes at the database level.</span></span> <span data-ttu-id="6ba2e-164">En d'autres termes, si vous ne spécifiez pas les attributs de langue et de classement pour un objet, par défaut, l'objet hérite les attributs de son parent plus proche.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-164">In other words, if you do not specify the language and collation attributes for an object, by default, the object inherits the attributes of its closest parent.</span></span>  
  
 <span data-ttu-id="6ba2e-165">Pour les colonnes, les attributs de langue et de classement sont hérités au moment de la création, selon les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ba2e-165">For columns, the language and collation attributes are inherited at creation, according to the following rules:</span></span>  
  
1.  <span data-ttu-id="6ba2e-166">L'objet dimension parente fait l'objet de recherches pour trouver les attributs de langue et de classement.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-166">The parent dimension object is searched for language and collation attributes.</span></span> <span data-ttu-id="6ba2e-167">Si les deux valeurs existent, elles sont copiées dans les attributs de colonne ; si une seule valeur existe, l'autre est déduite de la valeur existante et les deux sont affectées ; si aucune valeur n'existe, passez à l'étape suivante.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-167">If both values exist, they are copied to the column attributes; if only one exists, the other is inferred from the existing one and both are assigned; if none exist, move to next step.</span></span>  
  
2.  <span data-ttu-id="6ba2e-168">L'objet base de données fait l'objet de recherche à l'aide du processus décrit à l'étape 1 pour les dimensions ; si aucun attribut n'est trouvé, passez à l'étape suivante.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-168">The database object is searched using the same process described in Step 1 for dimensions; if no attributes are found, move to the next step.</span></span>  
  
3.  <span data-ttu-id="6ba2e-169">L'objet serveur fait l'objet de recherche à l'aide du processus décrit à l'étape 1 pour les dimensions ; si aucun attribut n'est trouvé, la colonne utilise l'identificateur de langue Windows et déduit l'attribut de classement de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-169">The server object is searched using the same process described in Step 1 for dimensions; if no attributes are found, the column uses the Windows language identifier and infers the collation attribute from that value.</span></span>  
  
 <span data-ttu-id="6ba2e-170">Il est important de noter qu'en général l'identificateur de langue et l'ordre de classement dans la base de données source ont peu d'effet, si ce n'est aucun, sur la façon dont les valeurs sont stockées dans la colonne du modèle tabulaire.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-170">It is important to note that typically the language identifier and collation order in the source database has little to no effect on how values are stored in the tabular model column.</span></span> <span data-ttu-id="6ba2e-171">L'exception indique si la base de données source transforme ou filtre les valeurs demandées.</span><span class="sxs-lookup"><span data-stu-id="6ba2e-171">The exception is if the source database transforms or filters the requested values.</span></span>  
  
  