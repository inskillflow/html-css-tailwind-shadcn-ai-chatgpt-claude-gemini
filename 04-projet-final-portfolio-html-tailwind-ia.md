# PROJET FINAL : Page Portfolio Ultra-Professionnelle


**Objectif : Construire une page qui impressionne, étape par étape**  
**Format : Prompts quasi-complets, vous ajoutez les détails finaux**


## RÉSULTAT FINAL

À la fin de ce module, vous aurez une page portfolio avec :

- Header glassmorphism avec navigation fluide
- Hero section avec gradient animé et photo professionnelle
- Section "À propos" avec layout 2 colonnes
- Grid de 6 projets avec hover effects avancés
- Section compétences avec icônes et barres de progression
- Témoignages avec avatars et étoiles
- Formulaire de contact stylé avec validation
- Footer avec réseaux sociaux
- Animations fluides sur scroll
- 100% responsive et validé W3C

**Cette page vaudrait 500-1000 EUR en freelance.**

---

## ARBORESCENCE DU PROJET

Créez cette structure maintenant :

```bash
mkdir portfolio-pro
cd portfolio-pro
mkdir assets
mkdir assets/projets
mkdir assets/photos
touch index.html
touch prompts-log.md
```

---

## ÉTAPE 1 : SQUELETTE HTML PREMIUM

### Votre mission

Générez le squelette HTML avec métadonnées SEO optimales.

### Prompt quasi-complet (complétez les parties en CAPITALES)

```
Génère le squelette HTML5 complet pour un portfolio professionnel.

Head :
- Meta charset UTF-8
- Title : "VOTRE_NOM - Développeur IA & Cloud | Portfolio"
- Meta description : "Portfolio professionnel de VOTRE_NOM : projets IA, machine learning, déploiements cloud. VOTRE_SPECIALITE."
- Meta viewport responsive
- Meta Open Graph :
  - og:title : "Portfolio VOTRE_NOM"
  - og:description : même que meta description
  - og:type : website
- Tailwind v3 CDN : https://cdn.tailwindcss.com
- Google Fonts : Lien vers "Inter" (weights 400, 600, 700)

Body :
- Classes : antialiased bg-slate-50 text-slate-800
- Style : font-family: 'Inter', sans-serif

Commentaire dans body : "<!-- Contenu premium à ajouter -->"

Temperature : 0.1
Top-p : 0.8
Max tokens : 600
```

**Complétez ces champs :**
- VOTRE_NOM : ...........................
- VOTRE_SPECIALITE : ...........................

**Générez maintenant.**

### Code attendu (vérifiez le vôtre)

```html
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8">
  <title>[Votre Nom] - Développeur IA & Cloud | Portfolio</title>
  <meta name="description" content="Portfolio professionnel...">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta property="og:title" content="Portfolio [Votre Nom]">
  <meta property="og:description" content="...">
  <meta property="og:type" content="website">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="antialiased bg-slate-50 text-slate-800" style="font-family: 'Inter', sans-serif;">
  <!-- Contenu premium à ajouter -->
</body>
</html>
```

**Actions :**
1. Copiez dans `portfolio-pro/index.html`
2. Ouvrez dans le navigateur (fond gris clair, police Inter si chargée)
3. Documentez dans `prompts-log.md`

---

## ÉTAPE 2 : HEADER GLASSMORPHISM

### Qu'est-ce que le glassmorphism ?

Effet de "verre dépoli" : fond semi-transparent + flou + bordure subtile.

**Exemple visuel :**
```
Fond normal :     ████████  (opaque)
Glassmorphism :   ░░▒▒▓▓░░  (semi-transparent + flou)
```

### Prompt quasi-complet

```
Génère un header avec effet glassmorphism.

Structure :
- Tag <header>
- Classes : fixed top-0 left-0 right-0 z-50 bg-white/70 backdrop-blur-md border-b border-white/20 shadow-sm

Container :
- Classes : mx-auto max-w-7xl px-6 py-4 flex items-center justify-between

Logo :
- Tag <a> vers index.html
- Texte : "VOTRE_NOM" en gros + sous-titre "VOTRE_TITRE" en petit
- Structure : 
  <a href="index.html" class="flex flex-col">
    <span class="text-xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">VOTRE_NOM</span>
    <span class="text-xs text-slate-500">VOTRE_TITRE</span>
  </a>

Navigation desktop :
- Tag <nav> avec classes : hidden md:block
- Tag <ul> avec classes : flex gap-8
- 5 liens (choisissez vos sections) :
  1. SECTION_1 (ex: Accueil, #home)
  2. SECTION_2 (ex: Projets, #projects)
  3. SECTION_3 (ex: Compétences, #skills)
  4. SECTION_4 (ex: À propos, #about)
  5. SECTION_5 (ex: Contact, #contact)
- Classes liens : text-slate-700 hover:text-blue-600 font-semibold transition-all duration-300 relative after:absolute after:bottom-0 after:left-0 after:w-0 after:h-0.5 after:bg-blue-600 hover:after:w-full after:transition-all

Bouton menu mobile :
- Tag <button> id="menuToggle"
- Classes : md:hidden p-2 rounded-lg hover:bg-slate-100 transition-colors
- Contenu : SVG hamburger (3 lignes) ou texte "☰"

Menu mobile (overlay) :
- Tag <div> id="mobileMenu"
- Classes : hidden fixed inset-0 bg-black/50 z-40
- Div intérieur : fixed right-0 top-0 bottom-0 w-64 bg-white shadow-2xl p-6
- Même 5 liens que desktop, mais en colonne (flex flex-col gap-4)
- Bouton fermer en haut : X

Script JS :
- Toggle #mobileMenu au clic sur menuToggle
- Fermer au clic sur bouton X
- Fermer au clic sur l'overlay noir

Temperature : 0.2
Top-p : 0.85
Max tokens : 1000
```

**Complétez ces champs :**
- VOTRE_NOM : ...........................
- VOTRE_TITRE : ...........................
- SECTION_1 à 5 : ...........................

**Générez maintenant.**

### Tests obligatoires

**Test 1 : Glassmorphism visible**
1. Ajoutez temporairement du contenu sous le header (lorem ipsum long)
2. Scrollez
3. Le header doit rester fixe avec effet de flou sur le contenu en dessous

**Test 2 : Menu mobile**
1. Mode responsive (iPhone)
2. Cliquez sur ☰
3. Menu slide depuis la droite
4. Fond noir semi-transparent visible
5. Cliquez sur X ou sur le fond noir : menu se ferme

**Test 3 : Underline animation**
1. Desktop mode
2. Passez souris sur un lien nav
3. Une ligne bleue doit apparaître sous le lien (animation fluide)

**Si un test échoue :** Notez-le, vous corrigerez après avoir vu toutes les sections.

---

## ÉTAPE 3 : HERO SECTION PREMIUM

### Caractéristiques

- Gradient animé en arrière-plan
- Photo professionnelle de vous (ou placeholder)
- Titre avec effet de dégradé de texte
- Sous-titre animé (typing effect avec JS)
- 2 boutons (primaire + secondaire)
- Icônes de réseaux sociaux

### Prompt quasi-complet

