# Les 5 règles et ½ de l’API ReST

## **Uniforme**

* L’interface est uniforme à tous les niveaux. Tous les éléments _\(et connecteurs\)_ communiquent en utilisant la même interface.
* Chaque ressource est identifiée de façon unique et canonicalisée avec son URL.

## **Stateless**

* Une API ReST ne doit pas maintenir de session.

Cela évite entre autres, les problèmes de "load balancing" par exemple.

## **Cacheable**

* Il doit être possible de mettre les ressources en cache à tous les niveaux _\(front, connecteur intermédiaire, back, etc…\)_.
* Il doit être possible d’utiliser les implémentations standards de cache HTTP.

## **Client / Serveur : "Separation of Concerns"**

* L’API ReST n’est pas concernée par l’affichage, les interactions utilisateur et la session.
* Tous ces éléments doivent être gérés par le client _\(Ex. : application web frontend\)._

## **Layered**

* La présence de “connecteurs” intermédiaires doit être implicite pour le client et le serveur _\(composant de cache / sécurité etc…\)_.

## Code à la demande

Règle optionnelle ou plutôt inadaptée.

C’est le paramètre “extra” que l’on retrouve dans certaines RFC pour garder un peu de souplesse.

#### 3.5. Les formats d’échange {#3.5}

* En théorie, le format d’échange est libre.
* En pratique, le format doit être standard et non-linéaire _\(Hypermedia\)_.
* Plus concrètement, le format le plus utilisé aujourd’hui est le JSON.
  * L’univers JavaScript est en expansion permanente.
  * Contrairement aux technologies backend habituelles, le nombre de librairies et d’outils utilisés est volontairement restreint pour éviter de surcharger les clients JavaScript.
  * On retrouve des outils JSON dans tous les langages.
  * JSON est facile et rapide \(au sens performance\) à manipuler.

#### 3.6. Les méthodes HTTP utilisées {#3.6}

* **GET** : Récupération d’une ressource ou d’une collection.
* **POST** : Création d’une ressource_._
* **PUT** : Remplacement d’une ressource ou d’une collection.
* **PATCH** : Modification d’une ressource ou d’une collection.
* **DELETE** : Suppression d’une ressource ou d’une collection.
* Plus exactement :
  * La méthode **POST** peut servir à modifier une ressource mais ce n’est pas recommandé.
  * La méthode **PUT** peut servir à créer une ressource si on en connaît l’identifiant par avance par exemple. La seule contrainte sur la méthode **PUT** est qu’elle doit être idempotente. Le nombre d’exécution d’une même requête ne doit pas impacter le résultat.



