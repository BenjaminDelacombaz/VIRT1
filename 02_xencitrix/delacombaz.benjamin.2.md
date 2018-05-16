# VIRT1

Benjamin Delacombaz

SI-T1a

16.05.2018

## Xen Citrix

### Installation et configuration Xen Citrix

1. Créez une machine virtuelle avec 2 cartes réseau (NAT et Host Only), 60 GB de disque et 4 GB de RAM
2. Montez l'ISO de Xen Citrix
3. Démarrez la VM
4. Appuyez sur enter
5. Choisissez le bon clavier
6. Acceptez l'EULA
7. Choisissez le disque ou sera installé votre hyperviseur
8. Choisissez local media
9. N'installez pas de pak supplémentaire
10. Verifiez les sources d'installation
11. Entrez un mot de passe
12. Choisissez l'interface réseau
13. Configurez l'adresse ip en statique
14. Choisissez un nom pour le serveur et entrez un dns (1.1.1.1)
15. Choisissez europe puis Zurich
16. Entrez le temps manuellement
17. Installez XenServer
18. Spécifiez l'heure

### XenCenter

1. Installez XenCenter
2. Cliquez sur Add New Server
3. Entrez l'adresse IP de votre serveur puis vos credential

### ISO LocalISO

1. Connectez-vous en ssh à votre server
2. Controllez l'existence du répertoire suivant: /var/opt/xen/iso_import. S'il n'existe pas lancez la commande suivante:
```
# mkdir -p /var/opt/xen/iso_import
```
3. Si le LocalISO n'existe pas, lancez la commande suivante:
```
# xe sr-create name-label=LocalISO type=iso device-config:location=/var/opt/xen/iso_import device-config:legacy_mode=true content-type=iso
```
4. Télechargez et installez WinSCP
5. Connectez-vous à votre serveur et uploadez votre image ISO
