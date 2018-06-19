# OAuth 2 Risques & Recommandations



**TLS EVERYWHERE!** OAuth 2 n’oblige malheureusement pas l’utilisation du TLS pour les "Redirect URI" mais le recommande fortement.

L'**Authorization Server** doit **vérifier** que le **Client** possède bien le **nom de domaine** associé à la **Redirect URI**. _\(E.g. : Vérification de la capacité du client à ajouter une entrée DNS TXT proposée aléatoirement par l'**Authorization Server**\)_

L'**Authorization Server** devrait permettre aux **Client**s de **renouveler rapidement le Client Secret.**

L'**Authorization Server** devrait obliger les **Client**s à **renouveler régulièrement le Client Secret.**

* Le **Client Secret** est souvent stocké dans une variable d’environnement sur le serveur d’application.
* Une erreur de configuration suffit pour compromettre tout le système.
* L'**Authorization Server** peut permettre de modifier le **Redirect URI** simplement en présentant le **Client ID** et le **Client Secret**.

Les **Redirect URIs** sont des absolute URIs _\(scheme, fqdn, port, path\)_ et ne doivent pas contenir de “fragment” _\(\#…\)_.

L'**Authorization Server** doit vérifier les **Redirect URI**s avec une **égalité stricte**.  
E.g. : [`https://www.wishtack.com/oauth?source=test`](https://www.wishtack.com/oauth?source=test) est strictement différente de [`https://www.wishtack.com/oauth`](https://www.wishtack.com/oauth).