```
Génère une hero section premium.

Structure :
- Tag <section> id="home"
- Classes : relative min-h-screen flex items-center overflow-hidden

Background animé :
- Div : absolute inset-0 bg-gradient-to-br from-blue-600/20 via-purple-600/20 to-pink-600/20
- Div formes décoratives :
  <div class="absolute top-20 right-20 w-72 h-72 bg-blue-500/30 rounded-full blur-3xl"></div>
  <div class="absolute bottom-20 left-20 w-96 h-96 bg-purple-500/30 rounded-full blur-3xl"></div>

Container principal :
- Classes : relative mx-auto max-w-7xl px-6 py-20
- Layout : grid md:grid-cols-2 gap-12 items-center

Colonne gauche (texte) :
1. Badge au-dessus du titre :
   - Tag <span>
   - Texte : "👋 Disponible pour projets" (ou VOTRE_BADGE)
   - Classes : inline-block px-4 py-2 bg-blue-600/10 text-blue-600 rounded-full text-sm font-semibold mb-6

2. Titre principal :
   - Tag <h1>
   - Texte : "Bonjour, je suis VOTRE_NOM"
   - Classes : text-5xl md:text-6xl font-bold mb-4
   - Effet gradient : 
     <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">VOTRE_NOM</span>

3. Sous-titre :
   - Tag <p>
   - Texte : "VOTRE_TITRE_PROFESSIONNEL"
   - Classes : text-2xl md:text-3xl text-slate-600 font-semibold mb-6

4. Description :
   - Tag <p> id="typedText"
   - Texte : "VOTRE_DESCRIPTION_COURTE" (ex: "Spécialisé en IA générative, LLM, et architectures cloud scalables.")
   - Classes : text-lg text-slate-600 mb-8 max-w-xl

5. Boutons :
   - Bouton primaire :
     * Tag <a> href="#projects"
     * Texte : "Voir mes projets"
     * Classes : inline-block px-8 py-4 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-xl font-semibold shadow-lg hover:shadow-xl hover:scale-105 transition-all duration-300
   
   - Bouton secondaire :
     * Tag <a> href="#contact"
     * Texte : "Me contacter"
     * Classes : inline-block ml-4 px-8 py-4 border-2 border-slate-300 text-slate-700 rounded-xl font-semibold hover:border-blue-600 hover:text-blue-600 transition-all duration-300

6. Réseaux sociaux :
   - Div : mt-8 flex gap-4
   - 4 liens (GitHub, LinkedIn, Twitter, Email) :
     * Classes : w-12 h-12 flex items-center justify-center rounded-full bg-slate-200 hover:bg-blue-600 hover:text-white transition-all duration-300
     * Contenu : Icônes (utilisez émojis temporairement ou texte)

Colonne droite (photo) :
- Div container : relative
- Image :
  * Tag <img>
  * Src : CHEMIN_VOTRE_PHOTO (ou "https://ui-avatars.com/api/?name=VOTRE_INITIALES&size=500&background=3b82f6&color=fff" en placeholder)
  * Alt : "Photo de VOTRE_NOM"
  * Classes : w-full max-w-md mx-auto rounded-3xl shadow-2xl border-8 border-white/50
- Décoration autour de la photo :
  * Div : absolute -top-4 -right-4 w-24 h-24 bg-yellow-400 rounded-full blur-2xl opacity-70

Temperature : 0.3
Top-p : 0.85
Max tokens : 1200
```

**Complétez ces champs AVANT de générer :**

- VOTRE_NOM : ...........................
- VOTRE_BADGE : ...........................
- VOTRE_TITRE_PROFESSIONNEL : ...........................
- VOTRE_DESCRIPTION_COURTE : ...........................
- CHEMIN_VOTRE_PHOTO : ...........................
- VOTRE_INITIALES (pour placeholder) : ...........................

**Choix à faire :**

Réseaux sociaux (choisissez 3-4) :
- [ ] GitHub
- [ ] LinkedIn
- [ ] Twitter
- [ ] Email
- [ ] Autre : ...........................

**Générez maintenant.**

### Code attendu (structure)

Vous devriez obtenir quelque chose comme :

```html
<section id="home" class="relative min-h-screen flex items-center overflow-hidden">
  <!-- Background animé -->
  <div class="absolute inset-0 bg-gradient-to-br from-blue-600/20 via-purple-600/20 to-pink-600/20"></div>
  <div class="absolute top-20 right-20 w-72 h-72 bg-blue-500/30 rounded-full blur-3xl"></div>
  <div class="absolute bottom-20 left-20 w-96 h-96 bg-purple-500/30 rounded-full blur-3xl"></div>
  
  <!-- Contenu -->
  <div class="relative mx-auto max-w-7xl px-6 py-20 grid md:grid-cols-2 gap-12 items-center">
    
    <!-- Colonne gauche -->
    <div>
      <span class="inline-block px-4 py-2 bg-blue-600/10 text-blue-600 rounded-full text-sm font-semibold mb-6">
        👋 Disponible pour projets
      </span>
      
      <h1 class="text-5xl md:text-6xl font-bold mb-4">
        Bonjour, je suis
        <span class="bg-gradient-to-r from-blue-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
          [Votre Nom]
        </span>
      </h1>
      
      <p class="text-2xl md:text-3xl text-slate-600 font-semibold mb-6">
        Développeur IA & Cloud
      </p>
      
      <p class="text-lg text-slate-600 mb-8 max-w-xl">
        Spécialisé en IA générative, LLM, et architectures cloud scalables.
      </p>
      
      <div class="flex flex-wrap gap-4">
        <a href="#projects" class="inline-block px-8 py-4 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-xl font-semibold shadow-lg hover:shadow-xl hover:scale-105 transition-all duration-300">
          Voir mes projets
        </a>
        <a href="#contact" class="inline-block px-8 py-4 border-2 border-slate-300 text-slate-700 rounded-xl font-semibold hover:border-blue-600 hover:text-blue-600 transition-all duration-300">
          Me contacter
        </a>
      </div>
      
      <div class="mt-8 flex gap-4">
        <a href="#" class="w-12 h-12 flex items-center justify-center rounded-full bg-slate-200 hover:bg-blue-600 hover:text-white transition-all duration-300">G</a>
        <a href="#" class="w-12 h-12 flex items-center justify-center rounded-full bg-slate-200 hover:bg-blue-600 hover:text-white transition-all duration-300">L</a>
        <a href="#" class="w-12 h-12 flex items-center justify-center rounded-full bg-slate-200 hover:bg-blue-600 hover:text-white transition-all duration-300">T</a>
      </div>
    </div>
    
    <!-- Colonne droite -->
    <div class="relative">
      <img src="https://ui-avatars.com/api/?name=JD&size=500&background=3b82f6&color=fff" alt="Photo de Jean Dupont" class="w-full max-w-md mx-auto rounded-3xl shadow-2xl border-8 border-white/50">
      <div class="absolute -top-4 -right-4 w-24 h-24 bg-yellow-400 rounded-full blur-2xl opacity-70"></div>
    </div>
    
  </div>
</section>
```

### Tests obligatoires

**Test 1 : Effet glassmorphism**
1. Scrollez la page (ajoutez du contenu temporaire si besoin)
2. Le header doit avoir un effet de verre dépoli
3. Le contenu derrière doit être légèrement visible et flouté

**Test 2 : Gradient du nom**
1. Le nom doit avoir un dégradé bleu → violet → rose
2. Si texte noir : la classe `bg-clip-text` manque

**Test 3 : Boutons hover**
1. Hover sur bouton primaire : échelle augmente (scale-105)
2. Hover sur bouton secondaire : bordure devient bleue
3. Transitions fluides (duration-300)

**Test 4 : Responsive**
1. Mobile : photo en dessous du texte (grid devient 1 colonne)
2. Desktop : photo à droite (2 colonnes)

### Photo : où la trouver ?

**Option 1 : Photo professionnelle (recommandé)**
- Prenez une photo nette, fond neutre
- 500x500px minimum
- Placez dans `assets/photos/profile.jpg`

**Option 2 : Générer avec IA**
- Freepik AI Image Generator (gratuit)
- Prompt : "Professional headshot photo, software developer, neutral background, studio lighting"
- Téléchargez, renommez `profile.jpg`

**Option 3 : Placeholder (temporaire)**
- Utilisez : `https://ui-avatars.com/api/?name=VosInitiales&size=500&background=3b82f6&color=fff`
- Remplacez VosInitiales par vos vraies initiales

