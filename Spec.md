# Spécifications fonctionnelles et techniques (SFT)

## Contexte

Cette spécification décrit les fonctionnalités et les exigences techniques de l'application .NET développée pour la gestion des ordres de préparation (OP) en termes de chargement et de recherche ainsi que l'envoi de fichiers log.

## Fonctionnalités de l'application

### Chargement des OPs

- **Description :** Permettre à l'utilisateur de charger des OPs depuis un fichier CSV ou manuellement.

- **Entrée :** 
    
    - Fichier CSV contenant les colonnes : OP, Statut, Cible.

    - Ajout manuel des même champ (OP, Statut, Cible) via une interface utilisateur pour chaque OP.

- **Sortie :** 

    - Affichage des OPs chargés dans une grille de données `DataGridView`.

- **Exigeance :**

    - L'application doit permettre le chargement simultané de plusieurs entrées.

    - Les données saisies manuellement doivent suivre le même format que le fichier CSV.

### Recherche dans les fichiers log

- **Description :** Rechercher les numéros d'OP dans les fichiers log en appliquant des filtres spécifiques.

- **Entrée :** 
    
    - Sélection du dossier contenant les fichiers log.

    - Filtres : période (date de début et date de fin), statut des OP, cible.

- **Sortie :** 

    - Liste des fichiers log correspondant aux critères de filtre.

    - Affichage des résultats de la recherche avec les colonnes : OP, Statut, Cible, Chemin_fichier_log.

- **Exigeance :**

    - L'application doit parcourir les fichiers log sélectionnés pour trouver des occurrences de chaque numéro d'OP.

    - Les résultats doivent être affichés de manière claire dans un contrôle `DataGridView`.

### Envoie des fichiers au WebService

- **Description :** Envoyer les fichiers log contenant les numéros d'OP au webservice.

- **Entrée :** 
    
    - Fichier de paramètre JSON.

    - Chemins des fichiers log trouvés.

- **Sortie :** 

    - Confirmation de l'envoi avec un message d'état (succès ou échec).

- **Exigeance :**

    - Utiliser des requêtes adéquates au WebService pour envoyer les fichiers.

    - Gérer les réponses du webservice pour indiquer le succès ou l'échec de l'envoi.

### Interface utilisateur

- **Description :** Créer une interface utilisateur moderne et intuitive.

- **Elements d'interface :** 

    - Boutons pour charger des fichiers CSV, ajouter manuellement des OP, démarrer la recherche, et envoyer les résultats.

    - Zone de texte pour entrer les filtres lors de la recherche.

    - Grille de données pour afficher les OPs et les résultats de la recherche.

- **Exigeance :**

    - L'interface doit être responsive et adaptée à différentes résolutions d'écran.

### Gestion des erreurs

- **Description :** Gérer les erreurs potentielles lors du chargement de fichiers, de la recherche et de l'envoi au webservice.

- **Exigeance :**

    - Afficher des messages d'erreur appropriés dans des boîtes de dialogue.

    - *BONUS* : Logger les erreurs pour un diagnostic ultérieur.

## Exigences techniques

### Environnement de développement

- **Langage de programmation :** C# (.NET Framework)

- **IDE :** Visual Studio 2022

- **Version minimum du système d'exploitation :** WINDOWS 10

### Exigences fonctionnelles

- Charger les numéros d'OP depuis un fichier CSV ou manuellement.

- Appliquer des filtres pour sélectionner les fichiers log pertinents.

- Parcourir les fichiers log pour rechercher des occurrences de numéros d'OP.

- Afficher les résultats de la recherche avec les chemins des fichiers log.

- Envoyer les fichiers log trouvés au webservice configuré.

### Exigences non fonctionnelles

- **Performance :** L'application doit être réactive, avec un temps de réponse optimal lors du chargement et de la recherche.

- **Usabilité :** L'interface doit être intuitive et facile à utiliser pour les utilisateurs finaux.

- **Sécurité :** L'application doit gérer les données sensibles avec soin lors de l'envoi au webservice.

## Livrables

- Code source de l'application.

- Documentation utilisateur décrivant les étapes d'utilisation.

- Documentation technique décrivant l'architecture de l'application et les fonctionnalités mises en œuvre.

