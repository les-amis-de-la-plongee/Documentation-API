# Documentation de l'API Backend

## Introduction

Cette documentation détaille l'ensemble des routes disponibles dans l'API backend, leur utilisation, les paramètres attendus, les réponses retournées et les codes d'erreur possibles.

L'API est construite avec Express.js et utilise MongoDB comme base de données. Elle gère l'authentification, les profils utilisateurs, les événements, les médias et d'autres fonctionnalités pour une application de club de plongée.

## Table des matières

- [Authentification](./auth/README.md)
- [Profil utilisateur](./users/README.md)
- [Événements](./events/README.md)
- [Administration](./admin/README.md)
- [Médias](./media/README.md)
- [Comité](./comite/README.md)
- [Sites de plongée](./diving-sites/README.md)
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