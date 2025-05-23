
# Documentation API - Événements

Cette section décrit les endpoints API liés aux événements de plongée.

## Table des matières

- [Obtenir tous les événements](#obtenir-tous-les-événements)
- [Obtenir un événement par ID](#obtenir-un-événement-par-id)
- [Créer un nouvel événement](#créer-un-nouvel-événement)
- [Mettre à jour un événement](#mettre-à-jour-un-événement)
- [Supprimer un événement](#supprimer-un-événement)
- [S'inscrire à un événement](#sinscrire-à-un-événement)
- [Se désinscrire d'un événement](#se-désinscrire-dun-événement)
- [Obtenir la liste des participants](#obtenir-la-liste-des-participants)

## Obtenir tous les événements

Récupère une liste de tous les événements disponibles.

### Requête

```
GET /api/events
```

### Paramètres de requête optionnels

| Paramètre | Type   | Description                              |
|-----------|--------|------------------------------------------|
| start     | date   | Date de début pour filtrer les événements |
| end       | date   | Date de fin pour filtrer les événements   |
| type      | string | Type d'événement (plongée, formation, etc.) |

### Réponse de succès

```
Status: 200 OK
```

```json
[
  {
    "id": 1,
    "title": "Plongée à la Gabinière",
    "description": "Exploration du site de la Gabinière à Port-Cros",
    "location": "Port-Cros, Hyères",
    "date": "2023-07-15T09:00:00Z",
    "endDate": "2023-07-15T12:00:00Z",
    "type": "dive",
    "maxParticipants": 12,
    "currentParticipants": 8,
    "minLevel": 2,
    "createdAt": "2023-06-01T10:00:00Z",
    "updatedAt": "2023-06-01T10:00:00Z"
  },
  {
    "id": 2,
    "title": "Formation Niveau 1",
    "description": "Formation théorique pour le niveau 1",
    "location": "Local du club",
    "date": "2023-07-20T18:00:00Z",
    "endDate": "2023-07-20T20:00:00Z",
    "type": "training",
    "maxParticipants": 15,
    "currentParticipants": 6,
    "minLevel": 0,
    "createdAt": "2023-06-02T14:00:00Z",
    "updatedAt": "2023-06-02T14:00:00Z"
  }
]
```

## Obtenir un événement par ID

Récupère les détails d'un événement spécifique.

### Requête

```
GET /api/events/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Réponse de succès

```
Status: 200 OK
```

```json
{
  "id": 1,
  "title": "Plongée à la Gabinière",
  "description": "Exploration du site de la Gabinière à Port-Cros",
  "location": "Port-Cros, Hyères",
  "date": "2023-07-15T09:00:00Z",
  "endDate": "2023-07-15T12:00:00Z",
  "type": "dive",
  "maxParticipants": 12,
  "currentParticipants": 8,
  "minLevel": 2,
  "createdAt": "2023-06-01T10:00:00Z",
  "updatedAt": "2023-06-01T10:00:00Z",
  "organizer": {
    "id": 5,
    "firstName": "Jean",
    "lastName": "Dupont",
    "email": "jean.dupont@example.com"
  }
}
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Événement non trouvé"
}
```

## Créer un nouvel événement

Ajoute un nouvel événement dans le système.

### Requête

```
POST /api/events
```

### Corps de la requête

```json
{
  "title": "Sortie épave du Donator",
  "description": "Plongée sur l'épave mythique du Donator",
  "location": "Saint-Raphaël",
  "date": "2023-08-10T08:00:00Z",
  "endDate": "2023-08-10T14:00:00Z",
  "type": "dive",
  "maxParticipants": 8,
  "minLevel": 3,
  "organizerId": 5
}
```

### Réponse de succès

```
Status: 201 Created
```

```json
{
  "id": 3,
  "title": "Sortie épave du Donator",
  "description": "Plongée sur l'épave mythique du Donator",
  "location": "Saint-Raphaël",
  "date": "2023-08-10T08:00:00Z",
  "endDate": "2023-08-10T14:00:00Z",
  "type": "dive",
  "maxParticipants": 8,
  "currentParticipants": 0,
  "minLevel": 3,
  "organizerId": 5,
  "createdAt": "2023-06-15T10:00:00Z",
  "updatedAt": "2023-06-15T10:00:00Z"
}
```

### Réponse d'erreur

```
Status: 400 Bad Request
```

```json
{
  "message": "Données invalides",
  "errors": [
    "Le titre est requis",
    "La date est requise"
  ]
}
```

## Mettre à jour un événement

Modifie un événement existant.

### Requête

```
PUT /api/events/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Corps de la requête

```json
{
  "title": "Sortie épave du Donator - Mise à jour",
  "maxParticipants": 10,
  "date": "2023-08-11T09:00:00Z"
}
```

### Réponse de succès

```
Status: 200 OK
```

```json
{
  "id": 3,
  "title": "Sortie épave du Donator - Mise à jour",
  "description": "Plongée sur l'épave mythique du Donator",
  "location": "Saint-Raphaël",
  "date": "2023-08-11T09:00:00Z",
  "endDate": "2023-08-10T14:00:00Z",
  "type": "dive",
  "maxParticipants": 10,
  "currentParticipants": 0,
  "minLevel": 3,
  "createdAt": "2023-06-15T10:00:00Z",
  "updatedAt": "2023-06-15T11:30:00Z"
}
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Événement non trouvé"
}
```

## Supprimer un événement

Supprime un événement du système.

### Requête

```
DELETE /api/events/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Réponse de succès

```
Status: 204 No Content
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Événement non trouvé"
}
```

## S'inscrire à un événement

Permet à un utilisateur de s'inscrire à un événement.

### Requête

```
POST /api/events/:id/register
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Corps de la requête

```json
{
  "userId": 12
}
```

### Réponse de succès

```
Status: 200 OK
```

```json
{
  "message": "Inscription réussie",
  "event": {
    "id": 1,
    "title": "Plongée à la Gabinière",
    "currentParticipants": 9
  },
  "user": {
    "id": 12,
    "firstName": "Marie",
    "lastName": "Dubois"
  }
}
```

### Réponse d'erreur

```
Status: 400 Bad Request
```

```json
{
  "message": "Inscription impossible",
  "error": "L'événement est complet"
}
```

```
Status: 403 Forbidden
```

```json
{
  "message": "Inscription impossible",
  "error": "Niveau de plongée insuffisant"
}
```

## Se désinscrire d'un événement

Permet à un utilisateur de se désinscrire d'un événement.

### Requête

```
DELETE /api/events/:id/register
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Corps de la requête

```json
{
  "userId": 12
}
```

### Réponse de succès

```
Status: 200 OK
```

```json
{
  "message": "Désinscription réussie",
  "event": {
    "id": 1,
    "title": "Plongée à la Gabinière",
    "currentParticipants": 8
  }
}
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Utilisateur non inscrit à cet événement"
}
```

## Obtenir la liste des participants

Récupère la liste des participants inscrits à un événement.

### Requête

```
GET /api/events/:id/participants
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

### Réponse de succès

```
Status: 200 OK
```

```json
[
  {
    "id": 8,
    "firstName": "Pierre",
    "lastName": "Martin",
    "email": "pierre.martin@example.com",
    "level": {
      "id": 3,
      "name": "Niveau 3"
    },
    "registeredAt": "2023-06-10T14:25:00Z"
  },
  {
    "id": 12,
    "firstName": "Marie",
    "lastName": "Dubois",
    "email": "marie.dubois@example.com",
    "level": {
      "id": 2,
      "name": "Niveau 2"
    },
    "registeredAt": "2023-06-12T09:30:00Z"
  }
]
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Événement non trouvé"
}
```