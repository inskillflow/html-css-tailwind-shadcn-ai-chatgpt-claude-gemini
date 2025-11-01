# ÉVALUATION PRATIQUE : Génération de composants web avec IA

**Durée : 3 heures**  
**Barème : 100 points**  
**Format : Pratique individuelle**

---

## CONSIGNES GÉNÉRALES

### Format de remise

```
evaluation-[votrenom]/
├── composants/
│   ├── header.html
│   ├── hero.html
│   ├── card-projet.html
│   ├── formulaire.html
│   └── footer.html
├── prompts-log.md
├── tests-temperature.md
└── analyse-erreurs.md
```

### Règles

1. Vous DEVEZ écrire vos prompts AVANT de consulter les exemples de correction
2. Documentez TOUS vos essais (même les ratés)
3. Si votre premier prompt ne fonctionne pas, essayez de le corriger VOUS-MÊME avant de voir la solution
4. Notez les différences entre votre prompt et le prompt de correction

---

## PARTIE 1 : EXPÉRIMENTATION TEMPÉRATURE (20 points)

### Objectif

Comprendre l'impact de la température sur la génération de code HTML/Tailwind.

### Exercice 1.1 : Votre premier essai (5 points)

**Consigne :**  
Sans consulter le cours, écrivez un prompt pour générer un bouton call-to-action.

**Contraintes :**
- Le bouton doit avoir un fond bleu
- Texte blanc
- Coins arrondis
- Effet hover

