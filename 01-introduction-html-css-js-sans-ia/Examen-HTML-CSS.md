# EXAMEN HTML / CSS  

**Durée totale : 2h00**  
**Total : 100 points**  

---

## PARTIE 1 – Questions théoriques (30 points)

### 1. Structure d’une page HTML (6 pts)

1.1. Écrivez la **structure minimale** d’une page HTML5 valide (doctype + balises principales).

**Zone de réponse 1.1 :**

```text
................................................................................
................................................................................
................................................................................
................................................................................
````

1.2. Expliquez en une phrase le rôle de chacune des balises suivantes :

* `<!DOCTYPE html>`
* `<html>`
* `<head>`
* `<body>`

**Zone de réponse 1.2 :**

```text
<!DOCTYPE html> :
................................................................................

<html> :
................................................................................

<head> :
................................................................................

<body> :
................................................................................
```

---

### 2. Balises et attributs (6 pts)

2.1. Expliquez la différence entre :

* une **balise** HTML
* un **attribut** HTML

**Zone de réponse 2.1 :**

```text
Balise HTML :
................................................................................
................................................................................

Attribut HTML :
................................................................................
................................................................................
```

2.2. Donnez un exemple de balise HTML complète contenant au moins **deux attributs** (par exemple un lien ou une image) et expliquez brièvement le rôle de chaque attribut.

**Zone de réponse 2.2 :**

```text
Exemple de balise :
................................................................................
................................................................................

Rôle du 1er attribut :
................................................................................
................................................................................

Rôle du 2e attribut :
................................................................................
................................................................................
```

---

### 3. Sémantique HTML (6 pts)

Expliquez la différence de rôle (en 1–2 phrases chacune) entre les balises suivantes, et donnez un exemple concret d’utilisation pour chacune :

* `<div>`
* `<header>`
* `<nav>`
* `<section>`
* `<article>`

**Zone de réponse 3 :**

```text
<div> :
- Rôle :
................................................................................
- Exemple d'utilisation :
................................................................................

<header> :
- Rôle :
................................................................................
- Exemple d'utilisation :
................................................................................

<nav> :
- Rôle :
................................................................................
- Exemple d'utilisation :
................................................................................

<section> :
- Rôle :
................................................................................
- Exemple d'utilisation :
................................................................................

<article> :
- Rôle :
................................................................................
- Exemple d'utilisation :
................................................................................
```

---

### 4. Sélecteurs CSS (6 pts)

Expliquez la différence entre les sélecteurs suivants et donnez **un exemple de règle CSS** pour chacun :

* Sélecteur de type (ex. `p`)
* Sélecteur de classe (ex. `.important`)
* Sélecteur d’identifiant (ex. `#menu`)

**Zone de réponse 4 :**

```text
Sélecteur de type :
- Explication :
................................................................................
- Exemple de règle :
................................................................................

Sélecteur de classe :
- Explication :
................................................................................
- Exemple de règle :
................................................................................

Sélecteur d'identifiant :
- Explication :
................................................................................
- Exemple de règle :
................................................................................
```

---

### 5. Box model et types d’éléments (6 pts)

5.1. Nommez et décrivez rapidement les **quatre parties** du **CSS box model**.

**Zone de réponse 5.1 :**

```text
1.
................................................................................
2.
................................................................................
3.
................................................................................
4.
................................................................................
```

5.2. Donnez la différence entre un élément **block** et un élément **inline**, avec **deux exemples** de chaque type.

**Zone de réponse 5.2 :**

```text
Différence block / inline :
................................................................................
................................................................................

Exemples d'éléments block :
1) .............................................................................
2) .............................................................................

Exemples d'éléments inline :
1) .............................................................................
2) .............................................................................
```

---

## PARTIE 2 – Analyse de code HTML / CSS (30 points)

### 6. Analyse d’un extrait HTML (15 pts)

On vous donne le code suivant :

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Ma page</title>
  </head>
  <body>
    <h1 class="titre">Bienvenue sur mon site</h1>

    <p id="intro">Ce site présente mes projets et mon CV.</p>

    <div class="bloc">
      <h2>Projet 1</h2>
      <p>Application web en JavaScript.</p>
    </div>

    <div class="bloc important">
      <h2>Projet 2</h2>
      <p>Site vitrine responsive.</p>
    </div>

    <footer>
      <p>Contact : moi@example.com</p>
    </footer>
  </body>
</html>
```

6.1. (4 pts) Indiquez **toutes les balises sémantiques** utilisées (autres que `<div>` et `<span>`) et expliquez en une phrase leur rôle.

**Zone de réponse 6.1 :**

```text
Liste des balises sémantiques et rôle :
................................................................................
................................................................................
................................................................................
................................................................................
```

6.2. (4 pts) Expliquez la différence entre `class="bloc"` et `class="bloc important"` dans ce code.

**Zone de réponse 6.2 :**

```text
................................................................................
................................................................................
................................................................................
```

6.3. (3 pts) Proposez une amélioration sémantique (au moins une balise à changer ou à ajouter) et expliquez pourquoi.

**Zone de réponse 6.3 :**

```text
Proposition :
................................................................................
................................................................................

