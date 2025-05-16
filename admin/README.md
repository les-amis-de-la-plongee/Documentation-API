# Routes Administration

## Obtenir tous les utilisateurs

- **URL** : `/api/admin/users`
- **Méthode** : `GET`
- **Description** : Récupère la liste de tous les utilisateurs
- **Authentification requise** : Oui (admin uniquement)

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Liste des utilisateurs avec leurs informations

```json
[
  {
    "_id": "id_utilisateur",
    "firstName": "Prénom",
    "lastName": "Nom",
    "email": "email@exemple.com",
    "role": "member",
    "status": "active",
    "joinDate": "2023-01-01",
    "image": true,
    "gender": "M",
    "birthDate": "1990-01-01",
    "address": "123 Rue Exemple",
    "city": "Ville",
    "postalCode": "12345",
    "birthCity": "Ville de naissance",
    "birthPostalCode": "12345",
    "phone": "0123456789",
    "country": "France",
    "profession": "Développeur",
    "emergencyContact": {
      "firstName": "Prénom contact",
      "lastName": "Nom contact",
      "relationship": "Relation",
      "phone": "0123456789"
    },
    "diver": {
      // Informations de plongeur
    }
  },
  // autres utilisateurs
]
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Mettre à jour un utilisateur

- **URL** : `/api/admin/users/:id`
- **Méthode** : `PUT`
- **Description** : Met à jour le profil d'un utilisateur spécifique
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'utilisateur à modifier


### Paramètres optionnels (body)

Tous les champs du profil utilisateur peuvent être mis à jour. Seuls les champs fournis seront modifiés.

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Profil utilisateur mis à jour


```json
{
  "code": 200,
  "message": {
    "firstName": "Prénom",
    "lastName": "Nom",
    "email": "email@exemple.com",
    "password": 60,
    "birthDate": "1990-01-01",
    "role": "member",
    "address": "123 Rue Exemple",
    "postalCode": "12345",
    "image": false,
    "gender": "M",
    "city": "Ville",
    "phone": "0123456789",
    "country": "France",
    "profession": "Développeur",
    "emergencyContact": {
      // Informations de contact d'urgence
    },
    "joinDate": "2023-01-01"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Aucune donnée fournie
- Format de date invalide



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur
- Tentative de modifier un administrateur



- **Code** : `404 Not Found`

- Utilisateur non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Supprimer un utilisateur

- **URL** : `/api/admin/users/:id`
- **Méthode** : `DELETE`
- **Description** : Supprime un utilisateur
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'utilisateur à supprimer


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": {
    "status": "utilisateur supprimé avec succès!",
    "user": {
      // Données de l'utilisateur supprimé
    }
  }
}
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Utilisateur non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Créer un événement

- **URL** : `/api/admin/event`
- **Méthode** : `POST`
- **Description** : Crée un nouvel événement
- **Authentification requise** : Oui (admin uniquement)


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| type | String | Type d'événement (doit être l'un des types prédéfinis)
| date | String | Date de l'événement (format YYYY-MM-DD)
| description | String | Description de l'événement
| public | Boolean | Indique si l'événement est public
| hours | Object | Heure de l'événement (voir structure ci-dessous)


### Structure de hours

```json
{
  "hour": 14, // Heure (0-23)
  "minute": 30 // Minutes (0-59)
}
```

### Types d'événements valides

- "Cours théorique"
- "Baptême"
- "Voyage"
- "Formation"
- "Entrainement"
- "Sortie"


### Réponse de succès

- **Code** : `201 Created`
- **Contenu** : Événement créé


```json
{
  "code": 201,
  "message": {
    "_id": "id_evenement",
    "type": "Cours théorique",
    "hours": {
      "hour": 14,
      "minute": 30
    },
    "date": "2023-06-15",
    "description": "Description de l'événement",
    "public": true,
    "CreatedAt": "2023-05-01T10:00:00.000Z"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Champs requis manquants
- Type d'événement invalide
- Format de date invalide



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Supprimer un événement

- **URL** : `/api/admin/event/:id`
- **Méthode** : `DELETE`
- **Description** : Supprime un événement
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'événement à supprimer


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": {
    "status": "Event supprimé avec succès!",
    "event": {
      // Données de l'événement supprimé
    }
  }
}
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Événement non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur