# Routes Événements

## Obtenir les événements

- **URL** : `/api/events`
- **Méthode** : `GET`
- **Description** : Récupère la liste des événements
- **Authentification requise** : Non (mais influence les résultats)

### Comportement

- Si l'utilisateur est authentifié (token fourni), tous les événements sont retournés
- Si l'utilisateur n'est pas authentifié, seuls les événements publics sont retournés

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :

```json
{
  "code": 200,
  "message": [
    {
      "_id": "id_evenement",
      "type": "Cours théorique",
      "hours": {
        "hour": 14,
        "minute": 30
      },
      "date": "2023-06-15",
      "description": "Description de l'événement",
      "public": true,
      "CreatedAt": "2023-05-01T10:00:00.000Z"
    },
    // autres événements
  ]
}
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Token invalide



- **Code** : `404 Not Found`

- Utilisateur non trouvé (si token fourni)



- **Code** : `500 Internal Server Error`

- Erreur serveur