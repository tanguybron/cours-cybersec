# Challenge Nikto

## Objectif du challenge : 
trouver le numéro OSVDB de la potentielle vulnérabilité de la machine docker déployée.

## Que faut-il faire ?
* Récupérer les machines : 
    * Télécharger le fichier [docker-compose.yml](./docker-compose.yml)
    * ```console docker-compose up -d``` (après avoir exécuté cette commande, le serveur web est lancé et est disponible à l'adresse : 10.5.0.2)
    * ```docker exec -it nikto_machine /bin/bash``` (cela lancera la machine attaquante avec nikto installé)
```shell 
docker-compose up -d
```
* Analyser la machine avec nikto et lire le numéro OSVDB de la vulnérabilité trouvée.
