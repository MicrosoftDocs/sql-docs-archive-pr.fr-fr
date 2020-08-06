---
title: Stratégie de mot de passe | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 902c46b4609a32139450843414a3c4d97b52fcf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87602008"
---
# <a name="password-policy"></a>Stratégie de mot de passe
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut exploiter les mécanismes de stratégie de mot de passe Windows. La stratégie de mot de passe s'applique à une connexion qui utilise l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à un utilisateur de base de données autonome avec un mot de passe.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut appliquer aux mots de passe utilisés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des stratégies de complexité et d'expiration identiques à celles de Windows. Cette fonctionnalité dépend de l'API `NetValidatePasswordPolicy` .  
  
## <a name="password-complexity"></a>Complexité des mots de passe  
 Les stratégies de mot de passe complexes sont conçues pour décourager les attaques en augmentant le nombre de mots de passe possibles. Lorsque la stratégie de mot de passe complexe est mise en œuvre, les nouveaux mots de passe doivent respecter les critères suivants :  
  
-   Le mot de passe ne doit pas contenir le nom du compte de l'utilisateur.  
  
-   Les mots de passe doivent compter au moins huit caractères.  
  
-   Les mots de passe doivent contenir des caractères appartenant à trois des quatre catégories suivantes :  
  
    -   Lettres majuscules de l'alphabet latin (A à Z)  
  
    -   Lettres minuscules de l'alphabet latin (a à z)  
  
    -   Chiffres de la base 10 (0 à 9)  
  
    -   Caractères non alphanumériques tels que : point d'exclamation (!), symbole dollar ($), signe dièse (#) ou pour cent (%).  
  
 Les mots de passe peuvent comporter jusqu'à 128 caractères. Vous devez utiliser des mots de passe aussi longs et complexes que possible.  
  
## <a name="password-expiration"></a>Expiration des mots de passe  
 Les stratégies d'expiration des mots de passe servent à gérer la durée de vie d'un mot de passe. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique la stratégie d'expiration des mots de passe, les utilisateurs sont invités à modifier leurs anciens mots de passe, et les comptes associés à des mots de passe arrivés à expiration sont désactivés.  
  
## <a name="policy-enforcement"></a>Mode d'application d'une stratégie  
 L'application de la stratégie de mot de passe peut être configurée séparément pour chaque connexion SQL Server. Utilisez [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) pour configurer les options de stratégie de mot de passe d’une connexion SQL Server. Les règles suivantes régissent la configuration du mode d'application des stratégies de mot de passe :  
  
-   Lorsque CHECK_POLICY prend la valeur ON, les actions suivantes se produisent :  
  
    -   CHECK_EXPIRATION prend également la valeur ON, sauf si la valeur OFF est définie explicitement.  
  
    -   L'historique du mot de passe est initialisé avec la valeur du hachage de mot de passe actuel.  
  
    -   Les options**Durée de verrouillage de compte**, **Seuil de verrouillage de compte**et **Réinitialiser le compteur de verrouillages du compte après** sont également activées.  
  
-   Lorsque CHECK_POLICY prend la valeur OFF, les actions suivantes se produisent :  
  
    -   CHECK_EXPIRATION ON prend également la valeur OFF.  
  
    -   L'historique du mot de passe est supprimé.  
  
    -   La valeur de `lockout_time` est réinitialisée.  
  
 Certaines combinaisons d'options de stratégie ne sont pas prises en charge.  
  
-   Si MUST_CHANGE est spécifié, CHECK_EXPIRATION et CHECK_POLICY doivent prendre la valeur ON. Sans quoi, l'instruction échoue.  
  
-   Si CHECK_POLICY prend la valeur OFF, CHECK_EXPIRATION ne peut pas prendre la valeur ON. Si cette combinaison d'options est utilisée dans une instruction ALTER LOGIN, l'instruction échoue.  
  
 Le paramètre CHECK_POLICY = ON interdit la création des mots de passe qui sont :  
  
-   NULL ou vides  
  
-   Identiques au nom de l'ordinateur ou de la connexion  
  
-   Égaux à : « password », « admin », « administrator », « sa », « sysadmin »  
  
 La stratégie de sécurité peut être définie dans Windows ou peut être reçue du domaine. Pour afficher la stratégie de mot de passe sur l’ordinateur, utilisez le composant logiciel enfichable MMC Stratégie de sécurité locale (**secpol.msc**).  
  
## <a name="related-tasks"></a>Tâches associées  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)  
  
 [ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [Créer un compte de connexion](authentication-access/create-a-login.md)  
  
 [Créer un utilisateur de base de données](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Mots de passe forts](strong-passwords.md)  
  
  
