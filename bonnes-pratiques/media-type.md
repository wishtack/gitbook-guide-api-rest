# Media Type

Le Media Type habituel défini avec le header `Content-Type` est `application/json`.

Il est courant de définir un Media Type spécifique pour une API ou éventuellement en fonction du "standard" utilisé. Exemple : `application/vnd.github+json`.

Les “media type” de type `application/vnd*` ne sont pas standards et peuvent éventuellement poser des problèmes avec certaines librairies ou connecteurs _\(Ex.: Web Application Firewall\)_.

Certains s’amusent à retourner un contenu HTML _\(présentation, documentation, démo etc…\)_ lorsque le client ne présente pas le bon Media Type dans le header `Accept`.

C’est élégant…

…mais pas pratique du tout ! Qui n’a jamais testé une URL d’API ReST sur son browser ?

{% hint style="info" %}
Nous verrons plus tard que pour des raisons sécurité, il est recommandé de rejeter les requêtes ne présentant pas le bon header `Content-Type`.
{% endhint %}

