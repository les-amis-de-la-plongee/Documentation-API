# Routes Sites de Plongée

## Obtenir tous les sites de plongée

- **URL** : `/api/diving-sites`
- **Méthode** : `GET`
- **Description** : Récupère la liste de tous les sites de plongée
- **Authentification requise** : Non

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :

```json
{
  "code": 200,
  "message": [
    {
      "_id": "id_site",
      "name": "Nom du site",
      "images": [
        "ID_image_1",
        "ID_image_2"
      ],
      "createdAt": "2023-05-01T10:00:00.000Z",
      "updatedAt": "2023-05-01T10:00:00.000Z"
    },
    // autres sites
  ]
}
```

### Réponses d'erreur

- **Code** : `500 Internal Server Error`

- Erreur serveur





## Créer un site de plongée

- **URL** : `/api/admin/diving-sites`
- **Méthode** : `POST`
- **Description** : Crée un nouveau site de plongée
- **Authentification requise** : Oui (admin uniquement)


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| name | String | Nom du site de plongée
| images | Array | Tableau d'URLs d'images


Exemple:

```json
{
  "name": "Nom du site",
  "images": [
    "ID_image_1",
    "ID_image_2"
  ]
}
```

### Réponse de succès

- **Code** : `201 Created`
- **Contenu** : Site de plongée créé


```json
{
  "code": 201,
  "message": {
    "_id": "id_site",
    "name": "Nom du site",
    "images": [
      "ID_image_1",
      "ID_image_2"
    ],
    "createdAt": "2023-05-01T10:00:00.000Z",
    "updatedAt": "2023-05-01T10:00:00.000Z"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Nom ou images manquants



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Mettre à jour le nom d'un site de plongée

- **URL** : `/api/admin/diving-sites/:id`
- **Méthode** : `PATCH`
- **Description** : Met à jour le nom d'un site de plongée
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du site de plongée


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| name | String | Nouveau nom du site


Exemple:

```json
{
  "name": "Nouveau nom du site"
}
```

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Site de plongée mis à jour


```json
{
  "code": 200,
  "message": {
    "_id": "id_site",
    "name": "Nouveau nom du site",
    "images": [
      "ID_image_1",
      "ID_image_2"
    ],
    "createdAt": "2023-05-01T10:00:00.000Z",
    "updatedAt": "2023-05-01T10:00:00.000Z"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Nom manquant ou invalide



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Site de plongée non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Supprimer un site de plongée

- **URL** : `/api/admin/diving-sites/:id`
- **Méthode** : `DELETE`
- **Description** : Supprime un site de plongée
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du site de plongée


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": "Le site de plongé à été supprimé avec succès !"
}
```

### Réponses d'erreur

- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Site de plongée non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Ajouter des images à un site de plongée

- **URL** : `/api/admin/diving-sites/:id/images`
- **Méthode** : `PATCH`
- **Description** : Ajoute des images à un site de plongée
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du site de plongée


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| images | Array | Tableau d'URLs d'images à ajouter


Exemple:

```json
{
  "images": [
    "ID_nouvelle_image_1",
    "ID_nouvelle_image_2"
  ]
}
```

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Site de plongée mis à jour


```json
{
  "code": 200,
  "message": {
    "_id": "id_site",
    "name": "Nom du site",
    "images": [
      "ID_image_1",
      "ID_image_2",
      "ID_nouvelle_image_1",
      "ID_nouvelle_image_2"
    ],
    "createdAt": "2023-05-01T10:00:00.000Z",
    "updatedAt": "2023-05-01T10:00:00.000Z"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Tableau d'images manquant ou vide



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Site de plongée non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Supprimer des images d'un site de plongée

- **URL** : `/api/admin/diving-sites/:id/images`
- **Méthode** : `DELETE`
- **Description** : Supprime des images d'un site de plongée
- **Authentification requise** : Oui (admin uniquement)


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du site de plongée


### Paramètres requis (body)

| Paramètre | Type | Description
|-----|-----|-----
| images | Array | Tableau d'URLs d'images à supprimer


Exemple:

```json
{
  "images": [
    "ID_image_a_supprimer_1",
    "ID_image_a_supprimer_2"
  ]
}
```

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Site de plongée mis à jour


```json
{
  "code": 200,
  "message": {
    "_id": "id_site",
    "name": "Nom du site",
    "images": [
      "ID_image_restante_1",
      "ID_image_restante_2"
    ],
    "createdAt": "2023-05-01T10:00:00.000Z",
    "updatedAt": "2023-05-01T10:00:00.000Z"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Tableau d'images manquant ou vide
- Un site doit contenir au moins une image



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Site de plongée non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur