# extruder-de-filament-pla
### ♻️ ReFilament — Ligne de recyclage PLA en filament 1.75 mm (prototype FabLab)

Projet réalisé **au FabLab de notre école** par **Maël & Martin**. Objectif : concevoir une ligne de transformation de **chutes/copeaux de PLA** issus d’impression 3D en **filament 1.75 mm** destiné à des impressions **brouillon / prototypes**.

---

## 1) Vue d’ensemble

Notre système est une ligne composée de trois sous-ensembles principaux :

1. **Module d’extrusion (base Noztek Pro)**  
   - Copeaux PLA → plastification dans une zone chauffée → extrusion via buse.

2. **Module de contrôle dimensionnel (métrologie optique)**  
   - Mesure du diamètre du filament **en ligne** via **microscope/caméra**.  
   - Traitement sur **Raspberry Pi 3B** (Python) + affichage via **IHM** (interface opérateur).

3. **Module de traction + bobinage (bobineuse)**  
   - La **vitesse de tirage** impose l’**étirage** du filament.  
   - Enroulement sur bobine standard avec **guidage** pour une répartition homogène.

---

## 2) Principe de fonctionnement (process)

### 2.1 Extrusion (Noztek Pro)
- Le PLA broyé/copeaux est entraîné puis fondu.
- La matière est extrudée au travers d’une buse : on obtient un filament “brut” (dans notre cas, typiquement **~3 mm** en sortie).

### 2.2 Calibrage par traction (cible 1.75 mm)
- La sortie matière à la buse est globalement constante.
- En augmentant la **vitesse de traction** (bobineuse), on augmente l’**étirage**, donc on **réduit le diamètre**.
- Le point clé du projet est de **stabiliser le diamètre à 1.75 mm** de manière répétable.

### 2.3 Métrologie optique (Raspberry Pi 3B)
- Un **microscope/caméra** observe le filament.
- Le **Raspberry Pi 3B** :
  - acquiert le flux vidéo,
  - calcule le diamètre (script Python),
  - alimente une **IHM** (lecture diamètre, états, réglages, etc.).
- Finalité : permettre une **régulation** (fermée à terme) de la vitesse de traction.

---

## 3) Réalisé ✅

### 3.1 Étude & intégration extrudeuse (Noztek Pro)
- Analyse fonctionnelle du module d’extrusion et de ses contraintes d’intégration.
- Définition de l’architecture globale de la ligne (extrusion → métrologie → traction/bobinage).

### 3.2 Module bobineuse (traction + enroulement)
- Bobineuse **conçue et fabriquée** par nos soins (structure + pièces imprimées 3D).
- Vitesse de traction **réglable**.
- Système de **guide-fil** pour l’enroulement régulier sur bobine (répartition homogène).

### 3.3 Tentative de métrologie mécanique (abandonnée)
- Essai d’un palpeur par contact (roulements + capteur).
- Résultats insuffisants en précision/stabilité (vibrations, dynamique du filament) → bascule vers la **métrologie optique**.

---

## 4) En cours / À réaliser 🚧

### 4.1 Intégration système (carénage + front panel)
- Intégration dans un châssis/enceinte type “machine” :
  - **plexiglas** (inspection visuelle + accès maintenance),
  - **profilés aluminium** (rigidité, modularité).
- Refonte de l’ergonomie : déport des commandes Noztek vers un **front panel** opérateur plus propre et accessible.

### 4.2 Métrologie optique + IHM (Raspberry Pi 3B)
- Intégration du microscope/caméra dans la ligne (positionnement, éclairage, stabilité).
- Mise en place de l’IHM : mesure diamètre, consigne, alarmes, log.

### 4.3 Alimentation centralisée
- Conception d’une distribution d’énergie unique pour :
  - Noztek Pro (chauffe + motorisation),
  - Raspberry Pi 3B + caméra + écran/clavier,
  - bobineuse.
- Objectifs : câblage propre, protections, interrupteur général, maintenance simplifiée.

### 4.4 Régulation diamètre (objectif technique)
- Mise en place d’un contrôle basé sur la mesure :
  - diamètre mesuré → ajustement vitesse bobineuse (et/ou paramètres process)
  pour converger vers **1.75 mm**.

---

## 5) Périmètre matière

- **Matière ciblée : PLA uniquement (pour l’instant)**  
  (les autres polymères ne sont pas dans le périmètre actuel du prototype).

---

## 6) Vision future 🔮 (traçabilité / “profil de bobine”)

À terme, on souhaite enregistrer un **profil de fabrication** pendant le bobinage (log de diamètre et paramètres process) exportable (USB / SD).  
But : améliorer la traçabilité et, à plus long terme, permettre une exploitation “intelligente” du filament recyclé pour des impressions plus stables.

---

---

## 7) Sécurité (prototype)

- Zones chaudes (extrusion) : brûlures
- Parties mobiles (bobineuse) : pincements/arrachement
- Électricité : protections obligatoires (fusible/disjoncteur, mise à la terre si applicable)
- Ventilation recommandée
