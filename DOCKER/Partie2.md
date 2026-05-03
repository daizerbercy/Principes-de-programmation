# Docker partie 2

## Gestion de volume avec Docker

``` shell
docker run -v
```
permet de **monter des volumes ou des répertoires de l'hôte** dans un conteneur pour assurer la persistance des données ou partager des fichiers

1. Bind mounts (montages liés)

``` bash
docker run -v /chemin/hote:/chemin/conteneur image
```

2. Volume gérés par Docker
``` shell
/var/lib/docker/volumes/
```

```shell
docker volume create monvolume
docker run -v monvolume:/chemin image
```

3. tmpfs
``` shell
docker run -tmpfs /chemin image
```

***
#### Test
``` shell
docker volume create monvolume
```

``` shell
docker volume ls
```

inspecter un volume
``` shell
docker volume inspect monvolume
```

supprimer un volume

``` shell
docker volume rm monvolume
```
PS: Il faut supprimer tous les conteneurs qui utilise le volume pour supprimer le volume.

***

``` shell
docker run -it -v monvolume:/data alpine sh
```

``` shell
docker rm -f <id_conteneur>
```


``` shell
docker run -it -v monvolume:/data alpine sh
```
lorsque tu relance cette on garde les modifications précédente.

***

#### Bind mounts
 à utilisé en projet

```
docker run -it -v ~/projets:/app alpine sh
```
Cette commande permet de synchronisé les données entre ``/app`` (dans docker) et  ``/projets`` (mon répertoire personnel)

Si j'effectue une modification dans l'un des répertoire ça se reflète aussi dans l'autre répertoire.


``` 
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=pass -v mysql_data:/var/lib/mysql mysql:8
```
ça marche sur Windows mais pas sur WSL


```
docker exec -it mysql mysql -u root -p 
```

créer un base de données et insérer des données

Arrêté le redémarré le et exécuter un autre conteneur et vérifier que les données sont bien accessible.

***
### Commandes mysql
```sql
SHOW DATABASES;
```

``` sql
USE nom_de_la_base;
```

``` sql
CREATE DATABASE nom_de_la_base;
```

```Sql
INSERT INTO nom_table (colonne1, colonne2, colonne3)
VALUES (valeur1, valeur2, valeur3);
```

``` Sql
CREATE TABLE plats (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(100),
    prix DECIMAL(5,2)
);
```

``` sql
EXIT;
```
***
### Gestion du réseau

``` shell
docker network ls
```
affiche les réseau

``` shell
docker network inspect bridge
```
bridge est le réseau par default


``` shell
docker run --network host nginx
```
ici on choisit de lancer Nginx sur le réseau host

``` shell
docker run --network none -it alpine sh
```
ici on lance la ligne de commande alpine sans réseau.

##### Créer votre propre réseau

``` shell
docker network create monreseau
```


``` shell
docker run -d --name site --network monreseau nginx
```

``` shell
docker run -d --name api --network monreseau alpine sleep 1000
```

***
Ajouter un conteneur à un réseau existant

``` shell
docker network connect monresau site
```

Le retirer 
``` shell
docker network disconnect monreseau site
```





