
# Mettre à jour un niveau de plongeur

Modifie un niveau de plongeur existant.

## Requête

```
PUT /api/diving-levels/:id
```

## Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

## Corps de la requête

```json
{
  "name": "Niveau 3 - PA60",
  "description": "Plongeur autonome jusqu'à 60m avec expérience"
}
```

## Réponse de succès

```
Status: 200 OK
```

```json
{
  "id": 3,
  "name": "Niveau 3 - PA60",
  "description": "Plongeur autonome jusqu'à 60m avec expérience",
  "createdAt": "2023-06-02T11:00:00Z",
  "updatedAt": "2023-06-02T12:30:00Z"
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