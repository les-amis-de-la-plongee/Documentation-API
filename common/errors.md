# Codes d'erreur

L'API utilise les codes d'erreur HTTP standard :

| Code | Nom                  | Description                                                  |
|------|----------------------|--------------------------------------------------------------|
| 200  | OK                   | La requête a réussi                                          |
| 201  | Created              | La ressource a été créée avec succès                         |
| 400  | Bad Request          | La requête est mal formée ou contient des données invalides  |
| 401  | Unauthorized         | Authentification requise ou échouée                          |
| 403  | Forbidden            | L'accès à la ressource est interdit                          |
| 404  | Not Found            | La ressource demandée n'existe pas                           |
| 500  | Internal Server Error| Une erreur est survenue côté serveur                         |

## Détails des erreurs courantes

### 400 Bad Request

Cette erreur est retournée lorsque la requête est mal formée ou contient des données invalides. Exemples :

- Champs obligatoires manquants
- Format de données invalide
- Validation échouée

Exemple de réponse :

```json
{
  "code": 400,
  "message": "Veuillez mentionner le type, la date, la description, le public et l'heure!"
}
```

### 401 Unauthorized

Cette erreur est retournée lorsque l'authentification est requise mais n'a pas été fournie ou est invalide. Exemples :

- Token JWT manquant
- Token JWT expiré ou invalide
- Utilisateur non autorisé à accéder à la ressource


Exemple de réponse :

```json
{
  "code": 401,
  "message": "Unauthorized"
}
```

### 403 Forbidden

Cette erreur est retournée lorsque l'utilisateur est authentifié mais n'a pas les droits nécessaires pour accéder à la ressource. Exemples :

- Tentative d'accès à une ressource réservée aux administrateurs
- Email déjà utilisé lors de l'inscription


Exemple de réponse :

```json
{
  "code": 403,
  "message": "Email déjà utilisé"
}
```

### 404 Not Found

Cette erreur est retournée lorsque la ressource demandée n'existe pas. Exemples :

- ID d'utilisateur inexistant
- ID d'événement inexistant
- Fichier média introuvable


Exemple de réponse :

```json
{
  "code": 404,
  "message": "Utilisateur non trouvé"
}
```

### 500 Internal Server Error

Cette erreur est retournée lorsqu'une erreur inattendue survient côté serveur. Exemples :

- Erreur de connexion à la base de données
- Exception non gérée dans le code


Exemple de réponse :

```json
{
  "code": 500,
  "message": "Internal server error"
}
```

## Gestion des erreurs côté client

Pour gérer efficacement les erreurs côté client, il est recommandé de :

1. Vérifier le code de statut HTTP de la réponse
2. Analyser le message d'erreur pour obtenir plus de détails
3. Afficher un message d'erreur approprié à l'utilisateur
4. Journaliser les erreurs 500 pour investigation ultérieure


Exemple de gestion d'erreur en JavaScript :

```javascript
fetch('/api/endpoint')
  .then(response => {
    if (!response.ok) {
      return response.json().then(err => {
        throw new Error(`${err.code}: ${err.message}`);
      });
    }
    return response.json();
  })
  .then(data => {
    // Traiter les données
  })
  .catch(error => {
    console.error('Erreur:', error);
    // Afficher un message d'erreur à l'utilisateur
  });
```