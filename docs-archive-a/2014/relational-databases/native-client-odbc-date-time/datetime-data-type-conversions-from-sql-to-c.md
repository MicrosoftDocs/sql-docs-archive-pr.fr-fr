---
title: Conversions de SQL en C | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], SQL to C
ms.assetid: 059431e2-a65c-4587-ba4a-9929a1611e96
author: rothja
ms.author: jroth
ms.openlocfilehash: 0cc1fe6049824217a12a291b7006599a4a3a7319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87612285"
---
# <a name="conversions-from-sql-to-c"></a>Conversions de SQL à C
  Le tableau suivant répertorie les aspects à prendre en compte lorsque vous effectuez une conversion de types date/heure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en types C.  
  
## <a name="conversions"></a>Conversions  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
||SQL_C_DATE|SQL_C_TIME|SQL_C_TIMESTAMP|SQL_C_SS_TIME2|SQL_C_SS_TIMESTAMPOFFSET|SQL_C_BINARY|SQL_C_CHAR|SQL_C_WCHAR|  
|SQL_CHAR|2, 3, 4, 5|2, 3, 6, 7, 8|2, 3, 9, 10, 11|2, 3, 6, 7|2, 3, 9, 10, 11|1|1|1|  
|SQL_WCHAR|2, 3, 4, 5|2, 3, 6, 7, 8|2, 3, 9, 10, 11|2, 3, 6, 7|2, 3, 9, 10, 11|1|1|1|  
|SQL_TYPE_DATE|OK|12|13|12|13, 23|14|16|16|  
|SQL_SS_TIME2|12|8|15|OK|10, 23|17|16|16|  
|SQL_TYPE_TIMESTAMP|18|7, 8|OK|7|23|19|16|16|  
|SQL_SS_TIMESTAMPOFFSET|18, 22|7, 8, 20|20|7, 20|OK|21|16|16|  
  
## <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|OK|Aucun problème de conversion.|  
|1|Les règles antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] s'appliquent.|  
|2|Les espaces de début et de fin sont ignorés.|  
|3|La chaîne est analysée en date, time, timezone ou timezoneoffset et autorise jusqu'à neuf chiffres pour les fractions de seconde. Si un timezoneoffset est analysé, l'heure est convertie en fuseau horaire du client. Si une erreur se produit pendant cette conversion, un enregistrement de diagnostic est généré avec SQLSTATE 22018 et le message « DateTime Field overflow ».|  
|4|Si la valeur n'est pas une valeur date, timestamp ou timestampoffset valide, un enregistrement de diagnostic est généré avec SQLSTATE 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ».|  
|5|Si l'heure n'est pas nulle, un enregistrement de diagnostic est généré avec SQLSTATE 01S07 et le message « Troncation fractionnelle ».|  
|6|Si la valeur n'est pas une valeur time, timestamp ou timestampoffset valide, un enregistrement de diagnostic est généré avec SQLSTATE 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ».|  
|7|Le composant date est ignoré.|  
|8|Si les fractions de seconde ne sont pas nulles, un enregistrement de diagnostic est généré avec SQLSTATE 01S07 et le message « Troncation fractionnelle ».|  
|9|Si la valeur n'est pas une valeur date, time, timestamp ou timestampoffset valide, un enregistrement de diagnostic est généré avec SQLSTATE 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ».|  
|10|Si la valeur est une heure valide, le composant date est défini à la date actuelle du client.|  
|11|Si la valeur est une date valide, l'heure est définie à zéro.|  
|12|Un enregistrement de diagnostic est généré avec SQLSTATE 07006 et le message « Violation de l'attribut de type de données restreint ».|  
|13|L'heure est définie avec la valeur zéro.|  
|14|Si la mémoire tampon n'est pas assez grande pour contenir un SQL_DATE_STRUCT, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « Valeur numérique hors limites ».|  
|15|La date est définie à la date actuelle du client.|  
|16|Si la mémoire tampon n'est pas assez grande pour contenir la valeur de chaîne convertie, mais uniquement les fractions de seconde, la troncation se produit et un enregistrement de diagnostic est généré avec SQLSTATE 01004 et le message « Troncation à droite de la chaîne de données ». Si la mémoire tampon n'est pas assez grande pour contenir la valeur de chaîne sans troncation de composants date, time ou offset, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « Valeur numérique hors limites ». Notez que pour date et timestampoffset, SQLSTATE 01004 n'est pas possible car la partie la plus à droite de la chaîne convertie ne contient pas de fractions de seconde. Par conséquent, toute troncation provoque la perte de données.|  
|17|Si la mémoire tampon n'est pas assez grande pour contenir un SQL_SS_TIME2_STRUCT, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « Valeur numérique hors limites ».|  
|18|Si l'heure n'est pas nulle, un enregistrement de diagnostic est généré avec SQLSTATE 01S07 et le message « Troncation fractionnelle ».|  
|19|Si le type de serveur est datetime ou smalldatetime, la valeur correspond au format de câble TDS et sera une valeur de 4 octets pour smalldatetime et une valeur de 8 octets pour datetime.<br /><br /> Si le type de serveur est datetime2, la valeur est renvoyée en tant que SQL_TIMESTAMP_STRUCT. Si la mémoire tampon n'est pas assez grande pour contenir la valeur retournée, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « Valeur numérique hors limites ».|  
|20|L'heure est convertie en fuseau horaire du client. Si une erreur se produit pendant cette conversion, un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « Dépassement de la capacité du champ datetime ».|  
|21|Si la mémoire tampon est assez grande pour contenir un SQL_SS_TIMESTAMPOFFSET_STRUCT, la valeur est renvoyée en tant que SQL_SS_TIMESTAMPOFFSET_STRUCT. Sinon, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « Valeur numérique hors limites ».|  
|22|La valeur est convertie au fuseau horaire du client avant que la date ne soit extraite. Cela procure une cohérence avec les autres conversions avec les types timestampoffset. Si une erreur se produit pendant cette conversion, un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « Dépassement de la capacité du champ datetime ». En conséquence, la date peut différer de la valeur obtenue par simple troncation.|  
  
 Le tableau dans cette rubrique décrit les conversions entre le type retourné au client et le type dans la liaison. Pour les paramètres de sortie, si le type de serveur spécifié dans SQLBindParameter ne correspond pas au type réel sur le serveur, une conversion implicite est effectuée par le serveur et le type retourné au client correspond au type spécifié par le biais de SQLBindParameter. Cela peut entraîner des résultats de conversion inattendus lorsque les règles de conversion du serveur sont différentes de celles répertoriées dans le tableau précédent. Par exemple, lorsqu'une date par défaut doit être fournie, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise 1900-1-1, plutôt que la date actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  
