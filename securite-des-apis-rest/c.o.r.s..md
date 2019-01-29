# C.O.R.S.

## Définitions

Cross-Origin Resource Sharing. [https://www.w3.org/TR/cors/](https://www.w3.org/TR/cors/)

L’ "origin" _\(_[_https://tools.ietf.org/html/rfc6454_](https://tools.ietf.org/html/rfc6454)_\)_ est composé des éléments suivants :

* Scheme : http / https / …
* FQDN : www.attacker.com / api.target.com / …
* Port : 80 / 443 / 8000

## Fonctionnement

![C.O.R.S. Flowchart](../.gitbook/assets/cors-flowchart.png)

Supposons que nous avons deux “origins” : [https://attacker.com](https://attacker.com) et [https://target.com](https://target.com).

### GET ou FETCH

Par défaut, si l’application [`https://attacker.com`](https://attacker.com/) émet une requête `GET` depuis le browser _\(en JavaScript\)_ vers l’_origin_ [`https://target.com`](https://target.com/), celle-ci ne **transmettra aucun des cookies des deux** _**origins**_.

Le browser analysera ensuite certains _headers_ C.O.R.S. _\(que nous verrons plus tard\)_ mais en leur absence, il ne transmettra pas la réponse à l’application.  
`Error: No 'Access-Control-Allow-Origin' header is present on the requested resource`

### Autre

S’il s’agit d’une requête **autre que `GET`** _\(ou similaire `HEAD`…\)_ le _browser_ envoie une _preflight request_ de type `OPTIONS` pour vérifier si la requête est autorisée en fonction de l’ _origin_ et de la méthode utilisée.

## Méfiez-vous des Fausses Solutions 

Ces mécanismes ont été mis en place pour éviter les attaques de type C.S.R.F _\(Cross Site Request Forgery\)_.

Malheureusement, le premier résultat sur lequel on tombe en recherchant le message d’erreur est le suivant :  
[https://stackoverflow.com/questions/20035101/why-does-my-javascript-get-a-no-access-control-allow-origin-header-is-present](https://stackoverflow.com/questions/20035101/why-does-my-javascript-get-a-no-access-control-allow-origin-header-is-present)

On y trouve les propositions suivantes :

* “The easy way is to just add the extension in google chrome to allow access using CORS.” [https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en-US](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en-US) 
* `chrome.exe --user-data-dir="C:/Chrome dev session" --disable-web-security` 
* “It’s very simple to solve if you are using PHP. Just add the following script in the beginning of your PHP page which handles the request:” `<?php header('Access-Control-Allow-Origin: *'); ?>`

## Sauvés par le C.O.R.S.

Après la mise en place du _header_ `Access-Control-Allow-Origin: *`, la requête émise depuis l’_origin_ [`https://attacker.com`](https://attacker.com/) vers  [`https://target.com`](https://target.com/) ne contient pas de cookies.

Il faut activer l’option `withCredentials` de l’objet XHR ou de la fonction `fetch` avec le paramètre `credentials: 'include'`.

La **requête est alors envoyée avec les cookies** mais encore une fois les spécifications C.O.R.S. sont rigoureuses et **il n’est pas possible de récupérer le contenu de la réponse** si le _header_ `Access-Control-Allow-Origin` vaut `*`.

Pour pouvoir transmettre des cookies et récupérer la réponse, il faut configurer le _header_ **`Access-Control-Allow-Credentials`** mais encore une fois, heureusement que ce n’est pas suffisant. **Cette fonctionnalité ne peut pas être activée si `Access-Control-Allow-Origin` vaut `*`**.

Il faut donc définir une _whitelist_ d’_origins_ mais malgré tous ces obstacles volontaires, certains vont jusqu’au bout…  
[http://stackoverflow.com/questions/26411480/angularjs-a-wildcard-cannot-be-used-in-the-access-control-allow-origin-he](http://stackoverflow.com/questions/26411480/angularjs-a-wildcard-cannot-be-used-in-the-access-control-allow-origin-he)

{% hint style="danger" %}
Please don’t!!!
{% endhint %}

Après cette ultime étape, n’importe quelle application depuis n’importe quel _origin_ peut communiquer librement avec votre API en utilisant les _credentials_ présents dans les _cookies_ de l’utilisateur actuellement authentifié.

![I Will Never Use Cookies Again](https://wishtackblog.files.wordpress.com/2017/03/i-will-never-use-cookies-again.gif?w=657)

Par précaution, même en l’absence de _cookies_, il vaut mieux éviter d’utiliser la valeur `*` pour le _header_ `Access-Control-Allow-Origin` sauf dans le cas d'une API publique.

Il est préférable d’implémenter une logique de _whitelist_ sur l’API qui vérifie le contenu du _header_ `Origin` de la requête et le renvoie dans le _header_ `Access-Control-Allow-Origin` de la réponse en cas d’autorisation réussie.

**La vérification de la** _**whitelist**_ **doit être stricte !** Il ne suffit pas de vérifier le FQDN.

{% hint style="success" %}
Pensez à implémenter une règle sur votre W.A.F. \(Web Application Firewall\), middlewares ou monitoring sécurité pour détecter et bloquer les réponses HTTP contenant le _header_ `Access-Control-Allow-Credentials`.
{% endhint %}

{% hint style="danger" %}
**Attention ! Les certificats clients et l’authentification de type "basic auth" sont également considérés comme des** _**credentials**_ et on rencontre les mêmes problèmes qu’avec les _cookies_.
{% endhint %}

