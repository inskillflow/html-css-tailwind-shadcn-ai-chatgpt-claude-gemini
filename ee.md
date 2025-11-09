Parfait — voici une **version courte, simple et notée** du même style, mais 100% centrée sur **PORTFOLIO HTML + Tailwind**. Copie/colle tel quel.

---

# Pratique 1 — Portfolio HTML + Tailwind (débutant)

*Fichier : `02-pratique-portfolio-html-tailwind.md`*
**Durée totale : 2 h** — **Barème : 100 points**

---

## PARTIE 1 — COMPRÉHENSION (20 points)

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

---

Si tu veux, je te le transforme en **doc “gpt15” Thinkific** ou en **`index.html` + `style` minimal** (même contenu, prêt à publier).
