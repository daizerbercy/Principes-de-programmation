# API REST de gestion des étudiants

## Description

Cette application est une API REST simple développée avec Flask permettant de gérer une liste d’étudiants.  
Elle prend en charge les opérations CRUD : création, lecture, mise à jour et suppression.

---

## Technologies utilisées

- Python 3.12.3
- Flask

---

## Installation

1. Installer les dépendances :
```bash
pip install flask
```

2. Lancer le serveur :
```bash
python api_student.py
```

Le serveur démarre sur :
```
http://127.0.0.1:5000/
```

---

## Endpoints principaux

### Vérification API

- `GET /`
    
- Retour : message de bienvenue
    
### Récupérer tous les étudiants

- `GET /students`
    
### Récupérer un étudiant

- `GET /students/<id>`
    
### Ajouter un étudiant

- `POST /students`
    
- Body (JSON) :
    
```json
{
  "name": "Nom",
  "age": 20
}
```

### Modifier un étudiant

- `PUT /students/<id>`
	
- Body (JSON) :
	
```json
{
  "name": "Nom",
  "age": 22
}
```
### Supprimer un étudiant

- `DELETE /students/<id>`

---

## Codes de réponse

- `200` : Succès
    
- `201` : Ressource créée
    
- `404` : Ressource non trouvée

---

## Remarques

- C'est Projet pédagogique pour comprendre le fonctionnement des API REST avec Flask.

- Les données sont stockées en mémoire (pas de base de données)
    
- Les données sont perdues à chaque redémarrage du serveur
    
- Aucun système d’authentification n’est implémenté
    
---

## Daïzer BERCY
API REST Python avec Flask
