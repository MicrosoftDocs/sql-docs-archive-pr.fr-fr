---
title: Choisir un algorithme de chiffrement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b2c5292b4a00a3ad81e53fdbc603bb584130613
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709083"
---
# <a name="choose-an-encryption-algorithm"></a>Choisir un algorithme de chiffrement
  Le chiffrement est l'une des mesures préventives à la disposition des administrateurs qui souhaitent sécuriser une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Les algorithmes de chiffrement définissent les transformations de données qui ne peuvent pas être facilement inversées par les utilisateurs non autorisés. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permet aux administrateurs et aux développeurs de choisir entre plusieurs algorithmes, notamment DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, RC4 128 bits, DESX, AES 128 bits, AES 192 bits et AES 256 bits.  
  
 Aucun algorithme unique ne convient pour toutes les situations et l'appréciation des avantages de chaque algorithme dépasse le cadre de la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Cependant, les principes suivants s'appliquent :  
  
-   Un chiffrement renforcé consomme en général davantage de ressources processeur qu'un chiffrement plus faible.  
  
-   Les clés longues produisent en général un chiffrement plus fort que les clés courtes.  
  
-   À longueur de clé égale, le chiffrement asymétrique est plus faible que le chiffrement symétrique, mais il est relativement lent.  
  
-   Le chiffrement par blocs avec des clés longues est plus fort que le chiffrement par flux.  
  
-   Les mots de passe longs et complexes sont plus forts que les mots de passe courts.  
  
-   Si vous chiffrez de grandes quantités de données, vous devez utiliser pour cela une clé symétrique, puis chiffrer cette clé avec une clé asymétrique.  
  
-   Les données chiffrées ne peuvent pas être compressées, mais les données compressées peuvent être chiffrées. Si vous utilisez la compression, vous devez compresser les données avant de les chiffrer.  
  
> [!IMPORTANT]  
>  L'algorithme RC4 est uniquement pris en charge pour des raisons de compatibilité descendante. Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100. (Non recommandé.) Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES. Dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures, le matériel chiffré à l'aide de RC4 ou de RC4_128 peut être déchiffré dans n'importe quel niveau de compatibilité.  
>   
>  L'utilisation répétée du même RC4 ou RC4_128 KEY_GUID sur différents blocs de données entraîne la même clé RC4 car [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne fournit pas automatiquement de salt. L'utilisation répétée de la même clé RC4 est une erreur connue qui entraîne un chiffrement très faible. Par conséquent, les mots clés RC4 et RC4_128 sont déconseillés. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Pour plus d'informations sur les algorithmes et la technologie de chiffrement, consultez la rubrique [Concepts fondamentaux sur la sécurité](https://go.microsoft.com/fwlink/?LinkId=62082) dans le Guide du développeur .NET Framework sur le site MSDN.  
  
 **Éclaircissement concernant les algorithmes DES :**  
  
-   DESX a été nommé incorrectement. Les clés symétriques créées avec ALGORITHM = DESX utilisent en fait le chiffrement TRIPLE DES avec une clé de 192 bits. L'algorithme DESX n'est pas fourni. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Les clés symétriques créées avec ALGORITHM = TRIPLE_DES_3KEY utilisent TRIPLE DES avec une clé de 192 bits.  
  
-   Les clés symétriques créées avec ALGORITHM = TRIPLE_DES utilisent TRIPLE DES avec une clé de 128 bits.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|Chiffrement à l'aide d'une clé symétrique.|[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|Chiffrement à l'aide d'une clé asymétrique.|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|Chiffrement à l'aide d'un certificat.|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)|  
|Chiffrement de fichiers de base de données à l'aide du chiffrement transparent des données.|[Chiffrement transparent des données &#40;TDE&#41;](transparent-data-encryption.md)|  
|Comment chiffrer une colonne d'une table.|[Chiffrer une colonne de données](encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Chiffrement SQL Server](sql-server-encryption.md)   
 [Hiérarchie de chiffrement](encryption-hierarchy.md)  
  
  
