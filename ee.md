
# Pratique 1 — Portfolio HTML + Tailwind (débutant)

*Fichier : `02-pratique-portfolio-html-tailwind.md`*
**Durée totale : 2 h** — **Barème : 100 points**



# PARTIE 1 — COMPRÉHENSION (20 points)

### 1.1 Définitions (6 pts)

1. **Balise sémantique (ex. `<header>`)** :
   ......................................................................................................................
2. **Responsive (mobile-first)** :
   ......................................................................................................................
3. **Classe Tailwind** :
   ......................................................................................................................

### 1.2 Squelette d’une page (6 pts)

Complétez les éléments manquants (mots-clés) :

```
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8">
  <title>Portfolio</title>
  <meta name="viewport" content="________________________">
  <script src="https://cdn.______________.com"></script>
</head>
<body>
  <!-- Contenu -->
</body>
</html>
```

### 1.3 Accessibilité (8 pts)

Cochez la/les bonne(s) réponse(s).

1. L’attribut **obligatoire** sur une image de contenu est :
   [ ] `title`  [ ] `class`  [ ] `alt`  [ ] `role`

2. Une image **décorative** doit avoir :
   [ ] `alt="image"`  [ ] `alt=""`  [ ] `alt="decor"`  [ ] rien

3. L’attribut qui **relie** un label à son champ est :
   [ ] `htmlFor`  [ ] `id`  [ ] `for`  [ ] `name`

---

## PARTIE 2 — PRATIQUE RAPIDE (Texte & Layout) (40 points)

### 2.1 Héro minimal (16 pts)

Complétez les classes Tailwind pour obtenir : **titre 3xl (mobile) → 5xl (md)**, paragraphe en **texte slate-700**, bouton **fond bleu** + **texte blanc**.

```html
<section class="px-4 py-16 md:py-24">
  <h1 class="________ ________ font-semibold">Développeur IA & Cloud</h1>
  <p class="mt-3 ________">Je construis des projets IA et Cloud.</p>
  <a href="#projects" class="inline-block mt-6 ________ ________ px-5 py-3 rounded-lg">
    Voir mes projets
  </a>
</section>
```

### 2.2 Grille de projets (12 pts)

Objectif : **1 colonne** mobile → **3 colonnes** dès `lg`, espace **gap-6**, cards blanches avec **ombre**.

```html
<section class="grid ________ ________">
  <article class="bg-white ________ rounded-xl p-4">Projet 1</article>
  <article class="bg-white ________ rounded-xl p-4">Projet 2</article>
  <article class="bg-white ________ rounded-xl p-4">Projet 3</article>
</section>
```

### 2.3 Header sticky (12 pts)

Objectif : header **collant** en haut, fond **blanc translucide**, **bordure bas**, nav centrée (container : `mx-auto max-w-6xl px-4 py-3`).

```html
<header class="________ ________ bg-white/90 backdrop-blur ________">
  <nav class="________ ________ ________ ________">
    <a class="font-semibold">[Votre Nom]</a>
    <ul class="hidden md:flex gap-6 text-sm">
      <li><a class="hover:text-blue-600 font-semibold" href="#projects">Projets</a></li>
      <li><a class="hover:text-blue-600 font-semibold" href="#contact">Contact</a></li>
    </ul>
  </nav>
</header>
```

---

## PARTIE 3 — MÉDIAS & FORMULAIRE (30 points)

### 3.1 Image de carte (10 pts)

Exigences : image **pleine largeur**, **hauteur fixe h-40**, **recadrage propre**.

```html
<img src="assets/projet.jpg" alt="____________________________" class="________ ________ ________">
```

### 3.2 Figure + légende (8 pts)

Complétez :

```html
<figure class="max-w-3xl mx-auto">
  <img src="assets/dashboard.png" alt="____________________________________" class="w-full rounded-lg border">
  <____________ class="mt-2 text-sm text-slate-500">
    Figure — Tableau de bord de suivi (accuracy, recall, latence)
  </____________>
</figure>
```

### 3.3 Formulaire de contact (12 pts)

Objectif : label lié, champ **plein largeur**, focus **anneau bleu**, bouton bleu arrondi.

```html
<form class="mt-6 max-w-xl mx-auto space-y-4" onsubmit="event.__________________(); alert('OK');">
  <div>
    <label for="email" class="block text-sm font-semibold">Email</label>
    <input id="email" type="email" required
           class="w-full border rounded-lg px-3 py-2 ________ ________">
  </div>

  <div>
    <label for="message" class="block text-sm font-semibold">Message</label>
    <textarea id="message" rows="4" required
              class="w-full border rounded-lg px-3 py-2"></textarea>
  </div>

  <button class="px-5 py-3 bg-blue-600 text-white ________">Envoyer</button>
</form>
```