---

## ÉTAPE 4 : SECTION PROJETS IMPRESSIONNANTE

### Caractéristiques wow

- Grid 3 colonnes avec cartes premium
- Images avec overlay au hover
- Tags de technologies
- Effet parallaxe subtil
- Boutons "Live Demo" et "Code"

### Prompt quasi-complet

```
Génère une section projets ultra-professionnelle.

Structure globale :
- Tag <section> id="projects"
- Classes : relative py-20 md:py-32 bg-white

Container :
- Classes : mx-auto max-w-7xl px-6

Header de section :
- Tag <div> classes : text-center mb-16
- Petit titre au-dessus :
  * Tag <span>
  * Texte : "Portfolio"
  * Classes : text-blue-600 font-semibold text-sm uppercase tracking-wider
- Titre principal :
  * Tag <h2>
  * Texte : "Projets Récents"
  * Classes : text-4xl md:text-5xl font-bold text-slate-800 mt-2
- Sous-titre :
  * Tag <p>
  * Texte : "Une sélection de mes meilleurs travaux"
  * Classes : mt-4 text-lg text-slate-600 max-w-2xl mx-auto

Grid de projets :
- Div : grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8

Créez 6 cards projet avec cette structure (VARIEZ les détails) :

Card projet (répétez 6 fois avec infos différentes) :
- Tag <article>
- Classes : group relative bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-500 border border-slate-100

Contenu de chaque card :
1. Container image (avec overlay hover) :
   - Div : relative overflow-hidden
   - Image : src="assets/projets/projet1.jpg", alt descriptif, classes : w-full h-56 object-cover transform group-hover:scale-110 transition-transform duration-500
   - Overlay hover : 
     <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/30 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
   - Boutons sur overlay (visibles au hover) :
     <div class="absolute inset-0 flex items-center justify-center gap-4 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
       <a href="#" class="px-4 py-2 bg-white text-slate-800 rounded-lg text-sm font-semibold hover:bg-blue-600 hover:text-white transition-colors">Live Demo</a>
       <a href="#" class="px-4 py-2 bg-white/10 backdrop-blur text-white rounded-lg text-sm font-semibold border border-white/30 hover:bg-white hover:text-slate-800 transition-colors">Code</a>
     </div>

2. Div contenu : p-6

3. Titre projet :
   - Tag <h3>
   - Texte : "TITRE_PROJET_X" (ex: "Chatbot IA Personnalisé")
   - Classes : text-xl font-bold text-slate-800 mb-2

4. Description :
   - Tag <p>
   - Texte : "DESCRIPTION_PROJET_X" (2-3 lignes max)
   - Classes : text-slate-600 text-sm mb-4

5. Tags technologies :
   - Div : flex flex-wrap gap-2
   - Chaque tag : <span class="px-3 py-1 bg-blue-50 text-blue-600 rounded-full text-xs font-semibold">TECHNO</span>
   - Technologies (choisissez 3-4 par projet) : Python, TensorFlow, React, Node.js, AWS, Docker, etc.

Variez pour les 6 projets :
- Projet 1 : VOTRE_CHOIX
- Projet 2 : VOTRE_CHOIX
- Projet 3 : VOTRE_CHOIX
- Projet 4 : VOTRE_CHOIX
- Projet 5 : VOTRE_CHOIX
- Projet 6 : VOTRE_CHOIX

Temperature : 0.25
Top-p : 0.85
Max tokens : 2000
```

**Complétez pour 6 projets :**

Projet 1 :
- Titre : ...........................
- Description : ...........................
- Technologies : ...........................

Projet 2 :
- Titre : ...........................
- Description : ...........................
- Technologies : ...........................

(etc. pour 6 projets)

**Générez maintenant.**

### Images de projets : où les trouver ?

**Option 1 : Freepik (recommandé)**
1. Allez sur freepik.com
2. Recherchez : "ai technology dashboard", "machine learning interface", "cloud architecture", "data pipeline", "chatbot interface", "neural network visualization"
3. Téléchargez 6 images (gratuites avec attribution)
4. Renommez : projet1.jpg à projet6.jpg
5. Placez dans `assets/projets/`

**Option 2 : Générer avec IA**
1. DALL-E, Midjourney, ou Stable Diffusion
2. Prompts suggestions :
   - "Modern AI dashboard interface, clean design, blue purple gradient, screenshot"
   - "Cloud architecture diagram, professional, minimal, tech aesthetic"
   - "Machine learning model visualization, graphs, data, modern UI"
3. Téléchargez, renommez

**Option 3 : Unsplash (photos tech)**
1. unsplash.com
2. Recherchez : "technology", "code", "data", "ai", "server"
3. Téléchargez gratuitement

**Option 4 : Placeholder temporaire**
```
https://picsum.photos/600/400?random=1
https://picsum.photos/600/400?random=2
...
```

### Tests obligatoires

**Test 1 : Hover effect sur cards**
1. Desktop mode
2. Passez souris sur une card
3. Image doit zoomer (scale-110)
4. Overlay noir doit apparaître
5. Boutons "Live Demo" et "Code" doivent apparaître

**Test 2 : Grid responsive**
1. Mobile (390px) : 1 colonne, cards empilées
2. Tablette (768px) : 2 colonnes
3. Desktop (1440px) : 3 colonnes, 2 lignes de 3

**Test 3 : Tags technologies**
1. Chaque projet doit avoir 3-4 tags
2. Tags en forme de pillules bleues
3. Lisibles, pas trop petits

### Variantes à tester (choisissez-en 2)

**Variante A : Cards avec pourcentage de progression**

Ajoutez dans chaque card :
```
Après la description, avant les tags :
- Div : mt-3 mb-3
- Texte : "Progression : 85%"
- Barre de progression :
  * Container : w-full h-2 bg-slate-200 rounded-full
  * Barre : w-[85%] h-2 bg-gradient-to-r from-blue-600 to-purple-600 rounded-full
```

**Variante B : Effet tilt 3D au hover**

Changez les classes de l'article :
```
Ajoutez : transform hover:-rotate-1 hover:translate-y-[-8px]
```

**Variante C : Grid 2x3 au lieu de 3x2**

Changez :
```
lg:grid-cols-3 → lg:grid-cols-2
```

Générez seulement 4 projets au lieu de 6.

**Variante D : Filtres par catégorie**

Ajoutez avant la grid :
```
Boutons filtres :
- Div : flex justify-center gap-4 mb-8
- 4 boutons : "Tous", "IA", "Cloud", "Web"
- Classes : px-6 py-2 rounded-full border-2 border-slate-200 hover:border-blue-600 hover:text-blue-600 transition-colors
```

(Note : JS pour filtrage fonctionnel sera ajouté plus tard)

---

## ÉTAPE 5 : SECTION COMPÉTENCES VISUELLE

### Prompt quasi-complet

