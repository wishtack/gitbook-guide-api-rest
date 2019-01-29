# Re.S.T. : REpresentational State Transfer

## **Ce qu’une API ReST n’est pas**

* ReST n’est pas un standard mais un **style d’architecture**.
* ReST ne concerne pas uniquement les APIs distantes ou HTTP. Une librairie peut être ReSTful.

## **Roy Thomas FIELDING : Papa du ReST**

* L’origine des API ReST date de l’année 2000.
* [https://www.ics.uci.edu/~fielding/pubs/dissertation/fielding\_dissertation.pdf](https://www.ics.uci.edu/~fielding/pubs/dissertation/fielding_dissertation.pdf)

## Description du ReST

* Une API ReST est **une interface abstraite du modèle de données** qu’on appelle **ressources**.
* On peut distinguer deux principaux types de ressources :
  * les **instances** _\(un utilisateur, un produit etc…\)_,
  * les **collections** _\(une liste d’instances\)_.
* L’API ReST permet d’**ajouter** / **modifier** / **supprimer** des ressources,

{% hint style="danger" %}
Contrairement aux APIs SOAP, il faut absolument éviter la logique impérative où on transmet des actions à l’API.
{% endhint %}

