# OAuth 2 Registration

Avant qu’un **Client** ne puisse communiquer avec un **Authorization Server**, il faut procéder à un enregistrement.

Cet enregistrement peut se faire de différentes manières _\(hors spec OAuth 2\)_.

* Par API.
* Via une interface applicative.
* Offline.
* Un mix.
* L'**Authorization Server** doit à minima obtenir les informations suivantes :
  * **Client type** : **confidential** ou **public**.
  * **Redirect URIs** : La ou les URIs vers lesquelles l'**Authorization Server** redirigera le **Resource Owner** après validation des autorisations.
* Si le **client type** est **public**, l'**Authorization Server** ne fournira pas de **Client Secret** est peut restreindre l’accès aux ressources.

