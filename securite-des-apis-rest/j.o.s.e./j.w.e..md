---
description: JSON Web Encryption
---

# J.W.E.

#### Représentation d’un contenu chiffré

```javascript
{
    // Integrity protected header but not encrypted!
    "protected": "eyJlbmMiOiJBMTI4Q0JDLUhTMjU2In0",
    "unprotected": {"jku":"https://server.example.com/keys.jwks"},
    "recipients":[
        {
            // Key and Alg hints.
            "header": {"alg":"RSA1_5","kid":"123"},
            // Encryption key encrypted using 123's public key.
            "encrypted_key": "UGhIOguC7IuEvf_N...XMR4gp_A"
        },
        {
            "header": {"alg":"A128KW","kid":"456"},
            "encrypted_key": "6KB707dM9YTIgHt...2IlrT1oOQ"
        }
    ],
    "iv": "AxY8DCtDaGlsbGljb3RoZQ",
    // Encrypted message.
    "ciphertext": "KDlTtXchhZTGufMYmO...4HffxPSUrfmqCHXaI9wOGY",
    // AEAD authentication tag.
    "tag": "Mz-VPPyU4RlcuYv1IwIvzw"
}
```

{% hint style="info" %}
Le chiffrement asymétrique a une taille limite de message _\(modulo – padding\)_. C’est pour cette raison que l’on génère une clé symétrique à la volée qui est ensuite chiffrée avec la clé publique asymétrique.
{% endhint %}

