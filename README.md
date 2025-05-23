# Documentation API

Cette documentation décrit les endpoints de l'API REST du système de gestion de club de plongée.

## Table des matières

- [Authentification](./auth/README.md)
- [Profil utilisateur](./users/README.md)
- [Événements](./events/README.md)
- [Administration](./admin/README.md)
- [Médias](./media/README.md)
- [Comité](./comite/README.md)
- [Sites de plongée](./diving-sites/README.md)
- [Niveaux de plongeur](diving-levels/README.md)
- [Événements](events/README.md)
- [Format des réponses](./common/responses.md)
- [Codes d'erreur](./common/errors.md)

## Authentification

L'API utilise JSON Web Tokens (JWT) pour l'authentification. Pour accéder aux routes protégées, vous devez inclure le token dans l'en-tête de la requête :

```js
  headers: {
    token: "votre_jwt_token"
  }
```

Le token est obtenu lors de la connexion et est valide pendant 30 jours.