```
Génère une section compétences visuelle.

Structure :
- Tag <section> id="skills"
- Classes : py-20 md:py-32 bg-slate-50

Header :
- Container : mx-auto max-w-7xl px-6 text-center mb-16
- Badge : "Expertise"
- H2 : "Compétences & Technologies"
- Sous-titre : "Outils que je maîtrise"

Grid compétences :
- Container : mx-auto max-w-7xl px-6
- Grid : grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6

Chaque compétence (créez 8 au minimum) :
- Div : group bg-white rounded-2xl p-6 shadow-md hover:shadow-xl transition-all duration-300 border border-slate-100 hover:border-blue-600

Contenu :
1. Icône/Emoji :
   - Div : w-16 h-16 mx-auto mb-4 bg-gradient-to-br from-blue-500 to-purple-600 rounded-xl flex items-center justify-center text-3xl
   - Contenu : EMOJI_TECHNO (ex: 🐍 pour Python)

2. Nom :
   - Tag <h3>
   - Texte : NOM_TECHNO
   - Classes : font-bold text-slate-800 mb-2 text-center

3. Niveau (barre visuelle) :
   - Tag <p> : text-xs text-slate-500 text-center mb-2, texte "NIVEAU%" (ex: "85%")
   - Container barre : w-full h-2 bg-slate-200 rounded-full overflow-hidden
   - Barre remplie : h-full bg-gradient-to-r from-blue-600 to-purple-600 rounded-full, style="width: NIVEAU%"

Compétences à inclure (CHOISISSEZ les vôtres) :
1. COMPETENCE_1 : emoji, nom, niveau
2. COMPETENCE_2 : emoji, nom, niveau
3. COMPETENCE_3 : emoji, nom, niveau
4. COMPETENCE_4 : emoji, nom, niveau
5. COMPETENCE_5 : emoji, nom, niveau
6. COMPETENCE_6 : emoji, nom, niveau
7. COMPETENCE_7 : emoji, nom, niveau
8. COMPETENCE_8 : emoji, nom, niveau

Suggestions d'émojis :
- Python : 🐍
- JavaScript : ⚡
- React : ⚛️
- AWS : ☁️
- Docker : 🐳
- Git : 🔧
- ML : 🤖
- Database : 💾

Temperature : 0.3
Top-p : 0.85
Max tokens : 1500
```

**Listez VOS 8 compétences :**

1. ...........................  /  emoji : ...  /  niveau : ...%
2. ...........................  /  emoji : ...  /  niveau : ...%
3. ...........................  /  emoji : ...  /  niveau : ...%
4. ...........................  /  emoji : ...  /  niveau : ...%
5. ...........................  /  emoji : ...  /  niveau : ...%
6. ...........................  /  emoji : ...  /  niveau : ...%
7. ...........................  /  emoji : ...  /  niveau : ...%
8. ...........................  /  emoji : ...  /  niveau : ...%

**Générez maintenant.**

### Tests obligatoires

**Test 1 : Hover effect cards**
1. Passez souris sur une card
2. Ombre s'intensifie
3. Bordure devient bleue
4. Transition fluide

**Test 2 : Barres de progression**
1. Chaque compétence a une barre
2. Largeur correspond au pourcentage (85% = barre à 85%)
3. Gradient bleu-violet visible

**Test 3 : Grid responsive**
1. Mobile : 2 colonnes
2. Tablette : 3 colonnes
3. Desktop : 4 colonnes

---

## ÉTAPE 6 : SECTION TÉMOIGNAGES

### Prompt quasi-complet

```
Génère une section témoignages élégante.

Structure :
- Tag <section> id="testimonials"
- Classes : py-20 md:py-32 bg-white

Header : (même structure que section précédente)
- Badge : "Témoignages"
- H2 : "Ce qu'on dit de mon travail"
- Sous-titre : "Retours de clients et collaborateurs"

Grid témoignages :
- Container : mx-auto max-w-7xl px-6
- Grid : grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8

Créez 3 témoignages :

Card témoignage (structure identique pour les 3) :
- Tag <article>
- Classes : bg-slate-50 rounded-2xl p-8 shadow-md hover:shadow-xl transition-all duration-300 border border-slate-100

Contenu :
1. Étoiles (5 étoiles pleines) :
   - Div : flex gap-1 mb-4
   - 5 fois : <span class="text-yellow-400 text-xl">★</span>

2. Citation :
   - Tag <p>
   - Texte : "CITATION_X" (ex: "Excellent développeur, code de qualité et respect des délais. Très professionnel.")
   - Classes : text-slate-700 italic mb-6 leading-relaxed

3. Auteur :
   - Div : flex items-center gap-4
   - Avatar :
     * Tag <img>
     * Src : "https://ui-avatars.com/api/?name=INITIALES_PERSONNE&size=48&background=random"
     * Classes : w-12 h-12 rounded-full
   - Infos :
     * Div : flex flex-col
     * Nom : <span class="font-bold text-slate-800">NOM_PERSONNE</span>
     * Titre : <span class="text-sm text-slate-500">TITRE_PERSONNE</span>

Témoignages (INVENTEZ ou utilisez ces exemples) :

Témoignage 1 :
- Citation : "VOTRE_CITATION_1"
- Nom : "NOM_1"
- Titre : "TITRE_1" (ex: "CTO, StartupTech")
- Initiales : "XX"

Témoignage 2 :
- Citation : "VOTRE_CITATION_2"
- Nom : "NOM_2"
- Titre : "TITRE_2"
- Initiales : "YY"

Témoignage 3 :
- Citation : "VOTRE_CITATION_3"
- Nom : "NOM_3"
- Titre : "TITRE_3"
- Initiales : "ZZ"

Temperature : 0.3
Top-p : 0.85
Max tokens : 1200
```

**Complétez 3 témoignages (inventez si besoin) :**

1. Citation : .................................................
   Nom : ........................  /  Titre : ........................

2. Citation : .................................................
   Nom : ........................  /  Titre : ........................

3. Citation : .................................................
   Nom : ........................  /  Titre : ........................

**Générez maintenant.**

### Tests obligatoires

**Test 1 : Étoiles visibles**
- 5 étoiles jaunes par témoignage
- Alignées horizontalement

**Test 2 : Avatars**
- Chaque témoignage a un avatar rond
- Initiales visibles (UI Avatars API)

**Test 3 : Hover effect**
- Ombre s'intensifie au hover
- Transition fluide

---

## ÉTAPE 7 : FORMULAIRE CONTACT PREMIUM

### Prompt quasi-complet

```
Génère une section formulaire de contact ultra-stylée.

Structure :
- Tag <section> id="contact"
- Classes : py-20 md:py-32 bg-gradient-to-br from-blue-50 to-purple-50

Container :
- Grid : mx-auto max-w-7xl px-6 grid md:grid-cols-2 gap-12 items-start

Colonne gauche (infos) :
1. Header :
   - Badge : "Contact"
   - H2 : "Travaillons ensemble"
   - P : "Une idée de projet ? Discutons-en."

2. Infos contact :
   - Div : space-y-6 mt-8
   - 3 items (email, téléphone, localisation) :
     * Structure : flex items-center gap-4
     * Icône : <div class="w-12 h-12 bg-blue-600 rounded-xl flex items-center justify-center text-white text-xl">EMOJI</div>
     * Texte : <span class="text-slate-700">VOTRE_INFO</span>
   
   Email : 📧  /  VOTRE_EMAIL
   Téléphone : 📱  /  VOTRE_TELEPHONE (ou "Sur demande")
   Localisation : 📍  /  VOTRE_VILLE, VOTRE_PAYS

3. Réseaux sociaux :
   - Titre : <p class="mt-12 mb-4 font-semibold text-slate-700">Suivez-moi</p>
   - Div : flex gap-4
   - 4 liens (GitHub, LinkedIn, Twitter, Email) :
     * Classes : w-12 h-12 flex items-center justify-center rounded-xl bg-white shadow-md hover:bg-blue-600 hover:text-white hover:scale-110 transition-all duration-300
     * Contenu : Initiales (G, L, T, @)

Colonne droite (formulaire) :
- Tag <form>
- Classes : bg-white rounded-3xl shadow-2xl p-8 md:p-10 border border-slate-100
- Attribut : onsubmit="event.preventDefault(); alert('Message envoyé ! Je vous répondrai sous 24h.'); this.reset();"

Champs (structure premium) :

1. Grid 2 colonnes :
   - Div : grid md:grid-cols-2 gap-6 mb-6
   
   Champ prénom :
   - Label : for="prenom", classes : block text-sm font-semibold text-slate-700 mb-2, texte "Prénom"
   - Input : id="prenom", type="text", required, placeholder="Jean"
   - Classes : w-full px-4 py-3 border-2 border-slate-200 rounded-xl focus:border-blue-600 focus:ring-4 focus:ring-blue-600/10 focus:outline-none transition-all
   
   Champ nom :
   - Structure identique, id="nom", placeholder="Dupont"

2. Email :
   - Label + input (structure identique)
   - Type : email, placeholder : "jean.dupont@email.com"
   - Classes : mb-6

3. Sujet :
   - Label + input
   - Placeholder : "Sujet de votre message"
   - Classes : mb-6

4. Message :
   - Label + textarea
   - Rows : 5
   - Placeholder : "Décrivez votre projet ou question..."
   - Classes : w-full px-4 py-3 border-2 border-slate-200 rounded-xl focus:border-blue-600 focus:ring-4 focus:ring-blue-600/10 focus:outline-none transition-all resize-none

5. Bouton submit :
   - Type : submit
   - Texte : "Envoyer le message"
   - Classes : w-full px-8 py-4 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-xl font-bold shadow-lg hover:shadow-xl hover:scale-[1.02] transition-all duration-300

Temperature : 0.15
Top-p : 0.8
Max tokens : 1500
```

