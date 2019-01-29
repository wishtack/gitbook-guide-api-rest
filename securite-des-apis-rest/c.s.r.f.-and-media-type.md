# C.S.R.F. & Media Type



L’une des erreurs classiques est d’accepter des _media types_ autres que `application/*json` _\(header `Content-Type`\)_.

Sans aucune autre erreur de configuration C.O.R.S., l’acceptation du _media type_`application/x-www-form-urlencoded` permet à l’attaquant de créer un formulaire et de déclencher une simple requête POST.

```javascript
document.querySelector('form').submit()
```

Dans ce cas, la plupart des frameworks _\(Ex. : expressjs\)_ récupèrent un objet :

```javascript
{
   email: 'pwned.by@attacker.io',
   grants: 'all'
}
```

{% hint style="danger" %}
**Il ne faut donc activer que le parser JSON.**
{% endhint %}

… mais supposons qu’il soit activé sur tous les "media types" et plus particulièrement `text/plain` pour simplifier la vie des développeurs "client-side".

1. L’attaquant n’a plus qu’à adapter légèrement le formulaire précédent :

```markup
<form
    method="POST"
    action="https://app.vulnerable.com/api/products/0/admins"
    enctype="text/plain">
    <input
         name='{"email": "pwned.by@attacker.io", "grants": "all", "extra": "'
        value='"}'>
</form>
```

2. Cela va alors envoyer le "body" suivant :

```javascript
{"email": "pwned.by@attacker.io", "grants": "all", "extra": "="}
```

3. L’API va alors "parser" le contenu suivant :

```javascript
{
    email: 'pwned.by@attacker.io',
    grants: 'all',
    extrat: '='
}
```

{% hint style="danger" %}
**La vérification du** _**media type**_ **des requêtes doit donc être rigoureuse.**
{% endhint %}

