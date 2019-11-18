# ReSTful donc Stateless

## Stateless ?

Supposons le scénario d’échange suivant. Est-il _stateless_ ?

{% tabs %}
{% tab title="🧐" %}
```http
GET /init
GET /select-cart?cartId=123ab
POST /add-product
POST /add-product
POST /update-product-count?productId=12345
GET /cart-summary
POST /pay
```
{% endtab %}

{% tab title="👍" %}
![No!](../.gitbook/assets/no.jpg)
{% endtab %}
{% endtabs %}

## Limites et Difficultés du Stateful

* L’effet "**never-click-back!**".
* Problèmes de "load balancing".
* Comment paralléliser l’ajout de deux produits dans deux paniers différents ?
* Comment mettre la ressource "/cart-summary" en cache.
* API peu intuitive et peu extensible.

## Exemple Stateless

```text
POST /carts/123ab/items
POST /carts/456cb/items
PATCH /items/33333
POST /carts/123ab/payments
GET /carts/123ab
```

## Les Avantages de l'Approche Stateless

* Pas de session à maintenir et donc pas de problème de _load balancing_.
* Moins de requêtes.
* Il est possible de paralléliser les requêtes.
* _Cacheable_.
* API intuitive et extensible.
  * L’API est human readable _\(pas besoin d’avoir la documentation en permanence sous les yeux\)_.
  * L’API est facile à étendre _\(ajout de propriétés par exemple\)_.
  * L’API peut répondre facilement à des besoins qui n’ont pas été anticipé _\(modification du nombre de produits dans le panier par exemple\)_.

En général, on peut comparer les approches stateful et stateless à la **métaphore de la destination géographique**.

Exemple :

* Coordonnées GPS d'un lieu.  vs. 
* Les indications pour s'y rendre :
  * Tournez à droite.
  * à 100m à gauche.
  * Au rond-point \(s’il n’a pas changé depuis\), sortez à la 3ème sortie.
  * Admirez la vue sur votre gauche
  * …



