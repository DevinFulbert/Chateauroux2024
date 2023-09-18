# Châteauroux IP / VLAN / SSH#

## Tableaux d'adressage


| N° de VLAN de service| Service         |Adresse IP du VLAN + plage    |    CIDR                |
|:--------------------:|:---------------:|:----------------------------:|:----------------------:|
| 210                  | Management      |172.28.0.0 /24 - 172.28.0.254 |     /24                |
| 211                  |                 |172.28.1.0 /24 - 172.28.1.254 |       /24              |
| 212                  |                 |172.28.2.0 /24 - 172.28.2.254 |          /24           |
| 213                  |                 |172.28.3.0 /24 - 172.28.3.254 |        /24             |


## Définition d'un nom de domaine et création d'un compte SSH sur SWITCH sisco

### Création d'un nom de domaine ##
![Commandes_domaine_cisco](img/domaine.png)

### Génération de la paire de clés asymétriques RSA
![Generate_key_RSA](img/keyRSA.png)

### Activation du protocole SSH sur le switch ou routeur Cisco
![Compte_SSH1](img/SSH1.png)

![Compte_SSH2](img/SSH2.png)

### Test de connexion SSH avec PuTTy
![Test_PuTTy_SSH](img/putty.png)

# En résumé :

### Voici toutes les commandes à utiliser pour configurer une connexion SSH à un switch ou routeur Cisco
![Resume_Commandes_SSH](img/resume.png)

