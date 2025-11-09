
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


