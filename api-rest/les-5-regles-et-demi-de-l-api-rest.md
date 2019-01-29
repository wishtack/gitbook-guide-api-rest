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

## **Client / Serveur : Separation of Concerns**

* L’API ReST n’est pas concernée par l’affichage, les interactions utilisateur et la session.
* Tous ces éléments doivent être gérés par le client _\(Ex. : application web frontend\)._

## **Layered**

* La présence de connecteurs intermédiaires doit être implicite pour le client et le serveur _\(composant de cache / sécurité etc…\)_.

## Code à la demande

Règle optionnelle ou plutôt inadaptée.

C’est le paramètre _extra_ que l’on retrouve dans certaines RFC pour garder un peu de souplesse.



