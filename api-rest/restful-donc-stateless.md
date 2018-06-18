# ReSTful donc Stateless

## Stateless ?

Supposons le scénario d’échange suivant. Est-il "stateless" ?

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

* Pas de session à maintenir et donc pas de problème de "load balancing".
* Moins de requêtes.
* Il est possible de paralléliser les requêtes.
* “Cacheable”.
* API intuitive et extensible.
  * L’API est human readable _\(pas besoin d’avoir la documentation en permanence sous les yeux\)_.
  * L’API est facile à étendre _\(ajout de propriétés par exemple\)_.
  * L’API peut répondre facilement à des besoins qui n’ont pas été anticipé _\(modification du nombre de produits dans le panier par exemple\)_.
* Affordances :

{% embed data="{\"url\":\"https://youtu.be/NK1Zb\_5VxuM\",\"type\":\"video\",\"title\":\"Affordances\",\"description\":\"Video: Don Norman explains affordances. Vintage video from 1994 - still highly relevant today.\\n\\nFrom: \\\"Defending Human Attributes in the Age of the Machine\\\" - CD-ROM from 1994. Copyright Don Norman - all rights reserved. Used with permission. \\n\\nAbout the Interaction Design Foundation: https://www.interaction-design.org/about\\nOnline self-paced design courses: https://www.interaction-design.org/courses\\n\\nFounded in 2002, the Interaction Design Foundation \(IDF\) specializes in education and career advancement for designers: we offer self-paced online courses on design as well as networking events in 84 countries in all major cities across the globe. Course Certificates issued by the Interaction Design Foundation are recognized by industry-leading corporations. Course Materials are developed by leading practitioners as well as by academics from top-tier universities like Stanford University, MIT.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.youtube.com/yts/img/favicon\_144-vfliLAfaB.png\",\"width\":144,\"height\":144,\"aspectRatio\":1},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://i.ytimg.com/vi/NK1Zb\_5VxuM/hqdefault.jpg\",\"width\":480,\"height\":360,\"aspectRatio\":0.75},\"embed\":{\"type\":\"player\",\"url\":\"https://www.youtube.com/embed/NK1Zb\_5VxuM?rel=0&showinfo=0\",\"html\":\"<div style=\\\"left: 0; width: 100%; height: 0; position: relative; padding-bottom: 75.0019%;\\\"><iframe src=\\\"https://www.youtube.com/embed/NK1Zb\_5VxuM?rel=0&amp;showinfo=0\\\" style=\\\"border: 0; top: 0; left: 0; width: 100%; height: 100%; position: absolute;\\\" allowfullscreen scrolling=\\\"no\\\"></iframe></div>\",\"aspectRatio\":1.3333},\"caption\":\"Affordances\"}" %}

En général, on peut comparer les approches stateful et stateless à la **métaphore de la destination géographique**.

Laquelle de ces deux indications vous semble la plus précise :

* Les coordonnées GPS d’une adresse à Strasbourg.
* Pour aller de Nice à l’adresse à Strasbourg :
  * Tournez à droite.
  * à 100m à gauche.
  * Au rond-point \(s’il n’a pas changé depuis\), sortez à la 3ème sortie.
  * Admirez la vue sur votre gauche
  * …