---

## PARTIE 4 — MINI-QUIZ (10 points)

Cochez la/les bonne(s) réponse(s).

1. Le responsive **mobile-first** signifie :
   [ ] On code d’abord pour desktop
   [ ] Les classes **sans préfixe** s’appliquent d’abord sur mobile
   [ ] Tailwind impose `md:` partout

2. Pour **centrer** un container max 1152px :
   [ ] `max-w-6xl mx-auto`
   [ ] `w-screen`
   [ ] `justify-center` seul

3. Pour **cacher sur mobile et montrer à partir de `md`** :
   [ ] `hidden md:block`
   [ ] `block md:hidden`
   [ ] `md:hidden`

4. Lien externe **sécurisé** en nouvel onglet :
   [ ] `target="_blank"`
   [ ] `target="_blank" rel="noopener"`
   [ ] `target="new"`

---

## BARÈME GLOBAL

| Partie                               | Points  |
| ------------------------------------ | ------- |
| Partie 1 — Compréhension             | 20      |
| Partie 2 — Pratique (texte & layout) | 40      |
| Partie 3 — Médias & formulaire       | 30      |
| Partie 4 — Mini-quiz                 | 10      |
| **Total**                            | **100** |

---

## CORRIGÉ (référence rapide)

> À garder pour vous, ou donner après remise.

**1.2** `content="width=device-width, initial-scale=1"` ; `tailwindcss`
**1.3** `alt` ; `alt=""` ; `for` + `id`

**2.1**
`text-3xl md:text-5xl` ; `text-slate-700` ; `bg-blue-600 text-white`

**2.2**
`grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6` ; `shadow`

**2.3**
`sticky top-0` ; `border-b` ; `mx-auto max-w-6xl px-4 py-3`

**3.1**
`alt="Aperçu du projet"` ; `w-full h-40 object-cover`

**3.2**
`figcaption`

**3.3**
`preventDefault` ; `focus:outline-none focus:ring-2 focus:ring-blue-500` ; `rounded-lg hover:bg-blue-500`

**4.1** mobile-first = classes de base pour mobile
**4.2** `max-w-6xl mx-auto`
**4.3** `hidden md:block`
**4.4** `target="_blank" rel="noopener"`




# Annexe 1 




# 1) Paramètres (API) — mémo rapide

| Paramètre           | Ce que ça contrôle                                               |  Plage utile |                        Valeur sûre (générale) | Risques si trop haut             |
| ------------------- | ---------------------------------------------------------------- | -----------: | --------------------------------------------: | -------------------------------- |
| `temperature`       | Variabilité/créativité du texte                                  |      0.0–1.2 | **0.2–0.3** (factuel) / **0.8–0.9** (créatif) | Hors-sujet, verbiage             |
| `top_p`             | Troncature par probabilité cumulée (alternative à `temperature`) |      0.5–1.0 |            **1.0** si tu règles `temperature` | Réponses erratiques si trop bas  |
| `max_tokens`        | Longueur **max** de la sortie                                    | selon besoin |       **80–120** (court) / **180–300** (long) | Coupures en fin de réponse       |
| `frequency_penalty` | Pénalise la répétition de tokens                                 |      0.0–1.0 |                                   **0.0–0.2** | Style haché, pertes de précision |
| `presence_penalty`  | Encourage nouvelles idées/sujets                                 |      0.0–1.0 |                                   **0.0–0.2** | Digressions, hors sujet          |
| `response_format`   | Structure (texte, JSON)                                          |            — |                                         texte | JSON invalide si mal spécifié    |
| `stop`              | Séquence(s) d’arrêt                                              |            — |                                             — | Troncature involontaire          |

> En **chat normal** (sans API), tu ne règles pas ces nombres, mais tu peux **mimer** l’effet via des consignes de **style** (“réponse factuelle…”, “développe, compare…”) et en **imposant la longueur** (“25–40 mots”, “150–200 mots”).


# 2) Préréglages prêts à copier (API)

