- G0 *(Mouvement rapide d'un axe)*
- G1 *(Mouvement linéaire d'un axe)*
- G1 *(Unités en mm)*
- G28 *(Home des axes/position 0)*
- G29 *(Calibration du plateau en 8/9 points = Compensation en Z lors de l'impression)*
- G90 et G91     
    - G91 *(positionnement relatif)*
Explications : Si en fin d'impression vous souhaitez déplacer l'axe Z et le faire monter de 20mm, la simple commande G1 Z20 fera descendre la tête à une hauteur de 20mm depuis le point 0 alors que si vous entrez la commande G91 G1 Z20 l'axe Z montera de 20mm mais cette fois, depuis sa position actuelle (en fin d'impression par exemple) et non par rapport au point 0.
    - G90 *(positionnement absolu)*
Explications : A l'inverse de la commande G91, la commande G90 prend en compte les déplacements depuis la position 0.
Si vous entrez la commande G90 G1 Z20 l'axe Z se placera à une hauteur de 20mm par rapport au point 0.
- M82 *(Extrudeur en mode absolu)*
- M83 *(Extrudeur en mode relatif)*
- M84 *(Désactivation des moteurs)
- M92 *(Définir les valeurs des pas/mm des axes)*
    - M92 X...Y...Z...E...
- M104 *(Définir la température de la Buse)*
    - M104 S200 *(Température de la Buse à 200°)*
- M109 *(Définir la température de la Buse et attendre la température cible)*
    - M109 S200 *(Température de la Buse à 200° et attendre)*
- M106 *(Activer le ventilateurs de la Buse)*
    - M106 S255 *(ventilateur à 100%)*
- M107 *(Arrêter des ventilateurs)*
- M114 *(Afficher la position actuelle de la tête d'impression)*
- M119 *(Afficher l'état des capteurs de fin de course)*
- M140 *(Définir la température du Plateau)*
    - M140 S60 *(Température du Plateau à 60°)*
- M190 *(Définir la température du Plateau et attendre la température cible)*
    - M190 S60 *(Température du Plateau à 60° et attendre)*
- M303 *(Calibration PID)*
- M301 *(Définition des valeurs du PID manuel pour la Buse)*
- M304 *(Définition des valeurs du PID manuel pour le Plateau)*
- M500 *(Sauvegarder les paramètres actules dans l'EEPROM)*
- M501 *(Charger les paramètres depuis l'EEPROM)*
- M502 *(Reset de l'EEPROM)*
- M503 *(Lecture des paramètres l'EEPROM)*
- M851 / M851 Z... *(Afficher / modifier la valeur du Z Offset)*
- M906 *(Ajuster le courant des drivers en mode UART)*
    - M906 X...Y...Z...
    - M906 T0 E...



