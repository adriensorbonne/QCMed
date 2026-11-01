# QCM B · Maths

Site de révision des **mathématiques du QCM** de l'épreuve écrite d'admissibilité n° 2 du **concours externe de Contrôleur des Finances Publiques**.

Le site propose des cours courts appuyés sur des exemples concrets, des exercices corrigés, une calculatrice scientifique et des PDF de cours à télécharger. Il s'adresse aux candidats qui préparent le concours, en particulier à ceux que les maths découragent : l'objectif est de comprendre la méthode plutôt que de la réciter.

> Le programme du concours comporte quatre blocs : connaissances générales, français, **mathématiques** et raisonnement logique. Ce site ne couvre que le bloc mathématiques (manipulation des nombres et algèbre).

## Ce que contient le site

Le site tient dans un seul fichier, `index.html`. Il comporte cinq onglets.

### Cours

- 28 chapitres courts, à lire dans l'ordre ou en sautant d'un chapitre à l'autre.
- Une machine interactive en page d'accueil illustre la notion de fonction (f(x) = 2x).
- Les chapitres couvrent :
  - **Nombres :** ensembles de nombres, multiples et diviseurs, critères de divisibilité, nombres premiers, nombres premiers entre eux, division euclidienne, valeur décimale et approchée, puissances et notation scientifique.
  - **Proportionnalité et pourcentages :** produit en croix, TVA.
  - **Algèbre :** développement et factorisation, identités remarquables, équations et inéquations du 1er degré, systèmes de deux équations (substitution et combinaison).
  - **Analyse :** fonctions, dérivée, primitives et intégrales. Cette partie relève du programme du QRC, la seconde partie de l'épreuve.

### Exercices

Deux sous-onglets :

- **Exos QCM :** 92 questions à choix multiples, avec correction immédiate et méthode. Un filtre par cours et un score permettent de s'entraîner par thème.
- **Exos Usuels :** 39 exercices rédigés, issus de fiches de travail, regroupés par thème (factorisation, problèmes du 1er degré, PGCD et divisibilité, division euclidienne, systèmes, second degré, etc.). L'énoncé s'affiche d'abord, la correction détaillée s'ouvre à la demande.

### Calculatrice

Une calculatrice scientifique intégrée : priorités opératoires, puissances, racines, fonctions trigonométriques, logarithmes, factorielle, pourcentages, notation scientifique, résultat précédent (Rép) et historique. Elle sert pendant un exercice sans quitter le site : les réponses et la place dans les exercices sont conservées quand on change d'onglet.

### PDFs

Un PDF par chapitre de cours, généré à la demande et téléchargeable, pour réviser hors connexion ou imprimer.

### Programme

Rappel de la structure de l'épreuve et détail du programme de mathématiques, avec un repère « cours disponible » sur chaque point déjà couvert. Les cours sont ajoutés au fur et à mesure.

## Sections liées

L'onglet Cours propose deux liens vers des sections séparées, chacune dans son propre fichier : **Réviser la spé maths du B** (`SpeMathsB.html`) et **Réviser la spé maths du A** (`SpeMathsA.html`). Elles reprennent les mêmes onglets (Cours, Exercices, Calculatrice, Programme, PDFs). Chacune propose un lien « Retour au site QCM B ». Les trois fichiers doivent se trouver dans le même dossier.

## Confort d'utilisation

- Mode clair et mode sombre (le choix est mémorisé).
- Interface adaptée au mobile : barre d'onglets fixée en bas de l'écran, liste des chapitres repliable, zones tactiles agrandies.
- Navigation au clavier et attributs d'accessibilité de base (focus visible, rôles ARIA).
- Pas de compte à créer côté serveur : tout fonctionne dans le navigateur.

## Accès

Une page de connexion demande un identifiant (le prénom) et un mot de passe commun. La session est conservée tant que l'onglet reste ouvert. Une seule connexion suffit pour les trois sites (QCM B, Spé Maths B, Spé Maths A) : se connecter ou se déconnecter sur l'un vaut pour les autres, tant qu'on navigue dans le même onglet.

**Cette protection est légère, pas sécurisée.** La vérification se fait dans le navigateur (empreinte SHA-256 du mot de passe, présente dans le code). Elle sert à limiter l'accès à un groupe de candidats, pas à protéger des données sensibles : le contenu des cours reste lisible dans le code source de la page. Une liste d'identifiants autorisés est prévue dans le code (`ALLOWED`), mais elle est vide : seul le mot de passe est contrôlé.

