# OAuth 2 Roles

OAuth 2 définit 4 rôles.

### Resource Owner

Une entité disposant de la légitimité et du pouvoir décisionnel lui permettant d’autoriser l’accès à une ou plusieurs ressources protégées.

_E.g.: L’utilisateur des services google qui souhaite autoriser une application d'agrégation d'agendas à accéder à son agenda._

### Resource Server

Ce service détient les ressources protégées. Il est capable de répondre aux requêtes d’accès à ces ressources en fonction des _access tokens_ présentés.

_E.g. : Google Calendar._

### Client

Une application émettant des requêtes à destination du **Resource Server** au nom du **Resource Owner** et avec son autorisation.  
Le **Client** peut être entièrement frontend _\(Web / Progressive Web App / Mobile Web App / Desktop etc…\)_ ou backend _\(Serveur / Minitel etc…\)_.

_E.g. : L’application d’agrégation d’agendas._

Nous distinguerons deux types de **Clients**

#### Confidential

Capable de garder un secret.  
  
_E.g. : Backend_

#### Public

Incapable de garder un secret.

_E.g. : Frontend, Single Page App, Progressive Web App, Mobile, Desktop, Appliance…_

### **Authorization Server**

Un serveur qui fournit des _access tokens_ après authentification du **Resource Owner** et obtention des autorisations.

_E.g. : Service d’authentification et d’autorisation google. Google accounts._

