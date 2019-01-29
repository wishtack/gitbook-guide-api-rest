# C.S.R.F. Mitigation

En attendant l’abandon des "credentials" de type "cookie", "basic auth" et certificat client, une solution de mitigation des attaques de type C.S.R.F. est de positionner un "cookie" _\(non http-only\)_ contenant **un "token" aléatoire et imprévisible** _**\(un nonce\)**_.

L’application client _\(JavaScript\)_ doit alors envoyer la valeur de ce "token" dans le "header" `Authorization` _\(Ex. : `Authorization: Bearer ..., Csrf: ...`\)_ à chaque requête.

L’API n’a plus qu’à **comparer les deux valeurs présentes dans le "cookie" et dans le "header"** pour s'assurer qu'il s'agit du bon token.

_En effet, dans le cas d'une attaque C.S.R.F., l'attaquant utilise les cookies sans y avoir accès en lecture ou écriture._

