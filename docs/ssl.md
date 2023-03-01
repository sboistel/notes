# SSL/TLS

Utilisé pour sécuriser les échanges en HTTPS.

## Fonctionnement

### HTTP

Les échanges entre le serveur et le client se font sans chiffrement et peuvent être interceptés et lus en clair.

### HTTPS sans clés asymétriques

Le client et le serveur échangent des infos grâce à une clé symétrique. Ils la possédent tous les deux et cela leur permet de déchiffrer les échanges. Ils doivent se partager cette clé et si quelqu'un l'intercepte il pourra déchiffrer les messages.

### HTTPS avec clés asymétriques sans CA

Le serveur possède une paire de clés rsa (privée et publique). Le serveur envoie au client sa clé publique afin qu'il puisse chiffrer les données qu'il transmet. Grâce à ça, le client envoie la clé de chiffrement symétrique chiffrée avec la clé publique, que le serveur va déchiffrer grâce à la clé privée. Ils possèdent donc chacun la clé symétrique sans l'avoir envoyée en clair. Mais si quelqu'un s'est fait passer pour le serveur et a envoyé ses propres clés à la place de celles du serveur, il pourra déchiffrer les messages.

### HTTPS

1. Une authorité de certification possède une paire de clé rsa. La clée privée est sécurisée et personne ne la connait, et la clé publique est distribuée à tous les navigateurs, et sera considérée comme une clé vérifiée.
2. Un serveur web veut certifier son identité. Il va créer une paire de clé rsa. Il va envoyer une requète à une CA avec des informations comme le nom de domaine, la clé publique du serveur et d'autres informations. Toutes ces informations vont être chiffrées grâce à un algorithme et le hash obtenu sera appelé empreinte du certificat. La CA va renvoyer ce certificat root en incluant l'empreinte, et va signer cette empreinte avec sa clé privée (elle sera donc chiffrée). On appelle ça la signature du certificat.
3. Un client souhaite se connecter au serveur web. Il va envoyer un Hello au serveur.
4. Le serveur répond en envoyant son certificat root contenant sa clé publique.
5. Le serveur reçoit le certificat. Il va utiliser la clé publique du CA pour déchiffrer la signature du certificat pour obtenir l'empreinte. Il va ensuite chiffrer grâce à l'algorithme communiqué l'ensemble des informations du certificat pour obtenir l'empreinte à nouveau. Il va comparer les deux empreintes. Si elles sont identiques, l'identité du serveur est validée. Si elles sont différentes, cela veut dire que des informations ont été modifées dans le certificat ou alors que ce n'est pas un certificat valide, il refuse donc la connexion.
6. Si la connexion est validée, alors il utilise la clé publique pour envoyer sa clé symétrique chiffrée au serveur qui pourra la déchiffrer grâce à sa clé privée. Ils peuvent alors initialiser la connexion sécurisée grâce à la clé symétrique.