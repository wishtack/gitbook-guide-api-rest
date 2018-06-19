---
description: JSON Web Key
---

# J.W.K.

#### Clé symétrique destinée à du chiffrement AES256 avec validation d’un hash HMAC SHA512.

```javascript
{
    "kty": "oct", // Key type : Octet Sequence.
    "alg": "A256CBC-HS512", // Algorithm intended for this key.
    "k": "GawgguFyGrWKav7AX4VKUg" // Key.
    "kid": "0" // Key Id.
}
```

#### Clé publique asymétrique destinée à la signature avec sa chaîne de certification X509.

```javascript
{
    "kty": "RSA", // Key type: RSA.
    "alg": "RS512", // RSA SHA512.
    "use": "sig", // signature.
    "kid": "1b94c", // Key Id.
    "n": "vrjOfz9Ccdgx5nQudyhdoR17V...",
    "e": "AQAB",
    "x5c": ["MIIDQjCCAiqgAwIBAgIGATz/FuLiMA0GCS...A6SdS4xSvdXK3IVfOWA=="]
}
```

#### Clé privée asymétrique destinée au chiffrement.

```javascript
{
    "kty": "RSA",
    "kid": "3j4h",
    "use": "enc",
    "n": "t6Q8PWSi1dkJj9hTP8hNYF...PFGGcG1qs2Wz-Q",
    "e": "AQAB",
    "d": "GRtbIQmhOZtyszfgKdg4...SdSgqcN96X52esAQ",
    "p": "2rnSOV4hKSN8sS4Cgc...Ngqh56HDnETTQhH3rCT5T3yJws",
    "q": "1u_RiFDP7LBYh3N4GXL...TB7LbAHRK9GqocDE5B0f808I4s",
    "dp": "KkMTWqBUefVwZ2_Dbj1...2pYhEAeYrhttWtxVqLCRViD6c",
    "dq": "AvfS0-gRxvn0bwJoMSnF...Y63TmmEAu_lRFCOJ3xDea-ots",
    "qi": "lSQi-w9CpyUReMErP1RsBL...2lNx_76aBZoOUu9HCJ-UsfSOI8"
}
```

