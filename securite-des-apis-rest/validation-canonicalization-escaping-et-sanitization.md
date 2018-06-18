# Validation : Canonicalization, Escaping & Sanitization

Toutes les propriétés échangées avec l’API ReST doivent être validées par l’API.

La validation doit également être implémentée côté client pour éviter les aller-retours inutiles.

## Canonicalization

L’API ReST doit convertir les données reçues vers leur forme canonique ou les rejeter.

Par exemple, les données suivantes :

```javascript
{
    "firstName": "joHn",
    "lastName": "  DoE",
    "url": "myWebsite.com"
}
```

... peuvent être converties en :

```javascript
{
    "firstName": "john",
    "lastName": "doe",
    "url": "https://mywebsite.com"
}
```

## Escaping

Ce n’est pas à l’API ReST de gérer l’escaping du contenu.

Par exemple, sur un blog, le commentaire suivant est cohérent :

```markup
<img src="not-found" onerror=alert(1)>
```

C’est au client de gérer l’escaping est d’éviter les attaques de type XSS.

## **Sanitization**

La “sanitization” est un jeu dangereux qui consiste à retirer le contenu potentiellement malicieux.

Pour l’exemple précédent, cela consisterait à retirer la partie `onerror` :

```markup
<img src="not-found">
```

Mais encore une fois, il s’agit d’une problématique client.

La difficulté est qu’il est toujours possible de trouver des techniques pour "bypass" la "sanitization".  
Certains en ont fait leur métier 😉  
[http://n0p.net/penguicon/php\_app\_sec/mirror/xss.html](http://n0p.net/penguicon/php_app_sec/mirror/xss.html)

