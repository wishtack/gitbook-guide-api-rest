# Polymorphisme

Il peut arriver qu’une ressource de type collection contienne plusieurs ressources de types légèrement différents. Par exemple, des produits de type différents : **livres** et **films**.

* Tout d’abord, il faut harmoniser le modèle de la ressource au maximum. Par exemple, livres et films ont un prix, il faut que ce soit la même propriété. Même si tel n’est pas le cas dans votre modèle de données _\(Ex. scraping\)_, créez des _computed fields_. On peut imaginer naïvement un _computed field_ `price` qui calcule le prix à partir de la durée du film :\).
*  Il suffit alors d’ajouter un _field_ `type` au modèle de votre ressource _\(qu’il faudra dûment documenté\)._
* Cela permet ensuite côté client de _remapper_ vers les classes associées.
* **L’abus de polymorphisme nuit gravement à la santé de votre API et de ses proches.**

```javascript
{
  "objects": [
    {
      "id": "1",
      "author": {"id": "3"},
      "price": {"amount": 10, "currency": "EUR"},
      "type": "book",
    },
    {
      "duration": 5400,
      "id": "2",
      "price": {"amount": 6, "currency": "USD"},
      "type": "movie"
   }
  ]
}
```

### Inheritance and Polymorphism with Swagger

[https://swagger.io/docs/specification/data-models/inheritance-and-polymorphism/](https://swagger.io/docs/specification/data-models/inheritance-and-polymorphism/)

{% embed url="https://swagger.io/docs/specification/data-models/inheritance-and-polymorphism/" %}



