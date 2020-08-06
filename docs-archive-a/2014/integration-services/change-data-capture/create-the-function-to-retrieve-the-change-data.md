---
title: Créer la fonction de récupération des données modifiées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],creating function
ms.assetid: 55dd0946-bd67-4490-9971-12dfb5b9de94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc1d5af0a64225aca4ff54570ad6504d25d62812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707731"
---
# <a name="create-the-function-to-retrieve-the-change-data"></a>Créer la fonction de récupération des données modifiées
  Une fois que vous avez terminé le flux de contrôle d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui effectue un chargement incrémentiel des données modifiées, la tâche suivante consiste à créer une fonction table qui récupère les données modifiées. Vous ne devez créer cette fonction qu'une seule fois avant le premier chargement incrémentiel.  
  
> [!NOTE]  
>  La création d'une fonction de récupération des données modifiées est la deuxième étape du processus de création d'un package qui effectue un chargement incrémentiel des données modifiées. Pour obtenir une description du processus global de la création de ce package, consultez [Capture de données modifiées &#40;SSIS&#41;](change-data-capture-ssis.md).  
  
## <a name="design-considerations-for-change-data-capture-functions"></a>Considérations relatives à la conception de fonctions de capture de données modifiées  
 Pour récupérer des données modifiées, un composant source dans le flux de données du package appelle l'une des fonctions de requête de capture de données modifiées suivantes :  
  
-   **cdc.fn_cdc_get_net_changes_<capture_instance>** Pour cette requête, la ligne unique renvoyée pour chaque mise à jour contient l’état final de chaque ligne modifiée. Dans la plupart des cas, vous n'avez besoin que des données retournées par une requête des modifications nettes. Pour plus d’informations, consultez [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).  
  
-   **cdc.fn_cdc_get_all_changes_<capture_instance>** Cette requête renvoie toutes les modifications qui se sont produites dans chaque ligne au cours de l’intervalle de capture. Pour plus d’informations, consultez [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).  
  
 Le composant source prend ensuite les résultats retournés par la fonction et les passe aux transformations et aux destinations en aval qui appliquent les données modifiées à la destination finale.  
  
 Toutefois, un composant source [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne peut pas appeler directement ces fonctions de capture de données modifiées. Un composant source [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nécessite des métadonnées sur les colonnes retournées par la requête. Les fonctions de capture de données modifiées ne définissent pas les colonnes de leur table de sortie. Ces fonctions ne retournent donc pas suffisamment de métadonnées pour un composant source [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Utilisez plutôt une fonction wrapper table car ce type de fonction définit explicitement les colonnes de sa table de sortie dans sa clause RETURNS. Cette définition explicite de colonnes fournit les métadonnées nécessaires à un composant source [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Vous devez créer cette fonction pour chaque table pour laquelle vous souhaitez récupérer des données modifiées.  
  
 Vous disposez de deux options pour créer une fonction wrapper table qui appelle la fonction de requête de capture de données modifiées :  
  
-   Vous pouvez appeler la procédure stockée système **sys.sp_cdc_generate_wrapper_function** pour créer les fonctions table pour vous.  
  
-   Vous pouvez écrire votre propre fonction table en utilisant les indications et l'exemple donnés dans cette rubrique.  
  
## <a name="calling-a-stored-procedure-to-create-the-table-valued-function"></a>Appel d'une procédure stockée pour créer la fonction table  
 La méthode la plus rapide et la plus facile pour créer les fonctions table dont vous avez besoin consiste à appeler la procédure stockée système **sys.sp_cdc_generate_wrapper_function** . Cette procédure stockée génère des scripts permettant de créer des fonctions wrapper spécifiquement conçues pour répondre aux besoins d'un composant source [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  La procédure stockée système **sys.sp_cdc_generate_wrapper_function** ne crée pas directement les fonctions wrapper. À la place, elle génère les scripts CREATE pour les fonctions wrapper. Le développeur doit exécuter les scripts CREATE que la procédure stockée génère avant qu'un package de chargement incrémentiel puisse appeler les fonctions wrapper.  
  
 Pour maîtriser l'utilisation de cette procédure stockée système, vous devez comprendre ce qu'elle fait, les scripts qu'elle génère et les fonctions wrapper que les scripts créent.  
  
### <a name="understanding-and-using-the-stored-procedure"></a>Présentation et utilisation de la procédure stockée  
 La procédure stockée système **sys.sp_cdc_generate_wrapper_function** génère des scripts permettant de créer des fonctions wrapper utilisées par les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les premières lignes de la définition de la procédure stockée sont les suivantes :  
  
 `CREATE PROCEDURE sys.sp_cdc_generate_wrapper_function`  
  
 `(`  
  
 `@capture_instance sysname = null`  
  
 `@closed_high_end_point bit = 1,`  
  
 `@column_list = null,`  
  
 `@update_flag_list = null`  
  
 `)`  
  
 Tous les paramètres de la procédure stockée sont facultatifs. Si vous appelez la procédure stockée sans fournir des valeurs pour chacun des paramètres, elle crée des fonctions wrapper pour toutes les instances de capture auxquelles vous avez accès.  
  
> [!NOTE]  
>  Pour plus d'informations sur la syntaxe de cette procédure stockée et ses paramètres, consultez [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql).  
  
 La procédure stockée génère systématiquement une fonction wrapper pour retourner toutes les modifications de chaque instance de capture. Si le *@supports_net_changes* paramètre a été défini lors de la création de l’instance de capture, la procédure stockée génère également une fonction wrapper pour retourner les modifications nettes de chaque instance de capture applicable.  
  
 La procédure stockée retourne un jeu de résultats à deux colonnes :  
  
-   Le nom de la fonction wrapper générée par la procédure stockée. Cette procédure stockée dérive le nom de fonction du nom de l'instance de capture. (Le nom de la fonction est « fn_all_changes_ » suivi du nom de l'instance de capture. Le préfixe utilisé pour la fonction de suivi des modifications nettes, s'il est créé, est « fn_net_changes_ ».)  
  
-   L'instruction CREATE pour la fonction wrapper.  
  
### <a name="understanding-and-using-the-scripts-created-by-the-stored-procedure"></a>Présentation et utilisation des scripts créés par la procédure stockée  
 En général, un développeur utilise une instruction INSERT...EXEC pour appeler la procédure stockée **sys.sp_cdc_generate_wrapper_function** et enregistrer les scripts qu'elle crée dans une table temporaire. Chaque script peut ensuite être sélectionné et exécuté individuellement afin de créer la fonction wrapper correspondante. Toutefois, un développeur peut également utiliser un jeu de commandes SQL pour exécuter l'ensemble des scripts CREATE, tel qu'indiqué dans l'exemple de code suivant :  
  
```  
create table #wrapper_functions  
      (function_name sysname, create_stmt nvarchar(max))  
insert into #wrapper_functions  
exec sys.sp_cdc_generate_wrapper_function  
  
declare @stmt nvarchar(max)  
declare #hfunctions cursor local fast_forward for   
      select create_stmt from #wrapper_functions  
open #hfunctions  
fetch #hfunctions into @stmt  
while (@@fetch_status <> -1)  
begin  
      exec sp_executesql @stmt  
      fetch #hfunctions into @stmt  
end  
close #hfunctions  
deallocate #hfunctions  
```  
  
### <a name="understanding-and-using-the-functions-created-by-the-stored-procedure"></a>Présentation et utilisation des fonctions créées par la procédure stockée  
 Pour parcourir systématiquement la chronologie des données de modification capturées, les fonctions wrapper générées s’attendent à ce que le *@end_time* paramètre d’un intervalle soit le *@start_time* paramètre de l’intervalle suivant. Lorsque cette convention est suivie, les fonctions wrapper générées peuvent effectuer les tâches suivantes :  
  
-   Mapper les valeurs de date/d'heure aux valeurs LSN utilisées en interne.  
  
-   Garantir qu'aucune donnée n'est perdue ou répétée.  
  
 Pour simplifier l'interrogation de l'ensemble des lignes d'une table de modifications, les fonctions wrapper générées prennent également en charge les conventions suivantes :  
  
-   Si le paramètre @start_time est Null, les fonctions wrapper utilisent la valeur LSN la plus basse dans l’instance de capture comme limite inférieure de la requête.  
  
-   Si le paramètre @end_time est Null, les fonctions wrapper utilisent la valeur LSN la plus élevée dans l’instance de capture comme limite supérieure de la requête.  
  
 La plupart des utilisateurs doivent être en mesure d'utiliser les fonctions wrapper que la procédure stockée système **sys.sp_cdc_generate_wrapper_function** crée sans modification. Toutefois, pour personnaliser les fonctions wrapper, vous devez personnaliser les scripts CREATE avant de les exécuter.  
  
 Lorsque votre package appelle les fonctions wrapper, il doit fournir des valeurs pour trois paramètres. Ceux-ci sont similaires aux trois paramètres que les fonctions de capture de données modifiées utilisent. Ces trois paramètres sont les suivants :  
  
-   La valeur de date/d'heure de début et celle de date/d'heure de fin de l'intervalle. Lorsque les fonctions wrapper utilisent des valeurs de date/d'heure comme points pour l'intervalle de requête, les fonctions de capture de données modifiées utilisent deux valeurs LSN comme points de fin.  
  
-   Le filtre de lignes. Pour les fonctions wrapper et les fonctions de capture de données modifiées, le *@row_filter_option* paramètre est le même. Pour plus d’informations, consultez [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) et [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).  
  
 Le jeu de résultats retourné par les fonctions wrapper inclut les données suivantes :  
  
-   Toutes les colonnes de données modifiées requises.  
  
-   Une colonne appelée __CDC_OPERATION qui utilise un champ à un ou deux caractères qui identifie l'opération associée à la ligne. Les valeurs valides de ce champ sont les suivantes : « I » pour insert (insertion), « D » pour delete (suppression), « UO » pour update old values (mise à jour des anciennes valeurs) et « UN » pour update new values (mise à jour des nouvelles valeurs).  
  
-   Mettre à jour les indicateurs, lorsque vous les demandez, qui apparaissent sous la forme de colonnes de bits après le code d’opération et dans l’ordre spécifié dans le *@update_flag_list* paramètre. Ces colonnes sont nommées en ajoutant « _uflag » au nom de colonne associé.  
  
 Si votre package appelle une fonction wrapper qui interroge toutes les modifications, elle retourne également les colonnes __CDC_STARTLSN et \__CDC_SEQVAL. Ces deux colonnes deviennent les première et deuxième colonnes, respectivement, du jeu de résultats. La fonction wrapper trie également le jeu de résultats en fonction de ces deux colonnes.  
  
## <a name="writing-your-own-table-value-function"></a>Écriture de votre propre fonction table  
 Vous pouvez également utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire votre propre fonction wrapper table qui appelle la fonction de requête de capture de données modifiées et qui stocke la fonction wrapper table dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la création d’une fonction Transact-SQL, consultez [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).  
  
 L'exemple suivant définit une fonction table qui récupère les modifications d'une table Customer pour l'intervalle de modification spécifié. Cette fonction utilise des fonctions de capture de données modifiées pour mapper les valeurs `datetime` aux valeurs binaires de numéros séquentiels dans le journal que les tables de modifications utilisent en interne. Cette fonction gère également plusieurs conditions spéciales :  
  
-   Lorsqu'une valeur NULL est passée pour l'heure de début, cette fonction utilise la valeur correspondante à la première heure disponible.  
  
-   Lorsqu'une valeur NULL est passée pour l'heure de fin, cette fonction utilise la valeur correspondante à la dernière heure disponible.  
  
-   Lorsque le numéro séquentiel dans le journal de début est égal au numéro séquentiel dans le journal de fin, ce qui indique habituellement qu'il n'y a pas d'enregistrements pour l'intervalle sélectionné, cette fonction se ferme.  
  
### <a name="example-of-a-table-value-function-that-queries-for-change-data"></a>Exemple d'une fonction table qui interroge les données modifiées  
  
```  
CREATE function CDCSample.uf_Customer (  
     @start_time datetime  
    ,@end_time datetime  
)  
returns @Customer table (  
     CustomerID int  
    ,TerritoryID int  
    ,CustomerType nchar(1)  
    ,rowguid uniqueidentifier  
    ,ModifiedDate datetime  
    ,CDC_OPERATION varchar(1)  
) as  
begin  
    declare @from_lsn binary(10), @to_lsn binary(10)  
  
    if (@start_time is null)  
        select @from_lsn = sys.fn_cdc_get_min_lsn('Customer')  
    else  
        select @from_lsn = sys.fn_cdc_increment_lsn(sys.fn_cdc_map_time_to_lsn('largest less than or equal',@start_time))  
  
    if (@end_time is null)  
        select @to_lsn = sys.fn_cdc_get_max_lsn()  
    else  
        select @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal',@end_time)  
  
    if (@from_lsn = sys.fn_cdc_increment_lsn(@to_lsn))  
        return  
  
    -- Query for change data  
    insert into @Customer  
    select   
        CustomerID,      
        TerritoryID,   
        CustomerType,   
        rowguid,   
        ModifiedDate,   
        case __$operation  
                when 1 then 'D'  
                when 2 then 'I'  
                when 4 then 'U'  
                else null  
         end as CDC_OPERATION  
    from   
        cdc.fn_cdc_get_net_changes_Customer(@from_lsn, @to_lsn, 'all')  
  
    return  
end   
go  
  
```  
  
### <a name="retrieving-additional-metadata-with-the-change-data"></a>Récupération de métadonnées supplémentaires avec les données modifiées  
 Même si la fonction table créée par l’utilisateur et présentée plus haut utilise uniquement la colonne **__$operation**, la fonction **cdc.fn_cdc_get_net_changes_<capture_instance>** renvoie quatre colonnes de métadonnées pour chaque ligne de modification. Si vous souhaitez utiliser ces valeurs dans votre flux de données, vous pouvez les retourner en tant que colonnes supplémentaires à partir de la fonction wrapper table.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|`binary(10)`|Numéro séquentiel dans le journal associé à la transaction de validation de la modification.<br /><br /> Toutes les modifications validées dans la même transaction partagent le même numéro séquentiel dans le journal de validation. Par exemple, si une opération de mise à jour sur la table source modifie deux lignes différentes, la table de modifications contient quatre lignes (deux avec les anciennes valeurs et deux avec les nouvelles valeurs), chacune avec la même valeur **__$start_lsn** .|  
|**__$seqval**|`binary(10)`|Valeur de classement utilisée pour classer les modifications de ligne dans une transaction.|  
|**__$operation**|`int`|Opération de langage de manipulation de données associée à la modification. Il peut s'agir d'une des méthodes suivantes :<br /><br /> 1 = suppression<br /><br /> 2 = insertion<br /><br /> 3 = mise à jour (valeurs avant l'opération de mise à jour)<br /><br /> 4 = mise à jour (valeurs après l'opération de mise à jour)|  
|**__$update_mask**|`varbinary(128)`|Masque de bits basé sur les ordinaux de colonne de la table de modifications identifiant les colonnes modifiées. Vous pouvez examiner cette valeur pour déterminer les colonnes qui ont été modifiées.|  
|**\<captured source table columns>**|varie|Les colonnes restantes retournées par la fonction sont les colonnes de la table source qui ont été identifiées comme colonnes capturées lorsque l'instance de capture a été créée. Si aucune colonne n'a été spécifiée à l'origine dans la liste des colonnes capturées, toutes les colonnes de la table source sont retournées.|  
  
 Pour plus d’informations, consultez [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).  
  
## <a name="next-step"></a>étape suivante  
 Après avoir créé la fonction table qui interroge les données modifiées, l'étape suivante consiste à commencer à concevoir le flux de données dans le package.  
  
 **Rubrique suivante :** [Récupérer et comprendre les données modifiées](retrieve-and-understand-the-change-data.md)  
  
  
