<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164060580-3fda5f97-c952-41f3-aea1-43b30f48e8a3.png" width="400"/>  
</p>
<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164056911-da4a19c8-fc3c-45bd-b51c-186f05931f83.png" width="400"/>  
</p>  
  
  
           
# FLSUN-SR FIRMWARE  

- [Télécharger firmware 1.4 SD](https://github.com/KORSiRO/FLSUN-SR/raw/main/Firmware%201.4/Firmware%201.4%20NanoV3-TFcard/Robin_nano_v3.bin)
- [Télécharger firmware 1.4 USB](https://github.com/KORSiRO/FLSUN-SR/raw/main/Firmware%201.4/Firmware%201.4%20NanoV3-Udisk/Robin_nano_v3.bin)
- [Télécharger firmware SCREEN](https://github.com/KORSiRO/FLSUN-SR/raw/main/Firmware%201.4/Firmware%201.4%20Screen/DWIN_SET.zip)
- [Vidéo MAJ Firmware v1.3/v1.4](https://www.youtube.com/watch?v=-RFSyTZ_7P0&ab_channel=FLSUN)

### Installation firmware MKS Robin Nano v3 :

- Faire un `Reset EEPROM` avant de flasher le nouveau firmware : `M502` suivi de `M500` (depuis un termnial ou depuis l'écran de la SR)
- Choisir le `Firmware`en suivant les liens ci-dessus
- Formater une `carte SD` ou une `clé USB` en `FAT32 4096 octets`  
- Copier le fichier `Robin_nano_v3.bin` à la racine de la carte SD/clé USB 
- Connecter la carte SD/clé usb à l'imprimante et l'allumer 
- Attendre quelques secondes que l'écran arrive à l'accueil
- Vérifier sur la `carte SD` que le fichier `Robin_nano_v3.bin` a été renommé en `ROBIN_NANO_V3.CUR` (flash réussi)
- Faire de nouveau un `Reset EEPROM` avec `M502` suivi de `M500` (depuis un termnial ou depuis l'écran de la SR)
- Redémarrer l'imprimante

### 2. Installation firmware écran FLSUN SR :

- Formater une `carte SD` en `FAT32 4096 octets`  
- Copier le dossier `DWIN_SET` à la racine de la carte SD  
- Connecter la carte SD à l'écran et allumer l'imprimante  
- Attendre la fin de la MAJ

<img src="https://user-images.githubusercontent.com/62854582/163845798-b82c77e4-c3e4-41aa-9e31-cc1e15ac41fc.png" width="300">

# CALIBRATION

### 1. PID Buse (firmware 1.4) :

- Créer un fichier texte que l'on appellera `PID Buse.gcode`
- Intégrer dans ce fichier : `M303 E0 S210 C8 U1`
- Noter ensuite les paramètres visible sur l'écran dans le menu `EEPROM` de la SR
- Imprimer le fichier `PID Buse.gcode` ou `PID Bed.gcode`, l'écran indique "impression terminée".
- La température de la buse va monter (PID en cours)
- Le PID est terminé quand la température est descendu à ~ 20° en dessous de la valeur `S` de départ
- On retourne dans le menu `EEPROM` et on vérifie que les données ont bien été modifiées
- On se rend dans `Console`sur l'écran de la SR et on rentre un `M500`pour sauvegarder les nouvelles valeurs

**:warning: Si la température de la buse est irrégulière :warning:**

Dans `Marlin > Configuration.h` repérer les lignes :

`#define BANG_MAX 255`  
`#define PID_MAX 255`  
`#define PID_FUNCTIONAL_RANGE 10`  

et les modifier :

`#define BANG_MAX 130`  
`#define PID_MAX 110`  
`#define PID_FUNCTIONAL_RANGE 20` 

### 2. PID Bed (firmware 1.4) :

- Créer un fichier texte que l'on appellera `PID Bed.gcode`
- Intégrer dans ce fichier : `M303 E-1 S70 C8 U1`
- Noter ensuite les paramètres visible sur l'écran dans le menu `EEPROM` de la SR
- Imprimer le fichier `PID Buse.gcode` ou `PID Bed.gcode`, l'écran indique "impression terminée".
- La température de la buse va monter (PID en cours)
- Le PID est terminé quand la température est descendu à ~ 20° en dessous de la valeur `S` de départ
- On retourne dans le menu `EEPROM` et on vérifie que les données ont bien été modifiées
- On se rend dans `Console`sur l'écran de la SR et on rentre un `M500`pour sauvegarder les nouvelles valeurs

**PS** : `U1`permet d'envoyer à la carte mère les nouvelles valeurs du PID

### 3. Extrudeur :

Depuis la `Console`sur l'écran de la SR on envoie les commandes :  

`M302 S0` (pour pouvoir extruder à froid)  
`M83` (pour passer en mode relatif)  
`G1 E100` (pour extruder 100mm)  

On mesure la distance extrudée et on fait le calcul : 
`(longueur demandée / longueur mesuréee) x steps actuels = nouveaux steps`

### 4. Delta Calibration :

<img src="https://user-images.githubusercontent.com/62854582/164052174-66a85777-bf06-4e9e-a63b-a6fb0d2b1a4f.png" width="350">

- Connecter la sonde pour le leveling
- Lancer la commande `G33`
- Attendre la fin et enregistrer avec la commande `M500`
- Faire un `Leveling` depuis l'écran de la SR
- Régler le `Z Offset`
- Sauvegarder avec la commande `M500`

Si besoin se référer au document `Delta Calibration Calculator

- [Télécharger Delta Calibration Calculator](https://github.com/KORSiRO/FLSUN-SR/raw/main/Calibration/Delta%20Calibration%20Calculator.xlsx)

# MODIFICATIONS DU FIRMWARE

- Utilisation du port **Micro SD** :
  * Configuration_adv.h : `//#define USB_FLASH_DRIVE_SUPPORT`                                                                                                                                     `//#define USE_OTG_USB_HOST`

- Utilisation du **port USB** :
  * Configuration_adv.h :  
  `#define USB_FLASH_DRIVE_SUPPORT`  
  `#define USE_OTG_USB_HOST`

- Utilisation **OMG-V2-S EXTRUDEUR (BOWDEN)** :  
  * Configuration.h :  
  `#define DEFAULT_AXIS_STEPS_PER_UNIT { 80, 80, 80, 385 }`  
  `#define INVERT_E0_DIR true`  
  * Configuration_adv.h :  
  `#define E0_CURRENT 1050`  

- Utilisation **BONDTECH LGX EXTRUDEUR (BOWDEN)** :
  * Configuration.h :  
  `#define DEFAULT_AXIS_STEPS_PER_UNIT { 80, 80, 80, 400 }`  
  `#define INVERT_E0_DIR false`  
  * Configuration_adv.h :  
  `#define E0_CURRENT 650`

- Utilisation **BONDTECH LGX LITE EXTRUDEUR (DIRECT DRIVE)** :
  * Configuration.h :  
  `#define DEFAULT_AXIS_STEPS_PER_UNIT { 80, 80, 80, 562 }`
  `#define INVERT_E0_DIR false`  
  `#define DEFAULT_MAX_FEEDRATE { 200, 200, 200, 120 }`  
  `#define DEFAULT_MAX_ACCELERATION { 6000, 6000, 6000, 1500 }`  
  `#define DEFAULT_ACCELERATION 2500`  
  `#define DEFAULT_RETRACT_ACCELERATION 2000`  
  `#define DEFAULT_XJERK 10.0`  
  `#define DEFAULT_YJERK 10.0`  
  `#define DEFAULT_ZJERK 10.0`  
  `#define DEFAULT_EJERK 2.5`  
  * Configuration_adv.h :  
  `#define E0_CURRENT 650`  
  `#define FILAMENT_CHANGE_UNLOAD_LENGTH 70`  
  `#define FILAMENT_CHANGE_FAST_LOAD_LENGTH 70`  
  `//#define STEALTHCHOP_E`  


***Liens utiles :***

- [Réglages de votre FLSUN SR](https://www.lesimprimantes3d.fr/forum/topic/46585-r%C3%A9glage-de-votre-flsun-sr/)
- [Bien débuter avec la FLSUN SR](https://www.lesimprimantes3d.fr/forum/topic/47145-mon-retour-dexp%C3%A9rience-et-comment-bien-d%C3%A9buter-avec-la-flsun-sr/)
- [FAQ FLSUN SR](https://www.imprimante3d.shop/accueil/foire-aux-questions-flsun-sr-super-racer/)
- [Forum FLSUN SR](https://www.lesimprimantes3d.fr/forum/140-flsun-3d/)
- [Pièces détachées FLSUN SR](https://www.3djake.fr/piecesdetachees/pieces-detachees-pour-flsun-super-racer)
