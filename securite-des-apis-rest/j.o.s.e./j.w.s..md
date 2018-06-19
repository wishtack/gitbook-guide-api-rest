---
description: JSON Web Signature
---

# J.W.S.

#### Représentation d’un contenu signé

```javascript
{
    "payload": "eyJpc3MiOiJqb2...kjp0cnVlfQ",
    "signatures": [
        {
            "protected":"eyJhbGciOiJSUzI1NiJ9",
            "header": {"kid":"123"},
            "signature": "cC4hiUPoj9E...cN_IoypGlUPQGe77Rw"
        },
        {
            "protected":"eyJhbGciOiJFUzI1NiJ9",
            "header": {"kid":"456"},
            "signature": "DtEhU3ljbEg8L38VWA...Kg6NU1Q"
        }
    ]
}
```

{% hint style="warning" %}
Il est possible d’utiliser des clés symétriques pour authentifier un message avec HMAC.  
**Il s’agit alors d’un message authentication code et non d’une signature**.
{% endhint %}

