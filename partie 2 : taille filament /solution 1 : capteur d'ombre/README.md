#  Solution 1 — Capteur d’ombre (*Shadow Sensor*)

##  Principe général

La première solution étudiée pour mesurer le diamètre du filament repose sur un **capteur d’ombre**, aussi appelé *shadow sensor*.  
Cette approche est **largement utilisée** par de nombreuses personnes cherchant à concevoir des extrudeuses ou des lignes de recyclage de filament.

Le principe est simple : **déduire le diamètre du filament à partir de l’ombre qu’il projette** lorsqu’il est traversé par un faisceau lumineux.

---

##  Architecture du système

Le système mis en place est composé des éléments suivants :

- **Un laser** pointé directement vers le filament
- **Le filament** positionné entre la source lumineuse et les capteurs
- **Quatre photo‑résistances**, placées derrière le filament
- Une **électronique de lecture** permettant de récupérer l’intensité lumineuse reçue par chaque capteur


---

##  Principe de mesure

- Le laser éclaire le filament de manière frontale.
- Le filament projette une **ombre partielle** sur les photo‑résistances.
- Les variations d’intensité lumineuse sont analysées.
- Le diamètre du filament est estimé **en fonction de la taille et de la répartition de l’ombre**.

Sur le papier, ce principe est :
- simple à comprendre,
- peu coûteux,
- relativement facile à mettre en œuvre.

---

##  Problèmes rencontrés

Malgré sa simplicité, cette solution s’est révélée **très instable** dans notre cas.

### Sensibilité à l’environnement
Les mesures varient fortement en fonction de :
- la **lumière ambiante**,
- les **reflets**,
- les **mouvements du filament**,
- la position exacte du filament dans le faisceau,
- la **qualité et la dispersion** des photo‑résistances.

### Manque de répétabilité
Même à diamètre constant :
- les valeurs mesurées **divergent fortement**,
- les résultats ne sont pas suffisamment fiables,
- les fluctuations sont trop importantes pour une exploitation sérieuse.

---

##  Capteurs *Shadow* du commerce

Il existe des **capteurs d’ombre industriels** disponibles dans le commerce, offrant :
- une meilleure qualité de fabrication,
- une meilleure répétabilité que les solutions DIY.

Cependant, ces capteurs présentent plusieurs inconvénients majeurs pour notre projet.

### Limitations identifiées
- **Coût élevé** par rapport aux performances attendues
- **Dimensions très réduites**
  - Le filament peut passer, mais
  - il est **difficile de garantir un positionnement parfaitement centré**
- Nécessité d’un **guidage extrêmement précis**
- Même avec un bon guidage, la **précision reste limitée**

---

##  Conclusion

Bien que le capteur d’ombre soit :
- largement utilisé,
- conceptuellement simple,
- attractif pour des prototypes rapides,

il ne répond pas aux exigences de notre projet.

### Raisons de l’abandon
- Sensibilité excessive à l’environnement
- Manque de stabilité et de répétabilité
- Difficulté d’intégration mécanique fiable
- Solution **non viable à l’échelle semi‑industrielle**

➡️ Cette approche a donc été **abandonnée au profit de solutions plus robustes**, mieux adaptées à un contrôle dimensionnel précis et exploitable sur le long terme.

