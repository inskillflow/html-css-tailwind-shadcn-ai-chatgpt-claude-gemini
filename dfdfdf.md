# COURS-PROJET : Portfolio Web avec IA Générative

**Durée totale : 20 heures**  
**Format : Construction progressive d'un portfolio 3 pages**  
**Technologies : HTML5, Tailwind v3, IA générative (ChatGPT/Claude)**

---

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

---

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

**Définition technique**  
La température modifie la distribution de probabilités des tokens générés. À 0, le modèle choisit toujours le token le plus probable (déterministe). À 1+, il explore des tokens moins probables.

**Application au code**

```
Temperature 0.1 - 0.3 : Code structuré (HTML, CSS, JSON)
Temperature 0.4 - 0.6 : Documentation, commentaires
Temperature 0.7 - 1.0 : Texte créatif, idées de design
```

**Exemple concret : génération d'un header**

Temperature 0.9 (INCORRECT) :
```html
<header class="sparkle-magic super-nav mega-header">
```
Problème : Classes inventées, inexistantes dans Tailwind.

Temperature 0.2 (CORRECT) :
```html
<header class="sticky top-0 bg-white border-b">
```
Classes valides, syntaxe précise.

### 2.2 Top-p : filtrage du vocabulaire

**Définition**  
Top-p (nucleus sampling) ne garde que les tokens cumulant p% de probabilité.

**Valeurs recommandées pour le code**

| Top-p | Usage | Effet |
|-------|-------|-------|
| 0.8 | HTML strict | Vocabulaire limité aux balises standard |
| 0.85 | Tailwind | Classes communes uniquement |
| 0.9 | Design | Légère variation autorisée |
| 1.0 | Créatif | Tout le vocabulaire disponible |

**Règle** : Pour du code, restez entre 0.8 et 0.9.

### 2.3 Max tokens : longueur de sortie

**1 token ≈ 4 caractères en français**

Exemples de budgets :

```
Header simple : 400 tokens (≈ 1600 caractères)
Section complète : 600 tokens
Page entière : 1000-1500 tokens
```

**Conseil** : Commencez bas, augmentez si tronqué.

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

## PARTIE 3 : MÉTHODE JSON

### 3.1 Pourquoi structurer en JSON

**Problème du prompt vague :**
```
"Fais un header cool"
```
Résultat : imprévisible, souvent incorrect.

**Solution JSON :**
```json
{
  "component": "header",
  "structure": {
    "tag": "header",
    "classes": "sticky top-0 bg-white/90 backdrop-blur border-b"
  },
  "content": {
    "logo": {"tag": "a", "href": "index.html", "text": "Portfolio"},
    "nav": {"responsive": "hidden md:flex", "items": ["Projets", "Contact"]}
  },
  "temperature": 0.2
}
```
Résultat : précis, reproductible, documenté.

### 3.2 Schema JSON standard pour composants HTML

```json
{
  "component": "nom_du_composant",
  "tag": "balise_html",
  "structure": {
    "container": "classes_tailwind_container",
    "layout": "flex_ou_grid"
  },
  "elements": [
    {
      "type": "type_element",
      "tag": "balise",
      "classes": "classes_tailwind",
      "attributes": {},
      "content": "texte_ou_placeholder"
    }
  ],
  "responsive": {
    "mobile": "classes_mobile",
    "tablet": "classes_md:",
    "desktop": "classes_lg:"
  },
  "generation_params": {
    "temperature": 0.2,
    "top_p": 0.8,
    "max_tokens": 500
  }
}
```

### 3.3 Conversion JSON vers prompt

**Processus en 3 étapes :**

1. Écrire le JSON avec spécifications complètes
2. Demander à l'IA : "Transforme ce JSON en code HTML/Tailwind. Respecte EXACTEMENT la structure."
3. Coller le JSON

**Avantages :**
- Traçabilité (JSON archivé)
- Reproductibilité (même JSON = même code)
- Itération facile (modifier JSON, régénérer)

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

**JSON de spécification :**

```json
{
  "document": "index.html",
  "structure": {
    "doctype": "html",
    "lang": "fr",
    "head": {
      "charset": "utf-8",
      "viewport": "width=device-width, initial-scale=1",
      "title": "Portfolio - Développeur IA & Cloud",
      "description": "Portfolio professionnel : projets IA, démos, architecture Cloud",
      "tailwind_cdn": "https://cdn.tailwindcss.com"
    },
    "body": {
      "classes": "antialiased text-slate-800 bg-white"
    }
  },
  "temperature": 0.1
}
```

**Prompt structuré pour ChatGPT/Claude :**

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

**JSON de spécification :**

```json
{
  "component": "header",
  "tag": "header",
  "position": "sticky top-0",
  "style": {
    "background": "bg-white/90",
    "backdrop": "backdrop-blur",
    "border": "border-b"
  },
  "container": {
    "classes": "mx-auto max-w-6xl px-4 py-3",
    "layout": "flex items-center justify-between"
  },
  "logo": {
    "tag": "a",
    "href": "index.html",
    "text": "[Votre Nom] - Dev IA & Cloud",
    "classes": "font-semibold text-lg"
  },
  "mobile_menu_button": {
    "id": "menuBtn",
    "classes": "md:hidden p-2 border rounded",
    "text": "Menu"
  },
  "nav": {
    "id": "menu",
    "tag": "ul",
    "classes": "hidden md:flex gap-6",
    "items": [
      {"text": "Projets", "href": "#projects"},
      {"text": "Démos IA", "href": "ai-demos.html"},
      {"text": "Architecture Cloud", "href": "cloud-architecture.html"},
      {"text": "Contact", "href": "#contact"}
    ],
    "link_classes": "hover:text-blue-600 font-semibold"
  },
  "javascript": {
    "functionality": "toggle menu mobile",
    "event": "click sur menuBtn",
    "action": "toggle classe 'hidden' sur #menu"
  },
  "temperature": 0.2
}
```

