# Routes Médias

## Télécharger son avatar

- **URL** : `/api/avatar`
- **Méthode** : `POST`
- **Description** : Télécharge une image comme avatar de l'utilisateur
- **Authentification requise** : Oui
- **Type de contenu** : `multipart/form-data`

### Paramètres requis (form-data)

| Paramètre | Type   | Description           |
|-----------|--------|-----------------------|
| file      | File   | Fichier image (jpeg, jpg, png, gif, webp) |

### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :

```json
{
  "code": 200,
  "message": {
    "file": {
      "_id": "id_utilisateur",
      "filename": "nom_fichier.jpg",
      "contentType": "image/jpeg",
      "length": 12345,
      "fileId": "id_fichier_gridfs"
    },
    "message": "L'avatar a été upload avec succès!",
    "uploadId": "id_upload"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Aucun fichier fourni
- Type de fichier non pris en charge



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié



- **Code** : `404 Not Found`

- Erreur lors de la sauvegarde du fichier



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Récupérer un avatar

- **URL** : `/api/avatar/:id`
- **Méthode** : `GET`
- **Description** : Récupère l'avatar d'un utilisateur
- **Authentification requise** : Non


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'utilisateur


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Fichier image


### Réponses d'erreur

- **Code** : `404 Not Found`

- Avatar non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Télécharger un média

- **URL** : `/api/media`
- **Méthode** : `POST`
- **Description** : Télécharge un fichier média
- **Authentification requise** : Oui
- **Type de contenu** : `multipart/form-data`


### Paramètres requis (form-data)

| Paramètre | Type | Description
|-----|-----|-----
| file | File | Fichier (jpeg, jpg, png, gif, webp, pdf, doc, docx, txt, mp4, mp3)


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": {
    "file": {
      "_id": "id_media",
      "userId": "id_utilisateur",
      "filename": "nom_fichier.jpg",
      "contentType": "image/jpeg",
      "length": 12345,
      "fileId": "id_fichier_gridfs"
    },
    "message": "Le média a été uploadé avec succès!",
    "uploadId": "id_upload"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- Aucun fichier fourni
- Type de fichier non pris en charge



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié



- **Code** : `404 Not Found`

- Erreur lors de la sauvegarde du fichier



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Récupérer un média

- **URL** : `/api/media/:id`
- **Méthode** : `GET`
- **Description** : Récupère un fichier média
- **Authentification requise** : Non


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du média


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Fichier média


### Réponses d'erreur

- **Code** : `404 Not Found`

- Média introuvable



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Supprimer un média

- **URL** : `/api/media/:id`
- **Méthode** : `DELETE`
- **Description** : Supprime un fichier média
- **Authentification requise** : Oui


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID du média à supprimer


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** :


```json
{
  "code": 200,
  "message": {
    "message": "Média supprimé avec succès",
    "mediaId": "id_du_média"
  }
}
```

### Réponses d'erreur

- **Code** : `400 Bad Request`

- ID du média invalide



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié



- **Code** : `404 Not Found`

- Média non trouvé



- **Code** : `500 Internal Server Error`

- Erreur serveur





## Télécharger l'avatar d'un utilisateur (admin)

- **URL** : `/api/admin/avatar/:id`
- **Méthode** : `POST`
- **Description** : Télécharge une image comme avatar d'un utilisateur spécifique
- **Authentification requise** : Oui (admin uniquement)
- **Type de contenu** : `multipart/form-data`


### Paramètres de chemin

| Paramètre | Type | Description
|-----|-----|-----
| id | String | ID de l'utilisateur


### Paramètres requis (form-data)

| Paramètre | Type | Description
|-----|-----|-----
| file | File | Fichier image (jpeg, jpg, png, gif, webp)


### Réponse de succès

- **Code** : `200 OK`
- **Contenu** : Similaire à la réponse de téléchargement d'avatar


### Réponses d'erreur

- **Code** : `400 Bad Request`

- Aucun fichier fourni
- Type de fichier non pris en charge



- **Code** : `401 Unauthorized`

- Utilisateur non authentifié ou non administrateur



- **Code** : `404 Not Found`

- Utilisateur non trouvé
- Erreur lors de la sauvegarde du fichier



- **Code** : `500 Internal Server Error`

- Erreur serveur