**Complétez vos informations :**

- VOTRE_EMAIL : ...........................
- VOTRE_TELEPHONE : ...........................
- VOTRE_VILLE : ...........................
- VOTRE_PAYS : ...........................

**Générez maintenant.**

### Tests obligatoires

**Test 1 : Validation complète**
1. Soumettez sans remplir : erreur sur premier champ
2. Remplissez nom/prénom, laissez email vide : erreur email
3. Email invalide (sans @) : erreur format
4. Tout rempli : alert + formulaire se vide (reset)

**Test 2 : Focus states**
1. Cliquez dans un champ
2. Bordure doit devenir bleue
3. Ring bleu clair apparaît autour
4. Transition fluide

**Test 3 : Responsive**
1. Mobile : prénom et nom empilés verticalement
2. Desktop : prénom et nom côte à côte

---

## ÉTAPE 8 : FOOTER PREMIUM

### Prompt quasi-complet

```
Génère un footer premium multi-sections.

Structure :
- Tag <footer>
- Classes : bg-slate-900 text-white pt-16 pb-8

Container principal :
- Classes : mx-auto max-w-7xl px-6

Grid 4 colonnes :
- Div : grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12 mb-12

Colonne 1 - À propos :
- H3 : "VOTRE_NOM", classes : text-xl font-bold mb-4
- P : "VOTRE_BIO_COURTE" (2-3 lignes), classes : text-slate-400 text-sm leading-relaxed
- Réseaux : flex gap-3 mt-6
  * 4 icônes sociales : w-10 h-10, bg-slate-800, rounded-lg, hover:bg-blue-600

Colonne 2 - Navigation :
- H4 : "Navigation", classes : font-semibold mb-4
- Ul : space-y-3
- 5 liens : Accueil, Projets, Compétences, À propos, Contact
- Classes liens : text-slate-400 hover:text-white transition-colors

Colonne 3 - Projets récents :
- H4 : "Projets récents"
- Ul : space-y-3
- 3 liens vers projets : text-slate-400 hover:text-blue-400 text-sm

Colonne 4 - Contact :
- H4 : "Contact"
- 3 items (email, tel, localisation) :
  * P : text-slate-400 text-sm, icône + texte

Barre de séparation :
- Div : border-t border-slate-800 pt-8

Footer bottom :
- Div : flex flex-col md:flex-row justify-between items-center gap-4 text-sm text-slate-400
- Gauche : "© <span id="year"></span> VOTRE_NOM. Tous droits réservés."
- Droite : "Fait avec ❤️ et IA générative"

Script :
document.getElementById('year').textContent = new Date().getFullYear();

Temperature : 0.2
Max tokens : 1200
```

**Complétez :**
- VOTRE_NOM : ...........................
- VOTRE_BIO_COURTE : ...........................
- Vos 3 projets récents (noms) : ...........................

**Générez maintenant.**

---

## ÉTAPE 9 : ANIMATIONS SCROLL

### Ajout d'animations au scroll

Vous allez ajouter un script qui anime les éléments quand ils deviennent visibles.

### Prompt pour le script

```
Génère un script JavaScript pour animer les éléments au scroll.

Fonctionnalité :
- Détecter quand un élément entre dans le viewport
- Ajouter une classe "animate-in" qui déclenche l'animation CSS
- Observer tous les éléments avec classe "scroll-animate"

Code :
1. Créer un IntersectionObserver
2. Observer tous les éléments .scroll-animate
3. Quand visible : ajouter classe "animate-in"
4. Threshold : 0.1 (10% visible suffit)

Configuration Tailwind à ajouter dans <head> AVANT le CDN :

<script>
  tailwind.config = {
    theme: {
      extend: {
        animation: {
          'fade-in': 'fadeIn 0.8s ease-out forwards',
          'slide-up': 'slideUp 0.8s ease-out forwards'
        },
        keyframes: {
          fadeIn: {
            '0%': { opacity: '0', transform: 'translateY(20px)' },
            '100%': { opacity: '1', transform: 'translateY(0)' }
          },
          slideUp: {
            '0%': { opacity: '0', transform: 'translateY(40px)' },
            '100%': { opacity: '1', transform: 'translateY(0)' }
          }
        }
      }
    }
  }
</script>

Temperature : 0.2
Max tokens : 600
```

**Générez le script.**

### Actions

1. Ajoutez le config Tailwind dans `<head>`
2. Ajoutez le script IntersectionObserver avant `</body>`
3. Ajoutez classe `scroll-animate opacity-0` sur :
   - Chaque card de projet
   - Chaque card de compétence
   - Chaque témoignage
4. Rechargez, scrollez : les éléments apparaissent progressivement

---

## ÉTAPE 10 : OPTIMISATIONS FINALES

### Prompt pour smooth scroll

```
Génère un style CSS pour smooth scroll.

Ajoute dans <head> avant Tailwind CDN :

<style>
  html {
    scroll-behavior: smooth;
  }
  
  /* Animation des barres de progression */
  @keyframes fillBar {
    from { width: 0%; }
    to { width: var(--target-width); }
  }
  
  .skill-bar {
    animation: fillBar 1.5s ease-out forwards;
    animation-delay: var(--delay);
  }
</style>

Temperature : 0.2
```

**Générez et ajoutez.**

### Prompt pour bouton "Retour en haut"

```
Génère un bouton "Retour en haut" qui apparaît au scroll.

Structure :
- Tag <button> id="scrollTop"
- Classes : fixed bottom-8 right-8 w-14 h-14 bg-blue-600 text-white rounded-full shadow-2xl hover:bg-purple-600 transition-all duration-300 opacity-0 pointer-events-none z-50
- Contenu : "↑"

Script JavaScript :
- Écouter scroll
- Si window.scrollY > 300 : retirer opacity-0 et pointer-events-none
- Sinon : remettre
- Au clic : scroll vers top avec smooth behavior

Temperature : 0.2
Max tokens : 400
```

**Générez et ajoutez.**

---

## ÉTAPE 11 : IMAGES ET CONTENU FINAL

### Checklist images nécessaires

**Photos à préparer :**
- [ ] Photo de profil (500x500px) : `assets/photos/profile.jpg`
- [ ] 6 images de projets (600x400px) : `assets/projets/projet1.jpg` à `projet6.jpg`

**Où les trouver :**

**Freepik (recommandé) :**
1. Compte gratuit sur freepik.com
2. Recherches suggérées :
   - "artificial intelligence interface"
   - "cloud computing dashboard"
   - "machine learning visualization"
   - "data analytics platform"
   - "neural network diagram"
   - "chatbot interface mockup"
3. Téléchargez format JPEG, 1920x1280
4. Redimensionnez à 600x400 (Paint, Photoshop, ou online-image-resizer.com)

