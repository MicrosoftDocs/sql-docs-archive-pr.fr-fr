---
title: Créer, modifier ou supprimer des index XML secondaires sélectifs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: rothja
ms.author: jroth
ms.openlocfilehash: e6f7296896b6421db5329565403cdcbaf10b26a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697611"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Créer, modifier ou supprimer des index XML secondaires sélectifs
  Décrit la procédure de création d'un index XML secondaire sélectif, ou de modification ou de suppression d'un index XML secondaire sélectif existant.  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> Création d'un index XML secondaire sélectif  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Procédure : Créer un index XML secondaire sélectif  
 **Créer un index XML secondaire sélectif à l'aide de Transact-SQL**  
 Créez un index XML secondaire sélectif en appelant l'instruction CREATE XML INDEX. Pour plus d’informations, consultez [CREATe XML INDEX &#40;Selective XML Indexes&#41;] (~/t-SQL/Statements/CREATE-XML-index-Selective-XML-indexes.  
  
 **Exemple**  
  
 L'exemple suivant crée un index XML secondaire sélectif sur le chemin d'accès `'pathabc'`. Le chemin d'accès à l'index est identifié par le nom qui lui a été donné lors de sa création à l'aide de l'instruction CREATE SELECTIVE XML INDEX. Pour plus d’informations, consultez [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> Modification d'un index XML secondaire sélectif  
 L'instruction ALTER n'est pas prise en charge pour les index XML secondaires sélectifs. Pour modifier un index XML secondaire sélectif, supprimez l'index existant et recréez-le.  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>Procédure : Modifier un index XML secondaire sélectif  
 **Modifier un index XML secondaire sélectif à l'aide de Transact-SQL**  
 1.  Supprimez l'index XML secondaire sélectif existant en appelant l'instruction DROP INDEX. Pour plus d’informations, consultez [DROP INDEX &#40;index XML sélectifs&#41;](../indexes/indexes.md).  
  
2.  Recréez l'index avec les options de votre choix en appelant l'instruction CREATE XML INDEX. Pour plus d’informations, consultez [CREATe XML INDEX &#40;Selective XML Indexes&#41;] (~/t-SQL/Statements/CREATE-XML-index-Selective-XML-indexes.  
  
 **Exemple**  
  
 L'exemple suivant modifie un index XML secondaire sélectif en le supprimant et en le recréant.  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> Suppression d'un index XML secondaire sélectif  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>Procédure : Supprimer un index XML secondaire sélectif  
 **Supprimer un index XML secondaire sélectif à l'aide de Transact-SQL**  
 Supprimez un index XML secondaire sélectif en appelant l'instruction DROP INDEX. Pour plus d’informations, consultez [DROP INDEX &#40;index XML sélectifs&#41;](../indexes/indexes.md).  
  
 **Exemple**  
  
 L'exemple suivant illustre une instruction DROP INDEX.  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](selective-xml-indexes-sxi.md)  
  
  
