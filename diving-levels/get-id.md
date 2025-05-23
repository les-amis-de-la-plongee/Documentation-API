
# Obtenir un niveau de plongeur par ID

Récupère les détails d'un niveau de plongeur spécifique.

## Requête

```
GET /api/diving-levels/:id
```

## Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

## Réponse de succès

```
Status: 200 OK
```

```json
{
  "id": 1,
  "name": "Niveau 1",
  "description": "Plongeur encadré jusqu'à 20m",
  "createdAt": "2023-06-01T10:00:00Z",
  "updatedAt": "2023-06-01T10:00:00Z"
}
```

## Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Niveau de plongeur non trouvé"
}
```