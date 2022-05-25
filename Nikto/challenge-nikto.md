# challenge Nikto

## Objectif du challenge : 
trouver le numéro OSVDB de la potentielle vulnérabilité de la machine docker déployée.

## Que faut-il faire ?
* Récupérer la machine sur docker hub : 
    * ```docker pull tanguybron/nikto```
    * ```docker run -it -p 80 tanguybron/nikto```

* Analyser la machine avec nikto et libre le numéro OSVDB de la vulnérabilité trouvée.