
# S'inscrire à un événement

Permet à un utilisateur de s'inscrire à un événement.

## Requête

```
POST /api/events/:id/register
```

## Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique de l'événement |

## Corps de la requête

```json
{
  "userId": 12
}
```

## Réponse de succès

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

## Réponse d'erreur

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