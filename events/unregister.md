
# Se désinscrire d'un événement

Permet à un utilisateur de se désinscrire d'un événement.

## Requête

```
DELETE /api/events/:id/register
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
  "message": "Désinscription réussie",
  "event": {
    "id": 1,
    "title": "Plongée à la Gabinière",
    "currentParticipants": 8
  }
}
```

## Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Utilisateur non inscrit à cet événement"
}
```