**Générer avec IA :**
1. Freepik AI Generator, DALL-E, ou Midjourney
2. Prompts suggestions :

```
Projet IA :
"Modern AI chatbot interface, clean dashboard, blue purple gradient, professional screenshot, minimalist UI, high quality"

Projet Cloud :
"Cloud architecture diagram, AWS services, modern infographic style, professional, blue theme, technical illustration"

Projet ML :
"Machine learning model training interface, graphs, metrics, dark mode UI, professional software screenshot"
```

3. Téléchargez, renommez

**Unsplash (photos gratuites) :**
- unsplash.com
- Recherches : "technology", "abstract tech", "data visualization", "coding", "server room"
- Téléchargez, crop 600x400

### Attribution (si Freepik gratuit)

Ajoutez dans le footer :
```html
<p class="text-xs text-slate-500 mt-4">
  Images par <a href="https://www.freepik.com" class="underline hover:text-white">Freepik</a>
</p>
```

---

## ÉTAPE 12 : VALIDATION W3C

### Process de validation

1. Allez sur https://validator.w3.org/
2. Onglet "Validate by Direct Input"
3. Copiez tout le contenu de `index.html`
4. Cliquez "Check"

**Résultat attendu : 0 erreurs, 0 warnings**

### Erreurs fréquentes et corrections

**Erreur 1 : "Attribute 'for' without matching 'id'"**

Correction :
```html
<!-- Mauvais -->
<label for="email">Email</label>
<input id="mail">

<!-- Bon -->
<label for="email">Email</label>
<input id="email">
```

**Erreur 2 : "Unclosed tag"**

Vérifiez que chaque `<div>` a son `</div>`.

**Erreur 3 : "Duplicate ID"**

Cherchez les ID dupliqués (Ctrl+F pour trouver).

### Prompt de correction si erreurs

```
Le validateur W3C signale cette erreur :
"[COLLER_ERREUR_EXACTE]"

Corrige cette erreur dans le code suivant :
[COLLER_SECTION_CONCERNEE]

Temperature : 0.1
```

---

## ÉTAPE 13 : TESTS RESPONSIVE COMPLETS

### Breakpoints à tester obligatoirement

| Device | Largeur | Checks |
|--------|---------|--------|
| iPhone SE | 375px | Header burger, grid 1 col, footer empilé |
| iPhone 12 | 390px | Idem |
| iPad | 768px | Grid 2 col projets, nav desktop apparaît |
| iPad Pro | 1024px | Grid 3 col, layout optimal |
| Desktop | 1440px | Tout aligné, espacements larges |
| Large Desktop | 1920px | Container max-w-7xl centré |

### Tests détaillés

**Test mobile (iPhone 12, 390px) :**
- [ ] Header : bouton menu visible, nav cachée
- [ ] Hero : photo sous le texte, titre 5xl lisible
- [ ] Projets : 1 colonne, cards pleine largeur
- [ ] Compétences : 2 colonnes
- [ ] Témoignages : 1 colonne
- [ ] Formulaire : 1 colonne, champs pleine largeur
- [ ] Footer : 1 colonne, éléments empilés

**Test tablette (iPad, 768px) :**
- [ ] Header : nav horizontale visible
- [ ] Hero : 2 colonnes, photo à droite
- [ ] Projets : 2 colonnes
- [ ] Compétences : 3 colonnes
- [ ] Formulaire : prénom/nom sur même ligne

**Test desktop (1440px) :**
- [ ] Projets : 3 colonnes
- [ ] Compétences : 4 colonnes
- [ ] Témoignages : 3 colonnes
- [ ] Footer : 4 colonnes

**Si un test échoue :** Notez la section et le breakpoint, vérifiez les classes `md:` et `lg:`.

---

## ÉTAPE 14 : POLISH FINAL

### Micro-interactions à ajouter

**1. Loading state sur bouton formulaire**

Prompt :
```
Modifie le bouton submit du formulaire pour afficher un loading state.

Au clic :
1. Texte devient "Envoi en cours..."
2. Ajouter classe : opacity-75 cursor-wait
3. Désactiver le bouton (disabled)
4. Après 2 secondes : alert, reset formulaire, réactiver

Temperature : 0.2
Max tokens : 400
```

**2. Compteur de projets**

Prompt :
```
Ajoute un compteur animé dans la section hero.

Structure :
- Div : flex gap-12 mt-12
- 3 statistiques :
  * Div : text-center
  * Nombre : <span class="text-4xl font-bold text-blue-600" data-count="VALEUR">0</span>
  * Label : <p class="text-sm text-slate-600 mt-1">LABEL</p>

Stats :
1. NOMBRE_PROJETS+ / Projets réalisés
2. NOMBRE_CLIENTS+ / Clients satisfaits  
3. NOMBRE_ANNEES+ / Années d'expérience

Script : animer de 0 à la valeur cible en 2 secondes quand visible.

Temperature : 0.25
Max tokens : 600
```

Complétez vos chiffres (soyez réaliste ou inventez) :
- Projets : ...........................
- Clients : ...........................
- Années : ...........................

**3. Effet parallaxe sur background**

Prompt :
```
Ajoute un effet parallaxe sur les formes décoratives du hero.

Script :
- Écouter mousemove sur window
- Calculer position souris (clientX, clientY)
- Déplacer légèrement les divs avec blur (transform translate)
- Formule : translateX(mouseX / 50), translateY(mouseY / 50)

Temperature : 0.25
Max tokens : 400
```

---

## ÉTAPE 15 : CAPTURES D'ÉCRAN PROFESSIONNELLES

### Outils recommandés

**Option 1 : DevTools natifs**
1. F12 → Mode responsive
2. Sélectionnez device
3. Capture : Ctrl+Shift+P → "Capture screenshot"

**Option 2 : Extensions navigateur**
- Full Page Screen Capture (Chrome)
- FireShot (Firefox)

**Option 3 : Outils en ligne**
- screely.com (ajoute mockup navigateur)
- shots.so (mockup browser + background)

### Captures obligatoires

**1. Hero section (desktop) :**
- Largeur : 1920px
- Capturez : header + hero complet
- Format : PNG, qualité max
- Nom : `screenshot-hero-desktop.png`

**2. Projets section (desktop) :**
- Grid 3x2 visible complète
- Nom : `screenshot-projects-desktop.png`

**3. Vue mobile (iPhone 12) :**
- Scroll jusqu'à montrer 2-3 sections
- Nom : `screenshot-mobile.png`

**4. Formulaire avec focus :**
- Un champ en focus (bordure bleue + ring visible)
- Nom : `screenshot-form-focus.png`

**Placez dans `assets/`**

---

## ÉTAPE 16 : README PROFESSIONNEL

### Prompt pour README

```
Génère un README.md professionnel pour ce portfolio.

Structure markdown :

# Portfolio - VOTRE_NOM

## Description
Portfolio professionnel présentant mes projets en IA et Cloud.

## Caractéristiques
- Liste des features (responsive, animations, glassmorphism, etc.)

## Technologies utilisées
- HTML5
- Tailwind CSS v3
- JavaScript vanilla
- Google Fonts (Inter)

## Sections
- Hero avec gradient animé
- NOMBRE_PROJETS projets présentés
- Compétences visuelles avec barres
- Témoignages
- Formulaire contact
- Footer complet

## Génération avec IA
Ce portfolio a été généré avec l'aide de l'IA générative.
Paramètres utilisés : température 0.15-0.3, top-p 0.8-0.85.
Voir `prompts-log.md` pour tous les prompts.

## Installation locale
```bash
git clone [votre-repo]
cd portfolio-pro
# Ouvrir index.html dans navigateur
```

## Captures d'écran
[Insérer liens vers captures]

## Crédits
- Images : Freepik / IA générée
- Police : Inter (Google Fonts)
- Framework : Tailwind CSS

## Contact
- Email : VOTRE_EMAIL
- LinkedIn : VOTRE_LINKEDIN
- GitHub : VOTRE_GITHUB

## Licence
Tous droits réservés © ANNEE VOTRE_NOM

Temperature : 0.3
Max tokens : 800
```

