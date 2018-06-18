# Nommage

## Convention de Nommage

* **kebab-case** pour les URLs.
* **camelCase** pour les paramètres en “query string” et pour les “fields” des ressources.
* **kebab-case pluriel** pour les noms des ressources dans les URLs.
  * Je recommande tout de même de convertir les pluriels vers des variables avec un suffixe \`List\`. Dans les URLs, c’est joli mais dans le code c’est trop subtil et ça provoque facilement des conflits.

## Vocabulaire

Utilisez des noms explicites respectant la "métaphore" _\(ou "ubiquitous language"\)_ du service.

## URLs

Les URLs doivent être construites de la façon suivante :

```http
/resources
/blogs

/resources/:resourceId
/blogs/:blogId

/resources/:resourceId/subresources
/blogs/:blogId/posts
```

Evitez donc les URLs de type :  

```http
/blogs/:blogId/summary
```

Ce n’est pas du ReSTafaring. De nombreuses librairies sont conçues ainsi. Contourner ces règles vous obligera à modifier, détourner et torturer les librairies et frameworks que vous utilisez.

