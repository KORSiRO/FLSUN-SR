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

- [Firmware Foxies Nano v3 / BTT SKR 1.3](https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/Firmwares/SR)

### 1. Installation firmware MKS Robin Nano v3 :

- Faire un `Reset EEPROM` avant de flasher le nouveau firmware : 
  - `M502` *(Reset EEPROM)*   
  - `M500` *(Sauvegarder)*
- Choisir le `Firmware` en suivant les liens ci-dessus
- Formater une `carte SD` ou une `clé USB` en `FAT32 4096 octets`  
- Copier le fichier `Robin_nano_v3.bin` à la racine de la carte SD/clé USB 
- Connecter la carte SD/clé usb à l'imprimante et l'allumer 
- Attendre quelques secondes que l'écran arrive à l'accueil
- Retirer la `carte SD` de l'imprimante
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

- Faire une marque à `120 mm`
- Retirer le PTFE du dessous de l'extrudeur *(extrusion à froid)*
- Extruder `100mm`
  - `M302 S0` *(pour pouvoir extruder à froid)*
  - `M83` *(pour passer en mode relatif)*
  - `G1 E100 F100` *(pour extruder 100mm)*
- Relever la longueur extrudée
- Récupérer les Steps actuel avec la commande
  - `M92`
- On fait le calcul suivant
  - `Steps actuel x 100mm` = `Steps pour 100mm`
  - `Steps pour 100mm / Longueur extrudée` = `Nouvelle valeur Steps`
- Entrer la commande
  - `M92 E...` *(remplacer `...`par la nouvelle valeur trouvée, deux décimales maximum)*
- Entrer la commande
  - `M500` *(Sauvegarder)*

- ***Je vous mets à disposition un fichier Excel que j'ai créé pour faciliter les calculs de calibration :***
  - [CALIBRATION AUTOMATISÉ IMPRESSION 3D](https://github.com/KORSiRO/FLSUN-SR/raw/main/Calibration/CALIBRATION%20AUTOMATIS%C3%89%20IMPRESSION%203D.xlsm)

<img src="https://user-images.githubusercontent.com/62854582/164967442-7625912c-e8dd-4232-b42c-b5381321197a.png" width="900">


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
- Réglez votre Z Offset
  - Chauffer la buse à votre température d'impression *(200-220° et sans filament pour éviter qu'il ne coule de la buse)*
  - Chauffer le lit à votre température d'impression *(60-70°)*
  - Déplacer la buse à la hauteur `Z=0`
  - Placer un papier et ajuster le Z-Offset depuis l'écran de la SR
  - Sauvegarder

Si besoin se référer au document `Delta Calibration Calculator`

- [Delta Calibration Calculator](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3/files/8146727/Delta.Calibration.Calculator.zip) *(Guilouz)*   

