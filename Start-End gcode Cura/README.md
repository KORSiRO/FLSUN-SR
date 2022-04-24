***Gcode Cura avec la purge en arc de cercle*** 

- G-Code de démarrage :

G21 ; Unités en millimètres  
G90 ; Positionnement absolu  
M82 ; Axe E en mode absolu  
M140 S{material_bed_temperature} ; Température du plateau (pour Cura)  
M104 S{material_print_temperature} ; Température de la buse (pour Cura)  
M190 S{material_bed_temperature} ; Attente la température du plateau (pour Cura)  
M109 S{material_print_temperature} ; Attente de la température de la buse (pour Cura)  
G28 ; Origines des axes  
M420 S1 ; Activation du maillage ; Descente de la Hotend et passage à la position de départ  
G1 Z150  
G1 X-130 Y0 Z0.4 F3000 ; Extrude environ 40mm en imprimant un arc de 90 degrés  
G3 X0 Y-130 I130 Z0.3 E40 F1500 ; Rétraction et déplacement de la hotend vers le haut  
G92 E0  
G1 E-1.5 F1800  
G0 Z0.5  
G1 E0 F300

- G-Code de fin :

G91 ; Positionnement relatif  
G1 E-1 F300 ; Rétraction avant déplacement de la hotend vers le haut  
G1 Z+5 E-5 F6000 ; Déplacement de la hotend vers le haut  
G28 X0 Y0 ; Origines des axes  
G90 ; Positionnement absolu  
G92 E0 ; Réinitialisation de l'extrudeur  
M104 S0 ; Arrêt de la chauffe de la buse  
M140 S0 ; Arrêt de la chauffe du plateau  
M107 ; Arrêt des ventilateurs  
M84 ; Désactivation des moteurs
