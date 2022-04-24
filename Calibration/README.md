# DELTA CALIBRATION :

<img src="https://user-images.githubusercontent.com/62854582/164968249-0cc8d785-9708-43a9-9d65-7d5d514f637a.png" width="1000">

# CALIBRATION AUTOMATISÉ IMPRESSION 3D :

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
