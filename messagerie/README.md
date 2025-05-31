
# API de Messagerie - Documentation

## Table des matières

### Conversations
- [GET /conversations](./conversations/get-conversations.md) - Récupérer toutes les conversations
- [GET /conversations/:userId](./conversations/get-messages-with-user.md) - Récupérer les messages avec un utilisateur

### Messages Privés
- [POST /send](./messages/send-private-message.md) - Envoyer un message privé
- [PUT /message/:messageId](./messages/update-message.md) - Modifier un message
- [DELETE /message/:messageId](./messages/delete-message.md) - Supprimer un message
- [PATCH /message/:messageId/read](./messages/mark-as-read.md) - Marquer comme lu

### Réactions
- [POST /message/:messageId/reactions](./reactions/add-reaction.md) - Ajouter une réaction
- [DELETE /message/:messageId/reactions](./reactions/remove-reaction.md) - Supprimer une réaction
- [GET /message/:messageId/reactions](./reactions/get-reactions.md) - Récupérer les réactions

### Groupes
- [POST /groups](./groups/create-group.md) - Créer un groupe
- [GET /groups](./groups/get-user-groups.md) - Récupérer les groupes de l'utilisateur
- [POST /groups/:groupId/members](./groups/add-member.md) - Ajouter un membre
- [DELETE /groups/:groupId/leave](./groups/leave-group.md) - Quitter un groupe

### Messages de Groupe
- [POST /groups/:groupId/messages](./groups/messages/send-group-message.md) - Envoyer un message de groupe
- [GET /groups/:groupId/messages](./groups/messages/get-group-messages.md) - Récupérer les messages du groupe
- [PUT /groups/:groupId/messages/:messageId](./groups/messages/update-group-message.md) - Modifier un message de groupe
- [DELETE /groups/:groupId/messages/:messageId](./groups/messages/delete-group-message.md) - Supprimer un message de groupe

### Réactions de Groupe
- [POST /groups/:groupId/messages/:messageId/reactions](./groups/reactions/add-group-reaction.md) - Ajouter une réaction
- [DELETE /groups/:groupId/messages/:messageId/reactions](./groups/reactions/remove-group-reaction.md) - Supprimer une réaction
- [GET /groups/:groupId/messages/:messageId/reactions](./groups/reactions/get-group-reactions.md) - Récupérer les réactions
