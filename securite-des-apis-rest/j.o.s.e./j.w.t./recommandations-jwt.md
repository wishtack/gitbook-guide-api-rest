# Recommandations JWT

Il faut utiliser des **clés RSA** pour la signature.

Il faut instaurer une **rotation régulière et automatique des clés**.  
Les clés publiques doivent être publiées automatiquement également.

Etant donné que la rotation doit avoir une durée plus longue que la durée de vie des tokens, il faut réduire la durée de vie des tokens. _\(E.g. : l’implémentation OpenID Connect de Google semble appliquer une rotation de 3 à 4 jours mais je recommanderais une durée encore plus courte\)_

Pour réduire les risques, utilisez de nombreuses clés.

Idéalement, les clés secrètes ne devraient être manipulées que par des services dédiés hautement sécurisés avec des mécanismes de monitoring avancés.  
Cf. [https://www.vaultproject.io/](https://www.vaultproject.io/)

Les tokens JWT peuvent être utilisés comme **mécanisme complémentaire** d’un mécanisme de token classique. On peut wrapper des tokens dans un token JWT afin de vérifier rapidement leur validité et leur expiration avant de le vérifier auprès d’une base de données ou d’un tiers.