| Objectif              | `temperature` | `top_p` | `max_tokens` | `frequency_penalty` | `presence_penalty` | Style à indiquer dans le prompt                                       |
| --------------------- | ------------: | ------: | -----------: | ------------------: | -----------------: | --------------------------------------------------------------------- |
| **Direct & court**    |   **0.1–0.2** |     1.0 |       **80** |                 0.0 |                0.0 | “**Une phrase, 25–40 mots, factuel, sans liste ni code.**”            |
| **Direct & long**     |   **0.2–0.3** |     1.0 |  **160–220** |                 0.0 |                0.0 | “**120–160 mots, ton académique, sans liste.**”                       |
| **Élargi & court**    |       **0.8** |     1.0 |  **100–140** |                 0.1 |                0.1 | “**30–50 mots, ajoute une nuance/contre-exemple, 1 phrase.**”         |
| **Élargi & long**     |       **0.9** |     1.0 |  **220–320** |             0.1–0.2 |            0.1–0.2 | “**150–200 mots, compare, exemples + anti-pattern, mini-code.**”      |
| **Code-only**         |       **0.1** |     1.0 |   selon bloc |                 0.0 |                0.0 | “**Réponds uniquement par le code complété, aucun commentaire.**”     |
| **QCM télégraphique** |       **0.1** |     1.0 |    **60–90** |                 0.0 |                0.0 | “**Réponses seulement, format court ‘1)… 2)…’, sans justification.**” |



# 3) Équivalents “sans API” (consignes de style à coller)

| Cible              | À écrire dans le prompt (équiv. réglages)                                                                                 |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **Direct & court** | “**Style température ≈ 0.1** : réponse **factuelle**, **une seule phrase (25–40 mots)**, **sans liste**, **sans code**.”  |
| **Direct & long**  | “**Temp ≈ 0.2** : **120–160 mots**, **ton académique**, **pas de liste**, **pas de digression**.”                         |
| **Élargi & court** | “**Temp ≈ 0.9** : **30–50 mots**, **une nuance** (comparaison/avertissement), **une seule phrase**.”                      |
| **Élargi & long**  | “**Temp ≈ 0.9** : **150–200 mots**, **compare**, **exemples + contre-exemples**, **mini-code** autorisé, **sans puces**.” |
| **Code-only**      | “**Réponds uniquement par le code**, **aucun commentaire ni texte**.”                                                     |



# 4) Mini-exemples (pour ta Q1.1 “balise sémantique `<header>`”)

* **Direct & court (≈0.1)** : “Une balise sémantique HTML, comme `<header>`, indique la fonction d’une zone (en-tête) pour améliorer structure, accessibilité et interprétation par les moteurs de recherche, sans imposer de style par défaut.”
* **Élargi & long (≈0.9)** : paragraphe 150–200 mots **avec** comparaison à `<div>`, mini-code `<header>...</header>`, et **anti-pattern** (ne pas l’utiliser pour la mise en page seule).


<br/>

# Annexe 2 - Comment ça fonctionne par défaut



* **Dans l’app ChatGPT** (sans API), tu **ne règles pas** `temperature`, `top_p`, `max_tokens`, etc. Ils ont des **valeurs par défaut**.
* Quand tu écris *“sois concis, précis, le plus court possible”*, tu **n’changes pas** ces nombres : tu **influences le style** et la **longueur désirée**.
* Si tu demandes *“500 mots”*, le modèle **essaiera** d’atteindre ~500 mots **si** sa limite de sortie le permet (sinon il s’arrête avant).



## Ce qui se passe “sous le capot”

* **Température** : reste à la valeur par défaut du chat. Dire “sois précis” **n’abaisse pas** la vraie température, mais pousse le modèle à **répondre de façon plus déterministe**.
* **Max tokens** (longueur max) : dans le chat, c’est **fixé par le modèle**. Ta consigne “500 mots” est une **intention** ; le modèle s’y conforme **tant que** la limite n’est pas atteinte.
* **Top-p / pénalités** : non modifiées en chat. Tes consignes peuvent seulement **orchestrer** le style, pas les nombres.



## Mapping pratique (ce que tu écris → ce que ça implique)

| Ce que tu écris dans le prompt                                 | Effet observé (chat normal)        | Réglage **API** équivalent (si un jour tu l’utilises)      |
| -------------------------------------------------------------- | ---------------------------------- | ---------------------------------------------------------- |
| “**Sois concis** / **réponse courte**”                         | Le modèle vise 1–3 phrases         | `temperature: 0.2`, `max_tokens: 80–120`                   |
| “**Sois précis / factuel**”                                    | Style plus direct, peu d’exemples  | `temperature: 0.1–0.3`                                     |
| “**Le plus court possible**”                                   | Tente une phrase minimale          | `max_tokens: 40–80`, `temperature: 0.1–0.2`                |
| “**Donne 500 mots**”                                           | Tente ~500 mots (si limite OK)     | `max_tokens: 700–900` (≈ 500 mots), `temperature: 0.3–0.6` |
| “**Développe, compare, nuances, exemples et contre-exemples**” | Réponse plus longue, créative      | `temperature: 0.8–0.9`, `max_tokens: 220–400`              |
| “**Uniquement le code** / **sans liste** / **une phrase**”     | Forme stricte respectée            | `response_format: "text"`, + consigne système stricte      |
| “**En 25–40 mots**”                                            | Le modèle compte approximativement | `max_tokens: 60–80` (marge de sécurité)                    |

