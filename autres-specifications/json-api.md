# JSON API

[http://jsonapi.org/](http://jsonapi.org/)

* Créé par le co-fondateur de [http://www.tilde.io](http://www.tilde.io/), une entreprise de conseil _\(en jsonapi ?\)._
* C’est une spécification et non un standard.

```javascript
{
    "links": {
        "self": "http://example.com/articles",
        "next": "http://example.com/articles?page[offset]=2",
        "last": "http://example.com/articles?page[offset]=10"
    },
    "data": [{
        "type": "articles",
        "id": "1",
        "attributes": {
            "title": "JSON API paints my bikeshed!"
        },
        "relationships": {
            "author": {
                "links": {
                    "self": "http://example.com/articles/1/relationships/author",
                    "related": "http://example.com/articles/1/author"
                },
                "data": {"type": "people", "id": "9"}
            },
            "comments": {
                "links": {
                    "self": "http://example.com/articles/1/relationships/comments",
                    "related": "http://example.com/articles/1/comments"
                },
                "data": [
                    {"type": "comments", "id": "5"},
                    {"type": "comments", "id": "12"}
                ]
            }
        },
        "links": {
            "self": "http://example.com/articles/1"
        }
    }],
    "included": [{
        "type": "people",
        "id": "9",
        "attributes": {
            "first-name": "Dan",
            "last-name": "Gebhardt",
            "twitter": "dgeb"
        },
        "links": {
            "self": "http://example.com/people/9"
        }
    }, {
        "type": "comments",
        "id": "5",
        "attributes": {
            "body": "First!"
        },
        "relationships": {
            "author": {
                "data": {"type": "people", "id": "2"}
            }
        },
        "links": {
            "self": "http://example.com/comments/5"
        }
    }, {
        "type": "comments",
        "id": "12",
        "attributes": {
            "body": "I like XML better"
        },
        "relationships": {
            "author": {
                "data": {"type": "people", "id": "9"}
            }
        },
        "links": {
            "self": "http://example.com/comments/12"
        }
    }]
}
```

## Cool 👍

* Définition d’un format strict mais extensible.
* Standardisation des paramètres de _sorting_, _filtering_ et de pagination _\(l’implémentation reste libre pour la pagination\)_.
* L’idée du _resource linking_ avec des _relationships_ est intéressante.

## Pas cool 👎

* Risque de collision entre les _fields_ présents dans `attributes` et `relationships`.
* Pas de différence entre un lien vers une instance ou une collection.
* Les _one-to-one relationships_ sont ambigües et ne respectent pas la convention : `/resources/:resourceId/sub-resources/:subResourceId`
* Attention, les exemples utilisés dans la spec adoptent des conventions inhabituelles et ne sont pas imposés par la spec.
  * L’utilisation des _fields_ en kebab-case n’est pas dans le standard.
  * La propriété `type` n’est pas forcément au pluriel.
* L’idée des _bulk operations_ sur les _relationships_ est très intéressante mais malheureusement pas appliquée aux ressources.
* De nombreuses implémentations mais la plupart ne sont plus maintenues depuis des mois voire des années.

 



