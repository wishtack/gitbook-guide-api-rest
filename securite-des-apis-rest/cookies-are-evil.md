# Cookies are EVIL

![Cookies are Evil!](../.gitbook/assets/cookies-are-evil.jpg)

Les "cookies" nous **exposent à des vulnérabilités de type C.S.R.F.** _\(Cross Site Request Forgery\)_ que nous aborderons plus tard.

Les clients ne sont **pas toujours des "browsers"** _\(Mobile, Desktop, un micro-service, un partenaire\)_.

Les “cookies” seront **envoyés à chaque requête**.

Il y a un **couplage fort entre le "cookie" et la session**. En revanche, en utilisant le "header" `Authorization` nous pouvons envoyer des requêtes avec des “tokens” différents à la même API.  
  
Exemple : une session avec plusieurs comptes utilisateurs sans établir aucun lien entre les utilisateurs. C’est le cas sur les services google / twitter / facebook etc… ou encore **la fonctionnalité "voir ma page facebook en tant que X".**

