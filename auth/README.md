# Routes d'Authentification

## Inscription

- **URL** : `/api/register`
- **Méthode** : `POST`
- **Description** : Crée un nouvel utilisateur
- **Authentification requise** : Non

### Paramètres requis (body)

| Paramètre | Type   | Description           |
|-----------|--------|-----------------------|
| firstName | String | Prénom de l'utilisateur |
| lastName  | String | Nom de l'utilisateur  |
| email     | String | Email de l'utilisateur |
| password  | String | Mot de passe (min. 6 caractères) |
| role      | String | Rôle de l'utilisateur (généralement "member") |

### Paramètres optionnels (body)

| Paramètre | Type   | Description           |
|-----------|--------|-----------------------|
| birthDate | String | Date de naissance (format YYYY-MM-DD) |
| address   | String | Adresse postale |
| postalCode| String | Code postal |
| gender    | String | Genre |
| city      | String | Ville |
| birthCity | String | Ville de naissance |
| birthPostalCode | String | Code postal de naissance |
| phone     | String | Numéro de téléphone |
| country   | String | Pays |
| profession| String | Profession |
| emergencyContact | Object | Contact d'urgence (voir détails ci-dessous) |

### Structure de emergencyContact

```json
{
  "firstName": "Prénom du contact",
  "lastName": "Nom du contact",
  "relationship": "Relation avec l'utilisateur",
  "phone": "Téléphone du contact"
}
```

### Réponse de succès

- **Code** : `201 Created`
- **Contenu** :


```json
{
  "code": 201,
  "message": {
    "_id": "id_utilisateur",
    "firstName": "Prénom",
    "lastName": "Nom",
    "email": "email@exemple.com",
    "role": "member",
    "status": "active",
    "joinDate": "2023-05-16"
    // autres champs utilisateur
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Champs obligatoires manquants
- Mot de passe trop court
- Email invalide



- **Code** : `403 Forbidden`

- Email déjà utilisé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Connexion

- **URL** : `/api/login`
- **Méthode** : `POST`
- **Description** : Authentifie un utilisateur et retourne un token JWT
- **Authentification requise** : Non


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| email | String | Email de l'utilisateur
| password | String | Mot de passe


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": {
    "token": "jwt_token_valide_30_jours"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Email ou mot de passe manquant
- Email invalide
- Mot de passe invalide



- **Code** : `500 Internal Server Error`

- Erreur serveur