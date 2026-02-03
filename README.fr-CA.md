# Vrai ⇄ Magnétique ⇄ Compas (hors ligne) — v1.1b (BASELINE)

Application web hors ligne qui :

- Calcule la **déclinaison magnétique** (Vrai ↔ Magnétique) avec **WMM-2025**
- Applique la **déviation du compas** (Magnétique ↔ Compas) à l’aide d’une table par pas de 15° avec interpolation
- Fonctionne hors ligne (PWA)
- Permet d’imprimer une **carte de déviation** (idéale à plastifier)
- Bascule **anglais / français canadien**

© 2026 Glen Carruthers. Tous droits réservés.

---

## Définitions rapides

### Nord vrai (NV) / Cap vrai (°V)
Direction par rapport au pôle Nord géographique (cartes et relèvements vrais).

### Nord magnétique (NM) / Cap magnétique (°M)
Direction par rapport au champ magnétique terrestre à votre position.

### Cap compas (°C)
Lecture réelle du compas du bateau.

### Déclinaison (variation)
Angle entre le **nord vrai** et le **nord magnétique** à un endroit et une date donnés.

- **Déclinaison Est = positive (+)**
- **Déclinaison Ouest = négative (−)**

Cette application calcule la déclinaison à l’aide du **World Magnetic Model 2025 (WMM-2025)**.

### Déviation
Erreur propre au **compas du bateau** causée par les influences magnétiques à bord  
(moteur, câblage, haut-parleurs, métal, électronique, etc.).

La déviation varie selon le cap et est mesurée en « mettant le compas au point » (swing).

Dans cette application :

- **Est = +**
- **Ouest = −**
- Valeurs saisies tous les **15°** (0° à 345°)
- Les caps intermédiaires sont calculés par **interpolation linéaire**
- Les cases vides sont traitées comme **0,0°**

---

## Convention de signe (important)

**Est = +, Ouest = −** pour la déclinaison et la déviation.

### Vrai ↔ Magnétique (déclinaison)

- **Magnétique = Vrai − Déclinaison**
- **Vrai = Magnétique + Déclinaison**

**Exemple :** Déclinaison = **+10° (10° Est)**  
Cap vrai = 120°V  

Cap magnétique = 120 − 10 = **110°M**

**Exemple :** Déclinaison = **−5° (5° Ouest)**  
Cap vrai = 120°V  

Cap magnétique = 120 − (−5) = 120 + 5 = **125°M**

---

### Magnétique ↔ Compas (déviation)

- **Compas = Magnétique − Déviation**
- **Magnétique = Compas + Déviation**

**Exemple :** Déviation = **+2° (2° Est)**  
Cap magnétique = 110°M  

Cap compas = 110 − 2 = **108°C**

**Exemple :** Déviation = **−3° (3° Ouest)**  
Cap magnétique = 110°M  

Cap compas = 110 − (−3) = 113 = **113°C**

---

## Fonctionnement de l’application

### 1) Déclinaison

Entrer :

- Latitude / Longitude  
- Altitude (facultatif)  
- Date (UTC)

Puis cliquer sur **Calculer la déclinaison**.

---

### 2) Conversion (Vrai / Magnétique / Compas)

Entrer **un seul** des éléments suivants :

- Cap vrai (°V)  
- Cap magnétique (°M)  
- Cap compas (°C)

Puis cliquer sur **Convertir**.

L’application calcule automatiquement les deux autres à l’aide :

- de la déclinaison
- de la table de déviation

> Remarque : lorsque vous entrez le cap compas, l’application estime le cap magnétique par itérations (normal puisque la déviation dépend du cap).

---

### 3) Table de déviation

- Entrer les valeurs tous les 15°
- Sauvegarder / charger des profils
- Importer / exporter en JSON
- Imprimer une **carte de déviation**

---

## Mise à jour du modèle magnétique (facultatif)

Vous pouvez importer un nouveau fichier **WMM JSON** lorsqu’un nouveau modèle est publié.

- Le modèle est conservé hors ligne dans le navigateur
- Bouton **Réinitialiser** pour revenir à WMM-2025 intégré

---

## Avis de sécurité

Cette application est fournie à titre d’aide et de formation.

Toujours vérifier :

- Les calculs avec des sources officielles
- La carte de déviation actuelle du bateau
- Les observations pratiques en navigation

---

## Fichiers

- `index.html` — application principale (v1.1b baseline)
- `manifest.json` — configuration PWA
- `service-worker.js` — fonctionnement hors ligne
- icônes — icônes de l’application

