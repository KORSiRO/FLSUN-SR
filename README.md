<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164060580-3fda5f97-c952-41f3-aea1-43b30f48e8a3.png" width="400"/>  
</p>
<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/164056911-da4a19c8-fc3c-45bd-b51c-186f05931f83.png" width="470"/>  
</p>  
  
# SOMMAIRE

- [Firmware](https://github.com/KORSiRO/FLSUN-SR#flsun-sr-firmware)
- [MAJ Firmware](https://github.com/KORSiRO/FLSUN-SR#maj-firmware)
- [Calibration](https://github.com/KORSiRO/FLSUN-SR/wiki/CALIBRATION)
- [Modifier son Firmware](https://github.com/KORSiRO/FLSUN-SR/blob/main/README.md#modifier-son-firmware)
- [Klipper](https://github.com/KORSiRO/FLSUN-SR#klipper)
- [Gcodes](https://github.com/KORSiRO/FLSUN-SR#gcodes)
- [Wiki](https://github.com/KORSiRO/FLSUN-SR#wiki)
- [Print Upgrades](https://github.com/KORSiRO/FLSUN-SR/blob/main/README.md#print-upgrades)
- [Achats/Upgrades](https://github.com/KORSiRO/FLSUN-SR#achats--upgrades)
- [Vidéos Utiles](https://github.com/KORSiRO/FLSUN-SR#vid%C3%A9os-utiles-)
- [Liens Utiles](https://github.com/KORSiRO/FLSUN-SR#liens-utiles-)


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# FIRMWARE  

- [Firmware Stock v1.3](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%20STOCK/Firmware%20v1.3)
- [Firmware Stock v1.4](https://github.com/KORSiRO/FLSUN-SR/tree/main/Firmware%20STOCK/Firmware%20v1.4)
- [Firmware Marlin Foxies Nano v3 / BTT SKR 1.3](https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/Firmwares/SR)
- [Firmware Marlin Guilouz Nano v3](https://github.com/Guilouz/Marlin-SuperRacer-MKS-Nano-V3)
- [Firmware BTT TFT70 / MKS TS35-R](https://github.com/KORSiRO/FLSUN-SR/tree/main/Ecran%20BTT-MKS)


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# MAJ Firmware

- [Vidéo MAJ Firmware v1.4](https://www.youtube.com/watch?v=yehdSc0RL4w) (*Marc Lacome*)

### 1. Installation firmware MKS Robin Nano v3 :

- Faire un `Reset EEPROM` avant de flasher le nouveau firmware : 
  - `M502` *(Reset EEPROM)*
  - `M501` *(Restore default)*   
  - `M500` *(Sauvegarder)*
- Choisir le `Firmware` en suivant les liens ci-dessus
- Formater une `carte SD` ou une `clé USB` de moins de `16Go` en `FAT32 4096 octets`  
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

<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>  

# 3. CALIBRATION

J'ai regroupé toutes les étapes de **CALIBRATION** sur mon wiki disponible ici : [Wiki Calibration](https://github.com/KORSiRO/FLSUN-SR/wiki/CALIBRATION))

<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# MODIFIER SON FIRMWARE  

Si vous souhaitez modifier votre firmware, en partant du Marlin de Foxies disponible à cette adresse [Marlin Foxies](https://github.com/Foxies-CSTL/Marlin_2.0.x/tree/FLSUN_BUGFIX-MULTI?fbclid=IwAR34Tz7Op_wXBo1DShOGLOJi6iBsfOE6q6NOg22aWTG1cRsf-gMyx2zhFOo), voici la marche à suivre :

- [7.4 Build your own Firmware](https://github.com/Foxies-CSTL/Marlin_2.0.x/wiki/7.TIPS#74build-your-own-firmware)

*Comme le précise Foxies, si vous souhaitez modifier, ajouter ou supprimer des paramètres seul le fichier `FLSUNQ_Config.h` doit être modifié !*


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# KLIPPER  

Si Klipper vous tente aller voir par ici > [KLIPPER](https://github.com/KORSiRO/All4Klipper/blob/main/README.md)


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# GCODES

Voici une liste des Gcodes les plus utilisés
- [Liste Gcodes](https://github.com/KORSiRO/FLSUN-SR/blob/main/Gcodes/README.md)


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# WIKI 

- [Wiki Foxies](https://github.com/Foxies-CSTL/Marlin_2.0.x/wiki)
- [Wiki MKS Robin Nano v3](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X/wiki)


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

# PRINT UPGRADES

***Si vous souhaitez imprimer des upgrades voici une liste comprenant des liens vers différentes upgrades.***

- [Print Upgrades](https://github.com/KORSiRO/FLSUN-SR/tree/main/Upgrades)


# ACHATS / UPGRADES

***Si vous souhaitez acheter et améliorer votre imprimante, voici une petite liste de quelques produits qui pourraient vous intéresser.***  

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


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

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


<p align="center">  
  <img src="https://user-images.githubusercontent.com/62854582/167669092-4a8a8bbb-ee5d-487c-b9f2-bc66dcab2f81.png" width="1666"/>  
</p>

#### ***Liens utiles :***

- [Astuces GCODE](https://github.com/Foxies-CSTL/Marlin_2.0.x/wiki/7.TIPS#77-gcodes_tips) 
- [Acheter la FLSUN SR sur le site FLSUN Officiel](https://flsun3d.com/products/super-racer-sr?variant=40603765964968)
- [Achat d'upgrades FLSUN SR](https://3dprintbeginner.com/flsun-super-racer-upgrades/)
- [Achat de pièces FLSUN SR UK](https://3dshop.uk/shop/?fbclid=IwAR1Y0GOOC41b5J-Bqt2wZyGOiTt_f7fpOraHMp70RvTT1GG_tVasPDtyA7A)
- [Achat de pièces FLSUN SR FR](https://www.3djake.fr/flsun?gclid=Cj0KCQjwheyUBhD-ARIsAHJNM-O0nvq2NI-9NGgqqKDdVpPXA_Pl542JmV7Xj7oKrFoWndvxpyJbVv8aAohHEALw_wcB)
- [Forum FLSUN SR](https://www.lesimprimantes3d.fr/forum/140-flsun-3d/)
- [Bien débuter avec la FLSUN SR](https://www.lesimprimantes3d.fr/forum/topic/47145-mon-retour-dexp%C3%A9rience-et-comment-bien-d%C3%A9buter-avec-la-flsun-sr/)
- [FAQ FLSUN SR](https://www.imprimante3d.shop/accueil/foire-aux-questions-flsun-sr-super-racer/)
   
       
*Toutes les informations collectées proviennent de différentes sources.  
Je tiens à remercier toutes les personnes qui proposent leur aides, participations et contributions.  
Grâce à elles, il est possible d'avoir beaucoup d'informations à disposition.   
Ce github a vu le jour pour permettre de faciliter les recherches à tous le monde.  
En espérant que vous trouviez réponses à vos questions :wink:*



*[Guilouz](https://github.com/Guilouz), [Foxies](https://github.com/Foxies-CSTL), [Marc Lacome](https://www.youtube.com/channel/UCLqBYBC_OC8KNELy-IhUVLQ), [pyriame](https://www.lesimprimantes3d.fr/forum/profile/13525-pyriame/), [Le GüeroLoco](https://www.youtube.com/channel/UCrFGsH4pplqjFXJqLcjykNQ), [JSTECH](https://www.youtube.com/channel/UCEnNq7HN3JwuOjVAEmzGEbw), [Motard Geek](https://www.lesimprimantes3d.fr/forum/profile/2-motard-geek/), [Les Imprimantes 3D](https://www.lesimprimantes3d.fr/), [3DPrintBeginner](https://3dprintbeginner.com), [Denis Gignac](https://www.youtube.com/channel/UCZaTi2oW15syhG-VStDF8QQ), [Olivier Richard 3DLand-Shop](https://www.youtube.com/channel/UC7RgbWvwyzr6SnVPcy7GbEA), [Infos et tutos Informatique](https://www.youtube.com/channel/UC25vp3h-86eAkkBLsV13FEg), [IAMAMAKER](https://www.youtube.com/channel/UC69hBzipW2Xp_xWK2dnpZ0A)*
