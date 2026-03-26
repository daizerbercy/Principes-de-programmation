# Service Web SOAP en Java (JAX-WS)
## Description
Implementation d'un service web SOAP simple en Java avec JAW-WS et JAXB.
Il expose plusieurs opérations accessibles via HTTP et échange des données au format XML

Le service permet :

- d’effectuer une conversion simple (`convertir`)
- de calculer une somme (`somme`)
- de retourner un objet `Etudiant` (`getEtudiant`)

***
## Architecture

```
src/
├── MonserviceWeb.java   # Service SOAP (endpoints)
├── Etudiant.java        # Modèle de données (JAXB)
└── Application.java     # Déploiement du service
```

***
## Lancement

1. Compilation
```
javac *.java
```

2. Exécution
```
java Application
```

3. Accéder au service via :
```
http://localhost:8888/?wsdl
```

***
## Technologies

- Java SE 8 (Corretto)
- JAX-WS (Web Services SOAP)
- JAXB (Conversion objets Java ↔ XML)

***
## Exemple de réponse

```
<etudiant> 
	<identifiant>1</identifiant> 
	<nom>Mario</nom> 
	<moyenne>19.0</moyenne> 
</etudiant>
```

***
## Remarques

- Ce projet est un exemple simple destiné à l’apprentissage
- Il fonctionne en local (pas de serveur applicatif externe requis)
- Il n'y a pas de securité et de gestion des erreurs

***
## Daïzer BERCY

Service Web Java SOAP
