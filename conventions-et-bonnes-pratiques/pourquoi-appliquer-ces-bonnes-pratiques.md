# Pourquoi Appliquer ces Bonnes Pratiques

Au delà de la **généricité** et la **facilité** de **compréhension** et **d’implémentation**, l’application de ses bonnes pratiques permet d’implémenter des librairies et des **connecteurs génériques** sans aucune connaissance de l’API.

* Un cache peut facilement :
  * Anticiper la récupération de la section suivante d’une ressource paginée.
  * Récupérer une ressource depuis sa collection en cache.
  * Maintenir la synchronisation entre les données locales et celles de l’API _\(Progressive Web Apps\)_.
  * [https://github.com/wishtack/wishtack-steroids/tree/master/packages/rest-cache](https://github.com/wishtack/wishtack-steroids/tree/master/packages/rest-cache)
* Un connecteur générique peut gérer les autorisations d’accès aux ressources ou même filtrer les propriétés _readonly_ ou _hidden_.

