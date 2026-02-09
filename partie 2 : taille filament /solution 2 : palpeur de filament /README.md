#  Solution 2 — Palpeur de filament (contact mécanique)

##  Présentation générale

La deuxième solution étudiée pour la mesure du diamètre du filament est le **palpeur de filament par contact mécanique**.  
C’est **probablement la solution la plus répandue** dans les projets DIY et semi‑professionnels de fabrication de filament : on trouve de très nombreux modèles et variantes en ligne.

Le principe consiste à **mettre le filament en contact avec un capteur mécanique**, dont la déformation permet d’estimer le diamètre.

---

##  Principe de fonctionnement

### Architecture du palpeur

Le système est composé de :
- Un **bras de levier mécanique** en contact avec le filament
- Un **aimant** fixé sur ce bras
- Un **capteur à effet Hall**
- Une carte de lecture (type **Arduino**)

Lorsque le filament passe dans le palpeur :
- il pousse légèrement le bras mécanique,
- le bras se déplace,
- l’aimant modifie le champ magnétique perçu par le capteur à effet Hall,
- la variation du champ est traduite en **valeur numérique**, interprétée comme un diamètre.

### Amplification mécanique

Un point intéressant de cette solution est l’**amplification mécanique** :
- pour **1 mm de variation de diamètre**,  
- le bras de levier se déplace d’environ **4 à 5 mm**.

Sur le papier, cela permet d’augmenter la résolution du capteur et d’obtenir une meilleure sensibilité.

---

##  Contrainte liée au contact physique

Contrairement aux solutions optiques, le palpeur implique un **contact direct avec le filament**.

### Problème principal
- Le filament est encore **chaud et relativement souple** en sortie d’extrusion.
- Le contact mécanique peut **déformer légèrement le filament**.

### Conséquence
- Il est nécessaire de **rallonger la phase de refroidissement** du filament avant la mesure.
- Le filament doit arriver dans le palpeur **suffisamment rigide** pour éviter toute déformation induite par le capteur.

Cela complique l’intégration du palpeur dans la ligne de production.

---

##  Résultats obtenus

Malgré un temps de développement conséquent, les résultats ne sont pas satisfaisants.

### Instabilité des mesures

- Le capteur est **très sensible** aux micro‑mouvements du filament.
- Un simple **déplacement du filament dans l’axe du palpeur** entraîne de fortes variations de mesure.

### Exemple concret

Pour un filament standard d’imprimante 3D mesuré à **1,75 mm réel** :
- les valeurs lues à l’ordinateur varient entre :
  - **1,50 mm**
  - **1,90 mm**

Ces écarts sont **totalement incompatibles** avec un contrôle fiable du diamètre.

---

##  Tentatives d’amélioration

Afin de stabiliser le système, plusieurs ajustements ont été testés :
- Ajout d’un **ressort**
- Ajout d’**élastiques** pour limiter les oscillations du bras
- Ajustement des contraintes mécaniques

### Résultat
- Les améliorations réduisent légèrement les variations,
- mais la **précision reste insuffisante**,
- le système continue de produire des mesures incohérentes.

---

##  Alternatives industrielles

Il existe des :
- palpeurs plus performants,
- capteurs industriels de très haute précision.

Cependant, ces solutions présentent plusieurs limites pour notre projet :
- **Coût élevé**
- **Faible contrôle sur le fonctionnement interne**
- **Intégration complexe** dans une architecture DIY / FabLab

De plus :
- ne pas maîtriser la partie capteur rend :
  - la **programmation** plus complexe,
  - l’**asservissement des moteurs** plus difficile,
  - la compréhension globale du système moins maîtrisée.

---

## ❌ Conclusion

Malgré sa popularité et son apparente simplicité, le palpeur de filament par contact mécanique ne répond pas aux besoins du projet.

### Raisons principales de l’abandon
- Déformation possible du filament
- Nécessité d’un refroidissement prolongé
- Très faible précision
- Mesures instables et non répétables
- Difficulté à exploiter pour un asservissement fiable

➡️ Cette solution a donc été **abandonnée**, au profit d’une approche **sans contact**, plus précise et plus maîtrisable pour un projet semi‑industriel.

---
