# API REST Flask + MySQL

## Description

API REST développée avec Flask permettant de gérer des étudiants via une base de données MySQL.  

---

## Technologies

- Python 3.12.3
- Flask
- MySQL
- mysql-connector-python

---

## Structure du projet

```
.
│
├── app.py          # Point d'entrée (API Flask)
├── config.py       # Configuration base de données
├── db.py           # Connexion MySQL
├── repository.py   # Requêtes SQL
```

---
## Installation

```bash
pip install flask mysql-connector-python
```

---
## Base de données

```sql
CREATE DATABASE school_db;
USE school_db;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

---
## Lancement

```bash
python app.py
```

API disponible sur :

```
http://localhost:5000
```

---

## Endpoints

### Récupérer tous les étudiants

```
GET /students
```

### Récupérer un étudiant par ID

```
GET /students/<id>
```

---
## Remarques

- Ce projet est un exemple simple destiné à l’apprentissage
- Assurez-vous que le serveur MySQL est en cours d’exécution
- Vérifier la cohérence entre la base de données et les requêtes SQL

---
## Daïzer BERCY
