# Notes du premier cours (26 octobre 2023) 

## Bref aperçu sur les réseaux de neurones

### Notes de cours (à partir de notes d'Akka Zemmari - PR BM GP PF)

- [Les slides](deep.pdf)
- Points à retenir
  - D’abords il y a le neurone
  - Réseau de neurones
  - Réseaux à plusieurs couches
  - Apprentissage des paramètres
  - Couche de sortie
  - Exemple : reconnaissance d’écriture
  - Données d’entrainement
  - Objectif de l’entrainement
  - Fonction de perte (Loss Function)
  - Apprentissage ?
  - Descente du gradiant
  - A la recherche de la meilleure fonction

### Slides et vidéos du MIT (A.Amini)...

- Par exemple : https://introtodeeplearning.com/


### Mon premier DNN (Feuille jupyter)
(cela suppose quelques prerequis sur python...)

- [feuille Jupyter](DEEP_3.ipynb)

### Quelques liens utiles

- python :
- tutoriels Tensorflow : [Tensorflow](https://www.tensorflow.org/tutorials/quickstart/beginner)
- Un jeu de données "SSL" : https://github.com/bebetocf/ssl-dataset


## Retour sur le challenge technique SSL Vision Blackout

### Quelques articles

### Le projet

But : pour des robots SSL, mettre en oeuvre des solutions permettant de faire des matches sur un terrain division B en utilisant uniquement des informations de détection intégrées. 

Comment :
- Approche de vision (monoculaire ?) intégrée pour détecter des objets et estimer des positions relatives à l’intérieur du terrain. 
- Les connaissances préalables de l'environnement peuvent être exploitées en supposant que les objets se trouvent au sol et que la caméra embarquée a sa position fixée sur le robot. 

### Quelles techniques fondamentales sont nécessaires pour la « Vision Blackout » ?

Les incontournables :
1. Microprocesseurs séparés pour la vision embarquée et le contrôle du robot.
1. Communication entre les microprocesseurs
   + câble Ethernet
   + port USB
   + carte Citron
1. Détection de balle : plusieurs approches
1. Mouvements de base pour faciliter notre "navigation" :
  1. Rotation autour de l’axe du robot : utile rechercher la balle, s'aligner avec une cible, etc.
  1. Déplacement en ligne : ajuster l'orientation (en fonction d'une erreur dans le déplacement), ajuster la vitesse (en fonction de la distance à la cible) 
  1. Trajectoire circulaire autour d'un point : permettre au robot de rechercher un but tout en regardant le balle.
  1. Autres ?

(liste non exhaustive)
   
Les plus :
1. Prédire la trajectoire de la balle
1. Détection des balles en mouvement (Les balles se déplacent rapidement => flou) : problème si algorithmes basés sur la détection des contours.
(liste non exhaustive)

### Des pistes

- ROBOCIN : Méthode proposée sur un NVIDIA Jetson Nano
  + Utilise un réseau de neurones (architecture MobileNet SSD v2) pour détection d'objets 2D (balles, robots, buts, etc.) avec des distances allant jusqu'à 3,5 mètres. 
  + Camera Logitech C922 
  + Inertial sensors, to implement odometry estimation
  + capteurs inertiels (Accéléromètres, gyroscopes) : pour estimer la position, vitesse ou encore orientation
  + _An STM32F767ZI microcontroller unit (MCU), to receive target relative positions and navigation flags from the Nano and execute low-level control and trajectory estimation using inertial odometry_

- TIGER : méthode proposée sur ?

- NAMeC : que fait-on ?
