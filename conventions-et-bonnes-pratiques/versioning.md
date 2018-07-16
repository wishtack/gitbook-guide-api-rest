# Versioning

Etant donné que les APIs ReST sont conçues pour être utilisées par de multiples sources _\(clients mobiles / web / desktop / partenaires / public…\)_, elles évoluent souvent à un **rythme différent de celui des clients**. Il est donc **nécessaire des les versioner**.

Deux approches s’offrent alors à nous :

* Versioning par Media Type.
* Versioning par URL.

## Versioning par Media Type

Le versioning par “media type” consiste à utiliser le comportement standard des “headers” HTTP `Accept` et `Content-Type`.

Le client indique alors la version de l’API qu’il supporte dans le header `Accept` :  
`Accept: application/vnd.wishtack.v3+json`

L’API retourne alors les données dans la version correspondante avec le bon Media Type dans le header `Content-Type`.

* Séduisant mais légèrement complexe à mettre en place.
* Comment faire si la nouvelle version est implémentée dans un langage différent ou encore sur une plateforme différente ?
* Nous serions alors obligé d’utiliser un connecteur pour effectuer le "balancing". [https://github.com/Kong/kong/issues/402](https://github.com/Kong/kong/issues/402)

## Versioning par URL

Vu l’obstacle de "balancing" posé par le versioning par Media Type, pourquoi pas utiliser un "balancing" standard en amont… mais lequel ?

Nous pourrions utiliser le "path" de l’URL et procéder au **"balancing" en fonction du nom de domaine**. Cela nécessite toujours un connecteur : [https://getkong.org/docs/0.13.x/proxy/\#request-path](https://getkong.org/docs/0.13.x/proxy/#request-path) mais c'est une approche un peu plus classique et plus facile à configurer.

{% tabs %}
{% tab title="🧐" %}
Qui dit mieux ?
{% endtab %}

{% tab title="👍" %}
Yes ! Le DNS !  
  
[`https://v1.api.wishtack.com`](https://v1.api.wishtack.com/) NodeJS hosted on Amazon.  
[`https://v2.api.wishtack.com`](https://v2.api.wishtack.com/) Python hosted on Heroku.  
[`https://v3.api.wishtack.com`](https://v3.api.wishtack.com/) Python hosted on Heroku sur un monorépo avec l’API V2.[`https://v4.api.wishtack.com`](https://v3.api.wishtack.com/) Serverless functions sur un monorépo avec l’API V2 et V3.
{% endtab %}
{% endtabs %}

