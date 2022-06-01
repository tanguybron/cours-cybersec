# Challenge Nikto

## Objectif du challenge : 
trouver le numéro OSVDB de la potentielle vulnérabilité de la machine docker déployée.

## Que faut-il faire ?
Récupérer les machines : 

* Télécharger le fichier [docker-compose.yml](./docker-compose.yml)

* Déployer et utiliser les machines : 

```console 
$ docker-compose up -d
$ docker exec -it nikto_machine /bin/bash
```

* Analyser la machine avec nikto et lire le numéro OSVDB de la vulnérabilité trouvée.
