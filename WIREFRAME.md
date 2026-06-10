# BumBum V2 — Wireframe Ultra Détaillé
## Page produit pour A/B test sur ericfavrestore.sn

**Objectif** : Remplacer la page produit actuelle de BumBum pour augmenter le taux de conversion (page vue → achat). Cette page doit être intégrée dans WooCommerce comme template de page produit.

**Cible** : Femmes 20-45 ans, Sénégal, mobile-first (98% mobile).

**Fichier de référence** : `bumbum-v2-pro.html` dans ce même dossier.
**Assets** : Voir `ASSETS.md` pour toutes les URLs d'images.

---

## CONFIGURATION GLOBALE

### Couleurs (variables CSS)
```css
--orange: #E8651A        /* Primaire — CTA, accents, badges */
--orange-dark: #C85A15   /* Hover état boutons */
--gold: #C8860A          /* Accents premium, prix */
--cream: #FFF5EC         /* Fonds de section alternés */
--dark: #1A1A18          /* Texte principal */
--white: #FFFFFF         /* Fonds principaux */
--gray-mid: #666666      /* Texte secondaire (4.5:1 vérifié) */
--gray-light: #F5F5F5    /* Fonds subtils */
```

### Typographie
```css
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;400;500;600;700&family=Rubik:wght@400;500;600;700;800;900&display=swap');

/* Titres : Rubik 700-900 */
/* Corps : Nunito Sans 400 */
/* Labels/badges : Nunito Sans 600 */
```

### Espacement (grille 8px)
```
8px | 16px | 24px | 32px | 40px | 48px | 56px | 64px
```
- Entre sections majeures : 64px
- Entre sous-sections : 32px
- Padding cartes : 24px
- Gap composants : 16px

### Breakpoints
- Mobile : < 768px (design principal)
- Tablet : 768px - 1024px
- Desktop : > 1024px
- Container max-width : 1100px

---

## SECTION 0 — URGENCY BAR (sticky top)