**Complétez vos infos et générez.**

---

## ÉTAPE 17 : OPTIMISATIONS SEO

### Meta tags additionnels

Prompt :
```
Génère des meta tags SEO additionnels pour le head.

Inclus :
- Meta keywords : "VOTRE_NOM, développeur IA, machine learning, cloud computing, VOS_MOTS_CLES"
- Meta author : "VOTRE_NOM"
- Meta robots : "index, follow"
- Link canonical : "VOTRE_URL_FINALE" (ou mettre #)
- Favicon link : href="assets/favicon.ico"
- Meta theme-color : "#3b82f6" (bleu)

Twitter Card :
- twitter:card : summary_large_image
- twitter:title : "Portfolio VOTRE_NOM"
- twitter:description : même que meta description
- twitter:image : "VOTRE_URL/assets/screenshot-hero-desktop.png"

Temperature : 0.1
Max tokens : 400
```

**Générez et ajoutez dans le `<head>`.**

---

## ÉTAPE 18 : PERFORMANCE ET POLISH

### Checklist finale obligatoire

**HTML :**
- [ ] Validation W3C : 0 erreurs
- [ ] Toutes les images ont un `alt` descriptif
- [ ] Un seul H1 par page
- [ ] Hiérarchie de titres cohérente (H1 → H2 → H3)

**CSS/Tailwind :**
- [ ] Aucune classe inventée (toutes vérifiées)
- [ ] Responsive testé sur 5 breakpoints
- [ ] Hover effects fonctionnent
- [ ] Animations fluides (pas de lag)

**JavaScript :**
- [ ] Aucune erreur console (F12)
- [ ] Menu mobile fonctionne
- [ ] Formulaire valide correctement
- [ ] Scroll animations fluides
- [ ] Bouton retour en haut apparaît

**Performance :**
- [ ] Images optimisées (< 200 KB chacune)
- [ ] Polices chargées (Inter visible)
- [ ] Page charge en < 2 secondes

**Accessibilité :**
- [ ] Tous les liens ont du texte visible
- [ ] Contraste suffisant (texte lisible)
- [ ] Navigation au clavier possible (Tab)
- [ ] Labels liés aux inputs (for/id)

---

## RÉSULTAT FINAL

### Structure complète de index.html

```
<!doctype html>
<html>
  <head>
    <!-- Meta tags SEO -->
    <!-- Tailwind config animations -->
    <!-- Tailwind CDN -->
    <!-- Google Fonts -->
    <!-- Custom styles -->
  </head>
  <body>
    <!-- Header glassmorphism -->
    
    <main>
      <!-- Hero section gradient + photo -->
      <!-- Section À propos -->
      <!-- Section Projets (6 cards) -->
      <!-- Section Compétences (8 items) -->
      <!-- Section Témoignages (3 items) -->
      <!-- Section Contact (formulaire premium) -->
    </main>
    
    <!-- Footer 4 colonnes -->
    
    <!-- Bouton scroll top -->
    
    <!-- Scripts :
         - Menu toggle
         - Année dynamique
         - Scroll animations
         - Form loading
         - Parallaxe
         - Smooth scroll
    -->
  </body>
</html>
```

**Taille totale du fichier : 800-1200 lignes**

---

## LIVRABLES FINAUX

```
portfolio-pro/
├── index.html                         (page complète, 1000+ lignes)
├── assets/
│   ├── photos/
│   │   └── profile.jpg               (votre photo)
│   ├── projets/
│   │   ├── projet1.jpg               (6 images)
│   │   ├── projet2.jpg
│   │   ├── projet3.jpg
│   │   ├── projet4.jpg
│   │   ├── projet5.jpg
│   │   └── projet6.jpg
│   ├── screenshot-hero-desktop.png
│   ├── screenshot-projects-desktop.png
│   ├── screenshot-mobile.png
│   └── screenshot-form-focus.png
├── README.md                          (documentation complète)
└── prompts-log.md                     (tous vos prompts + paramètres)
```

**Format de remise :** `portfolio-pro-[votrenom].zip`

---

## BARÈME (100 points)

| Critère | Points | Détails |
|---------|--------|---------|
| **Code HTML** | **25** | |
| - Validation W3C | 10 | 0 erreurs |
| - Sémantique | 8 | Balises appropriées |
| - Accessibilité | 7 | Alt, labels, contraste |
| **Design Tailwind** | **30** | |
| - Classes valides | 10 | Aucune inventée |
| - Responsive | 12 | 5 breakpoints testés |
| - Effets avancés | 8 | Glassmorphism, gradients, hover |
| **Fonctionnalités** | **25** | |
| - Navigation mobile | 5 | Toggle fluide |
| - Animations scroll | 8 | IntersectionObserver |
| - Formulaire validation | 7 | HTML5 + loading state |
| - Bouton scroll top | 5 | Apparaît/disparaît |
| **Contenu** | **10** | |
| - Images qualité | 5 | 7 images optimisées |
| - Textes pertinents | 5 | Pas de lorem ipsum |
| **Documentation** | **10** | |
| - prompts-log.md | 6 | Tous prompts + params |
| - README.md | 4 | Complet et clair |
| **BONUS** | **+20** | |
| - Dark mode toggle | +5 | Switch fonctionnel |
| - Animations CSS custom | +5 | Keyframes originaux |
| - Performance 95+ | +5 | Lighthouse score |
| - Déploiement live | +5 | GitHub Pages ou Netlify |
| **Total** | **120** | (100 + 20 bonus max) |

---

## PROPOSITIONS DE CORRECTIONS

### Correction 1 : Header

<details>
<summary>Si votre header a des problèmes, cliquez ici</summary>

**Problèmes fréquents :**

1. **Menu mobile ne s'ouvre pas**
   - Vérifiez les ID : `menuToggle` et `mobileMenu`
   - Script doit être après le HTML, pas avant

2. **Glassmorphism invisible**
   - Vérifiez : `bg-white/70` (opacité 70%)
   - Vérifiez : `backdrop-blur-md` présent

3. **Underline animation ne marche pas**
   - Classes `after:` doivent toutes être présentes
   - Vérifiez : `relative` sur le lien parent

**Prompt de correction complet :**
```
Régénère le header avec ces corrections :
- ID menuToggle (pas menuBtn)
- bg-white/70 backdrop-blur-md (glassmorphism)
- Liens avec after: pseudo-element pour underline animation
- Script après le HTML

Temperature : 0.15
```

</details>

---

### Correction 2 : Hero section

<details>
<summary>Si votre hero a des problèmes, cliquez ici</summary>

**Problèmes fréquents :**

1. **Gradient invisible**
   - Augmentez opacité : `/20` → `/30`
   - Vérifiez formes décoratives (blur-3xl)

2. **Photo ne s'affiche pas**
   - Vérifiez chemin : `assets/photos/profile.jpg`
   - Ou utilisez placeholder UI Avatars

3. **Boutons pas côte à côte**
   - Container doit avoir : `flex gap-4`
   - Ou chaque bouton : `inline-block` + `ml-4` sur le 2ème

4. **Pas responsive**
   - Grid doit avoir : `grid-cols-1 md:grid-cols-2`
   - Photo doit passer en dessous sur mobile

**Prompt de correction :**
```
Corrige le responsive du hero :
- Mobile : photo sous le texte (grid-cols-1)
- Desktop : photo à droite (md:grid-cols-2)
- Titre : text-4xl mobile, md:text-6xl desktop

Temperature : 0.2
```

</details>

---

### Correction 3 : Grid projets

<details>
<summary>Si votre grid a des problèmes, cliquez ici</summary>

