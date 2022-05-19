# Cours John the Ripper

L’outil John va nous être très utile pour le cracking de mot de passe. En effet, si un attaquant parvient d’une manière ou d’une autre à récupérer une base de donnée d’un site contenant les identifiants et mots de passe des utilisateurs, la grande majorité du temps, ce dernier ne pourra pas lire le mot de passe directement. En effet, une sécurité a été ajoutée pour stocker les mots de passe au cas où ce genre de situation arriverait.

Sans entrer dans les détails, les mots de passe sont stockés sous forme de hash, ce qui correspond à passer le mot de passe de l’utilisateur dans une fonction complexe à sens unique. Ce qui signifie que même avec un hash, il est impossible de récupérer directement le mot de passe en clair. Lors de la connexion le hash entré et le hash stocké sont comparés pour voir si ce sont les mêmes.

Cependant il n’est pas impossible de trouver un mot de passe à partir du hash.

John nous permet d’effectuer une attaque brute force simple, ou par dictionnaire lorsque nous avons un ou plusieurs hashes à disposition.

Imaginons un fichier mdp.hashes contenant le hash d’une session. Le fichier pourrait contenir une ligne comme suit : 
```jeremy:$1$XT.ZwPx4$LpAfbyGhDRZ3QSxdCzUqD/:19123:0:99999:7:::```
où
```$1$XT.ZwPx4$LpAfbyGhDRZ3QSxdCzUqD/```

correspond au hash du mot de passe de connexion.

Ainsi john pourra nous être utile à casser le mot de passe par une attaque par dictionnaire en tapant la commande suivante :

```john -w=liste.txt mdp.hashes```

Ainsi cette ligne demande à john de calculer tous les hash des mots contenus dans liste.txt et de le comparer au hash de la session. Si les deux hashes sont les mêmes, alors le mot de passe est trouvé et John s’arrête.