Justification :
................................................................................
................................................................................
```

6.4. (4 pts) Ajoutez dans un bloc de code HTML la balise manquante pour intégrer correctement une feuille de style externe `style.css`.

**Zone de réponse 6.4 :**

```html
<!-- Ajoutez ici la balise manquante dans le <head> -->
................................................................................
................................................................................
```

---

### 7. Analyse d’un extrait CSS (15 pts)

On vous donne le code CSS suivant :

```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

h1.titre {
  color: darkblue;
  text-align: center;
}

#intro {
  font-size: 18px;
  line-height: 1.5;
}

.bloc {
  border: 1px solid #ccc;
  padding: 15px;
  margin: 10px;
}

.bloc.important {
  background-color: #f5f5f5;
  border-color: #333;
}
```

7.1. (4 pts) Expliquez la différence entre le sélecteur `h1.titre` et le sélecteur `.bloc.important`.

**Zone de réponse 7.1 :**

```text
................................................................................
................................................................................
................................................................................
```

7.2. (4 pts) Décrivez précisément l’apparence visuelle d’un élément ayant la classe `bloc important` (bordure, arrière-plan, marges, etc.).

**Zone de réponse 7.2 :**

```text
................................................................................
................................................................................
................................................................................
```

7.3. (3 pts) Que se passe-t-il si on ajoute une nouvelle règle :

```css
#intro {
  color: red;
}
```

Expliquez l’effet sur l’élément concerné.

**Zone de réponse 7.3 :**

```text
................................................................................
................................................................................
................................................................................
```

7.4. (4 pts) Proposez une règle CSS pour que tous les éléments `<footer>` aient un texte centré, une taille de police plus petite, et un fond gris clair. Écrivez la règle complète.

**Zone de réponse 7.4 :**

```css
/* Votre règle CSS pour <footer> */
................................................................................
................................................................................
................................................................................
```

---

## PARTIE 3 – Développement pratique (40 points)

### 8. Mini page “Portfolio simple” (25 pts)

Vous devez écrire le **code HTML et CSS** pour une petite page “Portfolio simple”.

#### 8.1. Structure HTML (15 pts)

Écrivez le HTML complet suivant les consignes :

* La page contient :

  * Un `<header>` avec le titre : « Portfolio de [Votre Nom] »
  * Une barre de navigation `<nav>` avec **3 liens** : Accueil, Projets, Contact
  * Une section principale `<main>` qui contient :

    * Une section `<section>` avec un titre `<h2>` « À propos » et un paragraphe de description
    * Une section `<section>` « Projets » contenant **au moins 2 projets** présentés sous forme de blocs (par exemple `<div class="projet">`) avec un titre de projet et une phrase de description.
  * Un `<footer>` avec un texte de copyright (année + nom).

Contraintes :

* Le document doit être un **HTML5 valide** (doctype, `<html>`, `<head>`, `<body>`, etc.).
* Ajoutez au moins **une classe** et **un id** pertinents dans votre code (par exemple pour le bloc principal ou la nav).

**Zone de réponse 8.1 (HTML complet) :**

```html
<!-- Votre code HTML complet pour la page Portfolio -->
<!DOCTYPE html>
................................................................................
<html lang="fr">
................................................................................
<head>
................................................................................
</head>
<body>
................................................................................
................................................................................
</body>
</html>
```

---

#### 8.2. Mise en forme CSS (10 pts)

Écrivez le CSS pour :

* Donner une police lisible au body (par exemple `font-family: Arial, sans-serif;`)
* Mettre un fond légèrement gris au `<header>` et centrer le titre
* Afficher les liens de navigation horizontalement (sur une seule ligne) avec un espacement entre eux
* Mettre les blocs de projets (`.projet`) avec :

  * une bordure légère
  * un peu de marge entre chaque bloc
  * un padding interne
* Centrer le texte du `<footer>` et lui donner une taille de police plus petite

**Zone de réponse 8.2 (CSS) :**

```css
/* Votre code CSS pour la page Portfolio */
................................................................................
................................................................................
................................................................................
................................................................................
................................................................................
```

---

### 9. Question responsive (15 pts)

Vous souhaitez que votre page soit plus agréable sur mobile.

9.1. (5 pts) Expliquez en quelques phrases :

* ce qu’est le **responsive design**,
* et pourquoi il est important aujourd’hui.

**Zone de réponse 9.1 :**

```text
................................................................................
................................................................................
................................................................................
................................................................................
```

9.2. (5 pts) Écrivez une **règle CSS avec media query** pour que, lorsque la largeur de l’écran est inférieure ou égale à `600px`, la taille de la police du body soit réduite et la couleur de fond du header soit différente.

Exemple de squelette à compléter :

```css
@media (max-width: 600px) {
  /* Vos règles ici */
}
```

**Zone de réponse 9.2 :**

```css
@media (max-width: 600px) {
  ..............................................................................
  ..............................................................................
}
```

9.3. (5 pts) Donnez **deux autres techniques** (sans les coder complètement) qui permettent d’améliorer le responsive design (par exemple : utilisation de certaines unités, propriétés, ou comportements CSS).

**Zone de réponse 9.3 :**

```text
Technique 1 :
................................................................................
................................................................................

Technique 2 :
................................................................................
................................................................................
```

---

**Fin de l’examen**
Relisez vos réponses, vérifiez l’indentation et la lisibilité de votre code.