**Problèmes fréquents :**

1. **Hover overlay ne s'affiche pas**
   - Vérifiez : `group` sur article
   - Vérifiez : `group-hover:opacity-100` sur overlay

2. **Images ne zoomment pas au hover**
   - Vérifiez : `group-hover:scale-110` sur img
   - Vérifiez : `overflow-hidden` sur container image

3. **Pas 3 colonnes sur desktop**
   - Vérifiez : `lg:grid-cols-3` présent
   - Testez à 1024px minimum

4. **Tags technologies mal alignés**
   - Container : `flex flex-wrap gap-2`
   - Chaque tag : `inline-block`

**Prompt de correction :**
```
Corrige les effets hover sur les cards :
- Parent article : classe "group"
- Image : transform group-hover:scale-110 transition-transform duration-500
- Overlay : opacity-0 group-hover:opacity-100
- Boutons overlay : opacity-0 group-hover:opacity-100

Temperature : 0.2
```

</details>

---

### Correction 4 : Formulaire

<details>
<summary>Si votre formulaire a des problèmes, cliquez ici</summary>

**Problèmes fréquents :**

1. **Validation ne fonctionne pas**
   - Tous les inputs doivent avoir : `required`
   - Email doit avoir : `type="email"`

2. **Focus ring invisible**
   - Chaque input doit avoir : `focus:ring-4 focus:ring-blue-600/10`
   - Et : `focus:border-blue-600`

3. **Grid 2 colonnes cassée**
   - Container doit avoir : `grid md:grid-cols-2 gap-6`
   - Email, sujet, message : `md:col-span-2` pour prendre 2 colonnes

4. **Reset ne fonctionne pas**
   - onsubmit doit finir par : `this.reset();`

**Prompt de correction :**
```
Corrige la validation du formulaire :
- Tous les champs : required
- Email : type="email"
- Focus : border-blue-600 + ring-4 ring-blue-600/10
- Submit : event.preventDefault() puis alert puis this.reset()

Temperature : 0.1
```

</details>

---

## PROPOSITIONS D'AMÉLIORATIONS BONUS

### Amélioration 1 : Dark mode toggle

Prompt :
```
Ajoute un bouton toggle dark mode dans le header.

Bouton :
- Position : à côté de la nav
- Icône : 🌙 (mode clair) / ☀️ (mode sombre)
- Classes : p-2 rounded-lg bg-slate-100 hover:bg-slate-200

Script :
- Au clic : toggle classe "dark" sur <html>
- Sauvegarder préférence : localStorage

Classes dark mode :
- body : dark:bg-slate-900 dark:text-slate-100
- sections : dark:bg-slate-800
- textes : dark:text-slate-300
- cards : dark:bg-slate-800 dark:border-slate-700

Temperature : 0.25
Max tokens : 1000
```

**Points bonus : +5**

---

### Amélioration 2 : Section blog (aperçus)

Prompt :
```
Génère une section "Derniers articles" avec 3 cards d'aperçu.

Structure :
- Même layout que projets
- Grid 3 colonnes
- Cards avec :
  * Image miniature (16:9)
  * Badge catégorie (IA / Cloud / Code)
  * Titre article
  * Extrait (2 lignes)
  * Date de publication
  * Lien "Lire la suite"

Temperature : 0.25
Max tokens : 1000
```

**Points bonus : +3**

---

### Amélioration 3 : Timeline expérience

Prompt :
```
Génère une section timeline verticale pour expérience professionnelle.

Structure :
- Ligne verticale centrale
- Items alternés gauche/droite
- Cercles sur la ligne
- Cards avec dates, postes, descriptions

Minimum 3 expériences.

Temperature : 0.3
Max tokens : 1200
```

**Points bonus : +4**

---

### Amélioration 4 : Lighthouse audit 95+

**Process :**
1. Ouvrez DevTools → Lighthouse
2. Lancez audit (Performance, Accessibility, Best Practices, SEO)
3. Objectif : 95+ sur tous
4. Corrections suggérées :
   - Images : format WebP, compression
   - Fonts : preload
   - Scripts : defer
   - Cache headers

**Points bonus : +5**

---

### Amélioration 5 : Déploiement GitHub Pages

**Process :**
1. Créez repo GitHub : `portfolio-pro`
2. Poussez le code
3. Settings → Pages → Deploy from main
4. Attendez 2-3 minutes
5. URL : `votreusername.github.io/portfolio-pro`

**Points bonus : +3**

---

## CHECKLIST AVANT REMISE

**Fichiers :**
- [ ] index.html (1000+ lignes, validé W3C)
- [ ] README.md (complet, captures insérées)
- [ ] prompts-log.md (tous les prompts de chaque étape)
- [ ] 7 images minimum (profile + 6 projets)
- [ ] 4 captures d'écran

**Tests :**
- [ ] 5 breakpoints responsive testés
- [ ] Menu mobile toggle
- [ ] Formulaire validation complète
- [ ] Animations scroll visible
- [ ] Hover effects sur tous les composants
- [ ] Aucune erreur console JavaScript

**Documentation :**
- [ ] Chaque prompt dans prompts-log avec température/top-p
- [ ] README liste toutes les features
- [ ] Crédits pour images/ressources

**Qualité :**
- [ ] Textes personnalisés (pas de lorem ipsum)
- [ ] Vos vraies infos (email, LinkedIn, etc.)
- [ ] Design cohérent (palette de couleurs uniforme)
- [ ] Professionnel (pas d'émojis partout, juste où approprié)

---

## EXEMPLE DE PROMPTS-LOG.MD FINAL

```markdown
# Log des prompts - Portfolio Pro

## Méthodologie
IA utilisée : ChatGPT 4
Approche : Prompts quasi-complets fournis par le cours, personnalisés avec mes infos
Durée totale : 8 heures

---

## Étape 1 : Squelette HTML
Date : 2024-01-15 10:00
Temperature : 0.1
Top-p : 0.8
Max tokens : 600

Prompt :
[prompt complet]

Résultat : OK en 1 génération
Ajustements : Changé title avec mon vrai nom

---

## Étape 2 : Header glassmorphism
Date : 2024-01-15 10:30
Temperature : 0.2
Top-p : 0.85
Max tokens : 1000

Prompt :
[prompt complet]

Résultat : OK après 1 correction
Ajustements : 
- Essai 1 : menu mobile ne toggle pas (ID incorrect)
- Essai 2 : corrigé ID menuToggle, fonctionne

---

[etc. pour toutes les 18 étapes]
```

---

## DURÉE ESTIMÉE PAR ÉTAPE

| Étape | Description | Temps |
|-------|-------------|-------|
| 1 | Squelette HTML | 15 min |
| 2 | Header glassmorphism | 30 min |
| 3 | Hero premium | 45 min |
| 4 | Section projets | 1h |
| 5 | Compétences | 45 min |
| 6 | Témoignages | 30 min |
| 7 | Formulaire premium | 45 min |
| 8 | Footer | 30 min |
| 9-10 | Animations + polish | 1h |
| 11 | Images (recherche/génération) | 1h 30min |
| 12-13 | Validation + tests | 45 min |
| 14-15 | Captures + README | 30 min |
| 16-18 | Optimisations | 45 min |
| **Total** | | **≈ 9h** |

---

**CETTE PAGE VAUT 500-1000 EUR EN FREELANCE.**

**Montrez-la fièrement dans vos candidatures !**

---

## PROCHAINES ÉTAPES (après validation)

1. **Déployez en ligne** (GitHub Pages gratuit)
2. **Partagez sur LinkedIn** avec captures
3. **Ajoutez dans votre CV** (lien vers le site)
4. **Itérez** : ajoutez plus de projets, blog, etc.
5. **Domaine custom** : `votrenom.dev` (10 EUR/an)

**FIN DU PROJET FINAL**

