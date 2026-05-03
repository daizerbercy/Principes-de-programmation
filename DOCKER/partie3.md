# Docker partie 3
dockerfile :
- sert a automatiser la création d'image docker
- c'est lorsque que l'on souhaite juste lancé une seule app


⚠️ **remarque :**
il est possible que pour que ça marche il faut exécuté l'app en tant que **root.**
- lancé le terminal en tant qu'administrateur sur PowerShell. (si vous utilisé Windows)
- passé en root sur linux `sudo su` (si vous utilisé Linux ou WSL2)


1. Je modifie le main de mon application flask (la fin)
``` python
from flask import Flask, jsonify, request

# créer l'application Flask

app = Flask(__name__)

#Une liste d'etudiants
  
students = [

    {"id":1, "name":"Youcef", "age":21},

    {"id":2, "name":"Samir", "age":41},

    ]

"""
......
"""
# Activer mode Debug pour voir les erreurs et recharger automatiquement le serveur
# Partie à modifier si dessous.
if __name__ == '__main__':
	#app.run(debug=True)
    app.run(host='0.0.0.0', port=80, debug=True)
```

2. je test en local
``` sh
python app.py
```
⚠️ remarque :
	Il faut adapté en fonction du nom de votre fichier python. vous l'avez peut être appelé d'une autre manière.

3.  je vérifie que ça fonction :
```
http://127.0.0.1:80
```

4. Je crée un dockerfile.
``` dockerfile
#1. On utilise une image python officielle

FROM python:3.12-slim

  

#2. On définit le répertoire de tavail

WORKDIR /app

  

#3. On install Flask

RUN pip install Flask

  

#4. On copie le fichier dans l'image

COPY app.py .

  

#5. On document le port utilisé

EXPOSE 5000

  

#6. On définit la commande qui démmare l'application

CMD ["python","app.py"]
```
⚠️ remarque : 
- attention au "." pour la commande `COPY`
- adapté le nom `app.py` en fonction de comment il se nomme dans votre répertoire courant.

5. Je lance les commandes suivante
 ```bash
 docker build -t mon-app .
 docker run -p 4900:80 mon-app
 ```
 ⚠️ remarque : 
- attention au "."
- `mon-app` et le port `4900` peut être adapté selon vos envie.
 
je vérifie que ça fonction :
```
http://127.0.0.1:4900
```
 ⚠️ remarque :
 - Le port est celui que vous avez choisit lors du `docker run -p 4900:80 ...`
***

## Héberger un image sur le cloud
le fonctionnement est équivalent à GitHub.

je crée mon compte ``daizerbercy`` sur (https://hub.docker.com/)

```sh
docker login
```

je test l'app sur docker  :
- comme vu précédemment pour m'assurer de son fonctionnement 
```shell
 docker build -t mon-app .
 docker run -p 4800:80 mon-app
```


1. je prépare un image pour Docker Hub
```sh
docker tag mon-app daizerbercy/myimage:1
```

2. j'envoie l'image sur Docker
```sh
docker push daizerbercy/myimage:1
```
⚠️ Remarque :
- l'image va apparaitre dans (https://hub.docker.com/repositories/daizerbercy)


3. si quelqu'un veux utilisé l'image hébergé sur le cloud il doit faire :
```sh
docker run -p <port>:80 daizerbercy/myimage:1
```
⚠️ Remarque :
- Cette image peut être lancé de n'importe où.  (le téléchargement sera fait automatiquement)
- il faut choisir un port ex : `4800`

le site sera accessible sur :
```
http://127.0.0.1:<port>
```
- le port est celui défini lors du run. ex : `4800`

***

## Docker Compose

On a pas eu le temps d'approfondir cette partie.

on utilise Docker compose quand on souhaite lancé plusieurs app ou services en même temps.

- Après avoir écrit les codes  (voir image sur WhatsApp)

testé :
```
docker-compose up
```
