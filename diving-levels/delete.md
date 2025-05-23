
# Supprimer un niveau de plongeur

Supprime un niveau de plongeur du système.

## Requête

```
DELETE /api/diving-levels/:id
```

## Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

## Réponse de succès

```
Status: 204 No Content
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