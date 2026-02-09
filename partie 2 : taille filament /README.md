# 📏 Contrôle du diamètre du filament PLA

## 🎯 Objectif

L’objectif de ce projet est d’obtenir un **filament PLA utilisable en impression 3D** avec un **diamètre nominal de 1,75 mm**.  
Le filament produit est destiné à des **impressions de type brouillon / prototypes**, ce qui implique des exigences de qualité raisonnables mais maîtrisées.

### Tolérances visées
- **Diamètre cible : 1,75 mm**
- **Plage acceptable : 1,70 mm à 1,80 mm**
- **Diamètre maximal absolu : 1,80 mm**
- En fonctionnement normal, le filament **ne doit pas dépasser 1,75 mm**

---

## 🧪 Solutions de mesure testées

### 1️⃣ Capteur optique type *Shadow* (laser + luminosité) — ❌ Abandonné

**Principe :**
- Un laser passe devant le filament.
- Des capteurs de luminosité mesurent l’ombre projetée (*shadow*).
- Le diamètre est déduit de la quantité de lumière bloquée.

**Résultats :**
- Temps investi : **~4 heures**
- Mesure très sensible à la lumière ambiante.
- Variations importantes en fonction de l’éclairage.

**Conclusion :**
- Précision insuffisante
- Manque de robustesse
- Solution non exploitable pour une installation propre  
➡️ **Solution abandonnée rapidement**

---

### 2️⃣ Palpeur mécanique + capteur à effet Hall — ❌ Abandonné

**Principe :**
- Le filament déforme un palpeur mécanique.
- La déformation actionne un bras de levier (≈ 1 cm de course).
- Un aimant fixé sur le bras modifie le champ mesuré par un capteur à effet Hall.
- La mesure est lue par une carte **Arduino**.

**Résultats :**
- Temps investi : **~40 heures**
- Le capteur à effet Hall n’est pas parfaitement linéaire.
- Vibrations importantes dues au passage du filament.
- Fort tremblement du bras de levier.

**Mesures observées :**
- Pour un filament réel de **1,75 mm**, les valeurs mesurées varient entre :
  - **1,50 mm et 1,80 mm**
- Même avec une moyenne, la précision reste insuffisante.

**Conclusion :**
- Instabilité mécanique
- Précision non acceptable pour un contrôle fiable  
➡️ **Solution abandonnée**

---

### 3️⃣ Métrologie optique par caméra (solution retenue) ✅

**Principe :**
- Utilisation d’une caméra type microscope optique.
- Passage du filament dans un guide imprimé en 3D.
- Bon contraste entre la couleur du filament et le fond du guide.
- Éclairage contrôlé pour une image stable.

**Traitement :**
- Caméra connectée à un **Raspberry Pi**.
- Récupération du flux vidéo.
- Calcul du diamètre via un **script Python**.
- Le code pilote ensuite le reste du processus.

**Avantages :**
- Mesure sans contact.
- Absence de vibrations mécaniques.
- Bonne répétabilité.
- Solution évolutive (IHM, régulation, enregistrement des données).

**Conclusion :**
➡️ **Solution la plus précise et la plus fiable**, actuellement exploitée dans le projet.

---

## ✅ Conclusion générale

Après plusieurs essais, la **métrologie optique par caméra** est la seule solution répondant aux contraintes du projet :

- Diamètre maîtrisé autour de **1,75 mm**
- Respect des tolérances **1,70 mm – 1,80 mm**
- Fiabilité compatible avec une ligne d’extrusion de FabLab
- Base solide pour une régulation automatique du diamètre

Cette approche constitue aujourd’hui le **système de contrôle dimensionnel principal** du projet ReFilament.
