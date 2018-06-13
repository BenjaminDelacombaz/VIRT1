# VIRT1

Benjamin Delacombaz

SI-T1a

08.06.2018

## MS Sql Server on Docker

1. Télécharger le container officiel de microsoft mssql-server-linux

2. Ajoutez dans les variables d'environement ACCEPT_EULA true

3. Ajoutez la variable SA_PASSWORD qui sera le password de la base de données, il faut un password du style: Qwertz123456?

4. Téléchargez SQL Server Management Studio et installez le

5. Connectez-vous avec les informations suivante:
```
Type de serveur: Moteur de base de données
Nom du serveur: [IP.du.container], [port]
Authentification: Authentification SQL Server
Connexion: sa
Mot de passe: LeMotDePasseQueVousAvezChoisi
```
