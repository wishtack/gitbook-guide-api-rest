# C.S.R.F. Mitigation

En attendant l’abandon des _credentials_ de type _cookie_, _basic auth_ et certificat client, une solution de mitigation des attaques de type C.S.R.F. est de positionner un _cookie_ _\(non http-only\)_ contenant **un** _**token**_ **aléatoire et imprévisible** _**\(un nonce\)**_.

L’application client _\(JavaScript\)_ doit alors envoyer la valeur de ce _token_ dans le _header_ `Authorization` _\(Ex. : `Authorization: Bearer ..., Csrf: ...`\)_ à chaque requête.

L’API n’a plus qu’à **comparer les deux valeurs présentes dans le** _**cookie**_ **et dans le** _**header**_ pour s'assurer qu'il s'agit du bon token.

_En effet, dans le cas d'une attaque C.S.R.F., l'attaquant utilise les cookies sans y avoir accès en lecture ou écriture._

