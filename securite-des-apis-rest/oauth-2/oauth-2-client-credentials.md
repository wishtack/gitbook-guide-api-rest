# OAuth 2 Client Credentials

Le **Client** peut demander un **Access Token** à l'**Authorization Server** afin d’accéder à ses propres données.

```javascript
POST https://accounts.google.com/token?
grant_type=client_credentials
&client_id=CLIENT_ID
&client_secret=CLIENT_SECRET
```



