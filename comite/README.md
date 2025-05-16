# Routes Comité

## Définir le comité

- **URL** : `/api/admin/comite`
- **Méthode** : `POST`
- **Description** : Définit la liste des membres du comité
- **Authentification requise** : Oui (admin uniquement)

### Paramètres requis (body)

Un tableau d'objets représentant les membres du comité :

```json
[
  {
    "name": "Nom du membre",
    "bio": "Biographie du membre",
    "role": "Rôle dans le comité",
    "image": "ID de l'image uploadé précédément (optionnel)"
  },
  // autres membres
]
```

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Liste des membres du comité créés


```json
{
  "code": 200,
  "message": [
    {
      "_id": "id_membre",
      "name": "Nom du membre",
      "bio": "Biographie du membre",
      "role": "Rôle dans le comité",
      "image": "ID de l'image uploadé précédément"
    },
    // autres membres
  ]
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Format de données invalide
- Champs requis manquants



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Obtenir le comité

- **URL** : `/api/comite`
- **Méthode** : `GET`
- **Description** : Récupère la liste des membres du comité
- **Authentification requise** : Non


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Liste des membres du comité


```json
{
  "code": 200,
  "message": [
    {
      "_id": "id_membre",
      "name": "Nom du membre",
      "bio": "Biographie du membre",
      "role": "Rôle dans le comité",
      "image": "ID de l'image uploadé précédément"
    },
    // autres membres
  ]
}
```

### Réponses d'erreur

- **Code** : `404 Not Found`

- Aucune donnée trouvée



- **Code** : `500 Internal Server Error`

- Erreur serveur