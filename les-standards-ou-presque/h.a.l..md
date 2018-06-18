# H.A.L.

* Hypertext Application Language.
* [https://tools.ietf.org/html/draft-kelly-json-hal-08](https://tools.ietf.org/html/draft-kelly-json-hal-08)
* Créé par le fondateur de [http://stateless.co/](http://stateless.co/), une entreprise de conseil.
* Ce n’est pas un standard non plus.

```javascript
{
    "_links": {
        "self": { "href": "/orders" },
        "curies": [{
            "name": "ea",
            "href": "http://example.com/docs/rels/{rel}",
            "templated": true
        }],
        "next": { "href": "/orders?page=2" },
        "ea:find": {
            "href": "/orders{?id}",
            "templated": true
        },
        "ea:admin": [{
            "href": "/admins/2",
            "title": "Fred"
        }, {
            "href": "/admins/5",
            "title": "Kate"
        }]
    },
    "currentlyProcessing": 14,
    "shippedToday": 20,
    "_embedded": {
        "ea:order": [{
            "_links": {
                "self": { "href": "/orders/123" },
                "ea:basket": { "href": "/baskets/98712" },
                "ea:customer": { "href": "/customers/7809" }
            },
            "total": 30.00,
            "currency": "USD",
            "status": "shipped"
        }, {
            "_links": {
                "self": { "href": "/orders/124" },
                "ea:basket": { "href": "/baskets/97213" },
                "ea:customer": { "href": "/customers/12369" }
            },
            "total": 20.00,
            "currency": "USD",
            "status": "processing"
        }]
    }
}
```

## Cool 👍

* Simple, clair et facile à implémenter.
* Les "templated links" sont très prometteurs et permettent un découplage entre le code client et l’API.
* Les "curies" permettent de facilement lier les ressources à leur documentation et pourquoi pas un schéma _\(mais ce n’est pas défini par H.A.L.\)_.

## Pas cool 👎

* Comme son nom l’indique, H.A.L. se focalise uniquement sur le "linking". Le périmètre est donc très limité.
* La propriété "\_embedded"  manque d’intérêt et peut provoquer des conflits entre les propriétés de la ressource et les propriétés "\_embedded".
* De nombreuses implémentations mais la plupart ne sont plus maintenues depuis des mois voire des années.

