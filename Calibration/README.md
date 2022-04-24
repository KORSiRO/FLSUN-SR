# Delta Calibration :

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
