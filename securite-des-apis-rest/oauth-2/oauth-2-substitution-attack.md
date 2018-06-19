# OAuth 2 Substitution Attack

## **Description de l’Attaque**

Cette attaque suppose que l’attaquant et la victime sont des **Resource Owners** inscrits auprès du même **Authorization Server**.

1. L’attaquant initie un **Authorization Code Flow** _\(ou **Implicit Flow**\)_.
2. L’attaquant interrompt le scénario à[ l’étape 3 ](oauth-2-authorization-code-flow.md)_\(quand il obtient l'**Authorization Code** ou l'**Access Token**\)_.
3. L’attaquant incite la victime à suivre un lien pointant vers l’URL contenant l'Authorization code ou l'**Access Token** obtenu à l’étape précédente _\(social engineering ou application malicieuse\)_.
4. La victime suit l’URL vers le **Client** qui interagit alors avec les ressources de l’attaquant.

## **Quelques Exemples de Scénarios**

### Banque

1. L’attaquant et la victime sont clients d’une même banque.
2. La victime se retrouve alors sur l’application de la banque avec les données de l’attaquant.
3. En pensant télécharger son propre RIB, la victime récupère le RIB de l’attaquant.

### Messagerie

1. L’attaquant usurpe l’identité de la victime en créant un faux compte sur Facebook.
2. L’attaquant ajoute des "amis" de la victime.
3. L’attaquant s’inscrit sur une application de messagerie utilisant le service OAuth 2 de Facebook.
4. La victime se retrouve sur l’application de messagerie avec le compte de l’attaquant et échange avec ses propres amis via ce compte.
5. L’attaquant se connecte à son tour sur l’application de messagerie pour récupérer les correspondances de la victime.

## **Origine de la Vulnérabilité et Solution**

Cette vulnérabilité existe car OAuth 2 n’impose aucun lien entre l’étape 1 _\(**demande** de l'**Authorization Code** ou **Access Token**\)_ et l’étape 3 _\(**récupération** de l'**Authorization Code** ou **Access Token**\)_.

Heureusement, il existe un paramètre **optionnel** `state`, initialement prévu pour que le **Client** puisse retrouver son état initial après l’autorisation.

Ce paramètre est désormais détourné de son objectif initial. Il permet de lutter contre cette attaque en vérifiant que le **Resource Owner** autorisé est bien celui à l’origine de la demande.

Cela s’implémente le plus souvent de la façon suivante :

1. Le **Client** génère un **nonce** imprédictible et unique à chaque demande d’autorisation.
2. Le **Client** le positionne par exemple dans un "cookie" et dans le paramètre `state` avant de rediriger le **Resource Owner** vers l'**Authorization Server**.
3. L'**Authorization Server** redirige alors le **Resource Owner** vers le **Client** en transmettant le `state` à l’identique.
4. Le **Client** vérifie que le `state` correspond au **nonce** dans le cookie.

Malheureusement, il s’agit d’une vulnérabilité conceptuelle dans le standard OAuth 2 et qui se joue à un mot près.

Le paramètre `state` est donc “RECOMMENDED” au lieu d’être “REQUIRED” laissant ainsi le choix au **Client** de rester vulnérable à cette attaque.

Si l'**Authentication Server** rend ce paramètre obligatoire, il n’est alors plus conforme au standard.

**OpenID Connect** ajoute une notion de **nonce** plus explicite mais pour rester compatible avec OAuth 2, ce paramètre est également optionnel 😭.

## **Solution et Contournements**

La solution la plus rigoureuse est de rendre le paramètre `state` obligatoire mais bien sûr, sans vérification côté **Client**, ce paramètre est inutile. Par contre, on sort alors du standard.

L'**Authorization Server** peut réduire le périmètre d’autorisation en l’absence du paramètre `state`.

C’est l’une des raisons pour lesquelles il est nécessaire de réduire la durée de vie de l'**Authorization Code** au minimum. En revanche, si le client utilise l'**Implicit Flow**, on ne peut pas réduire la durée de vie de l'**Access Token** à quelques minutes.

