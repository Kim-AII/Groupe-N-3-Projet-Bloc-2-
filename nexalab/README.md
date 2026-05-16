# NexaLab — Document d'Architecture

![HTML5](https://img.shields.io/badge/HTML5-sémantique-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-modulaire-1572B6?style=flat-square&logo=css3&logoColor=white)
![Responsive](https://img.shields.io/badge/Responsive-mobile%20·%20tablette%20·%20desktop-22d3ee?style=flat-square)
![Statut](https://img.shields.io/badge/Statut-En%20production-4f8ef7?style=flat-square)

> **Projet Intégrateur · Bloc 2 · Modules 3 & 4**  
> Académie de Programmation IFRI — Parcours L1  
> Groupe N°3 · 10 jours · Compétition inter-groupes

---

## Sommaire

1. [Présentation du projet et du client](#1-présentation-du-projet-et-du-client)
2. [Aperçu de la page](#2-aperçu-de-la-page)
3. [Arborescence du dépôt](#3-arborescence-du-dépôt)
4. [Architecture CSS modulaire](#4-architecture-css-modulaire)
5. [Charte graphique](#5-charte-graphique)
6. [Conventions de nommage](#6-conventions-de-nommage)
7. [Guide d'extensibilité](#7-guide-dextensibilité)
8. [Installation et lancement](#8-installation-et-lancement)
9. [Auteurs](#9-auteurs)

---

## 1. Présentation du projet et du client

### Contexte

**REBUILD** est le projet intégrateur du Bloc 2. L'objectif : concevoir et livrer, de zéro, la page d'accueil complète d'un client fictif — **NexaLab** — sous contraintes techniques strictes et en compétition avec cinq autres groupes.

Aucun JavaScript. Aucun framework. Aucun template. Tout est écrit à la main.

### Le client — NexaLab

> *"Fondé en 2018, NexaLab est un laboratoire d'innovation spécialisé dans le développement de solutions numériques pour les entreprises africaines ambitieuses. Notre mission : rendre la technologie de pointe accessible, utile et impactante."*

| Attribut | Détail |
| --- | --- |
| **Secteur** | Innovation technologique (IA · IoT · Data · Cybersécurité) |
| **Fondé en** | 2018 — présent dans 17 pays africains |
| **Audience cible** | Directeurs d'entreprise · Investisseurs · Jeunes talents tech |
| **Ton** | Confiant · Innovant · Accessible — on parle à des décideurs africains |
| **ADN visuel** | Sombre · Épuré · Technologique · Premium |
| **Objectif du site** | Convaincre en moins de 10 secondes |

### Périmètre technique

| Contrainte | Choix |
| --- | --- |
| Langages | HTML5 sémantique · CSS3 pur |
| JavaScript | Interdit |
| Frameworks CSS | Interdits |
| Mise en page | Flexbox (principal) · Grid (complémentaire) |
| Responsive | Mobile ≤ 768px · Tablette ≤ 1024px · Desktop |
| Versionnement | Git — branche `projet-integrateur` |

---

## 2. Aperçu de la page

La page d'accueil se compose de **9 sections obligatoires**, dans cet ordre :

| # | Section | Parti pris créatif |
| --- | --- | --- |
| 01 | **Header & Navigation** | Header fixe (`position: fixed`) avec `backdrop-filter: blur(12px)` et classe `.header--scrolled` déclenchée au scroll — navigation toujours accessible sur une page longue. |
| 02 | **Hero** | Vidéo plein écran en autoplay mute loop (`Nexlab-vid0.mp4`) avec overlay sombre — la technologie en mouvement dès la première seconde, avant toute lecture. |
| 03 | **À propos / Mission** | Layout 2 colonnes : texte engagé à gauche, `glass-container` avec grille de 4 cartes valeurs à droite — l'esthétique glassmorphism ancre NexaLab dans la modernité. |
| 04 | **Services / Expertises** | Bento-grid asymétrique CSS Grid : carte IA en vedette (`.service-card--featured`) flanquée de deux cartes secondaires et d'une carte wide — la hiérarchie visuelle traduit la spécialité principale du labo. |
| 05 | **Chiffres clés** | Fond image avec double overlay gradient + sparklines SVG inline décoratifs — 7 métriques crédibles (142 projets, 17 pays, 96 % satisfaction…) rendues mémorables par le contexte visuel fort. |
| 06 | **Équipe** | 4 vraies photos (`AR.jpeg`, `TH.jpeg`, `MS.jpeg`, `SA.jpeg`) avec overlay au hover révélant une citation — l'humain au cœur d'un laboratoire tech. |
| 07 | **Témoignages** | Même logique bento que les services (featured · secondary · wide) — cohérence architecturale assumée, 4 retours clients africains crédibles. |
| 08 | **Contact** | Formulaire 2 colonnes avec fond image (`.contact::before` en overlay) — inputs entièrement stylisés, `select` personnalisé, validation HTML5 native sans JS. |
| 09 | **Footer** | CSS Grid 4 colonnes (`2fr 1fr 1fr 1fr`), icônes réseaux sociaux en SVG local — structure institutionnelle claire, zéro dépendance externe pour les icônes. |

---

## 3. Arborescence du dépôt

```text
nexalab/
│
├── index.html                        ← Page unique — 9 sections · ~1 100 lignes
│
├── Styles/                           ← CSS découpé par section (1 fichier = 1 responsabilité)
│   ├── base.css                      ← Variables :root, reset, typo globale, utilitaires (.btn-primary, .container)
│   ├── header.css                    ← Header fixe, navigation, hamburger mobile, état --scrolled
│   ├── hero.css                      ← Section vidéo plein écran, badge, overlay, boutons
│   ├── about.css                     ← Layout 2 colonnes, glass-container, grille valeurs
│   ├── services.css                  ← Bento-grid services (featured · secondary · wide)
│   ├── stats.css                     ← Grilles de stats, sparklines, fond image, callout
│   ├── team.css                      ← Cartes membres, photo overlay hover, skill-tags
│   ├── testimonials.css              ← Cartes témoignages (même bento que services)
│   ├── contact.css                   ← Layout 2 colonnes, formulaire stylisé, fond image
│   └── footer.css                    ← Grid 4 colonnes, liens réseaux sociaux
│
└── assets/
    ├── fonts/
    │   ├── Grotesk/                  ← Space Grotesk Variable + DM Sans Variable (hébergés localement)
    │   │   ├── SpaceGrotesk-VariableFont_wght.ttf
    │   │   ├── DMSans-VariableFont_opsz,wght.ttf
    │   │   └── DMSans-Italic-VariableFont_opsz,wght.ttf
    │   └── Inter/                    ← Inter Tight Variable (hébergée localement)
    │       ├── InterTight-VariableFont_wght.ttf
    │       └── InterTight-Italic-VariableFont_wght.ttf
    └── images/
        ├── logo.png                  ← Logo officiel NexaLab
        ├── Nexlab-vid0.mp4           ← Vidéo hero (autoplay · muted · loop)
        ├── about.jpg                 ← Fond section Stats + Contact (overlay gradient)
        ├── AR.jpeg                   ← Photo ALLADAGBE Romano (équipe)
        ├── TH.jpeg                   ← Photo TOHOU Éméric (équipe)
        ├── MS.jpeg                   ← Photo MBAMBA Shanel (équipe)
        ├── SA.jpeg                   ← Photo SOZA Alma (équipe)
        ├── stats-bg.svg              ← SVG décoratif de fond section stats
        ├── nexalab_stats_bg.svg      ← Variante SVG fond stats
        ├── Contact-background.png    ← Fond section contact
        └── square-*.svg             ← Icônes réseaux sociaux (facebook, github, linkedin, x, youtube)
```

> **Pourquoi ce découpage ?**  
> Chaque fichier CSS correspond à exactement une section HTML. Cela permet à chaque membre du groupe de travailler en parallèle sans conflits de merge Git, et simplifie la maintenance : modifier l'apparence d'une section n'ouvre qu'un seul fichier.
---

## 4. Architecture CSS modulaire

| Fichier CSS | Responsabilité | Éléments HTML gérés |
| --- | --- | --- |
| `base.css` | Fondation commune — chargé en premier | `:root` (variables), `*` (reset), `body`, `h1–h4`, `p`, `.container`, `.btn-primary`, `.btn-outline`, `.btn-secondary`, `.section-label`, `.section-title` |
| `header.css` | En-tête fixe et navigation principale | `.header`, `.header--scrolled`, `.header__inner`, `.header__logo`, `.header__logo-mark`, `.header__logo-text`, `.header__nav`, `.header__nav-list`, `.header__nav-link`, `.header__cta`, `.header__hamburger`, `.header__menu-toggle` |
| `hero.css` | Section héro plein écran avec vidéo | `.hero`, `.hero__video`, `.hero__overlay`, `.hero__content`, `.hero__badge`, `.dot`, `.hero__title`, `.hero__text`, `.hero__buttons` |
| `about.css` | Section mission et valeurs | `.about-section`, `.content-left`, `.content-right`, `.glass-container`, `.grid-values`, `.value-card`, `.features-list`, `.highlight`, `.subtitle`, `.number` |
| `services.css` | Bento-grid des expertises | `.services`, `.services__header`, `.services__label`, `.services__title`, `.services__title--accent`, `.services__subtitle`, `.services__grid`, `.services__column`, `.service-card`, `.service-card--featured`, `.service-card--secondary`, `.service-card--wide`, `.service-card__inner`, `.service-card__top`, `.service-card__icon`, `.service-card__tag`, `.service-card__body`, `.service-card__name`, `.service-card__desc`, `.service-card__features`, `.service-card__feature`, `.service-card__feature-dot`, `.service-card__cta`, `.service-card__glow`, `.service-card__stripe` |
| `stats.css` | Chiffres clés et callout | `.stats`, `.stats__container`, `.stats__header`, `.stats__label`, `.stats__title`, `.stats__title--accent`, `.stats__subtitle`, `.stats__grid`, `.stats__grid--primary`, `.stats__grid--secondary`, `.stat-card`, `.stat-card--highlight`, `.stat-card__inner`, `.stat-card__value-row`, `.stat-card__number`, `.stat-card__unit`, `.stat-card__label`, `.stat-card__detail`, `.stat-card__sparkline`, `.stats__callout`, `.stats__callout-author`, `.stats__bg-line` |
| `team.css` | Cartes membres de l'équipe | `.team-section`, `.section-header`, `.section-tag`, `.section-title`, `.section-subtitle`, `.member-card`, `.card-accent-bar`, `.card-photo-wrap`, `.photo-placeholder`, `.card-overlay`, `.member-quote`, `.card-body`, `.role-badge`, `.member-name`, `.card-divider`, `.member-role`, `.skill-tags`, `.skill-tag`, `.social-links`, `.social-link` |
| `testimonials.css` | Cartes témoignages clients | `.testimonials`, `.testi-card`, `.testi-card--featured`, `.testi-card--secondary`, `.testi-card--wide`, `.testi-card__inner`, `.testi-card__tag`, `.testi-card__stars`, `.testi-card__text`, `.testi-card__quote-icon`, `.testi-card__author`, `.testi-card__author--wide`, `.testi-card__avatar`, `.testi-card__avatar--lg`, `.testi-card__author-info`, `.testi-card__name`, `.testi-card__role`, `.testi-card__glow`, `.testi-card__stripe`, `.testi-card__wide-content` |
| `contact.css` | Formulaire de contact | `.contact`, `.contact__inner`, `.contact__info`, `.contact__title`, `.contact__text`, `.contact__details`, `.contact__detail`, `.contact__detail-icon`, `.contact__detail-label`, `.contact__detail-value`, `.contact__form`, `.form__row`, `.form__group`, `.form__label`, `.form__input`, `.form__select`, `.form__textarea`, `.form__submit` |
| `footer.css` | Pied de page institutionnel | `.footer`, `.footer-brand`, `.footer-title`, `.footer-descrition`, `.footer-social`, `.footer-column`, `.footer-heading`, `.footer-link`, `.footer-copy`, `.social-link` |

**Ordre d'import dans `index.html`** — respecter cet ordre est obligatoire (`base.css` en premier, les autres en cascade) :

```html
<link rel="stylesheet" href="styles/base.css" />
<link rel="stylesheet" href="styles/header.css" />
<link rel="stylesheet" href="styles/hero.css" />
<link rel="stylesheet" href="styles/about.css" />
<link rel="stylesheet" href="styles/services.css" />
<link rel="stylesheet" href="styles/stats.css" />
<link rel="stylesheet" href="styles/testimonials.css" />
<link rel="stylesheet" href="styles/team.css" />
<link rel="stylesheet" href="styles/footer.css" />
<link rel="stylesheet" href="styles/contact.css" />
```

---

## 5. Charte graphique

### Palette de couleurs

Toutes les couleurs sont déclarées dans `base.css` — aucune valeur hexadécimale brute ne figure dans les fichiers de section.

| Variable CSS | Valeur | Rôle |
| --- | --- | --- |
| `--color-bg` | `#0a0c10` | Fond principal — noir profond, ancre l'identité tech |
| `--color-surface` | `#111318` | Fond des cartes et composants |
| `--color-surface-alt` | `#161a24` | Fond secondaire — photos, tags, zones imbriquées |
| `--color-border` | `#1e2230` | Bordures et séparateurs |
| `--color-accent` | `#4f8ef7` | **Bleu accent principal** — CTAs, liens actifs, highlights |
| `--color-accent-dark` | `#2563c4` | Bleu foncé — états hover des boutons primaires |
| `--color-secondary` | `#6c63ff` | Violet secondaire — dégradés, badges |
| `--color-text` | `#e2e8f0` | Texte principal |
| `--color-text-muted` | `#64748b` | Texte discret — métadonnées, placeholders |
| `--color-text-light` | `#94a3b8` | Texte intermédiaire — descriptions longues |
| `--color-white` | `#ffffff` | Titres (`h1–h6`) et textes sur fond coloré |
| `--color-danger` | `#ff6b6b` | États d'erreur |
| `--color-success` | `#22d3ee` | États de succès, confirmations |

> **Justification de la palette :** Le fond `#0a0c10` (quasi-noir) crée un environnement premium qui fait ressortir l'accent bleu `#4f8ef7`. Ce bleu tech est universellement associé à la confiance et à l'innovation numérique — choix calibré pour l'audience cible (décideurs, investisseurs). Le violet `#6c63ff` en secondaire apporte de la profondeur sans rompre la cohérence.

### Typographies

| Variable | Police | Format | Rôle |
| --- | --- | --- | --- |
| `--font-heading` | **Space Grotesk** | Variable font (wght 300–700) | Titres `h1–h6`, labels, boutons — géométrique et moderne |
| `--font-body` | **Inter** | Variable font | Corps de texte, paragraphes, métadonnées |
| — | **DM Sans** | Variable font (hébergée localement) | Utilisée dans hero et about comme alternative de lisibilité |
| — | **Inter Tight** | Variable font (hébergée localement) | Variante condensée pour les espaces contraints |

Les fonts **DM Sans** et **Inter Tight** sont hébergées localement dans `assets/fonts/` — le site est lisible hors connexion internet.

### Décisions visuelles

| Décision | Justification |
| --- | --- |
| Vidéo hero autoplay mute | Convaincre en < 10 secondes sans attente de chargement — la technologie est visible immédiatement |
| `backdrop-filter: blur(12px)` sur le header | Navigation lisible quelle que soit la section visible — esthétique glassmorphism premium |
| Bento-grid asymétrique (services & témoignages) | La carte featured impose une hiérarchie : l'IA est le service phare, le reste suit |
| SVG sparklines dans les stats | Les données chiffrées (142 projets, 96 % satisfaction) gagnent en crédibilité avec une courbe de tendance visuelle |
| Fond image + double overlay gradient (stats & contact) | Profondeur et chaleur humaine sans alourdir la performance — une seule image réutilisée sur deux sections |
| Photos réelles pour l'équipe | Humaniser un laboratoire tech africain — la confiance se bâtit sur des visages, pas des avatars |

### Échelle typographique (`base.css`)

```css
--text-xs:   0.75rem;   /* 12px — labels, badges        */
--text-sm:   0.875rem;  /* 14px — boutons, nav          */
--text-base: 1rem;      /* 16px — corps de texte        */
--text-lg:   1.125rem;  /* 18px — sous-titres proches   */
--text-xl:   1.25rem;   /* 20px — h4                    */
--text-2xl:  1.5rem;    /* 24px — h3                    */
--text-3xl:  1.875rem;  /* 30px — h2 mobile             */
--text-4xl:  2.25rem;   /* 36px — h2 desktop            */
--text-5xl:  3rem;      /* 48px — h1 desktop            */
--text-6xl:  3.75rem;   /* 60px — hero title max        */
```

---

## 6. Conventions de nommage

Le projet applique une **méthodologie BEM (Block Element Modifier)** pour les sections principales, avec quelques variantes fonctionnelles selon les composants.

### Logique BEM

```text
.block                  → Composant autonome
.block__element         → Partie d'un composant
.block--modifier        → Variante d'état ou de style
```

### 3 exemples concrets tirés du code

**Exemple 1 — Section Services (`services.css`)**

```css
/* Block */
.service-card { ... }

/* Elements */
.service-card__inner { padding: clamp(var(--space-lg), 3vw, var(--space-xl)); }
.service-card__icon  { width: 52px; height: 52px; }
.service-card__name  { font-family: var(--font-heading); font-size: 1.2rem; }

/* Modifiers */
.service-card--featured  { /* carte IA mise en avant, taille agrandie */ }
.service-card--secondary { flex: 1; }
.service-card--wide      { grid-column: 1 / -1; /* pleine largeur */ }
```

**Exemple 2 — Header navigation (`header.css`)**

```css
/* Block */
.header { position: fixed; backdrop-filter: blur(12px); }

/* Elements */
.header__inner      { display: flex; justify-content: space-between; }
.header__logo       { display: flex; align-items: center; gap: var(--space-xs); }
.header__logo-mark  { /* carré accent avec initiale */ }
.header__nav-link   { color: var(--color-text-light); }

/* Modifier — état au scroll */
.header--scrolled   { background-color: rgba(10, 12, 16, 0.95); }
```

**Exemple 3 — Témoignages (`testimonials.css`)**

```css
/* Block */
.testi-card { ... }

/* Elements */
.testi-card__inner        { display: flex; flex-direction: column; }
.testi-card__text         { font-style: italic; }
.testi-card__author       { display: flex; align-items: center; }
.testi-card__author-info  { display: flex; flex-direction: column; }
.testi-card__name         { font-weight: 600; }
.testi-card__avatar--lg   { /* avatar agrandi pour la carte wide */ }

/* Modifiers */
.testi-card--featured     { /* témoignage principal, plus grand */  }
.testi-card--secondary    { flex: 1; }
.testi-card--wide         { grid-column: 1 / -1; flex-direction: row; }
.testi-card__author--wide { /* layout horizontal sur carte wide */ }
```

> **Note de cohérence :** La section `about` utilise une convention fonctionnelle (`.content-left`, `.glass-container`, `.value-card`) plutôt que BEM strict — choix assumé pour un composant à usage unique. Les sections `services`, `stats`, `team`, `testimonials` et `contact` suivent le BEM.

---

## 7. Guide d'extensibilité

### Ajouter une nouvelle section

1.Créer `styles/ma-section.css` avec l'en-tête standard :
 ```css
   /* ============================================================
      ma-section.css — NexaLab
      Responsabilité : [description]
      Auteur         : [Prénom NOM]
   ============================================================ */
   ```

2.L'importer dans `index.html` **avant** `styles/footer.css` :
```html
   <link rel="stylesheet" href="styles/ma-section.css" />
   ```

3. Ajouter la balise sémantique dans `index.html` après la section précédente :
   ```html
   <section class="ma-section" id="ma-section" aria-labelledby="ma-section-heading">
     <div class="container">
       <h2 id="ma-section-heading">...</h2>
     </div>
   </section>
   ```

4.Ajouter le lien dans la navigation (`.header__nav-list`) et dans le footer.
5. Utiliser uniquement les variables de `base.css` — ne jamais écrire de valeurs hexadécimales directement.

### Ajouter une nouvelle page (ex. `blog.html`)

1. Dupliquer `index.html` → `blog.html`
2. Conserver les imports `base.css`, `header.css`, `footer.css` — ils sont communs à toutes les pages
3. Supprimer les imports des sections non pertinentes
4. Créer `styles/blog.css` pour le contenu spécifique
5. L'importer après `header.css` et avant `footer.css`

### Ajouter un nouveau composant réutilisable (ex. une card générique)

1. Nommer la classe selon BEM : `.card`, `.card__title`, `.card__body`, `.card--highlight`
2. Déclarer le composant dans le fichier CSS de la section qui l'utilise en premier
3. S'il est partagé par plusieurs sections : le déplacer dans `base.css`, section `5. UTILITAIRES`

### Modifier une couleur globalement

Toutes les couleurs passent par les variables de `base.css` :
```css
/* Changer l'accent principal — impacte tous les boutons, liens, highlights */
:root {
  --color-accent: #00d4ff; /* ancienne valeur : #4f8ef7 */
}
```

---

## 8. Installation et lancement

### Prérequis

- Un navigateur moderne (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Aucune installation de dépendances — le projet est 100 % statique

### Cloner le dépôt

```bash
git clone https://github.com/[organisation]/nexalab.git
cd nexalab
git checkout projet-integrateur
```

### Ouvrir localement

**Option 1 — Ouverture directe (simple)**

```bash
# Ouvrir index.html dans le navigateur par défaut
open nexalab/index.html          # macOS
start nexalab/index.html         # Windows
xdg-open nexalab/index.html      # Linux
```

**Option 2 — Serveur local recommandé (évite les restrictions CORS sur les fonts locales)**
```bash
# Avec Python (installé par défaut sur macOS/Linux)
cd nexalab
python3 -m http.server 8080
# Ouvrir http://localhost:8080 dans le navigateur
```

```bash
# Avec l'extension VS Code "Live Server"
# Clic droit sur index.html → "Open with Live Server"
```

### Structure après clonage

```
nexalab/
├── index.html     ← Point d'entrée unique
├── Styles/        ← 10 fichiers CSS (à renommer en styles/ sur Linux/macOS)
└── assets/        ← Fonts, images, vidéo, icônes SVG
```bash
mv nexalab/Styles nexalab/styles
```

---

## 9. Auteurs

Projet réalisé par le **Groupe N°3** de la promotion L1 — Académie de Programmation IFRI.

| Membre | Rôle dans le projet | Sections / Fichiers |
| --- | --- |
| **Faridath GABA ISSIFOU** | Contenu technique |  · `Header.css` `footer.css` · snippet HTML services & stats |
| **Mawoussi Sandrine AGBODJI** | Architecture & Base | `contact.css` ·  structure `index.html` |
| **N'DA Prielle Arifath** | Design & Hero | `team.css`· assets visuels |
| **Fréjus ZANKPO** | Contenu & Équipe | `testimonals.css` · · contenu rédactionnel |
| **Abdou-Hakim KARIM ISSAOU** | Livraison & Contact | `services.css` · `stats.css` · documentation README |
| **Ivan Claudel Idjäm OGA** | Livraison & Contact | `hero.css` · `about.css` · documentation README |
---

*Document d'architecture rédigé dans le cadre du Projet Intégrateur · Bloc 2 · Académie de Programmation IFRI — L1 · Mai 2026*
