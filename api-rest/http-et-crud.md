# HTTP & CRUD

## Les Méthodes HTTP Associées aux Opérations C.R.U.D.

### Create

* **POST** : Création d’une ressource_._

### Read

* **GET** : Récupération d’une ressource ou d’une collection.

### Update

* **PATCH** : Modification d’une ressource ou d’une collection.
* **PUT** : Remplacement d’une ressource ou d’une collection.

### Delete

* **DELETE** : Suppression d’une ressource ou d’une collection.

{% hint style="info" %}
* La méthode **POST** peut servir à modifier une ressource mais ce n’est pas recommandé.
* La méthode **PUT** peut servir à créer une ressource si on en connaît l’identifiant par avance par exemple. La seule contrainte sur la méthode **PUT** est qu’elle doit être idempotente. Le nombre d’exécution d’une même requête ne doit pas impacter le résultat.
{% endhint %}

