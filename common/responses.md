# Format des réponses

Toutes les réponses de l'API suivent un format standard :

```json
{
  "code": 200,
  "message": "données_ou_message"
}
```

- `code` : Code HTTP de la réponse
- `message` : Données retournées ou message d'information/erreur


## Exemples de réponses

### Réponse de succès avec données

```json
{
  "code": 200,
  "message": {
    "id": "60d21b4667d0d8992e610c85",
    "firstName": "Jean",
    "lastName": "Dupont",
    "email": "jean.dupont@exemple.com"
    // autres données
  }
}
```

### Réponse de succès avec tableau de données

```json
{
  "code": 200,
  "message": [
    {
      "id": "60d21b4667d0d8992e610c85",
      "name": "Nom de l'élément 1"
      // autres données
    },
    {
      "id": "60d21b4667d0d8992e610c86",
      "name": "Nom de l'élément 2"
      // autres données
    }
  ]
}
```

### Réponse de création réussie

```json
{
  "code": 201,
  "message": {
    "id": "60d21b4667d0d8992e610c85",
    "name": "Nom de l'élément créé"
    // autres données
  }
}
```

### Réponse d'erreur

```json
{
  "code": 400,
  "message": "Message d'erreur explicatif"
}
```

### Réponse de suppression réussie

```json
{
  "code": 200,
  "message": {
    "status": "Élément supprimé avec succès!",
    "element": {
      // Données de l'élément supprimé
    }
  }
}
```