## Technique

| Point | Détail |
|---|---|
| Format | Un seul fichier HTML avec CSS et JavaScript intégrés, sans framework ni serveur |
| Données | Les cours, exercices et corrections sont des tableaux JavaScript dans le fichier |
| Stockage | `localStorage` pour le thème, `sessionStorage` pour la session |
| PDF | Génération côté navigateur avec `html2canvas` et `jsPDF`, chargés à la demande depuis cdnjs |
| Hors connexion | Fonctionne sans réseau, sauf la génération des PDF (bibliothèques chargées à la volée) |

Les PDF sont des images de pages : le texte n'y est pas sélectionnable. Ce choix garantit l'affichage correct des symboles mathématiques (ℕ, ², √, ⊂, φ, ∫).

## Utiliser ou héberger le site

- **En local :** ouvrir le fichier HTML dans un navigateur récent.
- **En ligne :** déposer le fichier sur n'importe quel hébergement de pages statiques. La page ne dépend d'aucun serveur applicatif.

## Ajouter du contenu

Tout se trouve dans la balise `<script>` du fichier.

**Un cours** : ajouter un objet dans le tableau `COURSES`.

```js
{t:"Titre du cours", s:"Sous-titre (thème)", h:
"<h2>Titre</h2>"+
"<p>Texte…</p>"+
"<div class=\"formula\">Formule à retenir</div>"},
```

Le cours apparaît automatiquement dans la liste des chapitres et dans l'onglet PDFs.

**Un exercice QCM** : ajouter un objet dans le tableau `EXOS` (`c` = catégorie du filtre, `o` = les choix, `a` = indice de la bonne réponse, `e` = explication).

```js
{c:"Proportionnalité", q:"Question ?", o:["A","B","C","D"], a:1, e:"Explication."},
```

**Un exercice usuel** : ajouter un objet `{t, q, a}` (titre, énoncé, correction) dans le groupe voulu du tableau `USU`.

**Le programme** : mettre à jour l'onglet Programme à la main (repère « cours disponible ») et la liste `UPCOMING` des cours à venir.

## Limites connues

- Le contrôle d'accès n'est pas sécurisé (voir plus haut).
- Les PDF générés ne contiennent pas de texte sélectionnable.
- Le site couvre les mathématiques du QCM uniquement : pas de culture générale, de français ni de raisonnement logique.
- Certains points du programme n'ont pas encore de cours : PGCD et PPCM détaillés, monômes et polynômes, intérêts simples, prix d'achat, de vente et de revient, masses et densité.
- Des énoncés issus de fiches peuvent contenir des coquilles : en cas de doute sur une correction, se reporter à l'énoncé d'origine.

### Spé Maths B : onglet « Fonctions » et cours D/E

L'onglet **Fonctions** de `SpeMathsB.html` est un solveur de graphes : on saisit une expression en x (fonctions usuelles : racine, exp, ln, sin, cos, abs…), le graphe est tracé et des boutons affichent au choix le domaine, les zéros, l'ordonnée à l'origine, la parité, la dérivée formelle, ses variations, les asymptotes, une tangente, une valeur et une intégrale. L'analyse est numérique (sur [−60 ; 60] au moins), la dérivée est calculée de façon symbolique.

Les sections **D (statistiques et probabilités)** et **E (suites numériques)** du programme ont chacune un cours par point (14 chapitres avec schémas), également disponibles dans l'onglet PDFs.

### Exercices de Spé Maths B

L'onglet **Exercices** contient : **Exos QCM** (une centaine de questions, un thème par chapitre : nombres, divisibilité, division euclidienne, proportionnalité et TVA, calcul littéral, équations, fonctions usuelles, statistiques, dénombrement, probabilités, loi binomiale et espérance, suites, dérivées, intégrales) et **Exos Usuels** (fiches de dérivées, sujets des concours 2023, 2024 et 2026 avec corrections détaillées, exercices d'entraînement par thème).

