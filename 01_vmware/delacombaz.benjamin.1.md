# VIRT1

Benjamin Delacombaz

SI-T1a

09.05.2018

## VMware ESXI

### Installation et configuration ESXI

1. Créez une machine virtuelle avec 2 cartes réseau (NAT et Host Only)
2. Montez l'ISO d'ESXI
3. Démarrez la VM
4. Choisissez ESXi installer
5. Acceptez l'EULA
6. Séléctionez le disque d'installation
7. Séléctionez le clavier
8. Entrez le mot de passe pour le compte root
9. Une fois l'installation terminée, enlevez l'ISO

### Machine virtuelle Debian

1. Dans l'interface web VMware ESXI, cliquez sur stockage, puis sur datastore1
2. Cliquez sur navigateur de banque de données
3. Cliquez sur télécharger, choisissez l'ISO de Debian
4. Dans l'interface web VMware ESXI, cliquez sur machines virtuelles
5. Cliquez sur Créer/Enregistrer une machine virtuelle
6. Choisissez de créer une machine virtuelle
7. Entrez un nom, puis choisissez Linux comme famille d'OS, puis la version de votre Debian 
8. Choisissez dans quelle datastore elle doit être stockée
9. Pour le lecteur de CD/DVD, sélectionnez fichier ISO banque de de données et choisissez l'ISO de Debian précédemment ajouté
10. Démarrez la machine et faites l'installation de votre Debian

### Ajouter un datastore

1. Dans VMware Workstation, ajoutez un disque dur virtuelle à votre machine ESXI
2. Démarrez votre ESXI
3. Connectez-vous à l'aide de l'interface web
4. Cliquez sur stockage, puis nouvelle banque de données
5. Cliquez sur créez une banque de données VMFS
6. Donnez lui un nom et choisissez quel disque utiliser.
7. Sélectionnez utiliser tout l'espace disque et VMFS 5

<div style="page-break-after: always;"></div>

### Format OVA

1. Dans VMware Workstation, cliquez sur la machine virtuelle concernée
2. Cliquez sur le menu File->Export to OVF
3. Choisissez l'endroit ou vous voulez enregistrer votre fichier
4. Changez l'extension OVF par OVA

### Clone lié

1. Dans VMware Workstation, créez un snapshot de votre machine éteinte en faisant un clique droit sur la machine virtuelle puis snapshot->take a snapshot.
2. Faites un clique droit sur votre machine virtuelle puis cliquez sur manage->clone
3. Sélectionnez d'utiliser un snapshot pour la source du clone
4. Choisissez de créer un clone lié
5. Choisissez un nom et un répertoire

### Upload VMware Workstation -> ESXI

1. Dans VMware Workstation, faites un clique droit sur le clone précédemment créé, puis cliquez sur manage->upload
2. Sélectionnez un autre VMware vSphere serveur
3. Entrez l'IP, le nom d'utilisateur et le mot de passe de votre ESXI
4. Choisissez le nom de la machine et dans quel datastore elle doit être stockée

### VMware Tools

1. Dans l'interface web VMware ESXI, faites un clique droit sur votre machine virtuelle puis SE invité->Installation de VMware Tools
2. Sur windows, un 'cd' va être inséré, lancez l'autorun et attendez que les vmware tools soit installés

### Veeam Backup Free Edition

1. Créez une nouvelle machine virtuelle et installez windows server
2. Uploadez l'iso de VeamBackup dans un de vos datastore puis montez l'iso sur votre serveur
3. Lancez le setup.exe qui se trouve dans l'iso que vous avez monté
4. Choisissez Veam Backup & Replication
5. Laissez l'installation par défaut, si il manque certains modules, installez les
6. Une fois l'installation terminé, lancez l'application
7. Choisissez le serveur localhost avec le port par défaut
8. Ajoutez un serveur avec l'adresse IP de votre Hyperviseur
9. Cliquez sur le serveur que vous venez d'ajouter puis sur la VM que vous voulez backuper
10. Faites un clique droit sur la machine puis VeamZIP to C:\Backup
11. Une fois le backup terminé, supprimez votre VM
12. Cliquez sur l'onglet History puis sur Restore
13. Selectionnez votre fichier de backup
14. Cliquez sur votre VM puis sur restore (complètement)
15. Choisissez de restaurer au même endroit
