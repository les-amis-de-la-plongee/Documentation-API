
# Routes Profil Utilisateur

## Obtenir son profil

- **URL** : `/api/@me`
- **Méthode** : `GET`
- **Description** : Récupère le profil de l'utilisateur connecté
- **Authentification requise** : Oui

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :

```json
{
  "code": 200,
  "message": {
    "id": "id_utilisateur",
    "firstName": "Prénom",
    "lastName": "Nom",
    "email": "email@exemple.com",
    "password": 60, // Longueur du hash du mot de passe
    "birthDate": "1990-01-01",
    "role": "member",
    "status": "active",
    "joinDate": "2023-01-01",
    "image": "http://localhost:3000/api/avatar/id_utilisateur", // URL de l'avatar si existant
    "gender": "M",
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
      "honorability": true,
      "insurance": "Numéro assurance",
      "caciDate": "2023-01-01",
      "caciFile": "chemin_fichier",
      "licenseOrg": "Organisation",
      "licenseNumber": "Numéro licence",
      "licenseExpiry": "2024-01-01",
      "licenseFile": "chemin_fichier"
    }
  }
}
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Utilisateur non authentifié



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Mettre à jour son profil

- **URL** : `/api/@me`
- **Méthode** : `PUT`
- **Description** : Met à jour le profil de l'utilisateur connecté
- **Authentification requise** : Oui


### Paramètres optionnels (body)

Tous les champs du profil utilisateur peuvent être mis à jour. Seuls les champs fournis seront modifiés.

Exemple de body:

```json
{
  "firstName": "Nouveau prénom",
  "lastName": "Nouveau nom",
  "email": "nouvel.email@exemple.com",
  "birthDate": "1990-01-01",
  "address": "Nouvelle adresse",
  "postalCode": "12345",
  "gender": "F",
  "city": "Nouvelle ville",
  "phone": "0123456789",
  "country": "France",
  "profession": "Nouvelle profession",
  "emergencyContact": {
    "firstName": "Prénom contact",
    "lastName": "Nom contact",
    "relationship": "Relation",
    "phone": "0123456789"
  },
  "diver": {
    "honorability": true,
    "insurance": "Numéro assurance",
    "caciDate": "2023-01-01",
    "licenseOrg": "Organisation",
    "licenseNumber": "Numéro licence",
    "licenseExpiry": "2024-01-01"
  }
}
```

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Profil utilisateur mis à jour (même format que la réponse GET)


### Réponses d'erreur

- **Code** : `400 Bad Request`

- Aucune donnée fournie
- Aucune modification détectée



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Obtenir le profil d'un utilisateur

- **URL** : `/api/user/:id`
- **Méthode** : `GET`
- **Description** : Récupère le profil d'un utilisateur spécifique
- **Authentification requise** : Non


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'utilisateur (24 caractères)


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Profil utilisateur (même format que la réponse GET /@me)


### Réponses d'erreur

- **Code** : `400 Bad Request`

- ID manquant ou invalide



- **Code** : `404 Not Found`

- Utilisateur non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur