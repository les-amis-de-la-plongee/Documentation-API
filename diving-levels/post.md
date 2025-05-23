
# Créer un nouveau niveau de plongeur

Ajoute un nouveau niveau de plongeur dans le système.

## Requête

```
POST /api/diving-levels
```

## Corps de la requête

```json
{
  "name": "Niveau 3",
  "description": "Plongeur autonome jusqu'à 60m"
}
```

## Réponse de succès

```
Status: 201 Created
```

```json
{
  "id": 3,
  "name": "Niveau 3",
  "description": "Plongeur autonome jusqu'à 60m",
  "createdAt": "2023-06-02T11:00:00Z",
  "updatedAt": "2023-06-02T11:00:00Z"
}
```

## Réponse d'erreur

```
Status: 400 Bad Request
```

```json
{
  "message": "Données invalides",
  "errors": [
    "Le nom du niveau est requis"
  ]
}
```