- [Vidéo Delta Calibration](https://www.youtube.com/watch?v=kgCOhYoABYo&ab_channel=IAMAMAKER) (*IAMAMAKER*)

### 5. Linear Advance

Voici une vidéo du GüeroLoco qui explique tout en détails et de façon précise !
- [Linear Advance](https://www.youtube.com/watch?v=f6fzJTsnpds&ab_channel=LeG%C3%BCeroLoco)

# MODIFICATIONS FIRMWARE  

- [Modifications Firmware Guilouz](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3#possible-changes)  

# KLIPPER  

Si Klipper vous tente aller voir par ici > [KLIPPER](https://github.com/KORSiRO/FLSUN-SR/tree/main/Klipper)

# ACHATS / UPGRADES

- [Alimentation MEAN WELL 350w](https://fr.aliexpress.com/item/1005002054981187.html?gatewayAdapt=glo2fra&spm=a2g0o.order_list.0.0.21ef5e5bi97cvc)
- [BondTech LGX Lite Large Gears](https://www.3djake.fr/bondtech/extrudeuse-lgx-lite-large-gears?gclid=Cj0KCQjw6pOTBhCTARIsAHF23fLTZgbtQpC4bbwAT2e_H9K49WKUpjRObBl-nS-dZ4m-in6CQF5-uQEaAnnFEALw_wcB)
- [Direct Drive Sherpa Mini](https://fr.aliexpress.com/item/1005002487727392.html?aff_fcid=9acd42f568964aa1b70ac68b3436e745-1650800119514-00039-_ADRvOs&tt=CPS_NORMAL&aff_fsk=_ADRvOs&aff_platform=portals-tool&sk=_ADRvOs&aff_trace_key=9acd42f568964aa1b70ac68b3436e745-1650800119514-00039-_ADRvOs&terminal_id=807486d66e2f4b4da99660d6cc6d73fb&afSmartRedirect=y)
- [Heatbreak Bi-Metal](https://www.amazon.fr/Bim%C3%A9tallique-thermique-temp%C3%A9rature-imprimante-Creality/dp/B0971FNCM4/ref=sr_1_1?__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=3LLF9IN7JCGUA&keywords=Bim%C3%A9tallique+thermique+en+cuivre+et+titane+TC4+haute+temp%C3%A9rature+pour+imprimante+3D+CR10+S4+S5+Ender+3+V2+Ender3+Pro+Ender+5+CS3+Hotend+Upgrade&qid=1650799920&s=industrial&sprefix=bim%C3%A9tallique+thermique+en+cuivre+et+titane+tc4+haute+temp%C3%A9rature+pour+imprimante+3d+cr10+s4+s5+ender+3+v2+ender3+pro+ender+5+cs3+hotend+upgrade%2Cindustrial%2C56&sr=1-1)  
- [Magnet MK10 v2](https://www.hotends.fr/fr/accessoires/71-234-magnetmk10-v2.html#/47-qualite-capricorn_xs_19x4mm/76-extrudeur-taraudage_g1_8_m10/100-longueur-55_cm_flsun_sr)
- [OMG v2S](https://www.amazon.fr/Extrudeur-imprimante-double-entrainement-rapport/dp/B09PC93FFB)
- [Phaetus Hotend Rapido UHF](https://www.3djake.fr/phaetus/hotend-rapido-uhf)
- [Pièces de rechange SR](https://www.3djake.fr/piecesdetachees/pieces-detachees-pour-flsun-super-racer)
- [Plateau PEI](https://fr.aliexpress.com/item/1005003198020145.html?aff_fcid=a7a2f9a1cd5b4b988651b158c3cb547c-1650799798770-00492-_AC1P64&tt=CPS_NORMAL&aff_fsk=_AC1P64&aff_platform=shareComponent-detail&sk=_AC1P64&aff_trace_key=a7a2f9a1cd5b4b988651b158c3cb547c-1650799798770-00492-_AC1P64&terminal_id=807486d66e2f4b4da99660d6cc6d73fb&afSmartRedirect=y)
- [PTFE Capricorn](https://www.amazon.fr/Capricorn-Raccords-pneumatiques-coupe-tube-imprimante/dp/B089LXX6V5/ref=sr_1_3?__mk_fr_FR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=5QHLRUQP3K9F&keywords=reality%2BOfficial%2BCapricorn%2BBowden%2BPTFE%2BTubing%2BT%C3%A9flon%2BTube%2BCapricorn%2BPremium%2BXS%2BBowden%2Bpour%2Bfilament%2Bde%2B1%2C75%2Bmm%2Bavec%2BRaccord%2BPneumatique%2BPC4-M6%2Bet%2BPC4-M8%2Bet%2BCoupe-tube%2Bpour%2BToutes%2BLes%2BImprimantes%2B3D&qid=1650800069&sprefix=reality%2Bofficial%2Bcapricorn%2Bbowden%2Bptfe%2Btubing%2Bt%C3%A9flon%2Btube%2Bcapricorn%2Bpremium%2Bxs%2Bbowden%2Bpour%2Bfilament%2Bde%2B1%2C75%2Bmm%2Bavec%2Braccord%2Bpneumatique%2Bpc4-m6%2Bet%2Bpc4-m8%2Bet%2Bcoupe-tube%2Bpour%2Btoutes%2Bles%2Bimprimantes%2B3d%2Caps%2C73&sr=8-3&th=1)
- [Ventilateur Bloc de chauffe 4010](https://fr.aliexpress.com/item/1005003474807144.html?gatewayAdapt=glo2fra&aff_fcid=762c8e71f3b24783ba9e88342ecdbac5-1650800269612-00990-_u9niyN&aff_fsk=_u9niyN&aff_platform=api-new-link-generate&sk=_u9niyN&aff_trace_key=762c8e71f3b24783ba9e88342ecdbac5-1650800269612-00990-_u9niyN&terminal_id=807486d66e2f4b4da99660d6cc6d73fb&afSmartRedirect=y)
- [Ventilateurs Turbo 5015](https://fr.aliexpress.com/item/32867278180.html?aff_fcid=c3e167dd4d144ce993f8d854053c0b51-1650799837790-05229-_A1Yn9q&tt=CPS_NORMAL&aff_fsk=_A1Yn9q&aff_platform=shareComponent-detail&sk=_A1Yn9q&aff_trace_key=c3e167dd4d144ce993f8d854053c0b51-1650799837790-05229-_A1Yn9q&terminal_id=807486d66e2f4b4da99660d6cc6d73fb&afSmartRedirect=y)
- [Volcano MAX Hotends.fr](https://www.hotends.fr/fr/accueil/121-pack-v-max.html)
- [Volcano Trianglelab](https://fr.aliexpress.com/item/4000012110390.html?spm=a2g0o.productlist.0.0.669a63e4YIjKLt&algo_pvid=44039fdb-9ffe-4438-a24a-f9b54e87f1f7&algo_exp_id=44039fdb-9ffe-4438-a24a-f9b54e87f1f7-9&pdp_ext_f=%7B%22sku_id%22%3A%2210000000031213284%22%7D&pdp_pi=-1%3B8.57%3B-1%3B-1%40salePrice%3BEUR%3Bsearch-mainSearch)  


#### ***Vidéos utiles :***  

- [Assemblage de la FLSUN SR](https://www.youtube.com/watch?v=59f16PuayAU&t=1s) *(FLSUN)*
- [Installation de l'extrudeur OMG V2-S](https://www.youtube.com/watch?v=dvHlawF66Nw) *(My Tech Fun)*
- [Modification du capteur de nivellement automatique](https://www.youtube.com/watch?v=T1W7mJphzoA) *(JSTECH)*
- [Changement du firmware](https://www.youtube.com/watch?v=z3LmcFhDHHk&ab_channel=JSTECH) *(JSTECH)*
- [Maintenance Extrudeur](https://www.youtube.com/watch?v=TFeJfY321w8&ab_channel=DennisGignac) *(Dennis Gignac)*
- [Maintenance extrudeur + installation PEI](https://www.youtube.com/watch?v=aKYDvgTuacc&t=3s&ab_channel=JSTECH) *(JSTECH)*   
- [Remplacement de l'extrudeur](https://youtu.be/rzaumVlEIZM) *(FLSUN)*
- [Ajuster la tension des courroies](https://www.youtube.com/watch?v=N3sxU1_EIXY&ab_channel=FLSUN) *(FLSUN)*  
- [Maintenance des courroies et des rails linéaires](https://www.youtube.com/watch?v=05de4OFZCg0&ab_channel=DennisGignac) *(Dennis Gignac)*
- [Remplacement d'un chariot de roulement à billes sur la FLSun SR](https://www.youtube.com/watch?v=EmRWLrZj9kU&ab_channel=LeG%C3%BCeroLoco) *(Le GüeroLoco)*
- [Remplacement des rails linéaires](https://youtu.be/Kz_pey1oJfk) *(FLSUN)*
- [Amélioration FLSUN SR](https://www.youtube.com/watch?v=qsMoB8AFH08&ab_channel=JSTECH) *(JSTECH)*  
- [Mise à jour et réglages Flsun SuperRacer](https://www.youtube.com/watch?v=1fjbWBlSdbM&ab_channel=OlivierRichard3DLand-Shop) *(Olivier Richard 3DLand-Shop)*  
- [Imprimer via PC > USB](https://youtu.be/wfSc23aPTmI) *(FLSUN)*
- [Flsun Super racer réglages Cura](https://www.youtube.com/watch?v=cN8M4Pxr6G8&ab_channel=Infosettutosinformatique) *(Infos et tutos informatique)*

#### ***Liens utiles :***

- [Acheter la FLSUN SR sur le site FLSUN Officiel](https://flsun3d.com/products/super-racer-sr?variant=40603765964968)
- [Achat d'upgrades FLSUN SR](https://3dprintbeginner.com/flsun-super-racer-upgrades/)
- [Forum FLSUN SR](https://www.lesimprimantes3d.fr/forum/140-flsun-3d/)
- [Bien débuter avec la FLSUN SR](https://www.lesimprimantes3d.fr/forum/topic/47145-mon-retour-dexp%C3%A9rience-et-comment-bien-d%C3%A9buter-avec-la-flsun-sr/)
- [FAQ FLSUN SR](https://www.imprimante3d.shop/accueil/foire-aux-questions-flsun-sr-super-racer/)
   
       
*Toutes les informations collectées proviennent de différentes sources.  
Je tiens à remercier toutes les personnes qui proposent leur aides, participations et contributions.  
Grâce à elles, il est possible d'avoir beaucoup d'informations à disposition.   
Ce github a vu le jour pour permettre de faciliter les recherches à tous le monde.  
En espérant que vous trouviez réponses à vos questions :wink:*



*[Guilouz](https://github.com/Guilouz), [Foxies](https://github.com/Foxies-CSTL), [pyriame](https://www.lesimprimantes3d.fr/forum/profile/13525-pyriame/), [Le GüeroLoco](https://www.youtube.com/channel/UCrFGsH4pplqjFXJqLcjykNQ), [JSTECH](https://www.youtube.com/channel/UCEnNq7HN3JwuOjVAEmzGEbw), [Motard Geek](https://www.lesimprimantes3d.fr/forum/profile/2-motard-geek/), [Les Imprimantes 3D](https://www.lesimprimantes3d.fr/), [3DPrintBeginner](https://3dprintbeginner.com), [Denis Gignac](https://www.youtube.com/channel/UCZaTi2oW15syhG-VStDF8QQ), [Olivier Richard 3DLand-Shop](https://www.youtube.com/channel/UC7RgbWvwyzr6SnVPcy7GbEA), [Infos et tutos Informatique](https://www.youtube.com/channel/UC25vp3h-86eAkkBLsV13FEg), [IAMAMAKER](https://www.youtube.com/channel/UC69hBzipW2Xp_xWK2dnpZ0A)*
