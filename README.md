# FLSUN-SR FIRMWARE

- [Télécharger firmware 1.4 SD](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%201.4/Firmware%201.4%20NanoV3-TFcard)
- [Télécharger firmware 1.4 USB](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%201.4/Firmware%201.4%20NanoV3-Udisk)
- [Télécharger firmware SCREEN](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%201.4/Firmware%201.4%20Screen/DWIN_SET)

**1. Upgrade firmware FLSUN SR :**

- Formater une carte SD ou clé USB en `FAT32 4096`  
- Copier le fichier `Robin_nano_v3.bin` à la racine de la carte SD/clé usb  
- Connecter la carte SD/clé usb à l'imprimante et l'allumer  
- Attendre la fin de la MAJ

**2. Upgrade firmware Screen FLSUN SR :**

- Formater une carte SD en `FAT32 4096`  
- Copier le dossier `DWIN_SET` à la racine de la carte SD  
- Connecter la carte SD à l'écran et allumer l'imprimante  
- Attendre la fin de la MAJ

<img src="https://user-images.githubusercontent.com/62854582/163845798-b82c77e4-c3e4-41aa-9e31-cc1e15ac41fc.png" width="300">

# CALIBRATION

**1. PID Buse (firmware 1.4) :**

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

**2. PID Bed (firmware 1.4) :**

- Créer un fichier texte que l'on appellera `PID Bed.gcode`
- Intégrer dans ce fichier : `M303 E-1 S70 C8 U1`
- Noter ensuite les paramètres visible sur l'écran dans le menu `EEPROM` de la SR
- Imprimer le fichier `PID Buse.gcode` ou `PID Bed.gcode`, l'écran indique "impression terminée".
- La température de la buse va monter (PID en cours)
- Le PID est terminé quand la température est descendu à ~ 20° en dessous de la valeur `S` de départ
- On retourne dans le menu `EEPROM` et on vérifie que les données ont bien été modifiées
- On se rend dans `Console`sur l'écran de la SR et on rentre un `M500`pour sauvegarder les nouvelles valeurs

**PS** : `U1`permet d'envoyer à la carte mère les nouvelles valeurs du PID


