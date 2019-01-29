# Ressource d'Association

Supposons la ressource `/users/123ab/friends` :

```javascript
{
  "objects": [
    {
      "id": ...,
      "firstName": ...,
      "type": "user"
    } 
  ]
}
```

{% tabs %}
{% tab title="🧐" %}
Comment représenter la _datetime_ de création du lien entre les utilisateurs ?
{% endtab %}

{% tab title="👍" %}
Nous pouvons créer une ressource de type collection qui représente ces liens.

Exemple : `/friendships?userId=123ab`

```javascript
{
  "objects": [
    {
      "id": "FRIENDSHIP_ID_1",
      "creationDateTime": "2017-01-01T18:16:00.000Z",
      "friend": {
        "id": ...,
        "type": "user"
      }
    },
    ...
  ]
}
```

... puis la ressource d'instance `/friendships/FRIENDSHIP_ID_1` permettant d'accéder, modifier ou supprimer la relation.  
Exemple : `DELETE /friendships/FRIENDSHIP_ID_1`.
{% endtab %}
{% endtabs %}



