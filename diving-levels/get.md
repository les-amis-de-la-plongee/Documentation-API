
# Obtenir tous les niveaux de plongeur

Récupère une liste de tous les niveaux de plongeur disponibles.

## Requête

```
GET /api/diving-levels
```

## Réponse de succès

```
Status: 200 OK
```

```json
[
  {
    "id": 1,
    "name": "Niveau 1",
    "description": "Plongeur encadré jusqu'à 20m",
    "createdAt": "2023-06-01T10:00:00Z",
    "updatedAt": "2023-06-01T10:00:00Z"
  },
  {
    "id": 2,
    "name": "Niveau 2",
    "description": "Plongeur autonome jusqu'à 20m et encadré jusqu'à 40m",
    "createdAt": "2023-06-01T10:00:00Z",
    "updatedAt": "2023-06-01T10:00:00Z"
  }
]