> Règle d’approximation : **1 mot ≈ 1.3–1.6 tokens**. Donc **500 mots ≈ 700–800 tokens** (prévois `max_tokens` ≥ 800 côté API).



## Deux exemples concrets (ta situation)

### 1) “Définitions — Balise sémantique — sois concis, précis, le plus court possible”

* **Paramètres réels en chat** : par défaut (tu ne les vois pas).
* **Effet attendu** : 1 phrase, définition sèche, sans exemples inutiles.
* **Si c’était en API** :

  ```json
  {
    "temperature": 0.2,
    "max_tokens": 80,
    "messages": [
      {"role":"system","content":"Réponds factuellement et en une seule phrase."},
      {"role":"user","content":"Définis une balise sémantique en HTML (ex: <header>) en une phrase très courte, sans liste ni code."}
    ]
  }
  ```

### 2) “Réponse de **500 mots**, sois le plus long possible”

* **Paramètres réels en chat** : par défaut ; la sortie sera longue **jusqu’à la limite** du modèle.
* **Si c’était en API** :

  ```json
  {
    "temperature": 0.6,
    "max_tokens": 900,
    "messages": [
      {"role":"system","content":"Style clair, pédagogique, détaillé."},
      {"role":"user","content":"Écris ~500 mots sur les balises sémantiques HTML, centrées sur <header>, avec comparaison à <div> et implications accessibilité/SEO."}
    ]
  }
  ```


## Astuce infaillible sans API

Pour “simuler” les réglages :

* **Temp basse (précision)** → ajoute : *“réponse factuelle, une phrase, sans liste, vocabulaire simple.”*
* **Temp haute (créativité)** → ajoute : *“développe, compare, nuances, exemples concrets et contre-exemples.”*
* **Longueur** → impose **bornes** (“en 25–40 mots”, “en 150–200 mots”, “≈500 mots”).



<br/>

# Annexe 3 - Démonstration guidée (même question, plusieurs réponses)


L'objectif est de vous montrer qu’une même question

> 1. **Balise sémantique (ex. `<header>`)** : …
>    peut produire **des réponses variées** selon les consignes (style “température” et longueur).

# 1) Démonstration guidée (4 variantes canoniques)

Donne la **même question**, mais change la consigne. Demande aux étudiants : « Copiez/collez, comparez la forme et le contenu. »

| Variante             | Objectif                             | Prompt à donner tel quel                                                                                                                                                            | Extrait de réponse attendue (exemple)                                                                                                                                                                                         |
| -------------------- | ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A — Directe & courte | Précision, 1 phrase                  | **« Une seule phrase de 25–40 mots, définition factuelle d’une balise sémantique en HTML en citant `<header>`, sans code, sans liste, vocabulaire simple. »**                       | *Une balise sémantique, comme `<header>`, indique la fonction d’une section (en-tête) pour améliorer la structure du document, l’accessibilité et la compréhension par les moteurs de recherche, sans effet de style visuel.* |
| B — Directe & longue | Définition détaillée, ton académique | **« En 120–160 mots : définition précise d’une balise sémantique avec l’exemple `<header>` ; pas de listes, pas de digressions ; objectifs : structure, accessibilité, SEO. »**     | *… Contrairement à `<div>`, elle porte du sens exploitable par lecteurs d’écran ; `<header>` marque l’en-tête d’une page ou section (titre, logo, intro nav), ce qui renforce accessibilité et interprétation SEO…*           |
| C — Élargie & courte | Nuance/contre-ex., 1 phrase          | **« En 30–50 mots, explique une balise sémantique en prenant `<header>` ; ajoute une nuance (différence avec `<div>` ou mise en garde). Une seule phrase. »**                       | *… utile si on l’emploie à bon escient, et non pour de la mise en forme pure, rôle du CSS…*                                                                                                                                   |
| D — Élargie & longue | Comparaison + mini-code              | **« 150–200 mots : explique la notion avec `<header>`, compare à `<div>`, ajoute 1 mini-exemple HTML compact, mentionne accessibilité/SEO et 1 mauvaise pratique ; sans listes. »** | *…* `html<br><header><h1>Mon Site</h1><nav>…</nav></header>` *… mauvaise pratique : multiplier `<header>` sans logique structurelle…*                                                                                         |

