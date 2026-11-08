# QCMed · Réviser les maths (et l'informatique) du concours

Quatre sites de révision, chacun dans **un seul fichier HTML** (CSS et JavaScript intégrés, sans serveur ni framework), pour préparer l'épreuve écrite n° 2 des concours de la DGFiP (Contrôleur et Inspecteur des Finances Publiques).

| Fichier | Contenu |
|---|---|
| `index.html` | **QCM B** : maths du QCM (concours externe de Contrôleur) |
| `SpeMathsB.html` | **Spé maths B** : spécialité maths, niveau B |
| `SpeMathsA.html` | **Spé maths A** : spécialité maths, niveau Inspecteur |
| `Info.html` | **Informatique** : Python par les maths |

Les quatre fichiers doivent rester **dans le même dossier** (ils renvoient les uns vers les autres).

## Ce que contiennent les sites

Chaque site est organisé en onglets, avec mode clair/sombre, affichage adapté au mobile et formules composées en LaTeX (KaTeX, chargé à la demande ; sans réseau, l'affichage Unicode reste lisible).

| Onglet | Rôle |
|---|---|
| **Cours** | Chapitres courts avec exemples, schémas, pièges et « leurres » du QCM. Les cours hors programme sont signalés par une pastille orange. |
| **Exercices** | *Exos QCM* (correction immédiate), *Exos Usuels* (énoncé puis correction dépliable), *Test QCM*, *Calcul* (calculatrice). |
| **Fonctions** | Solveur de graphes : domaine, zéros, dérivée, variations, asymptotes, tangente, intégrale, fiche PDF. Spé A ajoute les courbes paramétrées γ(t). |
| **Suites** (QCM B, Spé B) | Nature, variations, expression et limite d'une suite, graphe, fiche PDF. |
| **Su/Se Fonctions** (Spé A) | Suites et séries de fonctions (convergence simple, uniforme, normale), séries numériques (nature et somme exacte quand elle est identifiable). |
| **Programme** | Structure de l'épreuve et programme, avec repère « cours disponible ». |
| **PDFs** | Un PDF par cours, généré à la demande. |
| **Codage** (Info) | Shell et éditeur Python (Pyodide, chargé depuis le réseau à la première ouverture). |

### Particularités par site

- **QCM B** : 37 cours (dont aires et volumes), 551 QCM (dont 410 issus du livre « Thème 3 Mathématiques », voir ci-dessous), exercices usuels classés *Au programme / Compléments / Hors programme*.
- **Spé maths B** : 64 cours (statistiques, probabilités, suites, hors programme tombés au concours : logarithme, récurrence, géométrie dans l'espace), 164 QCM, sujets 2023, 2024 et 2026 corrigés.
- **Spé maths A** : 100 cours (séries, intégration, calcul différentiel, algèbre linéaire et euclidienne, probabilités, structures algébriques, géométries, **statistiques descriptives et inductives**), 286 QCM dont 169 Vrai/Faux du livre, et les exercices décrits ci-dessous. Tous les points du programme de mathématiques (A) sont couverts.
- **Informatique** : 8 cours, « Méthodes en Python » (24 méthodes avec sortie calculée et bouton « Essayer dans l'Éditeur »), 18 exercices corrigés, 36 + 12 QCM.

### Vidéo d’ambiance

Un bandeau vidéo (formules sur fond matriciel, tiré du GIF fourni, converti en `fond.mp4` de 0,4 Mo avec l’image fixe `fond.jpg`) s’affiche dans l’onglet Cours de chaque site, entre les encadrés de navigation et le titre. Il est muet, en boucle, décoratif, et remplacé par l’image fixe si l’utilisateur a réduit les animations. **Les fichiers `fond.mp4` et `fond.jpg` doivent être placés à côté des pages HTML dans le dépôt.**

### Liste déroulante des cours

Dans l’onglet Cours de chaque site, deux listes déroulantes permettent d’atteindre un cours sans défiler : « Point du programme » (regroupement des cours selon le programme : par exemple, sur Spé A, A.1° séries et suites de fonctions, A.2° fonctions et calcul différentiel, A.3° structures algébriques, A.4° algèbre linéaire et euclidienne, A.5° géométries, B.1° probabilités, B.2°/3° statistiques) puis « Cours », qui ne liste que les cours du point choisi. Le choix filtre aussi la liste latérale ; les deux listes restent synchronisées avec le cours affiché. Sur ordinateur, la vidéo d’ambiance est élargie presque à la largeur de la fenêtre.

### Navigation entre les sites

Chaque site affiche en haut des encadrés cliquables (même présentation que sur le site du QCM B) vers **tous les autres sites**, sauf celui sur lequel on se trouve : le QCM B propose Spé B, Spé A et Informatique ; Spé A propose QCM B, Spé B et Informatique ; et ainsi de suite. Le lien « Retour au site QCM B » a été supprimé.

### Spé maths A › Exercices › Exos Usuels

Les exercices sont regroupés en trois sections, avec des filtres :

- **Annales de concours** : 15 exercices des sujets Inspecteur 2024, 2025, sujet zéro 2026 et 2026 (série et dilogarithme, hauteurs et cercles, carrés modulo 7, endomorphisme non diagonalisable, intégrales de Wallis, homothétie, groupe (ℤ/64ℤ)*, polynôme à racines multiples, éléments propres, intervalle de confiance, intégrale impropre, série de fonctions, loi de Poisson, matrice I + J, parabole). Corrections rédigées, vérifiées numériquement et **illustrées par 18 schémas** (courbes, figures géométriques, diagrammes) adaptés au thème clair/sombre et au mobile.
- **Entraînement** : 8 variantes dans l'esprit des sujets (mêmes méthodes, autres données).
- **Exercices par chapitre** : 237 exercices corrigés, classés par chapitre du livre : ch. 1 espaces vectoriels et applications linéaires (23), ch. 2 calcul matriciel (25), ch. 3 déterminants (17), ch. 4 réduction (31), ch. 5 espaces préhilbertiens (25), ch. 6 isométries et endomorphismes symétriques (32), ch. 8 séries numériques (26), ch. 9 suites et séries de fonctions (22), ch. 10 séries entières (24) et statistiques (12). Les corrections sont illustrées de schémas (plans et droites de ℝ³, vecteurs propres, spectres dans ℂ, suites, projections, symétries, rotations, polynômes de Tchebychev, moindres carrés, etc.). Les énoncés des ch. 1 à 3 et 4.1–4.18 ont été retranscrits à partir de photos : à comparer au livre en cas de doute.

**Tri des exercices** : deux rangées de filtres. La première choisit la *nature* (Tous, Annales de concours, Entraînement, Exercices par chapitre) ; la seconde, qui apparaît pour les annales et les exercices par chapitre, choisit le *sujet* (2024, 2025, sujet zéro 2026, 2026) ou le *chapitre*. Un compteur indique le nombre d’exercices affichés, et chaque fiche porte une pastille de sous-thème.

**Statistiques (programme B.2° et B.3°)** : un plan et 11 cours illustrés de 17 schémas (séries statistiques et histogramme, position, dispersion et concentration, corrélation et régression, estimateurs, maximum de vraisemblance, intervalles de confiance, tests d'hypothèses, tests usuels et khi-deux, synthèse) et 58 QCM répartis en cinq thèmes.

Dans l'exercice 2 de 2025, l'énoncé de l'homothétie est ambigu ; la correction donne le centre I = (8 ; 0) avec une remarque.

### QCM B › Exercices › Exos QCM : séries du livre « Thème 3 Mathématiques »

410 questions du livre (Nombres et opérations 110, Grandeurs et mesures 60, Algèbre 90, Géométrie 90, Statistiques et probabilités 60) sont intégrées aux Exos QCM, avec les trois niveaux du livre. Le livre ne donne que les lettres du corrigé : chaque réponse a été recalculée et comparée au corrigé (aucun écart), et une explication a été rédigée pour chaque question. Les figures de géométrie sont décrites en texte, les tableaux sont reproduits. Filtres : « Tout le Thème 3 », par niveau et par thème. Les questions alimentent aussi le Test QCM. Deux questions où le corrigé est discutable sont signalées dans leur explication (probabilité de Sophie, latitude).

### Test QCM

Test de 40 questions tirées des Exos QCM (équilibrées par thème, en favorisant les moins vues), chrono de 20 minutes, +1 par bonne réponse, note sur 20 = score ÷ 2. Résultat par thème, correction détaillée et **historique par identifiant et par site** (courbe, moyenne, meilleure note), stocké dans le navigateur.

## Accès

Une page de connexion demande un identifiant (le prénom) et un mot de passe commun. **Une seule connexion** vaut pour les quatre sites.

- **Mémoriser cet appareil** (case cochée par défaut) : l'appareil est reconnu sur les quatre sites jusqu'au prochain changement de mot de passe. Le jeton (`localStorage`, clé `qcmed-device`) ne contient que l'identifiant et un préfixe d'empreinte, jamais le mot de passe. Le bouton de déconnexion oublie l'appareil ; à décocher sur un ordinateur partagé.
- Une icône œil affiche ou masque le mot de passe.
- Mode administrateur (mot de passe distinct) : donne accès aux onglets PDFs masqués en mode normal (visibles après 10 minutes de présence).
- **Changer le mot de passe** : remplacer `PH` (et `AH` pour l'administrateur) dans les quatre fichiers. Tous les appareils mémorisés devront alors se reconnecter.

> **Protection légère, non sécurisée.** La vérification se fait dans le navigateur (empreinte SHA-256 présente dans le code). Elle limite l'accès à un groupe de candidats mais ne protège aucune donnée sensible : le contenu reste lisible dans le code source.

## Technique

| Point | Détail |
|---|---|
| Données | Cours (`COURSES`), QCM (`EXOS`) et exercices usuels (`USU`) sont des tableaux JavaScript dans chaque fichier |
| Stockage | `localStorage` (thème, appareil, historique des tests, code de l'éditeur), `sessionStorage` (session) |
| PDF | `html2canvas` et `jsPDF`, chargés à la demande (réseau requis) ; pages en images, texte non sélectionnable |
| Python | Pyodide 0.26.4 (numpy, scipy, matplotlib), plusieurs CDN en secours |
| Hors connexion | Tout fonctionne sauf les PDF, KaTeX et Pyodide à leur premier chargement |

## Héberger

Ouvrir le fichier dans un navigateur récent, ou déposer les quatre fichiers sur un hébergement de pages statiques (par ex. GitHub Pages). Après toute modification, **re-téléverser les fichiers sur le dépôt GitHub**.

## Ajouter du contenu

Tout se trouve dans la balise `<script>` du fichier.

```js
// Cours : tableau COURSES
{t:"Titre", s:"Sous-titre", h:"<h2>Titre</h2><p>Texte…</p><div class=\"formula\">Formule</div>"},

// QCM : tableau EXOS (c = catégorie du filtre, s = niveau (optionnel), t = tableau HTML (optionnel), o = choix, a = indice de la bonne réponse, e = explication)
{c:"Thème", q:"Question ?", o:["A","B","C","D"], a:1, e:"Explication."},

// Exercice usuel : objet {t, q, a} (titre, énoncé, correction) dans un groupe de USU
```

Les formules sont écrites en Unicode (`<sub>`, `<sup>`) et converties en LaTeX à l'affichage ; ajouter la classe `nomx` à un bloc pour l'exclure. Mettre aussi à jour l'onglet Programme (repère « cours disponible »).

## Limites connues

- Contrôle d'accès non sécurisé (voir plus haut).
- Les analyses des onglets Fonctions, Suites et Su/Se Fonctions sont numériques : les conclusions sont à justifier sur la copie.
- Certains énoncés issus de fiches ou du livre peuvent contenir des coquilles (par ex. le crible de l'exercice 18.12) : en cas de doute, se reporter à l'original.
- Les sites ne couvrent que les mathématiques (et l'informatique par les maths), pas la culture générale, le français ni le raisonnement logique.