### Spé Maths B : chapitres complétés et cours « hors programme »
- **15 nouveaux cours** (soit 64 au total). Huit complètent le programme : décimaux (ajoutés au cours « Manipulation des nombres »), racines carrées, comparaison de fractions et de puissances, changement d’écriture, échelle d’une carte, unités et conversions, réduire/ordonner/calculer, somme et produit d’inégalités (lien avec la fonction affine), repère orthonormé.
- L’onglet **Cours** comporte deux encadrés : « Cours du programme » et « Hors programme, tombés au concours ». Ce second encadré contient : logarithme (équations, inéquations, croissances comparées), raisonnement par récurrence, comparaison de moyennes, et géométrie dans l’espace en quatre cours.
- **Exercices** : 15 exercices corrigés ajoutés dans « Exos Usuels » (2 groupes) et 64 QCM supplémentaires (164 au total).
- L’onglet **Programme** indique désormais « cours disponible » pour presque tous les points. PDF des nouveaux cours : 50 à 64 (et 02 mis à jour).

### Spé Maths A : séries et suites de fonctions
- **8 cours** dans l’onglet Cours (plus une page d’introduction) : séries numériques (définition et convergence ; critères de comparaison ; séries alternées et convergence absolue), suites et séries de fonctions (modes de convergence ; régularité), séries entières (rayon de convergence ; somme, dérivation, intégration ; développement en série entière). Ils suivent les chapitres 8, 9 et 10 du manuel.
- **58 QCM** dans « Exos QCM » : les 41 énoncés Vrai/Faux des trois chapitres sont transformés en questions à 4 propositions (avec rappel de la réponse Vrai/Faux d’origine dans la correction), plus 17 questions de cours.
- « Exos Usuels » reste vide pour l’instant, en attente des exercices du programme A.
- Correction dans Spé Maths B : les symboles < et > des propositions QCM s’affichent désormais correctement.

## Mise à jour : exercices usuels (Spé A) et onglet Fonctions

- **SpeMathsA.html** : l’onglet Exercices › « Exos Usuels » contient maintenant les 72 exercices des chapitres 8 (séries numériques), 9 (suites et séries de fonctions) et 10 (séries entières), avec une correction proposée dépliable.
- **Onglet « Fonctions »** désormais présent dans les trois sites (`index.html`, `SpeMathsA.html`, `SpeMathsB.html`).
- **Bouton « Générer le PDF »** : visible après le tracé d’une fonction. Il crée une fiche A4 complète (courbe, domaine, parité, ordonnée à l’origine, zéros et signe, dérivée, tableau de variations, extremums, limites, asymptotes, tangente, valeur, intégrale, second graphique avec f′), quelles que soient les options cochées. Il utilise html2canvas et jsPDF, chargés à la demande (connexion requise).

