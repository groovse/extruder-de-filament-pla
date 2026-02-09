#  Solution 3 — Capteur optique par microscope numérique (solution retenue)

##  Présentation générale

La troisième solution étudiée, et **retenue comme solution finale**, est basée sur un **capteur optique sans contact**, utilisant un **microscope numérique du commerce**.

Cette approche vise à :
- éliminer toute interaction mécanique avec le filament,
- garantir une **mesure stable et répétable**,
- offrir une solution **évolutive et facilement calibrable**.

---

##  Matériel utilisé
<img width="864" height="1000" alt="image" src="https://github.com/user-attachments/assets/da413b90-6e9c-4090-832a-599bd835cdbd" />

### Microscope numérique

Le capteur principal est un microscope numérique grand public, utilisé comme une caméra externe classique :

- **Type** : Microscope numérique avec écran intégré  
- **Écran** : 7 pouces  
- **Modèle** : **MK7**  
- **Résolution optique** : de **180 nm à 500 nm**  
- **Grossissement** : de **×500 à ×1500**  
- **Éclairage intégré** : lumière LED intégrée assurant un éclairage constant du filament  
- **Connexion** : utilisable comme **caméra externe reliée à un ordinateur**

Ce microscope fournit une image stable, bien éclairée et suffisamment détaillée pour permettre une analyse précise du diamètre du filament.

---

##  Unité de traitement

- Le microscope est relié à un **ESP32**, utilisé comme unité de traitement embarquée.
- L’ESP32 :
  - récupère l’image fournie par le microscope,
  - traite l’information,
  - permet l’exploitation logicielle des données.

Même si cette solution est plus complexe qu’une simple carte Arduino, elle offre :
- plus de puissance de calcul,
- plus de flexibilité,
- une meilleure évolutivité logicielle.

---

## Principe de mesure

### Calibration initiale

1. Un **filament de référence** (diamètre connu : **1,75 mm**) est placé dans le système.
2. L’image du filament est affichée à l’écran.
3. Le diamètre du filament est mesuré en **nombre de pixels**.

Exemple :
- **1,75 mm ≈ 163 pixels** (valeur indicative)

Cette opération est répétée sur plusieurs points visibles à l’écran afin d’obtenir une **moyenne fiable**.

---

### Mesure du filament à tester

1. Le filament à analyser est ensuite inséré dans le guide.
2. Il est déroulé à une **vitesse volontairement plus élevée** que celle utilisée en impression.
   - Objectif : valider le comportement du système dans des conditions plus exigeantes.
3. Le diamètre est calculé :
   - en pixels,
   - puis converti en millimètres à partir de la calibration.

La mesure est moyennée sur toute la longueur du filament visible à l’écran.

---

##  Résultats obtenus

### Précision

- Précision obtenue : **de l’ordre du centième de millimètre**
- Mesures typiques :
  - entre **1,74 mm et 1,76 mm** pour un filament nominal à 1,75 mm

Cette précision est :
- **largement suffisante** pour le projet,
- et même **excellente** au regard de l’usage visé (prototypes / brouillon).

---

##  Avantages de la solution

- ✅ **Aucun contact mécanique** avec le filament
- ✅ Aucune déformation du filament
- ✅ Très bonne stabilité des mesures
- ✅ Très faible dérive dans le temps
- ✅ Calibration simple et rapide
- ✅ Solution facilement compréhensible et réglable par d’autres utilisateurs
- ✅ Compatible avec une **interface graphique** pour le réglage et la visualisation

---

##  Contraintes

-  Coût plus élevé que les solutions précédentes
-  Mise en œuvre plus complexe
-  Utilisation d’un microcontrôleur avancé (ESP32) assimilable à un petit ordinateur

Cependant, ces contraintes sont largement compensées par :
- la précision obtenue,
- la fiabilité,
- la facilité de calibration,
- et l’évolutivité du système.

---

##  Conclusion

La solution par **capteur optique et microscope numérique** est la seule à répondre pleinement aux objectifs du projet :

- précision élevée,
- stabilité des mesures,
- absence de contact,
- facilité d’exploitation logicielle,
- compatibilité avec une future régulation automatique.

➡️ Cette solution a donc été **retenue comme solution finale** pour le contrôle du diamètre du filament dans le projet ReFilament.

---
