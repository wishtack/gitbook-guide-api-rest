# Description et Fonctionnement de JWT

JWT définit la structure d’un token _\(**chiffré**, **signé** ou **non sécurisé**\)_ permettant de véhiculer des **claims** standards, publics ou privés.[ https://www.iana.org/assignments/jwt/jwt.xhtml](https://www.iana.org/assignments/jwt/jwt.xhtml)

Pour faciliter la transmission de tokens JWT, ce dernier est sérialisé dans un format compact _\(qui est également applicable à JWE et JWS\)_.

Chaque bloc _\(header / payload / signature etc…\)_ est encodé en base64 URL-safe et séparé par un `.`.

Cf. [https://jwt.io/](https://jwt.io/)

### Exemple

```javascript
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOmZhbHNlfQ.
FMy5mxG5mDjL4rW8defHN2fZ_U_ypDW6hUT-Oan2F6P36NzCEHq85IXWUChQc5vzCXa_SHWK9j1ZZG3vRwuEkEH-lA_FNPL2EAQjdqq_qxMhaS5SscW8RVb30rd7lw1-OvEESrKcAtqipDmkufpsv3R3YWBItF1Uev0wF1U9QGU
```

#### Header

```javascript
{"alg":"RS256","typ":"JWT"}
```

#### **Payload**

```javascript
{"sub":"1234567890","name":"John Doe","admin":false}
```

#### **Signature**

```text
14ccb99b11b99838cbe2b5bc75e7c73767d9532a435ba8544ce6a7d85e8fdfa3730841eaf392175940a141ce6fcc25da48758af63d59646def470b849041e500534f2f610042376aaaac4c85a4b94ac716f1155bdf4addee5c353af1044ab29c02daa2a439a4b9fa6cbf7477616048b45d547afd3017553d4065
```



