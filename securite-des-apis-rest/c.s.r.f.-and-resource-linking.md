# C.S.R.F. & "Resource Linking"

Nous avons évoqué [précédemment](../api-rest/h.a.t.e.o.a.s.-et-resource-linking.md) le problème de confiance lié au _resource linking_ en général.

Un client _\(browser ou autre\)_ **communique** généralement avec **plusieurs APIs**.

Une réponse malicieuse ou simplement maladroite d’une API pourrait pousser le client à forger une requête vers une autre API en envoyer le token d’authentification ou encore d’autres informations confidentielles.

```javascript
{
    "firstName": "Foo",
    "address": {
        "href": "https://api.attacker.com/"
    }
}
```

Il est possible de se protéger partiellement avec des règles C.S.P. _\(Content Security Policy\)_ `connect-src`  
[https://w3c.github.io/webappsec-csp/](https://w3c.github.io/webappsec-csp/)

Autrement, il est recommandé d’implémenter ou d’utiliser une librairie HTTP robuste avec des _whitelists_ strictes ou le rejet d’URLs absolues bien qu’une URL relative puisse être également malicieuse.

