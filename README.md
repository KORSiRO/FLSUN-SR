<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164060580-3fda5f97-c952-41f3-aea1-43b30f48e8a3.png" width="400"/>  
</p>
<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164056911-da4a19c8-fc3c-45bd-b51c-186f05931f83.png" width="470"/>  
</p>  
  
  
  
# FLSUN-SR FIRMWARE  

- [Firmware Stock v1.3](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%20STOCK/Firmware%20v1.3)

- [Firmware Stock v1.4](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%20STOCK/Firmware%20v1.4)

- [Firmware Guilouz Nano v3](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3)
- [Firmware Guilouz BTT TFT70](https://github.com/Guilouz/BTT-TFT70-SuperRacer)

- [Firmware Foxies Nano v3 + BTT TFT70/TFT35](https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/Firmwares/SR)


### 1. Installation firmware MKS Robin Nano v3 :

- Faire un `Reset EEPROM` avant de flasher le nouveau firmware : 
  - `M502` *(Reset EEPROM)*   
  - `M500` *(Sauvegarder)*
- Choisir le `Firmware` en suivant les liens ci-dessus
- Formater une `carte SD` ou une `clé USB` en `FAT32 4096 octets`  
- Copier le fichier `Robin_nano_v3.bin` à la racine de la carte SD/clé USB 
- Connecter la carte SD/clé usb à l'imprimante et l'allumer 
- Attendre quelques secondes que l'écran arrive à l'accueil
- Vérifier sur la `carte SD` que le fichier `Robin_nano_v3.bin` a été renommé en `ROBIN_NANO_V3.CUR` (flash réussi)
- Faire de nouveau un `Reset EEPROM`  
  - `M502` *(Reset EEPROM)*  
  - `M500` *(Sauvegarder)*
- Redémarrer l'imprimante

### 2. Installation firmware écran FLSUN SR :

- Formater une `carte SD` en `FAT32 4096 octets`  
- Copier le dossier `DWIN_SET` à la racine de la carte SD  
- Connecter la carte SD à l'écran et allumer l'imprimante  
- Attendre la fin de la MAJ

<img src="https://user-images.githubusercontent.com/62854582/163845798-b82c77e4-c3e4-41aa-9e31-cc1e15ac41fc.png" width="300">

# CALIBRATION  

- [Télécharger Printrun *(Pronterface)*](https://github.com/kliment/Printrun/releases)

### 1. PID Buse (firmware 1.4) :

- Créer un fichier texte que l'on appellera `PID Buse.gcode`
- Intégrer dans ce fichier :  
  - `M303 E0 S210 C8 U1` *(8 cycles de chauffe à 210°)*
- Noter ensuite les paramètres visible sur l'écran dans le menu `EEPROM` de la SR
- Imprimer le fichier `PID Buse.gcode` ou `PID Bed.gcode`, l'écran indique "impression terminée".
- La température de la buse va monter (PID en cours)
- Le PID est terminé quand la température est descendu à ~ 20° en dessous de la valeur `S` de départ
- On retourne dans le menu `EEPROM` et on vérifie que les données ont bien été modifiées
- On se rend dans `Console`sur l'écran de la SR et on rentre la commande :  
  - `M500` *(Sauvegarder)*  

***PS : `U1` permet d'envoyer à la carte mère les nouvelles valeurs du PID***

### 1.2 PID Buse depuis Pronterface ou Octoprint :

- Entrer la commande  
  - `M106 E0 S255` *(mise en route du ventilateur de la buse)*
- Entrer la commande  
  - `M303 E0 S210 C8` *(8 cycles de chauffe à 210°)*
- Une fois le PID terminé, entrer la commande  
  - `M301 P... I... D...` *(remplacer `...` par les nouvelles valeurs)*
- Entrer la commande  
  - `M500` *(Sauvegarder)*
- Entrer la commande  
  - `M106 E0 S0` *(Couper le ventilateur de la buse)*

### 2. PID Bed (firmware 1.4) :

- Créer un fichier texte que l'on appellera `PID Bed.gcode`
- Intégrer dans ce fichier :  
  - `M303 E-1 S60 C8 U1` *(8 cycles de chauffe à 60°)*
- Noter ensuite les paramètres visible sur l'écran dans le menu `EEPROM` de la SR
- Imprimer le fichier `PID Buse.gcode` ou `PID Bed.gcode`, l'écran indique "impression terminée".
- La température de la buse va monter *(PID en cours)*
- Le PID est terminé quand la température est descendu à ~ 20° en dessous de la valeur `S` de départ
- On retourne dans le menu `EEPROM` et on vérifie que les données ont bien été modifiées
- On se rend dans `Console` sur l'écran de la SR et on rentre la commande :  
  - `M500` *(Sauvegarder)*

### 2.2 PID Bed depuis Pronterface ou Octoprint :

- Entrer la commande  
  - `M303 E-1 S60 C8` *(8 cycles de chauffe à 60°)*
- Une fois le PID terminé, entrer la commande  
  - `M304 P... I... D...` *(remplacer `...` par les nouvelles valeurs)*
- Entrer la commande  
  - `M500` *(Sauvegarder)*

### 3. Extrudeur :

- Faire une marque à 120 mm
- Retirer le PTFE du dessous de l'extrudeur (extrusion à froid)
- Extruder 100mm :  
  - `M302 S0` *(pour pouvoir extruder à froid)*  
  - `M83` *(pour passer en mode relatif)*  
  - `G1 E100 F100` *(pour extruder 100mm)*
- Relever la longueur extrudée
- Récupérer les Steps actuel avec la commande :  
  - `M92`
- On fait le calcul suivant :  
  - `Steps actuel x 100mm` = `Steps pour 100mm`  
  - `Steps pour 100mm / Longueur extrudée` = `Nouvelle valeur Steps` 
- Entrer la commande:  
  - `M92 E...` *(remplacer `...`par la nouvelle valeur trouvée)*
- Entrer la commande :  
  - `M500` *(Sauvegarder)*

Se référer au document [CALIBRATION AUTOMATISÉ IMPRESSION 3D](https://github.com/KORSiRO/FLSUN-SR/raw/main/Calibration/CALIBRATION%20AUTOMATIS%C3%89%20IMPRESSION%203D.xlsm) afin de vous faciliter les calculs de calibration.


**PS** : activer les macros sous Excel pour enregistrer vos valeurs

### 4. Delta Calibration :

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

- [Delta Calibration Calculator](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3/files/8146727/Delta.Calibration.Calculator.zip)  

### 5. Linear Advance

Voici une vidéo du GüeroLoco qui explique tout en détails et de façon précise !
- [Linear Advance par le GüeroLoco](https://www.youtube.com/watch?v=f6fzJTsnpds&ab_channel=LeG%C3%BCeroLoco)

# MODIFICATIONS FIRMWARE  

- [Modifications Firmware Guilouz](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3#possible-changes)  

### ***Vidéos utiles :***  

- [Installation écran BTT TFT70](https://www.youtube.com/watch?v=vALnOhEb6vk&ab_channel=JSTECH) *(JSTECH)*  
- [Changement du firmware](https://www.youtube.com/watch?v=z3LmcFhDHHk&ab_channel=JSTECH) *(JSTECH)*
- [Maintenance Extrudeur](https://www.youtube.com/watch?v=TFeJfY321w8&ab_channel=DennisGignac) *(Dennis Gignac)*
- [Maintenance extrudeur + installation PEI](https://www.youtube.com/watch?v=aKYDvgTuacc&t=3s&ab_channel=JSTECH) *(JSTECH)*  
- [Installation BondTech LGX Lite](https://www.youtube.com/watch?v=Ql5lIAr7H58&ab_channel=JSTECH) *(JSTECH)*  
- [Remplacement de l'extrudeur](https://youtu.be/rzaumVlEIZM) *(FLSUN)*
- [Ajuster la tension des courroies](https://www.youtube.com/watch?v=N3sxU1_EIXY&ab_channel=FLSUN) *(FLSUN)*  
- [Maintenance des courroies et des rails linéaires](https://www.youtube.com/watch?v=05de4OFZCg0&ab_channel=DennisGignac) *(Dennis Gignac)*
- [Remplacement d'un chariot de roulement à billes sur la FLSun SR](https://www.youtube.com/watch?v=EmRWLrZj9kU&ab_channel=LeG%C3%BCeroLoco) *(Le GüeroLoco)*
- [Remplacement des rails linéaires](https://youtu.be/Kz_pey1oJfk) *(FLSUN)*
- [Amélioration FLSUN SR](https://www.youtube.com/watch?v=qsMoB8AFH08&ab_channel=JSTECH) *(JSTECH)*  
- [Mise à jour et réglages Flsun SuperRacer](https://www.youtube.com/watch?v=1fjbWBlSdbM&ab_channel=OlivierRichard3DLand-Shop) *(Olivier Richard 3DLand-Shop)*  
- [Imprimer via PC > USB](https://youtu.be/wfSc23aPTmI) *(FLSUN)*
- [Flsun Super racer réglages Cura](https://www.youtube.com/watch?v=cN8M4Pxr6G8&ab_channel=Infosettutosinformatique) *(Infos et tutos informatique)*


### ***Liens utiles :***

- [Acheter FLSUN SR sur le site FLSUN Officiel](https://flsun3d.com/products/super-racer-sr?variant=40603765964968)
- [Achat upgrades FLSUN SR](https://3dprintbeginner.com/flsun-super-racer-upgrades/)
- [Forum FLSUN SR](https://www.lesimprimantes3d.fr/forum/140-flsun-3d/)
- [Bien débuter avec la FLSUN SR](https://www.lesimprimantes3d.fr/forum/topic/47145-mon-retour-dexp%C3%A9rience-et-comment-bien-d%C3%A9buter-avec-la-flsun-sr/)
- [FAQ FLSUN SR](https://www.imprimante3d.shop/accueil/foire-aux-questions-flsun-sr-super-racer/)
- [Pièces détachées FLSUN SR](https://www.3djake.fr/piecesdetachees/pieces-detachees-pour-flsun-super-racer)  
- [Installer KLIPPER](https://3dprintbeginner.com/klipper-on-flsun-super-racer/)
   
       
*Toutes les informations collectées proviennent de différentes sources.  
Je tiens à remercier toutes les personnes qui proposent leur aides, participations et contributions.  
Grâce à elles, il est possible d'avoir beaucoup d'informations à disposition.  
La seule contribution personnelle est le fichier "CALIBRATION AUTOMATISÉ IMPRESSION 3D" que j'ai créé.  
Ce github a vu le jour pour permettre de faciliter les recherches à tous le monde.  
En espérant que vous trouviez réponses à vos questions :wink:*
