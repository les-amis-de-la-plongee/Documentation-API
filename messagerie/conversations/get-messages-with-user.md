# GET /conversations/messages/{userId}

Récupère la liste des messages échangés avec un utilisateur spécifique.

## URL

```
GET /conversations/messages/{userId}
```

## Paramètres

- `userId` (path, requis) : L'identifiant de l'utilisateur avec qui récupérer les messages.

## Réponse

- **200 OK** : Retourne un tableau de messages.
    ```json
    [
      {
        "id": "string",
        "senderId": "string",
        "receiverId": "string",
        "content": "string",
        "timestamp": "2024-06-10T12:34:56.789Z"
      }
    ]
    ```
- **404 Not Found** : Utilisateur non trouvé ou aucune conversation.

## Exemple de requête

```
GET /conversations/messages/12345
```

## Exemple de réponse

```json
[
  {
    "id": "1",
    "senderId": "12345",
    "receiverId": "67890",
    "content": "Bonjour !",
    "timestamp": "2024-06-10T12:34:56.789Z"
  }
]
```
