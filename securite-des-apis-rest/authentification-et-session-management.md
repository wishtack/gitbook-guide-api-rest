# Authentification et Session Management

## **De quoi avons nous besoin ?**

### **Session management ?**

Nope ! **L’API ReST doit être Stateless !**

Si des informations liées à la session doivent être maintenues, celles-ci doivent être gérées par le client.

Les données persistées par l’API ReST sont associées à des ressources.

Rien n’interdit l’expiration d’une ressource : `GET /carts/1234 => 404 Not Found`

{% hint style="warning" %}
Ne schtroumpfez pas !`SMURF /smurf-api/sessions/current`
{% endhint %}

### **Authentification**

Idéalement, il nous faudrait un mécanisme d’authentification même si les données de l’API sont publiques.

### **Identification**

L'identification n'est implémentée que si réellement nécessaire.

**L’authentification et l’identification sont des notions distinctes.**  
Il est possible d’authentifier un utilisateur sans l’identifier.  
Il est également possible d’identifier un utilisateur sans l’authentifier mais nous n’aurions aucune garantie de l’identité.

### **Logout et révocation**

Le "logout" peut provenir d’une autre source que l’utilisateur final.

{% hint style="danger" %}
Les "tokens" d’authentification **ne doivent pas être transmis dans l’URL.**  
`GET /users/123?token=asdf....`

L’authentification "basic-auth" ne doit pas être utilisée.

Les "tokens" doivent être transmis dans le "header" `Authorization`

`Authorization: Bearer xxxxxx, Extra yyyyy`
{% endhint %}

## **Mécanismes d’authentification**

Nous parcourerons plus tard les différents mécanismes d’authentification envisageables.

Globalement _\(modulo quelques étapes\)_, la plupart des mécanismes d’authentification fonctionnent ainsi :

1. Le service d’authentification fournit un "token" unique au client.
2. Le client transmet ce "token" aux APIs ReST du fournisseur de service.
3. Le fournisseur de service déduit les autorisations d’accès en fonction de ce "token".

## **Session Management côté client**

Le cas le plus complexe est celui où le client est un "browser".

Si vous souhaitez persister des données dans le "browser" afin que l’utilisateur puisse retrouver le même contexte en changeant de fenêtre ou après un "refresh" :

* Evitez absolument l’utilisation des "cookies" ne serait-ce que pour les raisons suivantes :
  * Ce n’est pas leur rôle.
  * Vous ne voulez pas envoyer toutes ces données au backend à chaque requête.
  * Cookies are EVIL ! 
* **`IndexedDB`** et **`localStorage`** sont là pour ça. 
* Problème 😱

  * L'**`IndexedDB`** et le **`localStorage`** n’ont pas de notion d’expiration sauf sur Firefox :  [https://developer.mozilla.org/en-US/docs/Web/API/IDBFactory/open](https://developer.mozilla.org/en-US/docs/Web/API/IDBFactory/open).
  * Jetez un coup d’oeil au contenu de vos storages après "logout" ou fermeture du "browser", vous serez surpris de découvrir ce qu’on y retrouve.

* Secure Storage
  * en attendant une solution "in-the-browser", il est recommandé de chiffrer les données stockées localement avec **une clé temporaire et unique pour chaque client transmise par l’API ReST,**
  * [https://github.com/jas-/crypt.io](https://github.com/jas-/crypt.io),
  * ou encore mieux, en stockant la clé via l'API browser `webauthn` quand celle-ci sera globalement disponible. [https://developers.google.com/web/updates/2018/05/webauthn](https://developers.google.com/web/updates/2018/05/webauthn) 

