# OAuth 2 Resource Owner Password Credentials Flow

Dans les rares cas où le lien de confiance entre le **Resource Owner** et le **Client** est très fort, le **Resource Owner** peut transmettre ses "credentials" directement au **Client**.

Le **Client** transmet alors les _credentials_ à l'**Authorization Server** pour obtenir un **Access Token**.

```javascript
POST https://auth.wishtack.com/v1/oauth/token?
grant_type=password
&username=...
&password=...
&client_id=CLIENT_ID // If client is confidential 
&client_secret=CLIENT_SECRET // If client is confidential
```

Ce **Flow** est rarement implémenté pour les raisons suivantes :

* Le **Resource Owner** ne peut pas valider les autorisations demandées.
* Il ne permet pas d’autres modes d’authentification que le password.
* Les **Client**s ne sont pas conçus pour véhiculer des credentials.
* Ce **Flow** est un peu le _default_ d’un _switch/case_ qu’on trouve souvent dans les specs afin d’augmenter les chances d’adoption.
* **OpenID Connect** n’interdit pas l’utilisation de ce **Flow** afin d’être compatible avec **OAuth 2** mais il est complètement occulté de la spec.

