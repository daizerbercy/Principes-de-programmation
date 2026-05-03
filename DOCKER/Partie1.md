# Docker partie 1
Docker est une plateforme qui permet de créer, déployer et exécuter des applications dans des conteneurs.

Un conteneur est un environnement léger qui contient :
- ton application
- ses dépendances 
- sa configuration.

Avantage de docker :
- La portabilité
- Isolation
- Légèreté
- Déploiement rapide

Intro rapide sur le Cloud

Linux containers LXC -> c'est le debut de la technologie de conteneurisation.

## Commande importante

``` shell
docker version
```

```shell
docker image ls
```

```shell
docker run hello-world
```

Montre les images ouverte.
```shell
docker ps -a
```


Lancer image alpine (light distro linux) 
```shell
docker run -it alpine:latest /bin/sh
```

dans docker :
installer curl dans docker
```shell
apk add --no-cache curl
```


~~si j'exit et je relance docker les données ne sont pas conserver.~~

```shell
docker run -it alpine:latest /bin/sh
```

Si tu veux conserver tu peux export vers tar et faire un import du tar.

Tu ne vas jamais faire ça en entreprise mais il y a ça :
```
docker export 737f33c02c3e -o mycontener.tar
```

Creer une image docker à partir du mycontener.tar
```shell
docker import mycontener.tar myimage:V1
```


Il faut verifier les images car il y a possibilité de supp tout un systeme d'exploitation avec une image docker.

Pour supprimer tu supprime d'abord les conteneur et ensuite l'image

Pour avoir les conteneur ID a supp
``` shell
docker ps -a
```

Tu mets toutes les id a supprimée.
``` shell
docker rm 42ea50933e4c
```

Pour supprimer l'image :
``` shell
docker rmi hello-world:latest
```

Raccourci pour forcer snas avoir a supprimer les conteneurs avant :
``` shell
docker rmi -f hello-world:latest
```


### Utiliser Serveur nginx sur docker.
Utiliser port nginx 80

``` shell
docker run -d -p 8080:80 [--name nomServeur] nginx
```

-d : detacher
-p : port
--name nomServeur optionnelle 

Pour y acceder :
```
http://localhost:8080
```

Ici on a choisit le port 8080.

Pour entre dans le serveur nginx
``` shell
 docker exec -it monserveur bash
```

Pour modifier le html du localhost
``` shell
cd /usr/share/nginx/html
```

``` shell
apt update
```

``` shell
apt install nano
```

Tu peux maintenant modifier la page html

``` shell
nano /usr/share/nginx/html/index.html
```

Pour arrêter le serveur Nginx
``` shell
docker stop f3bba176494c 
```

