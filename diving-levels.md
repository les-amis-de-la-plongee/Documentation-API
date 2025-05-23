
# Documentation API - Niveaux de plongeur

Cette section décrit les endpoints API liés aux niveaux de plongeur.

## Table des matières

- [Obtenir tous les niveaux de plongeur](#obtenir-tous-les-niveaux-de-plongeur)
- [Obtenir un niveau de plongeur par ID](#obtenir-un-niveau-de-plongeur-par-id)
- [Créer un nouveau niveau de plongeur](#créer-un-nouveau-niveau-de-plongeur)
- [Mettre à jour un niveau de plongeur](#mettre-à-jour-un-niveau-de-plongeur)
- [Supprimer un niveau de plongeur](#supprimer-un-niveau-de-plongeur)

## Obtenir tous les niveaux de plongeur

Récupère une liste de tous les niveaux de plongeur disponibles.

### Requête

```
GET /api/diving-levels
```

### Réponse de succès

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
```

## Obtenir un niveau de plongeur par ID

Récupère les détails d'un niveau de plongeur spécifique.

### Requête

```
GET /api/diving-levels/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

### Réponse de succès

```
Status: 200 OK
```

```json
{
  "id": 1,
  "name": "Niveau 1",
  "description": "Plongeur encadré jusqu'à 20m",
  "createdAt": "2023-06-01T10:00:00Z",
  "updatedAt": "2023-06-01T10:00:00Z"
}
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Niveau de plongeur non trouvé"
}
```

## Créer un nouveau niveau de plongeur

Ajoute un nouveau niveau de plongeur dans le système.

### Requête

```
POST /api/diving-levels
```

### Corps de la requête

```json
{
  "name": "Niveau 3",
  "description": "Plongeur autonome jusqu'à 60m"
}
```

### Réponse de succès

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

### Réponse d'erreur

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

## Mettre à jour un niveau de plongeur

Modifie un niveau de plongeur existant.

### Requête

```
PUT /api/diving-levels/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

### Corps de la requête

```json
{
  "name": "Niveau 3 - PA60",
  "description": "Plongeur autonome jusqu'à 60m avec expérience"
}
```

### Réponse de succès

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

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Niveau de plongeur non trouvé"
}
```

## Supprimer un niveau de plongeur

Supprime un niveau de plongeur du système.

### Requête

```
DELETE /api/diving-levels/:id
```

### Paramètres de chemin

| Paramètre | Type | Description |
|-----------|------|-------------|
| id        | int  | ID unique du niveau de plongeur |

### Réponse de succès

```
Status: 204 No Content
```

### Réponse d'erreur

```
Status: 404 Not Found
```

```json
{
  "message": "Niveau de plongeur non trouvé"
}
```