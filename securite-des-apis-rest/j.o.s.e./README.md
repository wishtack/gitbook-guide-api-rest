---
description: JavaScript Object Signing and Encryption
---

# J.O.S.E.

JOSE est un framework destiné à fournir une méthode pour transférer de manière sécurisée des **claims** _\(informations d’autorisations par exemple\)_ entre différentes **entités**.  
[https://datatracker.ietf.org/wg/jose/charter/](https://datatracker.ietf.org/wg/jose/charter/)

JOSE définit principalement les 4 éléments suivant :

### [**J.W.K. : JSON Web Key**](j.w.k..md)

Définit le format de la représentation JSON d’une clé cryptographique symétrique ou asymétrique.

### [**J.W.S. : JSON Web Signature**](j.w.s..md)

Définit la représentation d’un contenu signé.

### [**J.W.E. : JSON Web Encryption**](j.w.e..md)

Définit la représentation d’un contenu chiffré.

### [**J.W.T. : JSON Web Token**](../j.w.t./)

Définit une représentation compact et URL-safe d’un **token** _\(optionnellement signé ou chiffré ou signé **puis** chiffré\)_ ainsi que les **claims** standardisés et enregistrés auprès de l’IANA.

{% hint style="warning" %}
JOSE ne définit pas de mécanisme d’authentification ou d’autorisation.
{% endhint %}

