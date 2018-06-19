# Quoi de Neuf ?

**OpenID Connect** fournit les fonctionnalités supplémentaires suivantes :

### Authentification et Réauthentification

Le **Relying Party** peut demander à l'**OpenID Provider** **d’authentifier** ou **réauthentifier** l'**End-User**.

### Hint

Il peut **transmettre des informations supplémentaires** _\(hint\)_ comme l’identifiant du **End-User** pour faciliter la phase d’authentification.

### J.W.T.

OpenID Connect peut utiliser des tokens JWT mais on peut éviter de les transmettre au **End-User**.

### **Claims Distribués et Agrégés**

* Les données du **End-User** sont souvent distribuées entre plusieurs **OpenID Providers**. 
* Avec **OpenID Connect**, un **OpenID Provider** peut agréger les **claims** ou fournir toutes les informations nécessaires pour les récupérer chez un d’autres **OpenID Providers**.

### **Logout**

Lorsqu’un **End-User** logout de l'**OpenID Provider**, ce dernier peut notifier les **Relying Parties** par différents mécanismes.

### **Dynamic Client Registration**

Certains **OpenID Providers** peuvent activer cette fonctionnalité permettant à des “Relying Parties” de s’inscrire dynamiquement.

### **Discovery**

L'**OpenID Provider** peut fournir publiquement des informations permettant aux autres entités _\(**Relying Party**, **OpenID Provider**, …\)_ de découvrir dynamiquement les fonctionnalités et la configuration de l'**OpenID Provider**.  
[https://accounts.google.com/.well-known/openid-configuration](https://accounts.google.com/.well-known/openid-configuration)

### Claims et Scopes Supplémentaires

**OpenID Connect** définit quelques **claims** supplémentaires.

**OpenID Connect** définit quelques **scopes** qui englobent plusieurs **claims**.

![OpenID Connect](https://wishtackblog.files.wordpress.com/2017/03/openid-connect-map.png?w=748)