**Position** : Fixe en haut de page, z-index 100
**Fond** : `--dark` (#1A1A18)
**Hauteur** : ~40px

**Contenu** :
```
🔥 OFFRE LIMITÉE — Livraison gratuite pour le programme 84 jours [HH:MM:SS]
```

**Détails** :
- "🔥 OFFRE LIMITÉE" en `--orange`
- Texte principal en blanc
- Timer countdown en badge orange (Rubik 700, fond `--orange`, padding 2px 8px, border-radius 4px)
- Le timer se reset toutes les 24h (stocké en localStorage)
- Police : Nunito Sans 600, 0.85rem

---

## SECTION 1 — HERO (above the fold)

**Fond** : Blanc
**Layout mobile** : Image en haut (pleine largeur), infos en dessous
**Layout desktop** : 2 colonnes 50/50

### Colonne gauche — Image
- **Image** : `hero-new.png`
- Border-radius : 20px
- Gradient overlay subtil en bas pour lisibilité texte si nécessaire
- loading="eager" (above the fold)

### Colonne droite — Infos produit

#### 1. Nom produit
```html
<h1>BUM BUM Push-Up</h1>
```
- Rubik 900, 2.6rem mobile / 3rem desktop
- Couleur : `--dark`

#### 2. Sous-titre
```
Gel Volumateur Fessier
```
- Nunito Sans 500, 1.1rem
- Couleur : `--gray-mid`

#### 3. Rating + badge
```
★★★★★ (47 avis)    🇫🇷 Fabriqué en France
```
- 5 étoiles SVG individuelles (remplies, couleur #F5A623)
- "(47 avis)" en lien, Nunito Sans 400, 0.85rem
- Drapeau français en SVG (3 bandes bleu/blanc/rouge)
- "Fabriqué en France" Nunito Sans 500, 0.85rem

#### 4. Stat principale
```
+50% de galbe prouvé en 84 jours
Testé sur 81 femmes en laboratoire
```
- Ligne 1 : Rubik 700, 1.1rem, `--dark`
- Ligne 2 : Nunito Sans 400, 0.85rem, `--gray-mid`
- Fond : `--cream`, padding 12px 16px, border-radius 8px, border-left 3px `--orange`

#### 5. Sélecteur de paliers
3 options radio verticales :

**Option 1 — 1 tube**
```
○ 1 tube                                    18 000 CFA
  Découverte
```

**Option 2 — 2 tubes**
```
○ 2 tubes  [-5% sur le 2e]                  34 200 CFA
  Offre duo
```
- Badge "-5% sur le 2e" : fond `--gold`, texte blanc, 0.65rem, uppercase

**Option 3 — 3 tubes (PRÉ-SÉLECTIONNÉ)**
```
● 3 tubes  [Livraison gratuite]              54 000 CFA
  Programme 84 jours complet              [Recommandé]
```
- Badge "Livraison gratuite" : fond #2E7D32 (vert), texte blanc
- Badge "Recommandé" : position absolute top -10px right 12px, fond `--orange`, texte blanc, border-radius 10px

**Style des options** :
- Border : 2px solid #E0E0E0, border-radius 12px
- Sélectionnée : border `--orange`, fond `--cream`
- Radio : cercle 20px, inner dot 10px `--orange` quand selected
- Nom : Rubik 700, 0.95rem
- Description : Nunito Sans 400, 0.8rem, `--gray-mid`
- Prix : Rubik 800, 1.05rem, `--orange`, aligné à droite

**JavaScript** : Au clic sur une option, mettre à jour :
- Le prix dans le bouton CTA hero
- Le prix dans le sticky bar en bas
- Le prix dans le CTA final

#### 6. Bouton CTA
```html
<a class="btn-primary">AJOUTER AU PANIER — 54 000 CFA</a>
```
- Fond : `--orange`, hover `--orange-dark`
- Texte : blanc, Rubik 700, 1rem
- Padding : 16px 32px, min-height 48px
- Border-radius : 12px
- Width : 100%
- Active : transform scale(0.97)
- Transition : 200ms ease-out

#### 7. Moyens de paiement
```html
<img src="https://www.ericfavrestore.sn/wp-content/uploads/2025/10/payments-.png" alt="Moyens de paiement" height="44px">
```

#### 8. Trust points (3 lignes)
```
✓ Livraison Dakar 24-48h
✓ Disponible en pharmacie
✓ Paiement à la livraison
```
- Checkmark : SVG vert (#2E7D32), 12px
- Texte : Nunito Sans 500, 0.85rem
- Gap entre lignes : 8px

---

## SECTION 2 — TRUST BAR

**Fond** : `--cream`
**Padding** : 16px

**Layout** : 4 colonnes en grille (2×2 sur mobile, 4×1 sur desktop)

| Icône SVG | Texte |
|---|---|
| Microscope (orange) | Testé cliniquement |
| Feuille (orange) | 95% naturel |
| Drapeau FR (tricolore) | Fabriqué en France |
| Bâtiment (orange) | En pharmacie |

- Icônes : SVG inline stroke-based, 20px, couleur `--orange`
- Texte : Nunito Sans 600, 0.8rem, `--dark`
- Chaque item centré, padding 12px
- Hover : background blanc, translateY(-2px), transition 200ms

---

## SECTION 3 — RÉSULTATS

**Fond** : Blanc
**Padding** : 64px 0

### Titre
```
Des résultats prouvés, pas des promesses.
```
Rubik 800, 1.6rem, centré

### 3 stat cards (grille 3 colonnes, stack sur mobile)
```
[+50%]         [+13,2%]        [+6,2%]
de galbe       de fermeté      d'élasticité
```
- Chiffre : Rubik 900, 2.5rem, `--orange`
- Label : Nunito Sans 400, 0.85rem, `--gray-mid`
- Card : fond `--cream`, padding 24px, border-radius 12px, text-align center

### Preuve scientifique (sous les cards)
```
📊 Étude clinique sur 81 femmes pendant 84 jours — Résultats mesurés par imagerie 3D.
```
- Icône chart SVG
- Texte : Nunito Sans 400, 0.9rem, `--gray-mid`
- Centré

### Image packshot
- **Image** : `plage-secret.png`
- max-width : 280px, centré
- Border-radius : 20px
- loading="lazy"

---

## SECTION 4 — AVANT / APRÈS

**Fond** : Blanc
**Padding** : 0 0 64px

**Layout** : 2 colonnes côte à côte, gap 8px
- Gauche : `jour1.png` (Jour 1)
- Droite : `jour84.png` (Jour 84)
- Border-radius : 12px sur les bords extérieurs
- loading="lazy"

---

## SECTION 5 — MODE D'EMPLOI

**Fond** : `--cream`
**Padding** : 64px 0

### Titre
```
3 étapes. 2 minutes. Matin et soir.
```
Rubik 800, 1.6rem, centré

### Image tutoriel
- **Image** : `photo-02.jpg` (grille 4 cases : titre + 3 étapes)
- Pleine largeur container
- Border-radius : 20px
- loading="lazy"

### 3 étapes texte (sous l'image, grille 3 colonnes)
```
Étape 1              Étape 2              Étape 3
Appliquer une        Masser de bas        Laisser agir —
noisette matin       en haut pendant      l'effet chauffant
et soir              2 minutes            est normal
```
- Numéro : Rubik 700, `--orange`
- Texte : Nunito Sans 400, 0.85rem

---

## SECTION 6 — LIFESTYLE BANNER

**Image** : `magnific-05.jpg` (femme plage golden hour)
**Pleine largeur**, hauteur 300px mobile / 400px desktop
**Object-fit** : cover
**Overlay** : gradient noir semi-transparent en bas
**Texte overlay** :
```
Cet été, sois fière de tes courbes.
```
- Rubik 800, 1.6rem, blanc, text-shadow

---

## SECTION 7 — TABLEAU COMPARATIF

**Fond** : Blanc
**Padding** : 64px 0

### Titre
```
Pourquoi BumBum est différent.
```

### Tableau
| Critère | Artisanaux | Importés | BumBum |
|---|---|---|---|
| Efficacité prouvée | ✗ | ✗ | ✓ |
| Fabriqué en France | ✗ | ✗ | ✓ |
| 95% naturel certifié | ✗ | ✗ | ✓ |
| Sans risque cutané | ✗ | ✗ | ✓ |
| Disponible en pharmacie | ✗ | ✗ | ✓ |
| Étude clinique | ✗ | ✗ | ✓ |

- ✓ : SVG checkmark vert
- ✗ : SVG cross rouge/gris
- Colonne BumBum : fond `--cream`, font-weight 700
- Lignes alternées pour lisibilité
- Header : fond `--dark`, texte blanc

---

## SECTION 8 — AVIS CLIENTS

**Fond** : `--cream`
**Padding** : 64px 0

### Titre
```
Ce qu'elles en disent.
```

### 5 cartes avis (scroll horizontal sur mobile, grille sur desktop)

Chaque carte :
```
[Avatar initiales]  Nom Prénom — Ville
★★★★★
"Texte de l'avis..."
Vérifié ✓
```

**Avis** :
1. Aïssatou D. — Dakar : "J'ai vu la différence après 3 semaines. Mon jean me va enfin comme je veux."
2. Fatou S. — Thiès : "Mon mari a remarqué avant moi 😂 Je recommande à 100%."
3. Mariama N. — Dakar : "Enfin un produit qui tient ses promesses. Et l'odeur est top."
4. Khady B. — Mbour : "Je l'utilise depuis 2 mois, les résultats sont réels. Merci BumBum !"
5. Ndèye M. — Dakar : "J'avais tout essayé. BumBum est le seul qui a vraiment marché."

- Avatar : cercle 40px, fond `--orange`, initiales en blanc Rubik 700
- Nom : Nunito Sans 600, 0.9rem
- Ville : Nunito Sans 400, 0.8rem, `--gray-mid`
- Étoiles : 5 SVG dorés
- Texte avis : Nunito Sans 400, 0.9rem, italique
- "Vérifié ✓" : Nunito Sans 600, 0.75rem, `--orange`
- Carte : fond blanc, padding 24px, border-radius 12px, shadow

---

## SECTION 9 — 3 PROFILS D'USAGE

**Fond** : Blanc
**Padding** : 64px 0

### Titre
```
Pour qui ?
```

### 3 cartes (stack mobile, grille desktop)

**Profil 1 — Post-injection**
- Icône : SVG médical (orange)
- Titre : "Post-injection" — Rubik 700
- Texte : "Tu as fait du lipofilling ? BumBum maintient et prolonge tes résultats."

**Profil 2 — Complément sport**
- Icône : SVG haltère (orange)
- Titre : "Complément sport"
- Texte : "Tu fais des squats ? BumBum amplifie et accélère les résultats."

**Profil 3 — Solo, sans contrainte**
- Icône : SVG wellness (orange)
- Titre : "Solo, sans contrainte"
- Texte : "Pas de sport, pas d'injection. Juste BumBum, 2 fois par jour."

- Cartes : fond `--cream`, padding 24px, border-radius 12px
- Icônes : SVG inline stroke-based, 32px

---

## SECTION 10 — EXPERTISE LABORATOIRE

**Fond** : `--dark` (#1A1A18)
**Padding** : 64px 0
**Texte** : Blanc

### Structure
```
[INNOVER POUR VIVRE MIEUX]           ← gold, uppercase, letter-spacing 2px
Expert en Bien-Être & Santé           ← Rubik 800, 1.8rem, blanc
depuis 30 ans                         ← Rubik 800, 1.8rem, gold

[30 ans d'expertise] [Phytonutrition]  ← badges glass

Paragraphe descriptif StarPharm        ← Nunito Sans, 0.9rem, blanc 60%

[NOS INNOVATIONS BREVETÉES]            ← gold, uppercase

┌──────────────┬──────────────┐
│  SCULP-UP™   │ FENUGREXTINE™│        ← grille 2×2
├──────────────┼──────────────┤
│  CARBONÉTOL™ │ LITHOSIUM C™ │
└──────────────┴──────────────┘
```

- Badges innovations : fond rgba(255,255,255,0.06), border rgba(255,255,255,0.1), padding 12px, border-radius 8px, Rubik 700, 0.85rem
- Logo StarPharm : à intégrer quand URL WordPress disponible

---

## SECTION 11 — INGRÉDIENTS

**Fond** : Blanc
**Padding** : 64px 0

### Titre
```
Ce qu'il y a dedans.
```

### Image ingrédients
- **Image** : `freepik-01.jpg`
- Border-radius : 20px

### 4 cartes ingrédients
```
🌿 Sculp-UP™           🌿 Beurre de Karité
Actif breveté qui       Nourrit et hydrate
cible les adipocytes    la peau en profondeur

🌿 Baies Rouges        🌿 Calendula
Antioxydants pour       Apaise et protège
la fermeté              la peau
```

### Badges certifications
```
[ISO 16128] [CPNP] [Sans paraben]
```

---

## SECTION 12 — PHARMACIE

**Fond** : `--cream`
**Padding** : 64px 0

- **Image** : `produit-08.jpg` (produit sur comptoir pharmacie avec badges)
- Border-radius : 20px
- Centré, max-width 500px

---

## SECTION 13 — FAQ ACCORDION

**Fond** : Blanc
**Padding** : 64px 0

### Titre
```
Questions fréquentes
```

### 5 questions (élément `<details>/<summary>` natif)

1. **Combien de temps pour voir des résultats ?**
   → Premières semaines pour les premiers signes. Résultats optimaux à 84 jours d'utilisation régulière.

2. **C'est sans danger ?**
   → Oui. Fabriqué en France, notifié sur le portail européen CPNP, évaluation toxicologique complète. 95% d'ingrédients d'origine naturelle.

3. **Ça marche vraiment ?**
   → +50% de galbe prouvé en laboratoire sur 81 femmes pendant 84 jours. Ce ne sont pas des promesses marketing, ce sont des résultats mesurés.

4. **Comment commander ?**
   → Sur ce site (livraison Dakar 24-48h, paiement à la livraison) ou en pharmacie au Sénégal.

5. **L'effet chauffant est normal ?**
   → Oui, c'est le signe que l'actif Sculp-UP™ pénètre. Il favorise l'efficacité du gel.

**Style** :
- Summary : Rubik 600, 1rem, min-height 48px, cursor pointer
- Chevron SVG qui tourne à 180° quand ouvert
- Contenu : Nunito Sans 400, 0.9rem, padding 0 0 16px
- Transition hauteur : CSS grid trick (grid-template-rows 0fr → 1fr, 200ms)
- Séparateur : border-bottom 1px solid #E0E0E0

---

## SECTION 14 — CTA FINAL

**Fond** : `--cream`
**Padding** : 64px 0
**Centré**

```
Prête à essayer ?

54 000 CFA
Programme 3 tubes — Livraison gratuite

[COMMANDER MAINTENANT]

[Image moyens de paiement]
```

- Titre : Rubik 800, 1.6rem
- Prix : Rubik 900, 2rem, `--orange`
- Sous-texte : Nunito Sans 400, 0.85rem, `--gray-mid`
- Bouton : identique au hero CTA
- Paiements : image WordPress, height 40px, opacity 0.8

---

## SECTION 15 — STICKY BOTTOM BAR (mobile only)

**Position** : fixed bottom 0, z-index 1000
**Visible** : uniquement quand le hero CTA a scrollé hors de vue (IntersectionObserver)
**Masqué** : sur desktop (min-width 1024px)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BUM BUM Push-Up  |  54 000 CFA  |  [COMMANDER]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

- Fond : rgba(255,255,255,0.95) + backdrop-filter blur(12px)
- Padding : 12px 16px + env(safe-area-inset-bottom)
- Nom : Rubik 700, 0.8rem
- Prix : Rubik 800, 0.9rem, `--orange`
- Bouton : fond `--orange`, Rubik 700, blanc, border-radius 8px, min-height 40px
- Shadow : 0 -2px 16px rgba(0,0,0,0.1)
- Apparition : opacity 0→1 + translateY(100%→0), 200ms ease-out

---

## SECTION 16 — BOUTON WHATSAPP FLOTTANT

**Position** : fixed, bottom 80px (au-dessus du sticky bar), right 16px
**Z-index** : 999

- Cercle 56px, fond #25D366
- Icône WhatsApp SVG blanc
- Shadow : 0 4px 16px rgba(0,0,0,0.2)
- Hover : scale(1.1)
- Active : scale(0.95)
- Lien : `https://wa.me/221XXXXXXXX` (à remplacer par le vrai numéro)

---

## FOOTER

```
BumBum Push-Up — StarPharm × DistriPRO
Disponible en pharmacie et sur ericfavrestore.sn
```
- Fond : `--dark`
- Texte : blanc 60%, Nunito Sans, 0.8rem
- Padding : 32px

---

## ACCESSIBILITÉ & PERFORMANCE

### Obligatoire
- `prefers-reduced-motion` : désactive toutes les animations
- `:focus-visible` : outline 3px `--orange`, offset 2px sur tous les éléments interactifs
- Toutes les images : attributs `width`, `height`, `alt`, `loading="lazy"` (sauf hero = eager)
- Tous les SVG icons inline : pas d'emojis
- Contraste minimum 4.5:1 partout (vérifié : `--gray-mid` #666 sur blanc = OK)

### Performance
- 0 dépendance externe (pas de Bootstrap, jQuery, etc.)
- Google Fonts chargées avec `preconnect` + `display=swap`
- Images below-fold en `loading="lazy"`
- CSS inline dans `<style>` (pas de fichier externe)
- JS minimal (~30 lignes : tier selector + sticky bar observer + countdown)

---

## JAVASCRIPT REQUIS

### 1. Sélecteur de paliers
```javascript
function selectTier(n) {
    // Retire .selected de toutes les options
    // Ajoute .selected sur l'option cliquée
    // Met à jour le prix dans : hero CTA, sticky bar, CTA final
}
```

### 2. Sticky bar (IntersectionObserver)
```javascript
// Observer le bouton hero CTA
// Quand il sort du viewport → afficher sticky bar (opacity 1, translateY 0)
// Quand il revient → cacher sticky bar
```

### 3. Countdown timer
```javascript
// Stocke end time dans localStorage (24h)
// Affiche HH:MM:SS en temps réel avec requestAnimationFrame
// Reset quand expiré
```
