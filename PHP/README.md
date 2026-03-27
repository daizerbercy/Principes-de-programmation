# PHP + API TEST Flask

## Description

Mini application PHP consommant une API REST Flask pour afficher une liste d’étudiants.

---
## Technologies utilisées

- PHP (XAMPP)
- Python 3.12.3 
- Flask
- HTML / CSS

---
## Structure du projet

```
student_client/  
│  
├── assets/  
│ └── style.css  
│  
├── config/  
│ └── config.php  
│  
├── services/  
│ └── StudentService.php  
│  
├── tests/  
│ └── test_api.php
| └── test_api1.php
│ └── test_api2.php
| └── test_api3.php
| └── test_api4.php
| 
├── views/  
│ └── students.php
| 
├── test_api5.php # point d’entrée principal
```

---
## Installation et lancement

1. Cloner le projet dans XAMPP 
Placer le dossier dans :
``` powershell
C:\xampp\htdocs\
```

2. Lancer l'API Flask situé dans : https://github.com/daizerbercy/Principes-de-programmation/blob/main/API-REST/api_student.py
``` shell
python api_student.py
```

API accessible sur :
```
http://127.0.0.1:5000/students
```

3. Demarrer apache via XAMPP Control Panel

4. Lancer le projet PHP
Dans le navigateur :
```
http://localhost/student_client/test_api5.php
```

---
## Fonctionnalités

- Récupération des étudiants via une API REST
- Affichage dynamique en PHP
- Architecture simple :
  - `config/` → configuration (URL API)
  - `services/` → logique métier (appel API)
  - `views/` → affichage HTML
  - `assets/` → styles CSS.
  - `tests/` → scripts de test API

---
## Remarques
- Ce projet est un exemple simple destiné à l'apprentissage
- La structure est volontairement simple et ne reflète pas un projet complet de production

---
## Daïzer BERCY
