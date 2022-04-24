# DELTA CALIBRATION :

<img src="https://user-images.githubusercontent.com/62854582/164052174-66a85777-bf06-4e9e-a63b-a6fb0d2b1a4f.png" width="350">

- Connecter la sonde pour le leveling
- Chauffer le lit à votre température habituelle
- Depuis Pronterface ou autre, lancer la commande  
  - `G33`
- Attendre la fin et enregistrer avec la commande  
  - `M500`
- Retirer la sonde de leveling
- Chauffer la buse à votre température d'impression (sans filament pour éviter qu'il ne coule de la buse)
- Chauffer le lit à votre température d'impression
- Déplacer la buse à la hauteur `Z=0`
- Placer un papier et ajuster le Z-Offset depuis l'écran de la SR
- Sauvegarder

Si besoin se référer au document `Delta Calibration Calculator`

# CALIBRATION AUTOMATISÉ IMPRESSION 3D :

Ce document a été créé pour faciliter la calculs de calibration, n'hésitez pas à l'utiliser si besoin !

<img src="https://user-images.githubusercontent.com/62854582/164967442-7625912c-e8dd-4232-b42c-b5381321197a.png" width="900">

# TEMPÉRATURE DE BUSE IRRÉGULIÈRE :

Si la température de la buse est irrégulière vous pouvez essayer cette modification :

- Dans `Marlin` > `Configuration.h` repérer les lignes :

  - `#define BANG_MAX 255` 
  - `#define PID_MAX 255` 
  - `#define PID_FUNCTIONAL_RANGE 10`

- Modifier les valeurs :

  - `#define BANG_MAX 130`  
  - `#define PID_MAX 110`  
  - `#define PID_FUNCTIONAL_RANGE 20` 

- Explications : 

  - `BANG_MAX 255`              ***Puissance maximale (255) jusqu'à atteindre la valeur du PID***
  - `PID_MAX 255`               ***Puissance maximale (255) intervalle PID***
  - `PID_FUNCTIONAL_RANGE 10`   ***Intervalle température PID actif. Pour 200° le PID sera donc actif entre 190° et 210°***


***Cette modification permet d'avoir un écrat de température lors du PID beaucoup plus faible***
