# COURS-PROJET : Portfolio Web avec IA Générative

**Format : Construction progressive d'un portfolio 3 pages**  
**Technologies : HTML5, Tailwind v3, IA générative (ChatGPT/Claude)**



## TABLE DES MATIÈRES

1. [Introduction : IA générative et développement web](#partie-1-introduction)
2. [Fondamentaux : Température, Top-p, Tokens](#partie-2-fondamentaux-ia)
3. [Méthode JSON pour structurer vos prompts](#partie-3-methode-json)
4. [Construction Section 1 : Squelette + Header](#partie-4-squelette-header)
5. [Construction Section 2 : Hero Section](#partie-5-hero-section)
6. [Construction Section 3 : Section À propos](#partie-6-section-a-propos)
7. [Construction Section 4 : Grid de projets](#partie-7-grid-projets)
8. [Construction Section 5 : Formulaire contact](#partie-8-formulaire-contact)
9. [Construction Section 6 : Footer](#partie-9-footer)
10. [Construction Section 7 : Page Démos IA](#partie-10-page-demos-ia)
11. [Construction Section 8 : Page Architecture Cloud](#partie-11-page-architecture-cloud)
12. [Optimisation et validation finale](#partie-12-validation-finale)



# Références

Une sélection de ressources à consulter pour l’IA générative, le prototypage rapide et les ateliers AWS.

## 1. Assistants IA généralistes

1. **Claude**  
   Service d’IA conversationnelle d’Anthropic, très performant sur les longues sorties et l’analyse de documents.  
   → https://claude.ai/new

2. **ChatGPT**  
   Interface d’OpenAI, idéale pour la génération de code, la rédaction pédagogique et les assistants spécialisés.  
   → https://chatgpt.com/

3. **Google Gemini**  
   Accès aux modèles multimodaux de Google, utile pour les cas d’usage Google Workspace et la génération de contenu.  
   → https://gemini.google.com/app

---

## 2. Contenu pédagogique InSkillFlow / AWS

4. **01 – Introduction IA / ML / IA générative (GitHub)**  
   Document d’introduction aux fondements de l’IA générative, positionnement, vocabulaire et contexte AWS.  
   → https://github.com/inskillflow/Services-AWS-pour-les-Fondements-de-l-IA-Generative/blob/main/01-introduction-ia-ml-gen.md

5. **02 – Pratique 1 : Introduction IA / ML / IA générative (GitHub)**  
   Première pratique guidée pour manipuler les concepts vus dans l’introduction et les appliquer dans un atelier structuré.  
   → https://github.com/inskillflow/Services-AWS-pour-les-Fondements-de-l-IA-Generative/blob/main/02-pratique-1-introduction-ia-ml-gen.md


<br/>

## PARTIE 1 : INTRODUCTION

### Objectif du cours

Vous allez apprendre à utiliser l'IA générative pour construire un portfolio web professionnel. La clé : maîtriser les paramètres de génération pour obtenir du code précis et valide.

### Différence fondamentale

**IA pour texte créatif** VS **IA pour code**

| Aspect | Texte créatif | Code HTML/Tailwind |
|--------|---------------|-------------------|
| Température | 0.7 - 1.0 | 0.1 - 0.3 |
| Variabilité | Souhaitée | Indésirable |
| Erreurs | Tolérées | Bloquantes |
| Validation | Subjective | Syntaxique |

**Règle d'or** : Le code requiert une température BASSE pour éviter l'invention de syntaxe.

### Ce que vous allez livrer

```
portfolio/
├── index.html                  (page principale)
├── ai-demos.html              (démos IA avec modale)
├── cloud-architecture.html    (architecture)
├── assets/
│   ├── projet1.jpg
│   ├── projet2.jpg
│   ├── projet3.jpg
│   ├── screenshot-mobile.png
│   └── screenshot-desktop.png
├── README.md
└── prompts-log.md             (tous vos prompts documentés)
```

---

## PARTIE 2 : FONDAMENTAUX IA

### 2.1 Température : contrôle de la précision

**Définition simple**  
La température = le niveau de "créativité" de l'IA.
- Température BASSE (0.1-0.3) = l'IA choisit les mots les plus probables, prévisible, précis
- Température HAUTE (0.7-1.0) = l'IA explore, invente, surprend

**Pourquoi c'est critique pour le code**

Le code a UNE syntaxe correcte. Si l'IA "invente", ça casse tout.

---

### EXPÉRIENCE 1 : Testez vous-même

**Consigne :** Générez un bouton avec 3 températures différentes.

**Prompt à utiliser :**
```
Génère un bouton HTML avec classe Tailwind pour un call-to-action.
```

**Test A : Temperature 0.1**
```
Temperature : 0.1
Top-p : 0.8
Max tokens : 100
```

**Résultat attendu :**
```html
<button class="px-4 py-2 bg-blue-600 text-white rounded">Cliquez ici</button>
```
Classes standards, prévisibles.

**Test B : Temperature 0.5**
```
Temperature : 0.5
Top-p : 0.8
Max tokens : 100
```

**Résultat possible :**
```html
<button class="px-6 py-3 bg-indigo-500 text-white rounded-xl shadow-lg hover:scale-105">Découvrir</button>
```
Plus créatif, mais classes encore valides (si chanceux).

**Test C : Temperature 0.9**
```
Temperature : 0.9
Top-p : 0.8
Max tokens : 100
```

**Résultat possible :**
```html
<button class="sparkle-btn mega-action flash-pulse">Action!</button>
```
PROBLÈME : `sparkle-btn`, `mega-action`, `flash-pulse` = classes inventées, n'existent pas dans Tailwind !

---

### EXERCICE : Faites le test maintenant

1. Ouvrez ChatGPT ou Claude
2. Testez les 3 températures avec le prompt ci-dessus
3. Notez vos résultats dans `prompts-log.md` :

```markdown
## Expérience température

### Test 0.1
Résultat : [coller le code]
Classes valides : OUI / NON

### Test 0.5
Résultat : [coller le code]
Classes valides : OUI / NON

### Test 0.9
Résultat : [coller le code]
Classes valides : OUI / NON

Conclusion : [votre observation]
```

**Temps estimé : 10 minutes**

---

### Exemples concrets avec explications

**Exemple 1 : Header de navigation**

Temperature 0.9 (INCORRECT) :
```html
<header class="sparkle-magic super-nav mega-header floating-top">
  <nav class="ultra-links cosmic-spacing">
```
Problème : `sparkle-magic`, `super-nav`, `mega-header`, `floating-top`, `ultra-links`, `cosmic-spacing` = TOUT EST INVENTÉ.

Temperature 0.2 (CORRECT) :
```html
<header class="sticky top-0 bg-white border-b">
  <nav class="flex items-center justify-between">
```
Classes valides : `sticky`, `top-0`, `bg-white`, `border-b`, `flex`, `items-center`, `justify-between` = toutes existent dans Tailwind.

**Exemple 2 : Card de projet**

Temperature 0.8 (INCORRECT) :
```html
<div class="project-glow shadow-rainbow border-magical rounded-mega">
```
Problème : `project-glow`, `shadow-rainbow`, `border-magical`, `rounded-mega` = inventées.

Temperature 0.2 (CORRECT) :
```html
<div class="border shadow-sm rounded-lg">
```
Classes valides : `border`, `shadow-sm`, `rounded-lg` = standards Tailwind.

**Exemple 3 : Formulaire**

Temperature 0.7 (INCORRECT) :
```html
<input class="field-magic auto-validate glow-focus" type="text">
```
Problème : `field-magic`, `auto-validate`, `glow-focus` = n'existent pas.

Temperature 0.1 (CORRECT) :
```html
<input class="w-full border rounded p-3" type="text">
```
Classes valides : `w-full`, `border`, `rounded`, `p-3` = toutes réelles.

---

### Règle à mémoriser

**Pour TOUT code HTML/Tailwind dans ce cours :**
```
Temperature : 0.1 à 0.3 MAX
```

**Exception (rare) :**
- Gradient de couleurs : 0.3 OK (légère liberté)
- Tout le reste : 0.1-0.2

### 2.2 Top-p : filtrage du vocabulaire

**Définition simple**  
Top-p = "garde seulement les X% de mots les plus probables".

Exemple :
```
L'IA doit choisir le prochain mot après "Le soleil est..."

Probabilités :
"jaune" → 40%
"brillant" → 30%
"chaud" → 20%
"grand" → 5%
"délicieux" → 3%  ← bizarre mais possible
"carré" → 2%      ← incohérent

Top-p = 0.9 :
L'IA garde seulement "jaune" + "brillant" + "chaud" (= 90%)
Elle ignore "grand", "délicieux", "carré"

Top-p = 1.0 :
L'IA peut choisir n'importe quoi, même "carré" (incohérent)
```

**Application au code**

Pour du code, on veut que l'IA utilise SEULEMENT les classes Tailwind communes.

| Top-p | Effet sur les classes Tailwind |
|-------|-------------------------------|
| 0.8 | Classes ultra-standards (bg-white, text-xl, p-4) |
| 0.85 | Classes communes + quelques variantes (bg-blue-600, shadow-sm) |
| 0.9 | Toutes classes valides autorisées |
| 1.0 | RISQUE de classes inventées |

**Règle** : Pour du code, restez à 0.8 ou 0.85.

---

### EXPÉRIENCE 2 : Testez Top-p

**Prompt à utiliser :**
```
Génère une card de projet en HTML/Tailwind.
Inclus : image, titre H3, description courte.

Temperature : 0.2 (fixe)
Max tokens : 300
```

**Test A : Top-p 0.8**
```
Top-p : 0.8
```

**Résultat attendu :**
```html
<div class="border rounded p-4">
  <img src="projet.jpg" alt="Projet" class="w-full">
  <h3 class="font-bold mt-2">Titre</h3>
  <p class="text-sm">Description</p>
</div>
```
Classes basiques, sûres.

**Test B : Top-p 0.95**
```
Top-p : 0.95
```

**Résultat possible :**
```html
<article class="border-2 border-slate-200 rounded-xl shadow-md overflow-hidden">
  <img src="projet.jpg" alt="Projet" class="w-full h-48 object-cover">
  <div class="p-6">
    <h3 class="text-lg font-semibold text-slate-800">Titre</h3>
    <p class="mt-2 text-sm text-slate-600 leading-relaxed">Description</p>
  </div>
</article>
```
Plus de variété, classes toujours valides mais moins communes (`border-2`, `leading-relaxed`).

**Test C : Top-p 1.0**
```
Top-p : 1.0
```

**Résultat risqué :**
```html
<div class="card-enhanced border-stylish rounded-premium shadow-ultra">
```
PROBLÈME possible : `card-enhanced`, `border-stylish`, `rounded-premium`, `shadow-ultra` = risque d'invention.

---

### EXERCICE : Testez maintenant

1. Générez 3 fois avec top-p différents
2. Vérifiez chaque classe sur https://tailwindcss.com/docs
3. Notez les classes inventées (si présentes)

**Temps estimé : 15 minutes**

### 2.3 Max tokens : longueur de sortie

**Définition simple**  
Max tokens = combien de "morceaux de mots" l'IA peut générer maximum.

**Équivalence approximative :**
```
1 token ≈ 4 caractères en français
100 tokens ≈ 75 mots
400 tokens ≈ 300 mots
```

---

### EXPÉRIENCE 3 : Testez Max tokens

**Prompt à utiliser :**
```
Génère une section "À propos" avec :
- H2 "À propos"
- 2 paragraphes de présentation

Temperature : 0.2
Top-p : 0.8
```

**Test A : Max tokens 50**
```
Max tokens : 50
```

**Résultat attendu (TRONQUÉ) :**
```html
<section class="mx-auto max-w-6xl px-4 py-12">
  <h2 class="text-2xl font-semibold">À propos</h2>
  <p class="mt-3 text-slate-700">Je suis développeur
```
PROBLÈME : Coupé en plein milieu, balises non fermées.

**Test B : Max tokens 200**
```
Max tokens : 200
```

**Résultat attendu (COMPLET) :**
```html
<section class="mx-auto max-w-6xl px-4 py-12">
  <h2 class="text-2xl font-semibold">À propos</h2>
  <p class="mt-3 text-slate-700">Je suis développeur spécialisé en IA et Cloud.</p>
  <p class="mt-2 text-slate-700">Mes compétences incluent Python, ML, et déploiements scalables.</p>
</section>
```
Complet, balises fermées.

**Test C : Max tokens 1000**
```
Max tokens : 1000
```

**Résultat possible (TROP LONG) :**
```html
<section class="mx-auto max-w-6xl px-4 py-12">
  <h2 class="text-2xl font-semibold">À propos</h2>
  <p>...</p>
  <p>...</p>
  <p>...</p>
  <div>...</div>
  <!-- L'IA continue à ajouter du contenu non demandé -->
</section>
```
PROBLÈME : L'IA ajoute des éléments non demandés pour remplir le quota.

---

### EXERCICE : Trouvez le bon max_tokens

1. Testez avec 50, puis 200, puis 1000
2. Observez où le code est tronqué vs complet vs trop long
3. Notez le max_tokens optimal pour cette section

**Temps estimé : 10 minutes**

**Apprentissage :**
- Trop bas = tronqué (balises non fermées = erreur)
- Trop haut = verbeux (contenu non demandé)
- Optimal = juste assez pour le composant demandé

---

### Exemples de budgets recommandés

| Composant | Code typique | Max tokens | Justification |
|-----------|--------------|------------|---------------|
| Bouton simple | `<button class="...">Texte</button>` | 100 | Une ligne |
| Header | Header + nav + 4 liens | 400 | Structure moyenne |
| Section simple | Section + titre + texte | 250 | Quelques lignes |
| Grid 3 cards | Section + 3 articles répétitifs | 700 | Code répétitif mais long |
| Formulaire | Form + 4 champs + labels | 600 | Beaucoup d'attributs |
| Page complète | HTML head + body complet | 1200 | Document entier |

**Astuce :** Commencez toujours BAS (200-300), puis augmentez si tronqué.

### 2.4 Stop sequences : point d'arrêt

Utilisez pour contrôler précisément où l'IA s'arrête.

Exemple :
```json
"stop_sequences": ["</section>", "<!-- FIN -->"]
```

L'IA génère jusqu'à rencontrer cette chaîne, puis s'arrête.

### 2.5 Tableau de référence rapide

| Type de génération | Temp | Top-p | Tokens | Stop |
|-------------------|------|-------|--------|------|
| Structure HTML | 0.1-0.2 | 0.8 | 400-800 | `</html>` |
| Classes Tailwind | 0.2-0.3 | 0.85 | 300-600 | `</section>` |
| JavaScript simple | 0.2 | 0.85 | 400 | `</script>` |
| Documentation | 0.3-0.4 | 0.9 | 500 | n/a |
| Idées créatives | 0.7-0.9 | 0.95 | 700 | n/a |

---

## PARTIE 3 : ÉCRIRE DES PROMPTS EFFICACES

### 3.1 Le problème des prompts vagues

**Mauvais prompt :**
```
"Fais un header cool"
```
Résultat : L'IA invente n'importe quoi, classes inexistantes, structure bizarre.

**Bon prompt :**
```
Génère un header HTML avec :
- Tag <header>, classes sticky top-0 bg-white border-b
- Logo à gauche : lien vers index.html, texte "Portfolio"
- Navigation à droite : 3 liens (Projets, Démos, Contact)
- Responsive : menu caché sur mobile, visible sur desktop (md:)

Temperature : 0.2
```
Résultat : Code précis, utilisable immédiatement.

### 3.2 Règles d'un bon prompt

**1. Soyez précis sur la structure**
```
❌ "Fais une section"
✅ "Génère une section avec classe mx-auto max-w-6xl px-4 py-12"
```

**2. Listez tous les éléments**
```
❌ "Ajoute du contenu"
✅ "H2 avec texte 'Projets', puis grid de 3 cards"
```

**3. Spécifiez les classes Tailwind**
```
❌ "Rends ça joli"
✅ "Classes : border rounded-xl shadow-sm hover:shadow-lg"
```

**4. Mentionnez le responsive**
```
❌ "Adapte à mobile"
✅ "Mobile : grid-cols-1, Desktop (md:) : grid-cols-3"
```

**5. Indiquez les paramètres**
```
Temperature : 0.2
Max tokens : 600
```

### 3.3 Template de prompt efficace

Copiez et adaptez ce modèle :

```
Génère [composant] en HTML/Tailwind.

Structure :
- Tag : [balise]
- Classes conteneur : [classes]
- Layout : [flex/grid/...]

Contenu :
- Élément 1 : [détails]
- Élément 2 : [détails]
- ...

Responsive :
- Mobile : [comportement]
- Desktop (md:) : [comportement]

Temperature : [0.1-0.3]
Max tokens : [200-800]
```

**Exemple concret :**

```
Génère un bouton call-to-action en HTML/Tailwind.

Structure :
- Tag : <a>
- Classes : px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold
- Href : #projects

Contenu :
- Texte : "Voir mes projets"

Temperature : 0.2
Max tokens : 100
```

### 3.4 Quand être plus ou moins détaillé

**Composant simple (footer) :**
Prompt court OK, peu de risque d'erreur.

**Composant complexe (formulaire) :**
Prompt long nécessaire, beaucoup de détails critiques (id, for, required).

**Règle :** Si ça rate, ajoutez plus de détails au prompt.

---

## PARTIE 4 : SQUELETTE + HEADER

### 4.1 Création de l'arborescence

Commandes à exécuter :

```bash
mkdir portfolio
cd portfolio
mkdir assets
touch index.html
touch ai-demos.html
touch cloud-architecture.html
touch README.md
touch prompts-log.md
```

### 4.2 Génération du squelette HTML

**Prompt direct :**

```
Génère le squelette HTML5 complet selon ces spécifications JSON.
Inclus :
- DOCTYPE html
- Meta charset UTF-8
- Meta viewport pour responsive
- Title : "Portfolio - Développeur IA & Cloud"
- Meta description : "Portfolio professionnel : projets IA, démos, architecture Cloud"
- Script Tailwind v3 CDN : https://cdn.tailwindcss.com
- Body avec classes : antialiased text-slate-800 bg-white
- Commentaire dans body : "<!-- Contenu à ajouter -->"

NE GENERE QUE le squelette, sans contenu dans body.

Paramètres :
Temperature : 0.1
Top-p : 0.8
Max tokens : 400
```

**Résultat attendu :**

```html
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8">
  <title>Portfolio - Développeur IA & Cloud</title>
  <meta name="description" content="Portfolio professionnel : projets IA, démos, architecture Cloud">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="antialiased text-slate-800 bg-white">
  <!-- Contenu à ajouter -->
</body>
</html>
```

**Action :**
1. Copiez ce code dans `portfolio/index.html`
2. Ouvrez dans navigateur pour vérifier (page blanche normale)
3. Documentez dans `prompts-log.md` :

```markdown
## Section 1 : Squelette HTML
Date : [date]
Temperature : 0.1
Top-p : 0.8
Max tokens : 400

Prompt :
[collez votre prompt]

Résultat : OK
Ajustements : aucun
```

### 4.3 Génération du header

**Prompt direct :**

```
Génère un header sticky responsive selon ces spécifications :

Structure :
- Tag <header> avec classes : sticky top-0 bg-white/90 backdrop-blur border-b
- Container : mx-auto max-w-6xl px-4 py-3 flex items-center justify-between

Contenu :
1. Logo :
   - Tag <a> vers index.html
   - Texte : "[Votre Nom] - Dev IA & Cloud"
   - Classes : font-semibold text-lg

2. Bouton menu mobile :
   - Tag <button> avec ID "menuBtn"
   - Classes : md:hidden p-2 border rounded
   - Texte : "Menu"

3. Navigation :
   - Tag <ul> avec ID "menu"
   - Classes : hidden md:flex gap-6
   - 4 liens dans <li> :
     * Projets (#projects)
     * Démos IA (ai-demos.html)
     * Architecture Cloud (cloud-architecture.html)
     * Contact (#contact)
   - Classes liens : hover:text-blue-600 font-semibold

Script JavaScript :
- Sélectionner #menuBtn et #menu
- Au clic sur menuBtn, toggle la classe "hidden" sur #menu
- Utiliser addEventListener

NE GENERE QUE le header + script, pas le HTML complet.

Paramètres :
Temperature : 0.2
Top-p : 0.8
Max tokens : 600
```

**Résultat attendu :**

```html
<header class="sticky top-0 bg-white/90 backdrop-blur border-b">
  <nav class="mx-auto max-w-6xl px-4 py-3 flex items-center justify-between">
    <a href="index.html" class="font-semibold text-lg">[Votre Nom] - Dev IA & Cloud</a>
    <button id="menuBtn" class="md:hidden p-2 border rounded">Menu</button>
    <ul id="menu" class="hidden md:flex gap-6">
      <li><a class="hover:text-blue-600 font-semibold" href="#projects">Projets</a></li>
      <li><a class="hover:text-blue-600 font-semibold" href="ai-demos.html">Démos IA</a></li>
      <li><a class="hover:text-blue-600 font-semibold" href="cloud-architecture.html">Architecture Cloud</a></li>
      <li><a class="hover:text-blue-600 font-semibold" href="#contact">Contact</a></li>
    </ul>
  </nav>
</header>

<script>
  const btn = document.getElementById('menuBtn');
  const menu = document.getElementById('menu');
  btn?.addEventListener('click', () => {
    menu.classList.toggle('hidden');
  });
</script>
```

**Actions :**
1. Insérez ce code dans `index.html` dans le `<body>`, remplacez le commentaire
2. Ouvrez dans le navigateur
3. Testez sur DESKTOP (largeur > 768px) :
   - Le menu horizontal doit être visible
   - 4 liens affichés côte à côte
   - Pas de bouton "Menu"
4. Testez sur MOBILE (DevTools, F12, Ctrl+Shift+M, sélectionnez iPhone) :
   - Le menu horizontal disparaît
   - Bouton "Menu" apparaît
   - Clic sur "Menu" : liens apparaissent en dessous
   - Re-clic : liens disparaissent
5. Documentez dans `prompts-log.md`

---

### VARIANTES À TESTER

**Variante 1 : Changer la couleur du header**

Modifiez le prompt, changez :
```
bg-white/90 → bg-slate-900
```

Ajoutez aussi :
```
text-white (pour rendre le texte visible sur fond noir)
```

Générez, testez l'effet.

**Variante 2 : Header non-sticky**

Retirez du prompt :
```
sticky top-0
```

Générez, scrollez la page : le header défile avec le contenu (au lieu de rester fixe en haut).

**Variante 3 : Navigation toujours visible**

Changez dans le prompt :
```
hidden md:flex → flex
```

Retirez le bouton menu mobile.

Générez, testez : navigation visible même sur mobile (peut être trop large sur petit écran).

**EXERCICE : Testez au moins 2 variantes**

1. Générez la variante
2. Comparez avec l'original
3. Notez l'effet visuel

**Temps : 15 minutes**

---

### DÉPANNAGE : Menu mobile ne fonctionne pas

**Symptôme :** Clic sur "Menu" ne fait rien.

**Diagnostic étape par étape :**

1. Ouvrez la console navigateur (F12, onglet Console)
2. Vérifiez les erreurs JavaScript
3. Testez manuellement :

```javascript
// Tapez dans la console :
document.getElementById('menuBtn')
// Doit afficher : <button id="menuBtn">...</button>

document.getElementById('menu')
// Doit afficher : <ul id="menu">...</ul>
```

Si `null` : les ID sont incorrects.

**Solution :**

Nouveau prompt :
```
Le menu mobile ne toggle pas. Corrige le JavaScript.

Vérifications nécessaires :
1. Le bouton a l'ID "menuBtn" (exact, case-sensitive)
2. Le menu a l'ID "menu"
3. L'événement click est attaché après chargement du DOM
4. La fonction toggle ajoute/enlève "hidden" sur #menu

Temperature : 0.1
```

**EXERCICE : Cassez puis réparez**

1. Changez manuellement `id="menuBtn"` en `id="menuButton"` dans le HTML
2. Testez : ça casse
3. Utilisez le prompt ci-dessus pour corriger
4. Vérifiez que ça marche à nouveau

**Temps : 10 minutes**
**Apprentissage :** Importance des ID exacts, debugging JavaScript basique

---

## PARTIE 5 : HERO SECTION

### 5.1 Qu'est-ce qu'une hero section ?

**Définition**  
La hero section = première section de la page, grande, accrocheuse.

**Objectif :** Capter l'attention, résumer qui vous êtes en 3 secondes.

**Composants typiques :**
- Titre H1 (grand, visible immédiatement)
- Description courte (1-2 lignes max)
- Bouton call-to-action (CTA)
- Fond visuellement intéressant (gradient, image, couleur)

---

### 5.2 EXEMPLES DE VARIANTES (regardez les différences)

**Variante A : Minimaliste (fond blanc)**

```html
<section class="mx-auto max-w-6xl px-4 py-24">
  <h1 class="text-5xl font-semibold">Jean Dupont</h1>
  <p class="mt-3 text-slate-700">Développeur IA & Cloud</p>
  <a href="#projects" class="mt-6 inline-block px-5 py-3 bg-blue-600 text-white rounded">Voir mes projets</a>
</section>
```

**Variante B : Gradient subtil (recommandé)**

```html
<section class="relative overflow-hidden border-b">
  <div class="absolute inset-0 bg-gradient-to-br from-blue-500/10 via-purple-500/10 to-cyan-500/10"></div>
  <div class="relative mx-auto max-w-6xl px-4 py-24">
    <h1 class="text-5xl font-semibold">Jean Dupont</h1>
    <p class="mt-3 text-slate-700">Développeur IA & Cloud</p>
    <a href="#projects" class="mt-6 inline-block px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold">Voir mes projets</a>
  </div>
</section>
```

**Variante C : Fond coloré fort**

```html
<section class="bg-gradient-to-r from-blue-600 to-purple-600 py-24">
  <div class="mx-auto max-w-6xl px-4">
    <h1 class="text-5xl font-semibold text-white">Jean Dupont</h1>
    <p class="mt-3 text-blue-100">Développeur IA & Cloud</p>
    <a href="#projects" class="mt-6 inline-block px-5 py-3 bg-white text-blue-600 rounded-lg hover:bg-blue-50 font-semibold">Voir mes projets</a>
  </div>
</section>
```

**EXERCICE : Testez les 3 variantes**

1. Copiez chaque variante dans `index.html` (une à la fois)
2. Observez le rendu dans le navigateur
3. Choisissez celle que vous préférez

**Temps : 15 minutes**

**Question :** Laquelle est la plus professionnelle ? Laquelle attire le plus l'attention ?

---

### 5.3 Génération avec l'IA

Vous allez générer la **Variante B** (gradient subtil) avec l'IA.

**Prompt direct :**

```
Génère une hero section selon ces spécifications :

Structure :
- Tag <section> avec classes : relative overflow-hidden border-b
- Div overlay absolue : absolute inset-0 bg-gradient-to-br from-blue-500/10 via-purple-500/10 to-cyan-500/10
- Div contenu : relative mx-auto max-w-6xl px-4 py-16 md:py-24

Contenu :
- H1 responsive : text-3xl md:text-5xl font-semibold
  Texte : "Développeur IA & Cloud"
- Paragraphe : mt-3 max-w-2xl text-slate-700
  Texte : "LLM, RAG, pipelines de données, MLOps, déploiements scalables."
- Lien bouton : mt-6 inline-block px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold
  Href : #projects
  Texte : "Voir mes projets"

NE GENERE QUE la section, pas le HTML complet.

Paramètres :
Temperature : 0.3
Top-p : 0.85
Max tokens : 400
```

### 5.4 Résultat attendu

```html
<section class="relative overflow-hidden border-b">
  <div class="absolute inset-0 bg-gradient-to-br from-blue-500/10 via-purple-500/10 to-cyan-500/10"></div>
  <div class="relative mx-auto max-w-6xl px-4 py-16 md:py-24">
    <h1 class="text-3xl md:text-5xl font-semibold">Développeur IA & Cloud</h1>
    <p class="mt-3 max-w-2xl text-slate-700">LLM, RAG, pipelines de données, MLOps, déploiements scalables.</p>
    <a href="#projects" class="mt-6 inline-block px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold">Voir mes projets</a>
  </div>
</section>
```

### 5.5 Actions

1. Insérez dans `index.html` après le `</header>`
2. Ajoutez un `<main>` englobant :
```html
</header>

<main>
  <section class="relative overflow-hidden border-b">
    ...
  </section>
</main>
```
3. Testez le responsive :
   - Mobile : titre 3xl, padding py-16
   - Desktop : titre 5xl, padding py-24
4. Documentez dans `prompts-log.md`

---

### 5.6 TESTS PRATIQUES OBLIGATOIRES

**Test 1 : Responsive du titre**

1. Ouvrez DevTools (F12)
2. Mode responsive (Ctrl+Shift+M)
3. Sélectionnez "iPhone 12" (390px)
   - Le titre doit être moyen (3xl ≈ 30px)
4. Sélectionnez "Desktop" (1440px)
   - Le titre doit être grand (5xl ≈ 48px)
5. Redimensionnez manuellement la fenêtre
   - À 768px exactement : le titre grandit

**Résultat attendu :** Le titre grandit quand vous élargissez la fenêtre au-delà de 768px.

**Test 2 : Gradient visible ?**

1. Regardez le fond de la section
2. Vous devriez voir un léger dégradé bleu-violet-cyan
3. Si invisible : augmentez l'opacité dans le prompt :
   ```
   from-blue-500/10 → from-blue-500/20
   ```
4. Régénérez, comparez

**Test 3 : Bouton cliquable**

1. Cliquez sur "Voir mes projets"
2. La page doit scroller vers la section #projects (pas encore créée, donc rien ne se passe)
3. Vérifiez que le bouton change de couleur au hover

---

### 5.7 VARIANTES À EXPÉRIMENTER

**Variante 1 : Titre centré au lieu d'aligné à gauche**

Ajoutez dans le prompt :
```
Classes sur le conteneur : text-center
```

Résultat : tout est centré.

**Variante 2 : Gradient plus prononcé**

Changez dans le prompt :
```
from-blue-500/10 via-purple-500/10 to-cyan-500/10
→
from-blue-500/30 via-purple-500/30 to-cyan-500/30
```

Résultat : gradient plus visible, plus coloré.

**Variante 3 : 2 boutons au lieu d'1**

Ajoutez dans le prompt après le premier bouton :
```
Bouton secondaire :
- Tag <a>
- Href : #contact
- Texte : "Me contacter"
- Classes : mt-6 ml-4 inline-block px-5 py-3 border border-blue-600 text-blue-600 rounded-lg hover:bg-blue-50 font-semibold
```

Résultat : 2 boutons côte à côte (un plein, un outlined).

**EXERCICE OBLIGATOIRE : Testez au moins 2 variantes**

1. Générez chaque variante
2. Comparez visuellement
3. Choisissez votre préférée pour la suite

**Temps : 20 minutes**

---

### 5.8 Pourquoi temperature=0.3 ?

**Justification :**
- Structure HTML : stricte (0.2 aurait suffi)
- Gradient colors : `from-blue-500/10` - légère liberté acceptable (0.3)
- Classes Tailwind : toutes standards

Temperature 0.3 = compromis entre précision syntaxique et légère variabilité esthétique.

**EXPÉRIENCE : Testez avec 0.1 puis 0.3**

Même prompt, changez juste la température.

Temperature 0.1 :
```html
<div class="absolute inset-0 bg-gradient-to-br from-blue-500/10 to-blue-600/10"></div>
```
Gradient simple, 2 couleurs, prévisible.

Temperature 0.3 :
```html
<div class="absolute inset-0 bg-gradient-to-br from-blue-500/10 via-purple-500/10 to-cyan-500/10"></div>
```
Gradient plus créatif, 3 couleurs, plus intéressant.

**Testez :** Générez avec 0.1, puis 0.3, comparez le gradient obtenu.

**Temps : 10 minutes**

---

## PARTIE 6 : SECTION À PROPOS

### 6.1 Spécifications

Section simple avec titre + texte de présentation.

### 6.2 Prompt structuré

```
Génère une section "À propos" :

Structure :
- Tag <section> avec classes : mx-auto max-w-6xl px-4 py-12 md:py-16
- H2 : text-2xl md:text-3xl font-semibold, texte "À propos"
- Paragraphe : mt-3 text-slate-700, texte "[Votre texte de présentation]"

NE GENERE QUE la section.

Paramètres :
Temperature : 0.2
Top-p : 0.8
Max tokens : 200
```

### 6.3 Résultat attendu

```html
<section class="mx-auto max-w-6xl px-4 py-12 md:py-16">
  <h2 class="text-2xl md:text-3xl font-semibold">À propos</h2>
  <p class="mt-3 text-slate-700">[Votre texte de présentation]</p>
</section>
```

### 6.4 Actions

1. Insérez dans `index.html` dans `<main>`, après la hero section
2. Remplacez le placeholder par votre texte réel
3. Documentez

---

## PARTIE 7 : GRID DE PROJETS

### 7.1 Qu'est-ce qu'une grid de projets ?

**Définition**  
Grid = grille de cards (cartes), chacune présentant un projet.

**Caractéristiques :**
- Responsive : 1 colonne mobile, 2-3 colonnes desktop
- Cards identiques visuellement (cohérence)
- Chaque card : image + titre + description

**Pourquoi une grid et pas une liste ?**
- Plus visuel (images)
- Utilise mieux l'espace horizontal sur desktop
- Standard des portfolios modernes

---

### 7.2 EXEMPLES DE VARIANTES

**Variante A : Cards basiques (sans ombre)**

```html
<article class="border rounded-lg p-4">
  <img src="projet1.jpg" alt="Projet" class="w-full h-40 object-cover rounded">
  <h3 class="mt-3 font-semibold">Titre du projet</h3>
  <p class="mt-2 text-sm text-slate-600">Description courte.</p>
</article>
```

**Variante B : Cards avec ombre (recommandé)**

```html
<article class="border rounded-xl overflow-hidden shadow-sm hover:shadow-md transition-shadow">
  <img src="projet1.jpg" alt="Projet" class="w-full h-40 object-cover">
  <div class="p-4">
    <h3 class="font-semibold">Titre du projet</h3>
    <p class="mt-2 text-sm text-slate-600">Description courte.</p>
  </div>
</article>
```

**Variante C : Cards colorées**

```html
<article class="bg-gradient-to-br from-blue-50 to-purple-50 rounded-xl p-4 border">
  <img src="projet1.jpg" alt="Projet" class="w-full h-40 object-cover rounded-lg">
  <h3 class="mt-3 font-semibold text-blue-900">Titre du projet</h3>
  <p class="mt-2 text-sm text-slate-700">Description courte.</p>
</article>
```

**EXERCICE : Copiez les 3 variantes**

1. Créez un fichier `test-cards.html`
2. Copiez le squelette HTML de base
3. Collez les 3 cards une en dessous de l'autre
4. Observez les différences visuelles

**Temps : 15 minutes**

**Question :** Laquelle préférez-vous ? Pourquoi ?

---

### 7.3 Génération de la grid complète

**Prompt direct :**

```
Génère une section "Projets" avec grid responsive de 3 cards.

Structure :
- Section avec ID "projects", classes : mx-auto max-w-6xl px-4 py-12 md:py-16 border-t
- H2 : text-2xl font-semibold, texte "Projets"
- Div grille : mt-6 grid sm:grid-cols-2 lg:grid-cols-3 gap-6

Cards (3 au total, structure identique) :
- Tag <article>, classes : border rounded-xl overflow-hidden shadow-sm
- Image : src="assets/projet[1-3].jpg", alt descriptif du projet, classes : w-full h-40 object-cover
- Div contenu : p-4
  - H3 : font-semibold, titres respectifs :
    1. "Classifier d'images (CNN)"
    2. "RAG basique (simulé)"
    3. "Pipeline de données"
  - Paragraphe : mt-2 text-sm text-slate-600, descriptions :
    1. "Entraînement local, export ONNX, déploiement statique + API simulée."
    2. "Recherche contextuelle + synthèse (simulation sans backend)."
    3. "ETL simple, validation schéma, exposition via endpoint simulé."

NE GENERE QUE la section.

Paramètres :
Temperature : 0.2
Top-p : 0.8
Max tokens : 700
```

### 7.4 Résultat attendu

```html
<section id="projects" class="mx-auto max-w-6xl px-4 py-12 md:py-16 border-t">
  <h2 class="text-2xl font-semibold">Projets</h2>
  <div class="mt-6 grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
    
    <article class="border rounded-xl overflow-hidden shadow-sm">
      <img src="assets/projet1.jpg" alt="Aperçu du projet de classification d'images" class="w-full h-40 object-cover">
      <div class="p-4">
        <h3 class="font-semibold">Classifier d'images (CNN)</h3>
        <p class="mt-2 text-sm text-slate-600">Entraînement local, export ONNX, déploiement statique + API simulée.</p>
      </div>
    </article>

    <article class="border rounded-xl overflow-hidden shadow-sm">
      <img src="assets/projet2.jpg" alt="Aperçu du projet RAG" class="w-full h-40 object-cover">
      <div class="p-4">
        <h3 class="font-semibold">RAG basique (simulé)</h3>
        <p class="mt-2 text-sm text-slate-600">Recherche contextuelle + synthèse (simulation sans backend).</p>
      </div>
    </article>

    <article class="border rounded-xl overflow-hidden shadow-sm">
      <img src="assets/projet3.jpg" alt="Aperçu du pipeline de données" class="w-full h-40 object-cover">
      <div class="p-4">
        <h3 class="font-semibold">Pipeline de données</h3>
        <p class="mt-2 text-sm text-slate-600">ETL simple, validation schéma, exposition via endpoint simulé.</p>
      </div>
    </article>

  </div>
</section>
```

### 7.5 Actions

1. Insérez dans `<main>` après la section "À propos"
2. Créez 3 images placeholder dans `assets/` :
   - Option A : Utilisez https://via.placeholder.com/400x250 dans src (temporaire)
   - Option B : Créez 3 images 400x250px avec Paint/Photoshop
3. Documentez

---

### 7.6 TESTS PRATIQUES OBLIGATOIRES

**Test 1 : Responsive de la grid**

1. DevTools mode responsive (F12, Ctrl+Shift+M)
2. iPhone 12 (390px de large) :
   - Vous devez voir 1 seule card en largeur
   - Les 3 cards empilées verticalement
3. iPad (768px) :
   - 2 cards côte à côte
   - La 3ème card seule en dessous
4. Desktop (1440px) :
   - 3 cards alignées horizontalement
   - Toutes sur la même ligne

**Résultat attendu :** La grid s'adapte à la largeur.

**Test 2 : Hover effect sur les cards**

1. Desktop mode
2. Passez la souris sur une card
3. L'ombre doit s'intensifier (shadow-sm → shadow-md)
4. Transition douce visible

Si pas d'effet hover : vérifiez la classe `hover:shadow-md` dans le code.

**Test 3 : Images responsives**

1. Vérifiez que les images gardent leur proportion
2. Elles doivent toutes faire la même hauteur (h-40 = 160px)
3. Si déformées : `object-cover` doit être présent

---

### 7.7 VARIANTES À TESTER

**Variante 1 : Grid 4 colonnes au lieu de 3**

Changez dans le prompt :
```
lg:grid-cols-3 → lg:grid-cols-4
```

Ajoutez une 4ème card.

Résultat : 4 cards alignées sur grand écran (plus compact).

**Variante 2 : Gap plus large**

Changez :
```
gap-6 → gap-8
```

Résultat : plus d'espace entre les cards.

**Variante 3 : Cards avec bouton "Voir le projet"**

Ajoutez dans chaque card après la description :
```
- Lien bouton : 
  - Href : #
  - Texte : "Voir le projet"
  - Classes : mt-3 inline-block px-3 py-2 bg-blue-600 text-white text-sm rounded hover:bg-blue-500
```

Résultat : chaque card a un bouton cliquable.

**Variante 4 : Images plus grandes**

Changez :
```
h-40 → h-56
```

Résultat : images 224px de haut au lieu de 160px.

**EXERCICE OBLIGATOIRE : Testez 3 variantes**

1. Générez chaque variante séparément
2. Observez l'effet visuel
3. Choisissez votre combinaison préférée
4. Documentez laquelle vous gardez et pourquoi

**Temps : 25 minutes**

---

### 7.8 EXERCICE : Cassez le responsive

**Objectif :** Comprendre le responsive en le cassant volontairement.

**Action 1 : Retirez sm:grid-cols-2**

Code devient :
```html
<div class="grid lg:grid-cols-3 gap-6">
```

Testez sur tablette (768px) :
- Résultat : 3 colonnes au lieu de 2 (trop serré)

Remettez `sm:grid-cols-2`.

**Action 2 : Retirez grid-cols-1 (défaut)**

Code devient :
```html
<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
```

Testez sur mobile :
- Résultat : rien ne s'affiche correctement (grid sans colonnes définies)

Remettez : grid-cols-1 en premier.

**Action 3 : Mélangez l'ordre**

Code devient :
```html
<div class="grid lg:grid-cols-3 grid-cols-1 sm:grid-cols-2 gap-6">
```

Testez : ça marche quand même (Tailwind applique dans l'ordre des breakpoints).

**Apprentissage :**
- L'ordre des classes responsive n'importe pas toujours
- MAIS il faut TOUJOURS une valeur par défaut (grid-cols-1)
- Chaque breakpoint (sm:, md:, lg:) override le précédent

**Temps : 15 minutes**

---

## PARTIE 8 : FORMULAIRE CONTACT

### 8.1 Qu'est-ce qu'un formulaire HTML ?

**Définition**  
Formulaire = ensemble de champs où l'utilisateur entre des données.

**Éléments essentiels :**
- `<form>` : conteneur
- `<label>` : étiquette de champ (accessibilité)
- `<input>` : champ de saisie (texte, email, etc.)
- `<textarea>` : champ multiligne
- `<button>` : bouton de soumission

**Attributs critiques :**
- `for` sur label = `id` sur input (DOIVENT correspondre)
- `required` : champ obligatoire
- `type="email"` : validation email automatique

---

### 8.2 EXEMPLES : BON VS MAUVAIS

**Mauvais formulaire (cassé) :**

```html
<form>
  <label>Nom</label>
  <input type="text" placeholder="Votre nom">
  <button>Envoyer</button>
</form>
```

**Problèmes :**
- Pas de lien `for`/`id` (accessibilité cassée)
- Pas de `required` (validation inexistante)
- Pas de classes Tailwind (laid)
- Pas de gestion submit (formulaire vide soumis)

**Bon formulaire :**

```html
<form onsubmit="event.preventDefault(); alert('OK');">
  <label class="font-semibold" for="nom">Nom</label>
  <input id="nom" class="w-full border rounded p-3" type="text" placeholder="Votre nom" required>
  
  <button class="px-5 py-3 bg-blue-600 text-white rounded font-semibold">Envoyer</button>
</form>
```

**Correctif :**
- `for="nom"` lié à `id="nom"` (accessibilité OK)
- `required` (validation active)
- Classes Tailwind (professionnel)
- `onsubmit` prévient soumission réelle (simulation)

**EXERCICE : Testez le mauvais puis le bon**

1. Créez `test-form.html`
2. Copiez le squelette HTML
3. Testez le mauvais formulaire :
   - Cliquez "Envoyer" sans remplir : ça part quand même (BAD)
4. Remplacez par le bon formulaire :
   - Cliquez "Envoyer" sans remplir : message d'erreur navigateur (GOOD)
5. Remplissez les champs : alert apparaît

**Temps : 15 minutes**

**Apprentissage :** Importance de `required` et de la liaison label/input.

---

### 8.3 Génération avec l'IA

**Prompt direct :**

```
Génère une section formulaire de contact.

Structure :
- Section avec ID "contact", classes : mx-auto max-w-6xl px-4 py-12 md:py-16 border-t
- H2 : text-2xl font-semibold, texte "Contact"
- Form : mt-6 max-w-xl space-y-4
  - Attribut onsubmit : event.preventDefault(); alert('Simulation d'envoi réussie');

Champs (dans cet ordre) :
1. Label "Nom" + Input :
   - Label : font-semibold, attribut for="nom"
   - Input : id="nom", type="text", placeholder="Votre nom", required
   - Classes input : w-full border rounded p-3

2. Label "Email" + Input :
   - Label : font-semibold, attribut for="email"
   - Input : id="email", type="email", placeholder="Votre email", required
   - Classes input : w-full border rounded p-3

3. Label "Message" + Textarea :
   - Label : font-semibold, attribut for="message"
   - Textarea : id="message", rows="5", placeholder="Votre message", required
   - Classes : w-full border rounded p-3

4. Button submit :
   - Type : submit
   - Classes : px-5 py-3 bg-blue-600 text-white rounded hover:bg-blue-500 font-semibold
   - Texte : "Envoyer"

NE GENERE QUE la section.

Paramètres :
Temperature : 0.1
Top-p : 0.8
Max tokens : 600
```

### 8.3 Résultat attendu

```html
<section id="contact" class="mx-auto max-w-6xl px-4 py-12 md:py-16 border-t">
  <h2 class="text-2xl font-semibold">Contact</h2>
  <form class="mt-6 max-w-xl space-y-4" onsubmit="event.preventDefault(); alert('Simulation d\'envoi réussie');">
    
    <label class="font-semibold" for="nom">Nom</label>
    <input id="nom" class="w-full border rounded p-3" type="text" placeholder="Votre nom" required>
    
    <label class="font-semibold" for="email">Email</label>
    <input id="email" class="w-full border rounded p-3" type="email" placeholder="Votre email" required>
    
    <label class="font-semibold" for="message">Message</label>
    <textarea id="message" class="w-full border rounded p-3" rows="5" placeholder="Votre message" required></textarea>
    
    <button class="px-5 py-3 bg-blue-600 text-white rounded hover:bg-blue-500 font-semibold">Envoyer</button>
  </form>
</section>
```

### 8.4 Pourquoi temperature=0.1 ?

**Justification :**
Les formulaires ont une syntaxe très stricte :
- Attributs `id` doivent correspondre aux `for`
- Types d'input précis (`email` vs `text`)
- Attribut `required` obligatoire
- Événement `onsubmit` exact

Une température trop haute risque d'omettre ces détails critiques.

**EXPÉRIENCE : Température 0.5 vs 0.1**

Même prompt de formulaire.

Temperature 0.5 :
```html
<label for="userName">Nom</label>
<input id="name" type="text" required>
```
PROBLÈME : `for="userName"` mais `id="name"` - ne correspondent pas ! Accessibilité cassée.

Temperature 0.1 :
```html
<label for="nom">Nom</label>
<input id="nom" type="text" required>
```
CORRECT : `for="nom"` et `id="nom"` identiques.

**Testez :** Générez avec 0.5 puis 0.1, vérifiez les correspondances id/for.

**Temps : 10 minutes**

---

### 8.5 TESTS PRATIQUES OBLIGATOIRES

**Test 1 : Validation champ requis**

1. Cliquez "Envoyer" sans remplir aucun champ
2. Résultat attendu : Message d'erreur navigateur "Veuillez remplir ce champ"
3. Si ça part quand même : `required` manque

**Test 2 : Validation email**

1. Remplissez "nom" et "message"
2. Dans le champ email, tapez : `test` (sans @)
3. Cliquez "Envoyer"
4. Résultat attendu : "Veuillez inclure un @ dans l'adresse"
5. Si aucune erreur : `type="email"` manque

**Test 3 : Soumission complète**

1. Remplissez tous les champs correctement
2. Cliquez "Envoyer"
3. Résultat attendu : Alert "Simulation d'envoi réussie"
4. Si la page recharge : `event.preventDefault()` manque

**Test 4 : Lien label-input (accessibilité)**

1. Cliquez sur le TEXTE du label "Nom" (pas dans le champ)
2. Résultat attendu : Le curseur apparaît dans le champ nom
3. Si rien : `for="nom"` ne correspond pas à `id="nom"`

**Tous les tests doivent passer. Si un test échoue : régénérez avec temperature=0.1.**

---

### 8.6 VARIANTES À TESTER

**Variante 1 : Champ téléphone**

Ajoutez dans le prompt après le champ email :
```
Champ téléphone :
- Label : "Téléphone"
- Input : id="tel", type="tel", placeholder="06 12 34 56 78"
- Classes identiques aux autres inputs
```

Résultat : 4 champs au lieu de 3.

**Variante 2 : Select au lieu de textarea**

Remplacez le champ message par :
```
Select :
- Label : "Sujet"
- Select : id="sujet", required
- Options : "Question générale", "Collaboration", "Autre"
- Classes : w-full border rounded p-3
```

Résultat : menu déroulant au lieu de zone de texte.

**Variante 3 : Formulaire sur 2 colonnes**

Ajoutez dans le prompt :
```
Classes sur le form : grid md:grid-cols-2 gap-4
Champs nom et email : sur la première ligne
Message : span sur 2 colonnes (md:col-span-2)
```

Résultat : formulaire compact sur desktop.

**EXERCICE OBLIGATOIRE : Testez au moins 1 variante**

1. Générez la variante
2. Testez la validation
3. Comparez avec l'original

**Temps : 20 minutes**

---

### 8.7 EXERCICE : Cassez la validation

**Objectif :** Comprendre la validation en la cassant.

**Action 1 : Retirez `required`**

Enlevez `required` du champ nom.

Testez : vous pouvez soumettre sans nom (mauvais).

Remettez `required`.

**Action 2 : Changez type="email" en type="text"**

Testez : vous pouvez écrire "abc" sans @ (validation email cassée).

Remettez `type="email"`.

**Action 3 : Retirez event.preventDefault()**

Code devient :
```html
<form onsubmit="alert('OK');">
```

Testez : la page recharge après l'alert (comportement par défaut du form).

Remettez `event.preventDefault();`.

**Apprentissage :**
- `required` = validation côté client
- `type="email"` = validation format email
- `event.preventDefault()` = empêche rechargement page

**Temps : 15 minutes**

---

### 8.8 Génération avec l'IA

**Prompt direct :**

---

## PARTIE 9 : FOOTER

### 9.1 Prompt structuré

```
Génère un footer simple avec année dynamique.

Structure :
- Tag <footer>, classes : border-t
- Div : mx-auto max-w-6xl px-4 py-8 text-sm text-slate-500
  - Texte : "© <span id="year"></span> [Votre Nom]. Tous droits réservés."

Script JavaScript (après le footer, avant </body>) :
document.getElementById('year').textContent = new Date().getFullYear();

NE GENERE QUE le footer + script.

Paramètres :
Temperature : 0.1
Top-p : 0.8
Max tokens : 200
```

### 9.2 Résultat attendu

```html
<footer class="border-t">
  <div class="mx-auto max-w-6xl px-4 py-8 text-sm text-slate-500">
    © <span id="year"></span> [Votre Nom]. Tous droits réservés.
  </div>
</footer>

<script>
  document.getElementById('year').textContent = new Date().getFullYear();
</script>
```

### 9.3 Actions

1. Insérez après le `</main>`
2. Vérifiez que l'année s'affiche correctement (2024, 2025, etc.)
3. Documentez

### 9.4 Structure complète de index.html

À ce stade, votre `index.html` doit ressembler à :

```html
<!doctype html>
<html lang="fr">
<head>...</head>
<body class="antialiased text-slate-800 bg-white">
  
  <header>...</header>
  
  <main>
    <section><!-- hero --></section>
    <section><!-- à propos --></section>
    <section id="projects"><!-- projets --></section>
    <section id="contact"><!-- contact --></section>
  </main>
  
  <footer>...</footer>
  
  <script><!-- menu toggle --></script>
  <script><!-- année footer --></script>
</body>
</html>
```

---

## PARTIE 10 : PAGE DÉMOS IA

### 10.1 Spécifications

Page séparée avec liste de démos IA + modale fonctionnelle.

### 10.2 Prompt structuré (page complète)

```
Génère une page HTML complète "ai-demos.html" pour démonstrations IA.

Structure identique à index.html :
- Même head (title : "Démos IA - Portfolio")
- Même header (mais lien "Retour à l'accueil" au lieu de nav complète)

Main content :
- Container : mx-auto max-w-6xl px-4 py-12 md:py-16
- H1 : text-2xl md:text-3xl font-semibold, texte "Démos IA (simulées)"
- Paragraphe intro : mt-3 text-slate-700, texte "Exemples pédagogiques : entrée → sortie attendue, limites, biais."

Grid de démos :
- Div : mt-8 grid sm:grid-cols-2 lg:grid-cols-3 gap-6
- Une card pour l'exemple :
  - Article : border rounded-xl p-4
  - H2 : font-semibold, texte "Analyse de sentiment"
  - Paragraphe : mt-2 text-sm text-slate-600, texte "Entrée texte → score ∈ [-1, 1]. Limites : ironie, contexte, langue mixte."
  - Button : id="openModal", classes px-3 py-2 bg-blue-600 text-white rounded font-semibold hover:bg-blue-500, texte "Voir la démo"

Modale (cachée par défaut) :
- Div : id="modal", classes : fixed inset-0 bg-black/50 hidden items-center justify-center
- Div contenu : bg-white rounded-xl p-6 w-[90%] max-w-md
  - H3 : font-semibold, texte "Simulation - Analyse de sentiment"
  - Paragraphe : mt-3 text-sm
    Texte : "Entrée : "J'adore ce cours, mais les exercices sont exigeants."<br>Sortie simulée : score = 0.62 (positif modéré)."
  - Button : id="closeModal", classes px-3 py-2 border rounded font-semibold, texte "Fermer"

Script JavaScript :
- Sélectionner #modal, #openModal, #closeModal
- Au clic sur openModal : retirer "hidden", ajouter "flex" sur modal
- Au clic sur closeModal : ajouter "hidden", retirer "flex" sur modal

Génère le HTML COMPLET de la page.

Paramètres :
Temperature : 0.2
Top-p : 0.8
Max tokens : 1200
```

### 10.3 Résultat attendu

Structure complète dans un nouveau fichier.

### 10.4 Actions

1. Copiez le code dans `portfolio/ai-demos.html`
2. Testez la navigation depuis index.html (lien "Démos IA")
3. Testez la modale :
   - Clic sur "Voir la démo" : modale apparaît
   - Clic sur "Fermer" : modale disparaît
4. Documentez

### 10.5 Si la modale ne fonctionne pas

Prompt de correction :

```
La modale ne s'affiche pas correctement.
Corrige le JavaScript pour :
1. Vérifier que les éléments existent avant d'attacher les événements
2. Au clic sur #openModal : modal.classList.remove('hidden') puis modal.classList.add('flex')
3. Au clic sur #closeModal : inverse

Temperature : 0.1
```

---

## PARTIE 11 : PAGE ARCHITECTURE CLOUD

### 11.1 Prompt structuré

```
Génère une page HTML complète "cloud-architecture.html".

Structure identique à index.html :
- Même head (title : "Architecture Cloud - Portfolio")
- Même header (lien "Retour à l'accueil")

Main content :
- Container : mx-auto max-w-6xl px-4 py-12 md:py-16
- H1 : text-2xl md:text-3xl font-semibold, texte "Architecture Cloud (proposée)"
- Paragraphe intro : mt-3 text-slate-700, texte "Déploiement statique + CDN, API serverless simulée pour les démos IA, stockage d'assets."

Grid de sections :
- Div : mt-8 grid md:grid-cols-2 gap-8

Section 1 :
- Tag <section>, classes : border rounded-xl p-4
- H2 : font-semibold, texte "Vue haute-niveau"
- Liste UL : list-disc ml-5 mt-3 text-slate-700
  Items :
  - "Client → CDN → Hébergement statique (pages HTML)"
  - "Fonctions serverless (endpoints IA simulés)"
  - "Stockage d'assets (images projets)"
  - "Logs & monitoring basiques"

Section 2 :
- Tag <section>, classes : border rounded-xl p-4
- H2 : font-semibold, texte "Sécurité & coûts"
- Liste UL similaire
  Items :
  - "HTTPS, CORS minimal"
  - "Moindre privilège (lecture-only public)"
  - "Budget débutant : gratuit/quelques dollars"

Génère le HTML COMPLET de la page.

Paramètres :
Temperature : 0.2
Top-p : 0.8
Max tokens : 1000
```

### 11.2 Actions

1. Copiez dans `portfolio/cloud-architecture.html`
2. Testez la navigation depuis index.html
3. Vérifiez le responsive de la grid (1 col mobile, 2 col desktop)
4. Documentez

---

## PARTIE 12 : VALIDATION FINALE

### 12.1 Validation HTML W3C

**Processus :**
1. Ouvrez https://validator.w3.org/
2. Uploadez chaque fichier :
   - index.html
   - ai-demos.html
   - cloud-architecture.html
3. Corrigez les erreurs éventuelles

**Erreurs courantes :**
- Balises non fermées
- Attributs `id` dupliqués
- `alt` manquant sur images

**Si erreurs détectées :**

Prompt de correction :
```
Le validateur W3C signale cette erreur :
[collez l'erreur exacte]

Corrige uniquement cette partie du code.
Temperature : 0.1
```

### 12.2 Test responsive complet

**Breakpoints à tester :**

| Device | Largeur | Points de test |
|--------|---------|----------------|
| iPhone SE | 375px | Menu burger, grid 1 col |
| iPad | 768px | Grid 2 col projets |
| Desktop | 1440px | Grid 3 col, nav horizontale |

**Checklist :**
- [ ] Header : menu burger < 768px, nav horizontale ≥ 768px
- [ ] Hero : titre 3xl < 768px, 5xl ≥ 768px
- [ ] Grid projets : 1 col < 640px, 2 col < 1024px, 3 col ≥ 1024px
- [ ] Formulaire : largeur max-xl, centré
- [ ] Modale : w-[90%] sur mobile, max-w-md desktop

### 12.3 Captures d'écran

**Processus :**
1. Ouvrez DevTools (F12)
2. Mode responsive (Ctrl+Shift+M)
3. Sélectionnez iPhone 12 (390x844)
4. Capturez `screenshot-mobile.png`
5. Sélectionnez Desktop (1920x1080)
6. Capturez `screenshot-desktop.png`
7. Placez dans `assets/`

### 12.4 README.md

Créez `portfolio/README.md` :

```markdown
# Portfolio - Développeur IA & Cloud

## Description
Portfolio professionnel généré avec l'aide de l'IA générative.
Démontre l'utilisation de prompts structurés et de paramètres optimisés.

## Structure du projet

```
portfolio/
├── index.html                  (page principale)
├── ai-demos.html              (démos IA avec modale)
├── cloud-architecture.html    (architecture proposée)
├── assets/
│   ├── projet1.jpg
│   ├── projet2.jpg
│   ├── projet3.jpg
│   ├── screenshot-mobile.png
│   └── screenshot-desktop.png
├── README.md
└── prompts-log.md
```

## Technologies utilisées

- HTML5 (validation W3C)
- Tailwind CSS v3 (via CDN)
- JavaScript vanilla (navigation mobile, modale)

## Responsive design

- Mobile-first
- Breakpoints : 640px (sm), 768px (md), 1024px (lg)
- Testé sur iPhone SE, iPad, Desktop 1920px

## Prompts IA

Tous les prompts utilisés pour générer ce portfolio sont documentés dans `prompts-log.md`.

Paramètres typiques :
- Temperature : 0.1-0.3 (code structuré)
- Top-p : 0.8-0.85
- Max tokens : 200-1200 selon la section

## Validation

- HTML validé W3C : 0 erreurs
- CSS : Tailwind (pas de validation nécessaire)
- Accessibilité : attributs alt présents, labels liés aux inputs

## Navigation

- Page principale : `index.html`
- Sections : Hero, À propos, Projets, Contact
- Pages annexes : Démos IA, Architecture Cloud

## Captures d'écran

Voir `assets/screenshot-mobile.png` et `assets/screenshot-desktop.png`.
```

### 12.5 Prompts-log.md finalisé

Structure attendue :

```markdown
# Log des prompts - Portfolio IA

## Méthodologie

Tous les composants ont été générés avec :
- IA utilisée : ChatGPT 4 / Claude 3.5
- Méthode : JSON structuré → prompt détaillé → code HTML/Tailwind
- Principe : température basse (0.1-0.3) pour précision syntaxique

---

## Section 1 : Squelette HTML
Date : [date]
Temperature : 0.1
Top-p : 0.8
Max tokens : 400

**Prompt :**
```
[collez le prompt exact]
```

**Résultat :** OK / Ajustements nécessaires
**Ajustements :** [si applicable]

---

## Section 2 : Header responsive
[même structure pour chaque section]

---

[continuez pour toutes les sections]
```

### 12.6 Checklist finale

Avant de remettre le projet :

**Fichiers obligatoires :**
- [ ] portfolio/index.html (complet, validé)
- [ ] portfolio/ai-demos.html (modale fonctionnelle)
- [ ] portfolio/cloud-architecture.html (listes présentes)
- [ ] portfolio/assets/projet[1-3].jpg (3 images)
- [ ] portfolio/assets/screenshot-mobile.png
- [ ] portfolio/assets/screenshot-desktop.png
- [ ] portfolio/README.md (structure claire)
- [ ] portfolio/prompts-log.md (tous les prompts documentés)

**Tests fonctionnels :**
- [ ] Navigation entre pages fonctionne
- [ ] Menu mobile toggle (< 768px)
- [ ] Modale s'ouvre/ferme (ai-demos.html)
- [ ] Formulaire validation HTML5
- [ ] Année footer dynamique
- [ ] Validation W3C : 0 erreurs
- [ ] Responsive testé 3 breakpoints

**Documentation :**
- [ ] Chaque prompt loggé avec température/top-p
- [ ] JSON de spécification archivé (si utilisé)
- [ ] Ajustements documentés
- [ ] README complet

---

## ANNEXE A : RÉSOLUTION DE PROBLÈMES

### A.1 Classes Tailwind inventées

**Symptôme :** Classes comme `sparkle-nav`, `mega-header` dans le code généré.

**Cause :** Température trop haute (≥ 0.5).

**Solution :**
```
Régénère ce composant avec UNIQUEMENT des classes Tailwind v3 valides.
Vérifie chaque classe dans la documentation officielle.
Temperature : 0.1
```

### A.2 Menu mobile ne se toggle pas

**Symptôme :** Clic sur bouton "Menu" sans effet.

**Cause :** ID incorrects ou script manquant.

**Diagnostic :**
```javascript
console.log(document.getElementById('menuBtn')); // doit afficher l'élément
console.log(document.getElementById('menu'));    // doit afficher l'élément
```

**Solution :**
```
Corrige le script de toggle menu.
Vérifie que :
1. Le bouton a bien l'ID "menuBtn"
2. Le menu a bien l'ID "menu"
3. L'événement est attaché après chargement du DOM
4. classList.toggle('hidden') est appelé

Temperature : 0.1
```

### A.3 Grid ne s'adapte pas

**Symptôme :** 3 colonnes même sur mobile.

**Cause :** Classes responsive manquantes.

**Solution :**
```
Corrige la grid pour être responsive :
- Mobile (par défaut) : grid-cols-1
- Tablette (≥ 640px) : sm:grid-cols-2
- Desktop (≥ 1024px) : lg:grid-cols-3

Temperature : 0.2
```

### A.4 Modale ne se ferme pas

**Symptôme :** Modale reste visible après clic sur "Fermer".

**Diagnostic :**
```javascript
const closeBtn = document.getElementById('closeModal');
console.log(closeBtn); // doit afficher le bouton
```

**Solution :**
```
Corrige le handler de fermeture de modale.
Au clic sur #closeModal :
1. Ajouter classe "hidden" sur #modal
2. Retirer classe "flex" sur #modal

Temperature : 0.1
```

### A.5 Images ne s'affichent pas

**Symptôme :** Icônes "image cassée".

**Causes possibles :**
1. Chemin incorrect (`assets/projet1.jpg` vs `./assets/projet1.jpg`)
2. Fichiers manquants
3. Extensions incorrectes (JPG vs jpg)

**Solution :**
1. Vérifiez que les images existent dans `assets/`
2. Vérifiez les chemins dans le HTML
3. Utilisez des placeholders temporaires :
```html
<img src="https://via.placeholder.com/400x250" alt="...">
```

---

## ANNEXE B : TABLEAU RÉCAPITULATIF DES PARAMÈTRES

| Composant | Temp | Top-p | Tokens | Justification |
|-----------|------|-------|--------|---------------|
| Squelette HTML | 0.1 | 0.8 | 400 | Structure stricte, métadonnées précises |
| Header + nav | 0.2 | 0.8 | 600 | Navigation complexe, IDs critiques |
| Hero section | 0.3 | 0.85 | 400 | Gradient : légère liberté acceptable |
| Section simple | 0.2 | 0.8 | 200 | Structure minimale |
| Grid projets | 0.2 | 0.8 | 700 | Cards répétitives, classes identiques |
| Formulaire | 0.1 | 0.8 | 600 | Attributs critiques (id, for, required) |
| Footer | 0.1 | 0.8 | 200 | Minimal, script exact |
| Page complète | 0.2 | 0.8 | 1200 | Assemblage de composants connus |
| Modale JS | 0.2 | 0.85 | 400 | Script JS : syntaxe stricte mais logique simple |

**Règle générale :**
- 0.1 : Syntaxe critique (formulaires, IDs, scripts exacts)
- 0.2 : Structure standard (HTML/Tailwind classique)
- 0.3 : Légère liberté (gradients, couleurs)
- ≥ 0.4 : ÉVITER pour du code (risque d'invention)

---

## ANNEXE C : EXEMPLE DE PROMPTS-LOG.MD COMPLET

```markdown
# Log des prompts - Portfolio IA
Projet : Portfolio Développeur IA & Cloud
IA utilisée : ChatGPT 4
Date : 2024-01-15

---

## Section 1 : Squelette HTML
Temperature : 0.1
Top-p : 0.8
Max tokens : 400

**Prompt :**
```
Génère le squelette HTML5 complet selon ces spécifications JSON.
Inclus :
- DOCTYPE html
- Meta charset UTF-8
- Meta viewport pour responsive
- Title : "Portfolio - Développeur IA & Cloud"
- Meta description : "Portfolio professionnel : projets IA, démos, architecture Cloud"
- Script Tailwind v3 CDN : https://cdn.tailwindcss.com
- Body avec classes : antialiased text-slate-800 bg-white
- Commentaire dans body : "<!-- Contenu à ajouter -->"
```

**Résultat :** OK, code valide généré en 1 essai
**Ajustements :** Aucun

---

## Section 2 : Header sticky responsive
Temperature : 0.2
Top-p : 0.8
Max tokens : 600

**Prompt :**
```
Génère un header sticky responsive selon ces spécifications :
[prompt complet]
```

**Résultat :** OK après 1 ajustement
**Ajustements :** Script JS initialement manquant, régénéré avec temp=0.1

---

[etc. pour toutes les sections]
```

---

## CRITÈRES D'ÉVALUATION FINALE

### Barème sur 100 points

| Critère | Points | Détails |
|---------|--------|---------|
| **Code HTML** | **30** | |
| - Validation W3C | 10 | 0 erreurs sur les 3 pages |
| - Sémantique | 10 | Balises appropriées (header, main, section, article) |
| - Accessibilité | 10 | Alt présents, labels liés, hiérarchie titres |
| **Tailwind CSS** | **25** | |
| - Classes valides | 10 | Aucune classe inventée |
| - Responsive | 10 | Fonctionne sur 3 breakpoints testés |
| - Cohérence | 5 | font-semibold aux bons endroits, espacements logiques |
| **Fonctionnalités** | **20** | |
| - Navigation | 5 | Liens entre pages fonctionnent |
| - Menu mobile | 5 | Toggle sans erreur console |
| - Modale | 5 | Ouverture/fermeture fluide |
| - Formulaire | 5 | Validation HTML5 active |
| **Documentation** | **20** | |
| - Prompts-log.md | 10 | Tous les prompts + paramètres documentés |
| - README.md | 5 | Structure claire, captures présentes |
| - JSON specs | 5 | Archivés pour composants complexes |
| **Livrables** | **5** | |
| - Fichiers complets | 3 | 8 fichiers obligatoires présents |
| - Captures | 2 | Mobile + desktop de qualité |
| **Total** | **100** | |

### Grille de notation détaillée

**Validation W3C (10 pts) :**
- 0 erreurs : 10 pts
- 1-3 erreurs mineures : 7 pts
- 4-10 erreurs : 4 pts
- > 10 erreurs : 0 pts

**Responsive (10 pts) :**
- 3 breakpoints parfaits : 10 pts
- 2 breakpoints OK, 1 cassé : 6 pts
- 1 seul breakpoint : 3 pts
- Pas responsive : 0 pts

**Prompts-log.md (10 pts) :**
- Tous les prompts + params : 10 pts
- 70-99% documentés : 7 pts
- 50-69% : 4 pts
- < 50% : 0 pts

---

## DURÉE ESTIMÉE PAR SECTION

| Section | Temps | Détails |
|---------|-------|---------|
| Partie 1-3 : Théorie | 2h | Lecture, compréhension paramètres |
| Partie 4 : Squelette + Header | 1h | Génération + tests |
| Partie 5 : Hero section | 30min | Section simple |
| Partie 6 : À propos | 20min | Très simple |
| Partie 7 : Grid projets | 1h | 3 cards + images |
| Partie 8 : Formulaire | 45min | Validation HTML5 à tester |
| Partie 9 : Footer | 15min | Minimal |
| Partie 10 : Page Démos IA | 1.5h | Page complète + modale JS |
| Partie 11 : Page Architecture | 45min | Page avec listes |
| Partie 12 : Validation | 2h | W3C, responsive, captures, docs |
| Documentation | 1h | Prompts-log + README |
| **Total** | **≈ 11h** | Peut varier selon expérience |

---

## PROCHAINES ÉTAPES (MODULE 3 - optionnel)

Après validation de ce module, vous pouvez :

1. **Déploiement**
   - GitHub Pages
   - Netlify
   - Vercel

2. **Git local**
   - Initialisation repo
   - Commits par section
   - Branches features

3. **Optimisations avancées**
   - Tailwind build + purge
   - Images optimisées (WebP)
   - Lighthouse audit

4. **Contenu dynamique**
   - Fetch API pour projets
   - Backend serverless (Netlify Functions)
   - CMS headless (Strapi, Sanity)



