---
title: Liste de contrôle de préparation pour l’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87603155"
---
# <a name="checklist-of-preparation-for-data-mining"></a>Liste de vérification : préparation pour l'exploration de données
  Bien que les compléments d'exploration de données facilitent et agrémentent la création de modèles et leur expérimentation, lorsque vous devez obtenir des résultats reproductibles et utilisables, vous devez prévoir suffisamment de temps pour formuler les critères fondamentaux pour l'entreprise, ainsi que pour obtenir et préparer les données. Cette section fournit une liste de vérification pour vous aider à planifier les tâches d'inspection, et décrit les problèmes courants.  
  
## <a name="checklist-of-data-preparation"></a>Liste de vérification de la préparation des données  
 **J'ai identifié un résultat bien défini.**  
 Disposer d'un plan pour la façon dont vous allez utiliser les résultats. Les différents types de modèles génèrent des résultats différents. Un modèle de série chronologique génère des valeurs d'une série dans le futur, qui sont facilement compréhensible et utilisables. D'autres modèles génèrent des jeux complexes qui doivent être analysés par des experts techniques pour obtenir la plus grande valeur.  
  
-   Quel résultat voulez-vous ?  
  
-   Pouvez-vous définir la sortie en tant que colonne ou valeur unique, ou tout autre résultat utilisable ?  
  
-   Quels sont les critères pour savoir que le modèle est utile ?  
  
-   Comment allez-vous utiliser et interpréter ces résultats ?  
  
-   Pouvez-vous mapper les nouvelles données d'entrée aux résultats attendus ?  
  
 **Je connais la signification, les types de données et la distribution des données d'entrée.**  
 Prenez le temps d'explorer et comprendre vos données source. Il est important que les personnes qui examinent le modèle comprennent le type de données d'entrée qui a été utilisé et sachent interpréter les types de données et la variabilité, ainsi que l'équilibre et la qualité.  
  
-   De quel volume de données disposez-vous ? Les données sont-elles suffisantes pour la modélisation ?  
  
     Il n’est pas nécessaire qu’il soit très petit et équilibré.  
  
-   Les données proviennent-elles de plusieurs sources, ou d'une seule source ?  
  
-   Est-ce-que les données sont déjà traitée et nettoyées ? Des données d'entrée supplémentaires sont-elles disponibles ?  
  
-   Savez-vous comment il a été manipulé avant de le recevoir, comment les données ont peut-être été tronquées, résumées ou converties ?  
  
-   Les données d'entrée ont-elles des exemples de résultats qui peuvent être utilisés pour l'apprentissage ?  
  
 **Je comprends le niveau d'intégrité des données dont nous disposons et celui dont nous avons besoin.**  
 Des données incorrectes peuvent affecter la qualité du modèle ou empêcher la génération du modèle. Vous devez avoir une bonne compréhension de la distribution et de la signification des données, et de la manière dont elles sont parvenues à cet état. Vous devez comprendre s’il est possible ou approprié de simplifier les données en les étiquetant, en tronquant les types de données numériques ou en les résumant.  
  
-   Étiquettes de données : sont-elles claires et correctes ?  
  
-   Types de données : sont-ils appropriés et ont-ils été modifiés ?  
  
-   Avez-vous trié, nettoyé ou ignoré les données incorrectes ?  
  
     Avez-vous vérifié qu'il n'y a pas de doublons ?  
  
-   Comment allez-vous gérer les valeurs manquantes ? Les valeurs manquantes ont-elles une signification ?  
  
-   Avez-vous vérifié les sources pour déterminer si des erreurs ont été introduites lors du processus d'importation ?  
  
     Où sont stockées les données d'entrée ? Combien de temps resteront-elles disponibles ?  
  
     Existe-t-il un dictionnaire des données ? Pouvez-vous en créer un ?  
  
-   Si vous avez combiné des jeux de données, avez-vous recherché plusieurs colonnes représentant les mêmes données ?  
  
 **Je sais où les données sources sont stockées, où elles proviennent et comment elles sont traitées. Le processus peut être répété facilement si nécessaire.**  
 Les jeux de données uniques sont corrects pour les expériences, mais si vous souhaitez déplacer le modèle en production, pensez à l’avance sur la façon dont le processus de nettoyage peut être appliqué aux données opérationnelles. En outre, si vous avez des données opérationnelles, vous devez savoir comment elles peuvent avoir été altérées avant de vous y avoir. vous devez savoir comment elles ont été arrondies, ou résumées, certainement.  
  
-   Voulez-vous être en mesure de répéter l'expérience ?  
  
-   Quels outils utiliserez-vous pour préparer les données dans un format qui prend en charge l'analyse de données ? Peut-il être automatisé ou avez-vous besoin de quelqu'un pour la vérification et le nettoyage dans Excel ?  
  
-   Si les données proviennent d'un autre système, serez-vous en mesure de capturer et suivre les filtres appliqués ?  
  
-   Votre infrastructure de traitement des données peut-elle également appliquer des algorithmes d'apprentissage automatique, réaliser des tests et visualiser les résultats ?  
  
 **Nous nous sommes entendus sur la granularité souhaitée des prédictions et nos données ont été modifiées pour obtenir ces unités.**  
 Décidez de la granularité des résultats que vous recherchez avant de préparer des données. Par exemple, avez-vous besoin des prédictions de ventes chaque jour ou pour chaque trimestre ? Envisagez éventuellement de configurer différentes structures de données pour les mêmes données de façon à gérer différents niveaux de résumé.  
  
-   Quelle est l'unité de mesure ou l'unité de temps actuelle ?  
  
     Quelle unité souhaitez-vous utiliser dans les résultats ?  
  
-   Est-il possible de définir une unité de base (par exemple, jour/heure/min/instruction call) pour toutes les données d’entrée ?  
  
     Voulez-vous effectuer le cumul aux unités supérieures ?  
  
-   Est-ce-que les catégories sont étiquetées de façon cohérente ? Est-il facile d'ajouter ou de supprimer des catégories ?  
  
 **Notre conception expérimentale est renouvelable et reproductible.**  
 Tenez compte des stratégies pour analyser et valider vos résultats et planifier la capturer d'un instantané des données, pour garantir que vous pouvez tracer les effets sur les données. Si une valeur de départ aléatoire est utilisée, les résultats peuvent légèrement différer. Cela peut rendre la difficile la comparaison et la validation des modèles.  
  
-   Si vous apportez de nombreuses modifications personnalisées aux données, que se passera-t-il la prochaine fois que vous souhaiterez créer le modèle ?  
  
-   Une procédure manuelle ou un processus approuvé que vous devez utiliser pour traiter les données d'entrée et obtenir le résultat souhaité a-t-il déjà été défini ?  
  
-   Avez-vous décidé d'utiliser une valeur initiale pour le modèle ?  
  
 **Nous disposons des connaissances dans le domaine pour valider les résultats, ou nous avons accès à des experts techniques qui peuvent nous conseiller.**  
 Prenez le temps de valider les variables, le modèle et les résultats. Obtenez de l'aide auprès d'experts pour évaluer les interactions et les résultats. Toutefois, ne laissez pas les hypothèses prioritaires sur les preuves. Soyez ouvert aux résultats nouveaux et inattendus.  
  
-   La connaissance de domaine est-elle disponible pour faciliter le filtrage des données et réduire le bruit des données d'entrée ?  
  
-   Est-ce-que les experts en matière de domaine aident à comprendre et interpréter les résultats et proposent des améliorations ?  
  
## <a name="see-also"></a>Voir aussi  
 [Choisir les données pour l'exploration de données](choosing-data-for-data-mining.md)  
  
  