> But pédagogique : visualiser comment **la consigne** (basse vs haute “température” de style, court vs long) impacte **le niveau de détail**, **les comparaisons**, **les exemples** et **la forme** (phrase unique vs paragraphe).



# 2) Atelier “échelle de contraintes”

Même question, mais tu **augmentes progressivement** les contraintes :

1. **Niveau 1 (20 mots max)** : « Définis “balise sémantique” avec l’exemple `<header>` en **≤ 20 mots**, sans code. »
2. **Niveau 2 (une phrase + nuance)** : « Une phrase **30–45 mots**, ajoute une nuance vs `<div>`. »
3. **Niveau 3 (100–120 mots)** : « Définition + accessibilité + SEO, **100–120 mots**, sans liste. »
4. **Niveau 4 (avec mini-code)** : « Même contenu + **mini-exemple HTML** compact, **150–180 mots**. »

> Devoir : les étudiants collent leurs 4 sorties et notent ce qui **change** (densité, précision, structure, exemples, risques d’erreurs).



# 3) A/B Testing en binôme

* **A** demande : « Une phrase de 25–40 mots, factuelle, sans exemple supplémentaire. »
* **B** demande : « 150–200 mots, développe, compare à `<div>`, ajoute un contre-exemple. »
* Ils **échangent** et cochent ce qui diffère : longueur, structure, vocabulaire, présence de nuances/contre-exemples, code oui/non.



# 4) Rôles ciblés (persona prompting)

Donne 3 rôles pour la **même question** :

1. **Lecteur d’écran (accessibilité)** : « Réponds en 60–80 mots, focus ARIA/repérage structurel. »
2. **SEO** : « 60–80 mots, impact sur balisage sémantique et compréhension par moteurs. »
3. **Designer CSS** : « 60–80 mots, séparer sens (HTML) et présentation (CSS). »

> Comparez l’**angle** et les **exemples** choisis selon le rôle.



# 5) Contre-exemple guidé

* Prompt : « En 60–80 mots, donne **1 bon usage** de `<header>` et **1 contre-exemple** où `<header>` est mal employé. Sans liste. »
* Objectif : montrer que la **même notion** peut être expliquée avec une **structure dialectique** (pour/contre).



# 6) Tableau “paramètres de style”

*(À afficher avant l’activité ; ce ne sont pas des réglages techniques du chat, mais des **consignes de style** qui simulent température/longueur.)*

| Intention pédagogique | Formulation de consigne (à copier)                                                 | Effet attendu                           |
| --------------------- | ---------------------------------------------------------------------------------- | --------------------------------------- |
| Précision minimale    | « Une seule phrase, 25–40 mots, factuelle, sans liste ni code. »                   | Sortie compacte, peu d’exemples         |
| Nuances               | « Développe, compare, ajoute nuances, exemples et contre-exemples. 150–200 mots. » | Sortie riche, comparaisons, cas limites |
| Format strict         | « Une seule phrase. Pas de liste. Pas de code. »                                   | Respect de forme                        |
| Exemple imposé        | « Cite `<header>` explicitement. »                                                 | Ancrage concret                         |
| Mise en garde         | « Ajoute une mauvaise pratique fréquente. »                                        | Pensée critique                         |
| Contrôle longueur     | « En 100–120 mots (ne dépasse pas 120). »                                          | Stabilité de taille                     |



# 7) Mini-rubrique de correction (rapide)

* **Exactitude (4 pts)** : définition correcte, rôle de sens vs style.
* **Pertinence (3 pts)** : `<header>` bien positionné (page/section), mention accessibilité/SEO au bon endroit.
* **Concision/Format (2 pts)** : respecte phrase unique / bornes de mots / pas de liste si demandé.
* **Nuance (1 pt)** : comparaison utile (`<div>`, mauvaise pratique).



# 8) Fiche “prête à coller” pour les apprenants
> **Consigne** (choisissez 1 des 4) :
> A) Une phrase 25–40 mots, factuelle, avec `<header>`, sans code/liste.
> B) 120–160 mots, définition précise + accessibilité/SEO, sans liste.
> C) Une phrase 30–50 mots, avec nuance vs `<div>`.
> D) 150–200 mots, avec comparaison, mini-code, et 1 mauvaise pratique.
> **Après** : comparez les sorties A/B/C/D et surlignez ce qui change (longueur, densité, exemples, ton, structure).

