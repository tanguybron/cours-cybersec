# Challenge Nikto

## Objectif du challenge : 
trouver le numéro OSVDB de la potentielle vulnérabilité de la machine docker déployée.

## Que faut-il faire ?
Récupérer les machines : 
    1) Télécharger le fichier [docker-compose.yml](./docker-compose.yml)
    2) Déployer et utiliser les machines : 

```shell 
nikto@Desktop:~$ docker-compose up -d
nikto@Desktop:~$ docker exec -it nikto_machine /bin/bash
``` 
    3) Analyser la machine avec nikto et lire le numéro OSVDB de la vulnérabilité trouvée.
