# Que Faire ?

Malheureusement, **OpenID Connect** ne définit aucune règle concerne la signature des tokens JWT, le stockage et la rotation des clés.

**OpenID Connect** est l’un des standards les plus avancés actuellement sur les aspects authentification, autorisation et gestion d’identité en général.

Il faut idéalement éviter l'**Implicit Flow**.

Il faut utiliser des **clés asymétriques**.

Il faut mettre en place **une rotation régulière des clés**.

