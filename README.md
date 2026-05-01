# Groupe-N-3-Projet-Bloc-2-
Dépôt du groupe 3  pour le bloc 2 de L'académie de programmation 
# DevStart Agency — Site Web Officiel

> **Bloc 2 · Module 2 — Architecture Logicielle & Modularité**
> Académie de Programmation · IFRI L1 · Groupe 3

---

## 📌 Présentation du projet

**DevStart Agency** est une agence web fictive dont nous avons analysé et restructuré le code dans le cadre du Module 2.

L'objectif de ce module est de passer d'un code monolithique (tout dans un seul fichier CSS) à une **architecture modulaire** où chaque fichier a une seule responsabilité claire. Le design du site reste identique — seule l'organisation du code change.

---

## 🗂️ Structure des fichiers

```
devstart-agency/
│
├── index.html                  → Page d'accueil du site
│
├── styles/                     → Tous les fichiers CSS du projet
│   ├── base.css                → Reset CSS + variables globales (couleurs, polices)
│   ├── header.css              → Barre de navigation et logo
│   ├── hero.css                → Section d'accroche principale
│   ├── services.css            → Grille des cartes de services
│   ├── about.css               → Présentation de l'équipe
│   ├── testimonials.css        → Témoignages clients
│   ├── contact.css             → Formulaire de contact
│   ├── footer.css              → Pied de page
│   └── components.css          → Éléments réutilisables (boutons)
│
├── assets/                     → Ressources graphiques
│   ├── hero.png                → Image de la section hero
│   └── team.png                → Photo de l'équipe
│
└── README.md                   → Documentation du projet
```

---

## 🎨 Organisation des fichiers CSS

Chaque fichier CSS ne gère qu'**une seule partie** du site. C'est le principe de responsabilité unique appliqué au CSS.

| Fichier | Responsabilité |
|---|---|
| `base.css` | Reset CSS et variables globales de couleurs et polices |
| `header.css` | Mise en forme de la navigation et du logo |
| `hero.css` | Styles de la section d'accroche (titre, bouton CTA, image) |
| `services.css` | Grille et cartes des 4 services proposés |
| `about.css` | Layout et styles de la section présentation équipe |
| `testimonials.css` | Cartes de témoignages clients sur fond sombre |
| `contact.css` | Formulaire de contact (champs, bouton d'envoi) |
| `footer.css` | Pied de page avec liens et copyright |
| `components.css` | Classes réutilisables partagées entre sections (`.btn-primary`, `.btn-secondary`) |

> **Règle d'or :** si tu dois expliquer ce que fait un fichier et que ta réponse contient le mot *« et »*, c'est qu'il fait trop de choses.

---

## 🚀 Comment lancer le projet

Aucune installation requise. Il suffit d'ouvrir le fichier dans un navigateur :

```bash
# Ouvrir directement dans le navigateur
double-clic sur index.html

# Ou avec VS Code + extension Live Server
clic droit sur index.html → "Open with Live Server"
```

---

## 🌿 Branches GitHub

| Branche | Contenu |
|---|---|
| `main` | Code original du Module 1 — **ne pas modifier** |
| `module2` | Code réorganisé selon l'architecture modulaire |

Pour basculer sur la branche du Module 2 :

```bash
git checkout module2
```

---

## 👥 Équipe — Groupe 3

| Nom | Rôle |
|---|---|
| **Faridath GABA ISSIFOU** ⭐ | Chef de groupe |
| Mawoussi Sandrine AGBODJI | Rédactrice |
| N'DA Prielle Arifath | Analyse CSS|
| Fréjus ZANKPO | Architecte logiciel |
| Abdou-Hakim KARIM ISSAOU | Développeuret implémentation |
| Ivan Claudel Idjäm OGA | Corédacteur |

---

## 📄 Licence

Projet réalisé dans le cadre académique — Académie de Programmation · IFRI · 2026.
