# Nommage

## Convention de Nommage

* **kebab-case** pour les URLs.
* **under\_score** ou **camelCase** pour les paramètres en “query string” et pour les “fields” des ressources.
* **kebab-case pluriel** pour les noms des ressources dans les URLs.

## Vocabulaire

Utilisez des noms explicites respectant la métaphore _\(ou ubiquitous language\)_ du service.

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