**Prompt structuré :**

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
2. Testez dans le navigateur :
   - Desktop : menu horizontal visible
   - Mobile (< 768px) : bouton "Menu" apparaît, clic ouvre/ferme
3. Documentez dans `prompts-log.md`

**Si le code est incorrect :**

Exemple : le menu ne se toggle pas.

Nouveau prompt :
```
Le toggle ne fonctionne pas. Corrige le script JavaScript.
Le bouton #menuBtn doit ajouter/enlever la classe "hidden" sur #menu à chaque clic.
Ajoute une vérification que les éléments existent avant d'attacher l'événement.

Temperature : 0.1 (précision maximale)
```

---

## PARTIE 5 : HERO SECTION

### 5.1 Spécifications

Une hero section = section d'introduction visuelle avec :
- Fond dégradé subtil
- Titre principal (H1)
- Description courte
- Bouton call-to-action

### 5.2 JSON de spécification

```json
{
  "component": "hero-section",
  "tag": "section",
  "structure": {
    "wrapper": "relative overflow-hidden border-b",
    "overlay": {
      "classes": "absolute inset-0",
      "gradient": "bg-gradient-to-br from-blue-500/10 via-purple-500/10 to-cyan-500/10"
    },
    "content": {
      "classes": "relative mx-auto max-w-6xl px-4",
      "padding": "py-16 md:py-24"
    }
  },
  "elements": {
    "h1": {
      "text": "Développeur IA & Cloud",
      "classes": "text-3xl md:text-5xl font-semibold"
    },
    "description": {
      "tag": "p",
      "text": "LLM, RAG, pipelines de données, MLOps, déploiements scalables.",
      "classes": "mt-3 max-w-2xl text-slate-700"
    },
    "cta": {
      "tag": "a",
      "href": "#projects",
      "text": "Voir mes projets",
      "classes": "mt-6 inline-block px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold"
    }
  },
  "temperature": 0.3
}
```

### 5.3 Prompt structuré

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

### 5.6 Pourquoi temperature=0.3 ?

**Justification :**
- Structure HTML : stricte (0.2 aurait suffi)
- Gradient colors : légère liberté acceptable (0.3)
- Classes Tailwind : toutes standards

Temperature 0.3 = compromis entre précision syntaxique et légère variabilité esthétique.

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

### 7.1 Spécifications

Grid responsive de 3 cards projet avec image + titre + description.

### 7.2 JSON de spécification

```json
{
  "component": "projects-grid",
  "tag": "section",
  "id": "projects",
  "classes": "mx-auto max-w-6xl px-4 py-12 md:py-16 border-t",
  "header": {
    "h2": {
      "text": "Projets",
      "classes": "text-2xl font-semibold"
    }
  },
  "grid": {
    "classes": "mt-6 grid sm:grid-cols-2 lg:grid-cols-3 gap-6",
    "cards": [
      {
        "tag": "article",
        "classes": "border rounded-xl overflow-hidden shadow-sm",
        "image": {
          "src": "assets/projet1.jpg",
          "alt": "Aperçu du projet de classification d'images",
          "classes": "w-full h-40 object-cover"
        },
        "content": {
          "classes": "p-4",
          "title": {
            "tag": "h3",
            "text": "Classifier d'images (CNN)",
            "classes": "font-semibold"
          },
          "description": {
            "tag": "p",
            "text": "Entraînement local, export ONNX, déploiement statique + API simulée.",
            "classes": "mt-2 text-sm text-slate-600"
          }
        }
      },
      {
        "title": "RAG basique (simulé)",
        "description": "Recherche contextuelle + synthèse (simulation sans backend).",
        "image_src": "assets/projet2.jpg"
      },
      {
        "title": "Pipeline de données",
        "description": "ETL simple, validation schéma, exposition via endpoint simulé.",
        "image_src": "assets/projet3.jpg"
      }
    ]
  },
  "temperature": 0.2
}
```

### 7.3 Prompt structuré

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
   - Utilisez https://via.placeholder.com/400x250 temporairement
   - Ou créez des images 400x250px
3. Testez le responsive :
   - Mobile : 1 colonne
   - Tablette (≥640px) : 2 colonnes
   - Desktop (≥1024px) : 3 colonnes
4. Documentez

---

## PARTIE 8 : FORMULAIRE CONTACT

### 8.1 Spécifications

Formulaire avec validation HTML5 + simulation d'envoi.

### 8.2 Prompt structuré

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

### 8.5 Actions

1. Insérez dans `<main>` après la section projets
2. Testez la validation HTML5 :
   - Champs vides : erreur native navigateur
   - Email invalide : erreur format
   - Formulaire complet : alert apparaît
3. Documentez

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



