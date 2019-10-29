# Les 5 règles et ½ de l’API ReST

## **Uniforme**

* L’interface est uniforme à tous les niveaux. Tous les éléments _\(et connecteurs\)_ communiquent en utilisant la même interface.
* Chaque ressource est identifiée de façon unique et canonicalisée avec son URI.

> In order to obtain a uniform interface, multiple architectural constraints are needed to guide the behavior of components. REST is defined by four interface constraints: identification of resources; manipulation of resources through representations; selfdescriptive messages; and, hypermedia as the engine of application state.

## **Stateless**

* Une API ReST ne doit pas maintenir de session ou de contexte.

> Communication must be stateless in nature..., such that **each request from client to server must contain all of the information necessary to understand the request**, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client. This constraint induces the properties of visibility, reliability, and scalability. **Visibility** is improved because a monitoring system does not have to look beyond a single request datum in order to determine the full nature of the request. **Reliability** is improved because it eases the task of recovering from partial failures. **Scalability** is improved because not having to store state between requests allows the server component to quickly free resources, and further simplifies implementation because the server doesn’t have to manage resource usage across requests.

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



