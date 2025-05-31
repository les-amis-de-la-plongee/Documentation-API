# GET /conversations

Récupère la liste des conversations de l'utilisateur authentifié.

## URL

```
GET /conversations
```

## Réponse

- **200 OK** : Retourne un tableau de conversations.
    ```json
    [
      {
        "userId": "string",
        "username": "string",
        "lastMessage": {
          "id": "string",
          "content": "string",
          "timestamp": "2024-06-10T12:34:56.789Z"
        }
      }
    ]
    ```
- **401 Unauthorized** : Utilisateur non authentifié.

## Exemple de requête

```
GET /conversations
```

## Exemple de réponse

```json
[
  {
    "userId": "12345",
    "username": "alice",
    "lastMessage": {
      "id": "1",
      "content": "À bientôt !",
      "timestamp": "2024-06-10T12:34:56.789Z"
    }
  }
]
```
