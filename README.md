# SCRIPT POWERSHELL RECHERCHE OP DANS IL12 ET ENVOIE IL12 AU WEB SERVICE | SERVEUR DE TEST

### Où trouver les scripts ?

Connectez vous au serveut de test lmst, puis rendez vous dans le dossier de l'utilisateur *Public* (accessible par tous), vous trouverez les différents scripts dans le dossier *scripts*.

**A faire manuellement :** Créer un fichier CSV avec les colonnes suivante : *op* (numéro d'OP), *statut* (pre, rel, inp, pac, loa, shi), *cible* (ct ou m3).
Ce fichier doit contenir la liste des OPs à rechercher dans les il12. **PS :** *Le statut doit être le même pour chaque OP (recherche d'un statut à la fois)*.

## SCRIPT 1 : Recherche

Ce script permet de copier le chemin d’accès des fichiers il12 au statut demandé dans un fichier CSV basés sur les critères spécifiés pour une liste d’OPs souhaités.

### Paramètres

- **cible :** Cible souhaitée, "ct" ou "m3" **(OBLIGATOIRE)**
- **debut :** Date de début au format "ddMMyy" **(Optionnel, nécessite "fin" si fourni)**
- **fin :** Date de fin au format "ddMMyy" **(Optionnel, nécessite "debut" si fourni)**
- **debug :** Active le mode debug (0 ou 1) **(OBLIGATOIRE)**
- **chemin_liste_ops :** Chemin absolu vers le fichier csv de la liste des ops **(Optionnel car valeur par défaut : "%UserProfile%\Downloads\opl_to_il12\in\")**
- **fichier_liste_ops :** Nom du fichier CSV de la liste des ops **(Optionnel car valeur par défaut : "liste_op_a_verifier.csv")**
- **chemin_csv_final :** Chemin absolu de l'endroit où sera créer le fichier CSV final **(Optionnel car valeur par défaut : "%UserProfile%\Downloads\opl_to_il12\out\")**

### Fonctionnement

#### Validation des Paramètres

- Vérifie que les paramètres obligatoires sont fournis.
- Valide le format des dates si fournies.
- Si une seule date est fournie, demande l'autre date manquante.

#### Définition des Chemins et Modèles

- Définit les chemins de source, de destination et les fichiers CSV intermédiaires et finaux.

#### Chargement de la Liste des Opérations

- Charge la liste des opérations depuis un fichier CSV.
- Filtre les opérations en fonction de la cible spécifiée.

#### Récupération des Fichiers

- Récupère les fichiers du statut demandé dans le répertoire source.
- Filtre par date si les dates sont fournies.

#### Création du CSV Intermédiaire

- Génère un fichier CSV intermédiaire listant les fichiers correspondant au statut demandé.

#### Analyse des Fichiers et Création du CSV Final

- Parcourt les fichiers intermédiaires et vérifie la présence des opérations.
- Génère un fichier CSV final avec le chemin des fichiers trouvés et les opérations non trouvées.

#### Nettoyage

- Supprime les fichiers CSV intermédiaires si le paramètre clean est activé.

### Exemple d'Exécution

`PS> ctv2_il12_copie_statut_date.ps1 -cible ct -debut 300924 -fin 300924 -debug 1 -clean 0`

#### Format CSV Initial

|op      |statut |cible  |
|---     |:-:    |--:    |
|31753850|han    |ct     |
|31753851|han    |ct     |
|31753903|han    |m3     |

#### Fichers Générés

- **CSV Intermédiaire :** `00_liste_tous_fichier_statut_<statut>_<debut>-<fin>.csv` dans la variable système `%temp%`.
- **CSV Final :** `01_liste_filtree_fichier_statut_<statut>_<debut>-<fin>.csv` dans la destination finale renseignée ou par défaut.



    
