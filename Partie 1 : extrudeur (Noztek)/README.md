### 📄 Noztek Pro — Problématiques rencontrées & modifications apportées

Ce document décrit les principales **difficultés rencontrées** lors de l’utilisation de la **Noztek Pro** (extrudeuse semi-automatique) dans le cadre du projet **ReFilament**, ainsi que les **correctifs mécaniques et électriques** mis en place pour fiabiliser l’alimentation en matière et préparer une intégration plus “machine” (coffret + pupitre opérateur).

---

## 1) Rappel du fonctionnement de la Noztek Pro

La Noztek Pro est une machine semi-automatique avec un **pupitre (front panel)** très simple. On y retrouve typiquement **3 interrupteurs** :
<img width="752" height="561" alt="{0012DB52-219A-43E0-88F8-9B4413C1E524}" src="https://github.com/user-attachments/assets/54b93947-0ac6-4279-9864-ef0e330eedfe" />

1. **Ventilation / refroidissement filament**  
   Active un ventilateur permettant de refroidir le filament à la sortie.

2. **Entraînement vis sans fin (feed screw / auger)**  
   Active la **vis sans fin** qui avance la matière de manière continue.

3. **Chauffe (barrel heater)**  
   Active le système chauffant.  
   La température est régulée via un **asservissement** intégré (contrôle de température) avec **sondes** déjà intégrées à la machine, permettant de viser une consigne précise.

### Alimentation matière
Les copeaux de PLA sont versés dans un **entonnoir métallique** (trémie/réceptacle) monté directement au-dessus de la zone d’alimentation de la vis.

---

## 2) Problème principal : “bridging” (formation de ponts) dans la trémie

### Symptôme
En fonctionnement, les copeaux de PLA :
- **restaient coincés** dans l’entonnoir,
- ne descendaient pas correctement jusqu’à la vis sans fin,
- entraînaient une **alimentation intermittente** de la vis → débit instable → extrusion instable.

### Cause identifiée
Formation de **ponts de matière (bridging)** :
- les copeaux s’imbriquent et créent une voûte,
- la gravité seule ne suffit plus à les faire s’écouler,
- la trémie “a l’air pleine”, mais la vis est **sous-alimentée**.

---

## 3) Solution mise en place : agitateur anti-pont (anti-bridging)

Pour supprimer la formation de ponts, nous avons ajouté :

- un **moteur pas à pas** positionné au-dessus de la zone d’alimentation,
- un **bras / agitateur** mécanique qui tourne dans les copeaux,
- l’agitateur casse les voûtes et **force l’écoulement** du PLA vers la vis.

### Choix de commande
- Ce moteur **ne nécessite pas** de régulation fine.
- Fonctionnement possible **à 100% en continu** pendant la phase d’extrusion.

---

## 4) Contraintes électriques & intégration 24 V

### Architecture actuelle
- Les fonctions de commande (ventilation, vis, chauffe, etc.) reposent sur une logique d’alimentation en **24 V**.
- La machine dispose d’un **transformateur interne** (source 24 V) dimensionné pour ses sous-systèmes.

### Orientation d’intégration (prévue)
Dans le cadre de notre coffret global, nous prévoyons :
- de **sortir le transformateur** de la Noztek Pro,
- de l’intégrer dans la **caisse/armoire** du projet,
- afin de :
  - mutualiser la distribution **24 V** pour d’autres modules (bobineuse, électronique auxiliaire, etc.),
  - centraliser l’arrivée **230 V** pour alimenter **l’ensemble de la machine** (et pas uniquement la Noztek).

> Remarque : cette démarche vise une intégration plus propre (maintenance, sécurité, câblage), et un “système complet” au lieu d’une juxtaposition de sous-ensembles.

---

## 5) Refonte ergonomie : déport du pupitre opérateur (prévu)

Le pupitre d’origine (3 switches + régulation température) sera **déporté** sur un panneau frontal dédié, pour un usage plus lisible et industrialisé :

- montage sur une **face avant** (panneau / planche bois dans le prototype),
- commandes alignées, accessibles et repérées,
- **étiquetage clair** (ON/OFF, fonctions, consignes),
- meilleure intégration mécanique (finition + sécurité + maintenance).

---

## 6) Résultat attendu

Avec l’ajout de l’agitateur anti-pont + une intégration électrique/pupitre plus propre, on vise :

- alimentation matière **continue** (plus de bridging),
- débit d’extrusion **plus stable**,
- exploitation plus “machine” :
  - alimentation centralisée,
  - pupitre opérateur clair,
  - câblage maintenance-friendly.

---

## 7) À compléter (optionnel)

- Photos de la trémie avant/après
- Schéma mécanique de l’agitateur
- Schéma électrique (24 V : protections, distribution, repérage)
- Liste des composants (moteur, driver, alimentation, fixation)
- Procédure opérateur (mise en route : chauffe → vis → agitateur → ventilation, etc.)