## Onglet « Suites » (QCM B et Spé Maths B uniquement)
- Trois modes de saisie : **Un en fonction de n**, **Un+1 en fonction de Un** (avec le premier terme), **Un+2 en fonction de Un+1 et Un** (avec les deux premiers termes). Variables : `n`, `u` (= Un), `v` (= Un+1).
- Le site indique la nature (constante, arithmétique, géométrique, arithmético-géométrique, récurrente linéaire d'ordre 2 avec équation caractéristique), le sens de variation, l'expression de Un en fonction de n (ou la relation de récurrence déduite en mode 1), la limite en +∞ et un graphique des premiers termes.
- Les sens de variation et limites des suites non classiques sont constatés numériquement : à démontrer sur la copie.

## Déconnexion
Le bouton « Déconnexion (prénom) » est remplacé par une icône de sortie (info-bulle « Déconnexion »).

## Bouton « Générer le PDF » de l'onglet Suites
Après l'analyse d'une suite, le bouton crée une fiche A4 (suite étudiée, premiers termes, graphique, nature, variations, expression, limite).

## Onglet « Su/Se Fonctions » (Spé Maths A uniquement)
- Deux modes : **suite de fonctions** fn(x) et **série de fonctions** Σ un(x), sur un intervalle [a ; b] choisi, avec variables `n` et `x`.
- Suite : convergence simple, fonction limite (formes usuelles identifiées, sauts repérés), convergence uniforme (sup|fn − f| pour n croissant, point où se concentre le défaut, essais sur des segments qui l'évitent), rappel des théorèmes.
- Série : convergence simple, absolue, normale, uniforme (restes), rayon de convergence d'une série entière, continuité, intégration et dérivation terme à terme, valeurs de la somme.
- Bouton « Générer le PDF » après le résultat. Analyse numérique : les conclusions sont à justifier sur la copie (précision limitée là où la convergence est très lente).

## Chapitres « Géométrie : aires » et « Géométrie : volumes » (QCM B et Spé Maths B)
Deux nouveaux cours : un tableau des figures planes usuelles (contour bleu, aire en orange, formule de l'aire) et un tableau des solides usuels (arêtes bleues, intérieur haché orange, formule du volume), avec unités, exemples, effet d'un agrandissement et pièges. Ils apparaissent aussi dans l'onglet PDFs de la Spé B.

## Contre-exemples et leurres (QCM B)
Chaque cours du site QCM B se termine par un encadré « Contre-exemples et leurres du QCM » : énoncés qui ressemblent au chapitre sans s'y résoudre (par ex. ouvriers × jours pour le produit en croix) et affirmations tentantes mais fausses, avec le contre-exemple chiffré. L'encadré apparaît aussi dans les PDF des cours.

## Écriture LaTeX des formules (KaTeX)

Les symboles mathématiques (sommes ∑, intégrales ∫, puissances, indices, racines, limites, fractions « a/b », ensembles ℝ, intervalles, unités, etc.) sont désormais composés avec **KaTeX** (moteur de rendu des formules LaTeX), chargé à la demande depuis cdnjs (`KaTeX 0.16.9`).

- Les textes du site restent écrits en Unicode dans le code : un petit convertisseur (bloc `<script>` `/*MATHX*/` en fin de page) repère les expressions mathématiques et les remplace par leur rendu LaTeX. Si KaTeX ne peut pas être chargé (hors ligne), l'ancien affichage Unicode reste visible : rien n'est cassé.
- Les **graphiques SVG** (tableaux de variations, cercle de convergence, courbes…) gardent leur tracé, mais leurs étiquettes (x, f(x), f′(x), ±∞, « y = x », uₙ…) sont maintenant rendues en LaTeX via `foreignObject`.
- Non convertis volontairement : les PDF générés, les graphiques tracés sur `<canvas>` (onglets Fonctions / Suites / Su-Se Fonctions), les champs de saisie, les puces de fonctions et la navigation.
- Pour exclure un bloc de la conversion, lui ajouter la classe `nomx`.

## Spé Maths A : thème « Fonctions et calcul différentiel »

Onze cours ont été ajoutés à l'onglet **Cours** de `SpeMathsA.html` (cours 10 à 20), d'après les chapitres 11, 12, 13 et 15 du livre de référence :

- **Plan de la section** (introduction, notations, mode d'emploi) ;
- **Chap. 11, Intégration sur un intervalle** : intégrale sur un segment (fonctions continues par morceaux) ; intégrales généralisées (Riemann, logarithme, exponentielle, Chasles, doublement généralisée) ; intégrabilité et convergence absolue (changement de variable, intégration par parties, Cauchy-Schwarz, théorèmes de comparaison) ;
- **Chap. 12, Interversion limites-intégrales** : convergence dominée et intégration terme à terme ; intégrales à paramètre (continuité, classe C¹ et Cᵏ, exemple de la fonction Γ) ;
- **Chap. 13, Fonctions vectorielles et courbes paramétrées** : dérivée en un point et opérations (applications bilinéaires) ; classe Cᵏ ; arcs paramétrés (tangente, points singuliers, branches infinies, longueur) ;
- **Chap. 15, Calcul différentiel** : dérivées partielles, classe C¹, différentielle, règle de la chaîne ; gradient, lignes de niveau, plan tangent, dérivées d'ordre 2 (théorème de Schwarz) et extremums.

Chaque chapitre s'ouvre sur un **point d'histoire** (encadré « Un peu d'histoire ») et chaque cours donne des exemples calculés et des pièges (« Attention »). Cinq graphiques SVG illustrent les cours (encadrement par des fonctions en escalier, intégrale de Riemann, cycloïde, astroïde, lignes de niveau et gradient). La page Programme signale désormais les points couverts.

Sources des points d'histoire : MacTutor (cycloïde : Galilée 1599, Mersenne 1628, Roberval 1634, Huygens 1673, Jean Bernoulli 1696) ; Wikipédia (symétrie des dérivées secondes : Euler et Clairaut 1740, Lagrange 1797, Cauchy 1823, Lindelöf 1867, Schwarz 1873, Peano 1890 ; intégrale de Riemann 1854/1868 ; thèse de Lebesgue 1902) ; ProofWiki (vocabulaire « integral » 1690, *calculus integralis* 1696) ; article d'histoire sur Euler et la fonction Γ (lettre à Goldbach du 13 octobre 1729).

## Spé Maths A : fonctions vectorielles (courbes paramétrées planes)

Dans l'onglet **Fonctions** de `SpeMathsA.html` (uniquement), un interrupteur « f(x) / γ(t) » ouvre un second mode : l'étude d'une fonction vectorielle γ : I → ℝ², t ↦ (x(t) ; y(t)) (cas n = 2 ; le cas n = 3 sera ajouté plus tard).

- **Saisie** : `(x(t) ; y(t))`, variable `t`, mêmes fonctions que le mode f(x) ; l'intervalle I est donné par ses bornes (`0`, `2pi`, `-inf`, `+inf`…), avec a < b. Dix exemples en un clic (folium de Descartes, cycloïde, astroïde, cardioïde, spirales…).
- **Tracé** : courbe orientée (flèches), repère orthonormé, zoom/déplacement/pincement, lecture de t et M(t) au survol, point mobile M(t₀) (curseur, saisie ou toucher).
- **Informations** (activables comme dans le mode f(x)) : dérivées x′, y′ ; tableau de variations de x et de y par morceaux ; points où x′ ou y′ s'annule (tangentes horizontales/verticales) ; points stationnaires (γ′ = 0) avec les entiers p et q et leur nature (ordinaire, inflexion, rebroussement de 1re ou 2e espèce) ; points d'inflexion (det(γ′, γ″)) ; branches infinies : asymptotes horizontale, verticale ou oblique avec **position de la courbe** et points d'intersection éventuels, branches paraboliques ; tangente et normale en t₀, courbure, cercle osculateur ; longueur d'un arc entre deux paramètres et longueur totale (reconnaissance de formes simples comme 2π, 8, 6).
- **PDF** : bouton « Générer le PDF » (fiche A4 avec deux graphiques et toutes les informations).
- Les dérivées sont calculées formellement, les limites, racines et longueurs numériquement (pour un intervalle non borné, la recherche porte sur 40 unités de t autour de la partie finie de I). Vérifications faites : cercle (longueur 2π), arche de cycloïde (8), astroïde (6), cardioïde (16), asymptote y = −x − 1 du folium, asymptotes de (t ; t + 1/t), rebroussements de (t² ; t³).

## Spé Maths A : partie 4, calcul matriciel et algèbre linéaire

Treize cours ont été ajoutés à l'onglet **Cours** de `SpeMathsA.html` (cours 21 à 33), d'après les chapitres 1 à 4 de la partie « Calcul matriciel – Algèbre linéaire et bilinéaire » du livre de référence :

- **Plan de la partie 4** (introduction, fil conducteur : objet géométrique ↔ matrice dans une base) ;
- **Espaces vectoriels et applications linéaires** : espaces et sous-espaces, familles libres/génératrices, bases et coordonnées ; dimension, base incomplète, sommes directes, supplémentaires, formule de Grassmann ; applications linéaires, noyau, image, théorème du rang ; endomorphismes, projecteurs, symétries, hyperplans, sous-espaces stables ;
- **Calcul matriciel** : produit, transposée, trace, matrices usuelles ; matrice d'une application linéaire, changement de base, matrices semblables, rang ; inversibilité, opérations élémentaires, pivot de Gauss, systèmes linéaires ;
- **Déterminants** : propriétés et calcul (interprétation en aire/volume, orientation) ; développement, comatrice, formules de Cramer, déterminant d'un endomorphisme, Vandermonde ;
- **Réduction des endomorphismes** : éléments propres, polynôme caractéristique ; diagonalisation et puissances ; trigonalisation, polynômes annulateurs, Cayley-Hamilton, aperçu de la décomposition de Jordan.

Une trentaine de **schémas SVG** (thème clair/sombre, adaptés au mobile) illustrent les notions : libre/liée, plan engendré, coordonnées, somme directe, Grassmann, noyau/image, théorème du rang, projecteurs et symétries, hyperplans, produit matriciel (schéma de Falk), transformation du carré unité, changement de base, systèmes (droites sécantes/parallèles), aire et volume d'un déterminant, orientation, Cramer, vecteurs propres et ellipse, polynôme caractéristique, organigramme de diagonalisation, convergence des puissances. Les figures portent la classe `nomx` (pas de conversion LaTeX dans les textes SVG). Chaque cours s'ouvre sur un encadré « Un peu d'histoire » quand le chapitre en donne un (Grassmann/Peano, Cayley, Gauss/Cauchy, Cayley-Hamilton).

La partie euclidienne du programme (produit scalaire, projections orthogonales, isométries, Gram-Schmidt) n'est pas encore traitée. Dans l'onglet **Programme**, les trois premières puces du point 4° portent la mention « cours disponible ».
