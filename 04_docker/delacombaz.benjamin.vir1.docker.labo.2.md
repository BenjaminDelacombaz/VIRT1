# VIRT1

Benjamin Delacombaz

SI-T1a

06.06.2018

## Kitematic

### Installation Oracle et SQLDeveloper avec Docker

1. Installez Docker toolbox sur votre poste

2. Cherchez et créez docker-oracle-xe-11g

3. Si vous avez réussis à télécharger, démarrez le container

4. Pour vous connectez à l'interface web: lorsque le container est démarré, cliquez sur web preview connectez-vous à l'aide des credentials suivant: login:system, mdp:oracle et après fermez la fenêtre puis réouvrez la...

5. Téléchargez sqldeveloper et installez-le

6. Lancez dwldeveloper et connectez-vous avec les informations suivantes:
```
Nom de connexion : locale (Nom affiché pour la connexion)
Nom de l’utilisateur : system
Mot de passe : oracle
Nom de l’hôte : IPIPIP (remplacer par l’IP allouée par Docker / voir plus haut)
Port : 32773 (peut être différent, vérifier sur Kitematic)
SID : xe (Identifiant de base oracle par défaut pour Oracle Express)
```
