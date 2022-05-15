# ADVANCED DELTA CALIBRATION

<img src="https://user-images.githubusercontent.com/62854582/168473090-fb103b93-e0a6-467e-88ee-21d8095c0e28.png" width="400">

- [Télécharger](https://www.thingiverse.com/thing:745523)

# YACS CALIBRATION SQUARE :

<img src="https://user-images.githubusercontent.com/62854582/168472875-693bbd2a-6275-4b8e-b10d-9df140a27f79.png" width="400">

- [Télécharger](https://www.thingiverse.com/thing:2563185)



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
  - `PID_FUNCTIONAL_RANGE 10`   ***Intervalle température PID actif. Pour 200° le PID sera donc actif entre 195° et 205°***


***Cette modification permet d'avoir un écrat de température lors du PID beaucoup plus faible***
