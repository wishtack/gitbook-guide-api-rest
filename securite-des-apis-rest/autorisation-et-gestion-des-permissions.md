# Autorisation et Gestion des Permissions

En fonction des _credentials_ du client, les autorisations et permissions d’accès sur une ressource peuvent varier.

**Une même ressource** peut donc **retourner des informations différentes en fonction du client**. Cela ne transgresse pas les principes ReST.

Par exemple, pour la même ressource _user_, un rôle _owner_ et un rôle _friend_ n’auront pas accès aux mêmes opérations et propriétés :

**Avec le rôle** _**owner**_ **:** `GET /users/123`

```javascript
{
    "id": "123",
    "firstName": "John",
    "lastName": "DOE",
    "address": {
        "street": "...",
        ...
    }
}
```

**Avec le rôle** _**friend**_ **:** `GET /users/123`

```javascript
{
    "id": "123",
    "firstName": "John",
    "lastName": "DOE"
}
```

### Les Trois Niveaux d'Autorisation

1. **Niveau ressource :** autorisation d’accès à la ressource.
2. **Niveau verbe :** méthodes autorisées sur la ressource _\(create / read / update / delete\)_.
3. **Niveau propriété :** gestion de l’autorisation par propriété _\(read / write / mask / restricted values per role\)_. Ce dernier niveau est malheureusement souvent omis par la plupart des implémentations et frameworks d’API ReST.

Par exemple, la ressource _post_ d’un blog peut avoir une propriété `state` pouvant prendre les valeurs suivantes : `draft`, `private` ou `published`.

Les utilisateurs avec le rôle **administrator** peuvent **modifier cette propriété**.

En revanche, les utilisateurs avec le rôle **editor** peuvent **modifier toutes les autres propriétés sauf celle-ci**.

{% hint style="success" %}
Peu importe l’implémentation, les permissions doivent être faites à base de **whitelist**.
{% endhint %}

{% hint style="success" %}
**Séparez l'implémentation fonctionnelle et la gestion des permissions.**

Pour respecter la _separation of concerns_, améliorer la _scalability_ et faciliter l’implémentation et la compréhension de l’API ReST, il est recommandé d'implémenter la gestion des permissions sur un connecteur dédié.
{% endhint %}

Pour commencer, cette implémentation peut se faire dans un middleware du framework qui plus tard pourra être migré vers un service dédié ou une solution d'API management.

* Ce connecteur est similaire aux A.C.L. _\(Access Control List\)_ que l’on retrouve dans les filesystems ou sur les firewalls.