**Votre prompt (à écrire MAINTENANT, sans regarder d'exemples) :**

```
[Écrivez votre prompt ici]




Température choisie : _______
Top-p choisi : _______
Max tokens : _______
```

**Action :**
1. Écrivez votre prompt ci-dessus
2. Générez le code avec votre IA
3. Copiez le résultat ci-dessous

**Code généré :**

```html
[Collez le code ici]




```

**Auto-évaluation :**
- [ ] Le code est valide HTML
- [ ] Toutes les classes Tailwind existent
- [ ] Le bouton a bien un fond bleu
- [ ] L'effet hover fonctionne
- [ ] Score : ____/5

---

### Exercice 1.2 : Tests de température (10 points)

Maintenant, testez 3 températures avec LE MÊME prompt que ci-dessus.

**Test A : Temperature 0.1**

Code généré :
```html
[Collez ici]


```

Classes inventées (si présentes) : _______________________________

**Test B : Temperature 0.5**

Code généré :
```html
[Collez ici]


```

Classes inventées (si présentes) : _______________________________

**Test C : Temperature 0.9**

Code généré :
```html
[Collez ici]


```

Classes inventées (si présentes) : _______________________________

---

### Exercice 1.3 : Analyse (5 points)

Répondez à ces questions (3-5 lignes chacune) :

**1. Quelle température a produit le code le plus fiable ?**

..........................................................................................
..........................................................................................
..........................................................................................

**2. Avez-vous observé des classes inventées ? À quelle température ?**

..........................................................................................
..........................................................................................
..........................................................................................

**3. Quelle température recommandez-vous pour du code HTML/Tailwind ?**

..........................................................................................
..........................................................................................
..........................................................................................

---

## PARTIE 2 : GÉNÉRATION DE COMPOSANTS (60 points)

### Consignes

Pour chaque composant :
1. Écrivez VOTRE prompt (avant de voir la correction)
2. Générez le code
3. Testez dans le navigateur
4. Comparez avec la correction fournie
5. Analysez les différences

---

### Composant 1 : Header de navigation (15 points)

**Spécifications :**
- Header sticky qui reste en haut au scroll
- Fond blanc semi-transparent avec flou
- Logo "Portfolio Pro" à gauche
- 3 liens de navigation à droite : Projets, À propos, Contact
- Responsive : menu caché sur mobile (< 768px), bouton "Menu" visible

**Votre prompt (écrivez MAINTENANT, sans regarder plus bas) :**

```
[Écrivez votre prompt ici]












Température : _______
Top-p : _______
Max tokens : _______
```

**Votre code généré :**

```html
[Collez le code ici]








```

**Tests à effectuer :**
- [ ] Header reste fixe au scroll
- [ ] Fond semi-transparent visible
- [ ] Sur desktop (>768px) : 3 liens visibles
- [ ] Sur mobile (<768px) : bouton "Menu" visible, liens cachés
- [ ] Score auto-évaluation : ____/10

---

**CORRECTION (ne regardez qu'APRÈS avoir essayé) :**

<details>
<summary>Cliquez pour voir le prompt de correction</summary>

```
Génère un header de navigation en HTML/Tailwind.

Structure :
- Tag <header> avec classes : sticky top-0 bg-white/90 backdrop-blur border-b z-50
- Container : mx-auto max-w-6xl px-4 py-3 flex items-center justify-between

Éléments :
1. Logo :
   - Tag <a> vers index.html
   - Texte : "Portfolio Pro"
   - Classes : font-semibold text-lg text-slate-800

2. Bouton menu mobile :
   - Tag <button> avec id="menuBtn"
   - Classes : md:hidden px-3 py-2 border rounded
   - Texte : "Menu"

3. Navigation :
   - Tag <ul> avec id="menu"
   - Classes : hidden md:flex gap-6
   - 3 liens dans <li> :
     * Projets (#projects)
     * À propos (#about)
     * Contact (#contact)
   - Classes liens : text-slate-700 hover:text-blue-600 font-semibold transition-colors

Script JavaScript :
Ajouter toggle sur bouton menuBtn pour montrer/cacher #menu.

Temperature : 0.2
Top-p : 0.8
Max tokens : 600
```

**Code attendu :**

```html
<header class="sticky top-0 bg-white/90 backdrop-blur border-b z-50">
  <div class="mx-auto max-w-6xl px-4 py-3 flex items-center justify-between">
    <a href="index.html" class="font-semibold text-lg text-slate-800">Portfolio Pro</a>
    
    <button id="menuBtn" class="md:hidden px-3 py-2 border rounded">Menu</button>
    
    <ul id="menu" class="hidden md:flex gap-6">
      <li><a href="#projects" class="text-slate-700 hover:text-blue-600 font-semibold transition-colors">Projets</a></li>
      <li><a href="#about" class="text-slate-700 hover:text-blue-600 font-semibold transition-colors">À propos</a></li>
      <li><a href="#contact" class="text-slate-700 hover:text-blue-600 font-semibold transition-colors">Contact</a></li>
    </ul>
  </div>
</header>

<script>
  document.getElementById('menuBtn')?.addEventListener('click', () => {
    document.getElementById('menu')?.classList.toggle('hidden');
  });
</script>
```

</details>

**Analyse des différences (5 points) :**

Comparez votre prompt avec le prompt de correction.

**Qu'avez-vous oublié dans votre prompt ?**

..........................................................................................
..........................................................................................
..........................................................................................

**Quelles classes Tailwind manquaient dans votre code ?**

..........................................................................................
..........................................................................................

**Quelle température aviez-vous choisi ? Était-ce approprié ?**

..........................................................................................
..........................................................................................

---

### Composant 2 : Card de projet (15 points)

**Spécifications :**
- Card avec bordure et ombre
- Image en haut (400x250px, coins arrondis supérieurs)
- Titre du projet
- Description courte
- Bouton "Voir le projet"
- Hover : ombre s'intensifie

**Votre prompt (écrivez MAINTENANT) :**

```
[Écrivez votre prompt ici]












Température : _______
Top-p : _______
Max tokens : _______
```

**Votre code généré :**

```html
[Collez le code ici]








```

**Tests à effectuer :**
- [ ] Image s'affiche correctement
- [ ] Hover intensifie l'ombre
- [ ] Bouton cliquable
- [ ] Responsive : s'adapte à la largeur du container
- [ ] Score auto-évaluation : ____/10

---

**CORRECTION (ne regardez qu'APRÈS avoir essayé) :**

<details>
<summary>Cliquez pour voir le prompt de correction</summary>

```
Génère une card de projet en HTML/Tailwind.

Structure :
- Tag <article> avec classes : border border-slate-200 rounded-xl overflow-hidden shadow-sm hover:shadow-md transition-shadow

Contenu (dans cet ordre) :
1. Image :
   - Tag <img>
   - Src : assets/projet.jpg
   - Alt : "Aperçu du projet de classification"
   - Classes : w-full h-40 object-cover

2. Div conteneur : classes p-4

3. Titre :
   - Tag <h3>
   - Texte : "Classifier d'images"
   - Classes : font-semibold text-slate-800

4. Description :
   - Tag <p>
   - Texte : "Modèle CNN pour classification d'images. Précision 92% sur le dataset de test."
   - Classes : mt-2 text-sm text-slate-600

5. Bouton :
   - Tag <a>
   - Href : #
   - Texte : "Voir le projet"
   - Classes : mt-3 inline-block px-3 py-2 bg-blue-600 text-white text-sm rounded hover:bg-blue-500 transition-colors

NE GENERE QUE la card, pas de page complète.

Temperature : 0.2
Top-p : 0.8
Max tokens : 400
```

</details>

**Analyse (5 points) :**

**Différences entre votre prompt et la correction :**

..........................................................................................
..........................................................................................
..........................................................................................

**Classes que vous aviez oubliées :**

..........................................................................................

**Leçon apprise :**

..........................................................................................
..........................................................................................

---

### Composant 3 : Formulaire contact (15 points)

**Spécifications :**
- 3 champs : Nom (texte), Email (validation email), Message (multiligne)
- Chaque champ doit avoir un label lié
- Tous les champs sont requis
- Bouton "Envoyer" avec style bleu
- Simulation d'envoi (alert)

**Votre prompt (écrivez MAINTENANT) :**

```
[Écrivez votre prompt ici]














Température : _______
Top-p : _______
Max tokens : _______
```

**Votre code généré :**

```html
[Collez le code ici]








```

**Tests CRITIQUES à effectuer :**
- [ ] Cliquez "Envoyer" sans remplir : erreur "champ requis" apparaît
- [ ] Tapez "abc" dans email : erreur "@ manquant"
- [ ] Cliquez sur le label "Nom" : curseur va dans le champ
- [ ] Remplissez tout : alert apparaît
- [ ] Score auto-évaluation : ____/10

---

**CORRECTION :**

<details>
<summary>Cliquez pour voir le prompt de correction</summary>

```
Génère un formulaire de contact en HTML/Tailwind.

Structure :
- Tag <form> avec classes : max-w-xl space-y-4
- Attribut onsubmit : event.preventDefault(); alert('Message envoyé (simulation)');

Champs (dans cet ordre) :

1. Nom :
   - Label : for="nom", classes font-semibold, texte "Nom"
   - Input : id="nom", type="text", placeholder="Votre nom", required
   - Classes input : w-full border border-slate-300 rounded p-3 focus:border-blue-500 focus:outline-none

2. Email :
   - Label : for="email", classes font-semibold, texte "Email"
   - Input : id="email", type="email", placeholder="votre@email.com", required
   - Classes : w-full border border-slate-300 rounded p-3 focus:border-blue-500 focus:outline-none

3. Message :
   - Label : for="message", classes font-semibold, texte "Message"
   - Textarea : id="message", rows="5", placeholder="Votre message", required
   - Classes : w-full border border-slate-300 rounded p-3 focus:border-blue-500 focus:outline-none

4. Bouton :
   - Tag <button> type="submit"
   - Texte : "Envoyer"
   - Classes : w-full px-5 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-500 font-semibold transition-colors

NE GENERE QUE le formulaire.

Temperature : 0.1
Top-p : 0.8
Max tokens : 600
```

</details>

**Analyse (5 points) :**

**Attributs critiques que vous aviez oubliés :**

..........................................................................................

**Pourquoi temperature=0.1 et pas 0.3 pour un formulaire ?**

..........................................................................................
..........................................................................................

---

### Composant 4 : Grid responsive de 3 cards (15 points)

**Spécifications :**
- Section avec titre "Mes Projets"
- Grid responsive :
  - Mobile : 1 colonne
  - Tablette (≥640px) : 2 colonnes
  - Desktop (≥1024px) : 3 colonnes
- 3 cards identiques (utilisez la card du Composant 2)
- Espacement entre cards : gap-6

**Votre prompt (écrivez MAINTENANT) :**

```
[Écrivez votre prompt ici]














Température : _______
```

**Tests obligatoires :**
- [ ] DevTools mode responsive (F12, Ctrl+Shift+M)
- [ ] iPhone 12 (390px) : 1 colonne
- [ ] iPad (768px) : 2 colonnes
- [ ] Desktop (1440px) : 3 colonnes
- [ ] Score : ____/10

---

**CORRECTION :**

<details>
<summary>Cliquez pour voir le prompt de correction</summary>

```
Génère une section grid de projets responsive.

Structure :
- Tag <section> avec classes : mx-auto max-w-6xl px-4 py-12 md:py-16

Contenu :
1. Titre :
   - Tag <h2>
   - Texte : "Mes Projets"
   - Classes : text-2xl md:text-3xl font-semibold mb-8

2. Grid :
   - Tag <div>
   - Classes : grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6

3. Cards (3 identiques) :
   - Utilise cette structure pour chaque card :
     * Article : border border-slate-200 rounded-xl overflow-hidden shadow-sm hover:shadow-md transition-shadow
     * Image : src="assets/projet[1-3].jpg", alt descriptif, classes w-full h-40 object-cover
     * Div : p-4
     * H3 : font-semibold, titres "Projet 1", "Projet 2", "Projet 3"
     * P : mt-2 text-sm text-slate-600, description placeholder

Temperature : 0.2
Top-p : 0.8
Max tokens : 800
```

</details>

**Analyse (5 points) :**

**Classes responsive que vous aviez oubliées :**

..........................................................................................

**Différence entre votre approche et la correction :**

..........................................................................................
..........................................................................................

---

## PARTIE 2 : DÉBOGAGE DE CODE (20 points)

### Objectif

Identifier et corriger des erreurs dans du code généré avec une mauvaise température.

---

### Exercice 2.1 : Code cassé - Header (10 points)

**Contexte :**  
Un étudiant a généré ce header avec temperature=0.9. Le code ne fonctionne pas.

**Code problématique :**

```html
<header class="super-sticky magic-top shimmer-bg ultra-blur mega-border">
  <nav class="cosmic-container flex-ultimate space-galaxy">
    <a href="home.html" class="logo-enhanced text-massive weight-ultra">Mon Site</a>
    <ul class="nav-links-pro hidden mega-show gap-stellar">
      <li><a class="link-fancy hover-rainbow" href="#work">Travaux</a></li>
      <li><a class="link-fancy hover-rainbow" href="#about">Info</a></li>
    </ul>
  </nav>
</header>
```

**Votre mission :**

1. Identifiez TOUTES les classes inventées (listez-les)
2. Proposez les classes Tailwind VALIDES pour les remplacer
3. Réécrivez le code corrigé

**Classes inventées identifiées :**

..........................................................................................
..........................................................................................
..........................................................................................

**Code corrigé (écrivez VOTRE version) :**

```html
[Réécrivez le header avec classes valides]








```

**Prompt pour régénérer correctement :**

```
[Écrivez le prompt qui aurait dû être utilisé]






Temperature : _______
```

---

**CORRECTION :**

<details>
<summary>Cliquez pour voir la solution</summary>

**Classes inventées :**
- `super-sticky` → `sticky`
- `magic-top` → `top-0`
- `shimmer-bg` → `bg-white/90`
- `ultra-blur` → `backdrop-blur`
- `mega-border` → `border-b`
- `cosmic-container` → `mx-auto max-w-6xl px-4`
- `flex-ultimate` → `flex items-center justify-between`
- `space-galaxy` → supprimé
- `logo-enhanced` → supprimé
- `text-massive` → `text-lg`
- `weight-ultra` → `font-semibold`
- `nav-links-pro` → supprimé
- `mega-show` → `md:flex`
- `gap-stellar` → `gap-6`
- `link-fancy` → supprimé
- `hover-rainbow` → `hover:text-blue-600`

**Code corrigé :**

```html
<header class="sticky top-0 bg-white/90 backdrop-blur border-b z-50">
  <nav class="mx-auto max-w-6xl px-4 py-3 flex items-center justify-between">
    <a href="index.html" class="font-semibold text-lg text-slate-800">Mon Site</a>
    <ul class="hidden md:flex gap-6">
      <li><a class="text-slate-700 hover:text-blue-600 transition-colors" href="#work">Travaux</a></li>
      <li><a class="text-slate-700 hover:text-blue-600 transition-colors" href="#about">Info</a></li>
    </ul>
  </nav>
</header>
```

**Température recommandée : 0.2**

</details>

---

### Exercice 2.2 : Code cassé - Formulaire (10 points)

**Code problématique :**

```html
<form onsubmit="alert('Envoyé');">
  <label>Votre nom</label>
  <input type="text" placeholder="Nom">
  
  <label for="userEmail">Email</label>
  <input id="email" type="text" placeholder="Email">
  
  <button>Soumettre</button>
</form>
```

**Identifiez et corrigez 5 erreurs dans ce formulaire :**

**Erreur 1 :**

..........................................................................................

**Erreur 2 :**

..........................................................................................

**Erreur 3 :**

..........................................................................................

**Erreur 4 :**

..........................................................................................

**Erreur 5 :**

..........................................................................................

**Code corrigé :**

```html
[Réécrivez le formulaire corrigé]








```

---

**CORRECTION :**

<details>
<summary>Cliquez pour voir les 5 erreurs</summary>

**Erreur 1 :** Premier label n'a pas d'attribut `for` - accessibilité cassée  
**Correction :** `<label for="nom">Votre nom</label>` + `<input id="nom">`

**Erreur 2 :** `for="userEmail"` mais `id="email"` - ne correspondent pas  
**Correction :** Les deux doivent être identiques (`id="email"` et `for="email"`)

**Erreur 3 :** `type="text"` pour email au lieu de `type="email"` - pas de validation  
**Correction :** `type="email"`

**Erreur 4 :** Aucun attribut `required` - validation inexistante  
**Correction :** Ajouter `required` sur tous les inputs

**Erreur 5 :** `onsubmit="alert('Envoyé');"` sans `event.preventDefault()` - page recharge  
**Correction :** `onsubmit="event.preventDefault(); alert('Envoyé');"`

**Code corrigé complet :**

```html
<form class="max-w-xl space-y-4" onsubmit="event.preventDefault(); alert('Envoyé');">
  <label class="font-semibold" for="nom">Votre nom</label>
  <input id="nom" class="w-full border rounded p-3" type="text" placeholder="Nom" required>
  
  <label class="font-semibold" for="email">Email</label>
  <input id="email" class="w-full border rounded p-3" type="email" placeholder="Email" required>
  
  <button class="px-5 py-3 bg-blue-600 text-white rounded font-semibold" type="submit">Soumettre</button>
</form>
```

</details>

---

## PARTIE 3 : CRÉATION LIBRE (20 points)

### Exercice 3.1 : Composant au choix

**Consigne :**  
Choisissez UN composant parmi :
- Section "Compétences" avec liste de technologies
- Section "Témoignages" avec 2 citations
- Section "Expérience" avec timeline

**Spécifications minimales :**
- Responsive (mobile → desktop)
- Classes Tailwind valides uniquement
- Au moins 3 éléments distincts

**Votre prompt :**

```
[Écrivez votre prompt complet]
















Température : _______
Top-p : _______
Max tokens : _______
```

**Code généré :**

```html
[Collez le code ici]








```

**Tests effectués :**

1. .......................................................................................
2. .......................................................................................
3. .......................................................................................

**Validation W3C :**
- [ ] 0 erreurs
- [ ] 1-3 erreurs mineures
- [ ] Plus de 3 erreurs

**Score : ____/20**

---

## BARÈME DÉTAILLÉ

| Partie | Exercice | Points | Critères |
|--------|----------|--------|----------|
| **1** | Expérimentation température | **20** | |
| | 1.1 Premier essai | 5 | Prompt écrit + code généré |
| | 1.2 Tests 3 températures | 10 | 3 tests documentés + classes identifiées |
| | 1.3 Analyse | 5 | Réponses complètes, réflexion pertinente |
| **2** | Génération composants | **60** | |
| | 2.1 Header | 15 | Prompt + code + analyse différences |
| | 2.2 Card projet | 15 | Prompt + code + analyse |
| | 2.3 Formulaire | 15 | Prompt + code + 4 tests validés |
| | 2.4 Grid responsive | 15 | Prompt + tests 3 breakpoints |
| **3** | Débogage | **20** | |
| | 3.1 Header cassé | 10 | 15 classes inventées identifiées + correction |
| | 3.2 Formulaire cassé | 10 | 5 erreurs trouvées + code corrigé |
| **4** | Création libre | **20** | |
| | 4.1 Composant au choix | 20 | Originalité, qualité code, tests |
| | **BONUS : Validation W3C** | +5 | 0 erreurs sur tous les composants |
| | **TOTAL** | **120** | (100 pts de base + 20 bonus possibles) |

---

## CRITÈRES DE NOTATION DÉTAILLÉS

### Prompts (qualité)

**5/5 points :**
- Structure claire (balises, classes, responsive)
- Paramètres spécifiés et justifiés
- Détails complets (attributs, contenu)

**3/5 points :**
- Structure présente mais incomplète
- Paramètres présents mais non justifiés
- Quelques détails manquants

**1/5 points :**
- Prompt vague ("fais un header joli")
- Aucun paramètre mentionné
- Détails quasi-absents

### Code généré (qualité)

**5/5 points :**
- HTML valide (balises fermées)
- Classes Tailwind toutes valides (vérifiées)
- Responsive fonctionnel
- Tests passés

**3/5 points :**
- HTML valide mais classes approximatives
- Responsive partiel
- 50-80% des tests passés

**1/5 points :**
- HTML invalide ou classes inventées
- Pas responsive
- Tests échoués

### Analyse (réflexion)

**5/5 points :**
- Différences identifiées précisément
- Explications claires
- Leçons tirées pertinentes

**3/5 points :**
- Quelques différences notées
- Explications superficielles
- Réflexion minimale

**1/5 points :**
- Aucune analyse
- "Aucune différence" (faux)
- Pas de réflexion

---

## CONSEILS AVANT DE COMMENCER

### Stratégie recommandée

**1. Pour écrire votre prompt initial :**
- Fermez le cours
- Réfléchissez : qu'est-ce que je veux exactement ?
- Listez les éléments nécessaires
- Écrivez le prompt en langage naturel
- Choisissez température/top-p/tokens

**2. Après génération :**
- Testez IMMÉDIATEMENT dans navigateur
- Vérifiez chaque classe sur https://tailwindcss.com/docs
- Notez ce qui marche / ne marche pas

**3. Avant de voir la correction :**
- Essayez de corriger votre prompt vous-même
- Régénérez une 2ème fois si nécessaire
- Documentez vos tentatives

**4. Après avoir vu la correction :**
- Comparez ligne par ligne
- Comprenez POURQUOI la correction est meilleure
- Notez les patterns à réutiliser

---

## QUESTIONS FRÉQUENTES

**Q : Puis-je consulter la documentation Tailwind pendant l'évaluation ?**  
R : Oui, c'est même recommandé pour vérifier les classes.

**Q : Si mon premier prompt rate, ai-je le droit de réessayer ?**  
R : Oui, documentez simplement vos 2-3 essais dans prompts-log.md.

**Q : Mon code est différent de la correction, c'est grave ?**  
R : Non, si votre code est valide et respecte les specs. Il n'y a pas qu'une solution.

**Q : Je peux utiliser temperature=0.3 au lieu de 0.2 ?**  
R : Oui, du moment que vous justifiez le choix.

**Q : Combien de temps pour chaque partie ?**  
R : Partie 1 : 45 min, Partie 2 : 2h, Partie 3 : 15 min = 3h total.

---

## CHECKLIST FINALE

Avant de remettre, vérifiez :

**Fichiers obligatoires :**
- [ ] composants/header.html
- [ ] composants/hero.html
- [ ] composants/card-projet.html
- [ ] composants/formulaire.html
- [ ] composants/footer.html
- [ ] prompts-log.md (tous vos prompts + essais)
- [ ] tests-temperature.md (Partie 1)
- [ ] analyse-erreurs.md (Partie 2)

**Contenu vérifié :**
- [ ] Tous les prompts INITIAUX sont présents (avant correction)
- [ ] Tous les codes générés sont collés
- [ ] Toutes les analyses sont complétées
- [ ] Tests responsive documentés
- [ ] Température/top-p/tokens spécifiés partout

**Tests effectués :**
- [ ] Validation W3C sur au moins 3 composants
- [ ] Tests responsive (iPhone, iPad, Desktop)
- [ ] Tests fonctionnels (formulaire, menu mobile)

**Format de remise :**
- [ ] Archive ZIP nommée : evaluation-[votrenom].zip
- [ ] Taille < 5 MB

---

**BON COURAGE !**

**Rappel :** L'objectif n'est PAS d'avoir tout parfait du premier coup, mais de DOCUMENTER votre processus d'apprentissage (essais, erreurs, corrections).

