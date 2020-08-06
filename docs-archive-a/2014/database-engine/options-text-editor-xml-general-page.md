---
title: Options (éditeur de texte-XML-page général) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 46a9f913-d0b9-40ff-b382-9bbdec7461a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 70d7f3130342a6b8ac7e92e1eaf3e89869ff4148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694691"
---
# <a name="options-text-editor---xml---general-page"></a>Options (Éditeur de texte - XML - Page Général)
  Utilisez cette boîte de dialogue pour modifier le comportement d'édition général de l'Éditeur XML, qui permet de modifier des documents XML. Pour afficher ces paramètres, cliquez sur **Options** dans le menu **Outils** , développez le sous-dossier **XML** , puis cliquez sur **Général**.  
  
## <a name="setting-options-in-multiple-locations"></a>Définition d'options en plusieurs emplacements  
 Les options de l'Éditeur XML peuvent également être définies dans la boîte de dialogue **Tous les langages Général** . Si vous utilisez les boîtes de dialogue **tous les langages** pour définir des options différentes pour les autres [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] éditeurs, comme les éditeurs DMX ou MDX, vous devez réinitialiser les options de l’éditeur XML à l’aide de cette boîte de dialogue.  
  
## <a name="statement-completion"></a>Compléter automatiquement les instructions  
 **Répertorier automatiquement les membres**  
 Lorsque cette case à cocher est activée, les listes des membres, propriétés, valeurs ou méthodes disponibles s'affichent lorsque vous tapez dans l'éditeur. Sélectionnez un élément dans la liste contextuelle pour l'insérer dans votre code.  
  
 **Masquer les membres avancés**  
 Cette case à cocher n'est pas disponible.  
  
 **Informations sur les paramètres**  
 Lorsque cette case à cocher est activée, la syntaxe complète de la déclaration ou de la procédure en cours s'affiche à gauche du point d'insertion dans l'éditeur, avec tous les paramètres disponibles. Le paramètre suivant qui peut être affecté est affiché en gras.  
  
## <a name="settings"></a>Paramètres  
 **Activer l'espace virtuel**  
 Lorsque cette case à cocher est activée, des espaces sont insérés à la fin de chaque ligne de code. Activez cette case à cocher pour placer des commentaires à un point cohérent, en regard de votre code.  
  
 **Retour automatique à la ligne**  
 Lorsque cette case à cocher est activée, toute partie d'une ligne qui s'étend horizontalement au-delà de la zone visible de l'éditeur est affichée automatiquement à la ligne suivante. L'activation de cette case à cocher entraîne l'activation de la case à cocher **Afficher des glyphes visuels pour le retour automatique à la ligne** .  
  
 **Afficher des glyphes visuels pour le retour automatique à la ligne**  
 Lorsque cette case à cocher est activée, une flèche retour est affichée quand une ligne nécessite un retour automatique à la ligne suivante. Désactivez cette case à cocher si vous préférez ne pas afficher d'indicateurs.  
  
> [!NOTE]  
>  Ces flèches de rappel ne sont pas ajoutées à votre code et ne s'impriment pas. Ils servent de référence uniquement.  
  
 **Appliquer les commandes Couper ou Copier aux lignes vides en l'absence de sélection**  
 Cette case à cocher définit le comportement de l'éditeur lorsque vous placez le point d'insertion sur une ligne vide, n'effectuez aucune sélection et cliquez sur **Copier** ou **Couper**.  
  
 Lorsque cette case à cocher est activée, la ligne vide est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, une nouvelle ligne vide est insérée.  
  
 Lorsque cette case à cocher est désactivée, aucun élément n'est copié ou coupé. Si vous cliquez ensuite sur **Coller**, le dernier contenu copié est collé. Si aucune sélection n'a été copiée précédemment, aucune sélection n'est collée.  
  
 Ce paramètre n'a aucun effet sur les commandes **Copier** ou **Couper** lorsqu'une ligne n'est pas vide. Si aucun élément n'est sélectionné, la totalité de la ligne est copiée ou coupée. Si vous cliquez ensuite sur **Coller**, le texte de la totalité de la ligne et son caractère de fin de ligne sont collés.  
  
## <a name="display"></a>Afficher  
 **Numéros de ligne**  
 Lorsque cette case à cocher est activée, un numéro de ligne est affiché en regard de chaque ligne de code.  
  
> [!NOTE]  
>  Ces numéros de ligne ne sont pas ajoutés à votre code et ne s'impriment pas. Ils servent de référence uniquement.  
  
 **Activer la navigation dans les URL par simple clic**  
 Lorsque cette case à cocher est activée, le curseur est remplacé par une main avec un doigt tendu lorsqu'il passe sur une URL dans l'éditeur. Vous pouvez alors cliquer sur l'URL pour afficher la page correspondante dans votre navigateur Web.  
  
 **Barre de navigation**  
 Cette case à cocher n'est pas disponible.  
  
  
