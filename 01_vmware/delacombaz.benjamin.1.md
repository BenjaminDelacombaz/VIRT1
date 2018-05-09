# VIRT1

Benjamin Delacombaz

SI-T1a

09.05.2018

## VMware ESXI

### Installation et configuration ESXI


### Machine virtuelle Debian


### Ajouter un datastore

1. Dans VMware Workstation, ajoutez un disque dur virtuelle à votre machine ESXI
2. Démarrez votre ESXI
3. Connectez-vous à l'aide de l'interface web
4. Cliquez sur stockage, puis nouvelle banque de données
5. Cliquez sur créez une banque de données VMFS
6. Donnez lui un nom et choisissez quel disque utiliser.
7. Sélectionnez utiliser tout l'espace disque et VMFS 5

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


### Veeam Backup Free Edition


