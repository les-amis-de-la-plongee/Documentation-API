
# Obtenir la liste des participants

Récupère la liste des participants inscrits à un événement.

## Requête

```
GET /api/events/:id/participants
```

## Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

## Réponse de succès

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

## Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Événement non trouvé"
}
```