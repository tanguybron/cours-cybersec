# Reverse Shell
Avant de parler de reverse shell, il faudrait tout d’abord rappeler ce qu’est un shell.
Un shell est une couche logicielle qui fournit l’interface utilisateur du système d’exploitation. ( [wikipedia](https://fr.wikipedia.org/wiki/Interface_syst%C3%A8me) )
Différents shells existent : CMD, sh, bash, Powershell,...

Une autre notion avant de comprendre ce qu’est un reverse shell est qu’est-ce qu’un port ?
Un port informatique du point de vue logiciel est un système permettant aux ordinateurs de recevoir ou d’émettre des informations. ( [wikipedia](https://fr.wikipedia.org/wiki/Port_informatique#:~:text=En%20informatique%2C%20port%20informatique%20ou,qui%20d%C3%A9signe%20un%20portage%20informatique.) )

## Qu’est ce qu’un reverse shell ?

Pour dire ça simplement, c’est lorsqu’un ordinateur se connecte à un autre ordinateur mais que l’ordinateur initiateur transmet son shell à la destination. Ainsi, ce type d’attaque donne à l’attaquant un shell interactif sur une machine.

## Comment cela fonctionne-t-il ?
Vous n’êtes pas sans savoir que votre routeur vous protège d’un grand nombre de menaces qui pourraient venir de l’extérieur grâce à un firewall. En effet ce dernier n’accepte que des requêtes vers le port 80 et 443 de l’extérieur pour le http et le https. Toutes les autres sont bloquées. Cependant, toutes les requêtes et connexions sortantes sont autorisées sur n’importe quel port car l’ordinateur du réseau est considéré comme une machine de confiance. Cela permet à un attaquant de passer outre le firewall mit en place par le routeur. 

L’attaque commence avec une machine qui écoute sur un port (il s’agit de la machine de l’attaquant). Ensuite, la machine victime exécutera une commande qui la connectera à la machine attaquante et lui transmettra sa session. 

Peut-être vous demanderez vous pourquoi la machine victime voudrait à un moment donné exécuter cette commande… Cela peut être utile dans le domaine professionnel ou personnel si vous avez un ordinateur distant que vous voulez utiliser pour telle ou telle raison depuis un autre ordinateur, cela est possible. Dans le cas d’une attaque la commande pourra s’exécuter suite au téléchargement d’un fichier exécutable ou d’un fichier pdf ouvert avec un visionneur de pdf qui n’a pas été mis à jour.

## Et dans la pratique… Comment on fait ? (Metasploit)
Pour commencer, un attaquant va créer ou télécharger un payload qu’il pourra envoyer à sa victime. Un payload est un fichier qui va exécuter du code malveillant, et dans notre cas ouvrir une connexion entre l’attaquant et la victime.

Le module ```exploit/windows/fileformat/adobe_pdf_embedded_exe``` dans Metasploit nous permet de créer un payload pdf contenant un fichier exe dans son en-tête qui sera exécuté à l’ouverture du pdf. Il faudra configurer LHOST et LPORT comme l’adresse et le port de l’attaquant ou d’un serveur auquel les deux ordinateurs peuvent se connecter.

Une fois le payload préparé, il suffit de l’envoyer à la victime. Toutes les techniques sont possibles (email, lien, clé usb,...)

Désormais, il faut mettre en place le “listener” pour écouter et attendre une connexion sur le port spécifié dans LPORT lors de la création du payload.
Le module ```exploit/multi/handler``` fonctionne très bien. Il faut ensuite préparer l’écoute en faisant : ```set payload windows/meterpreter/reverse_tcp``` et en renseignant le LHOST et LPORT du payload pour dire à metasploit que nous avons un payload utilisant le protocole tcp et que nous allons ouvrir un meterpreter s’il y a une connexion d’une machine victime. Le meterpreter est un shell interactif qui permet à l’attaquant de faire un grand nombre de choses, upload/download de fichiers, stream de webcam, voir l’écran, créer des fichiers, ouvrir des pages web,...
Il faudra ensuite taper la commande exploit pour que la machine se mette sur écoute.

A partir de là, il suffit d’attendre que la victime ouvre le fichier malveillant qu’elle a téléchargé et l’attaquant aura un accès total à la machine.

## Tutoriel Complet 
Si vous voulez un tutoriel complet et imagé pour exécuter ces différentes manipulations, allez dans la rubrique tutoriel ou cliquez sur ce lien : [Tutoriel Reverse Shell](../reverse_shell/tuto-reverse-shell.md)