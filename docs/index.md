# Châteauroux IP / VLAN / SSH#

## Tableau du réseau de Châteauroux

| @ Réseau             | CIDR            |Broadcast                     |                  
|:--------------------:|:---------------:|:----------------------------:|
| 172.28.0.0           |    /19          |172.28.31.255                 |    

 



## Tableaux d'adressage VLAN


| N° de VLAN de service| Service         | @ VLAN                       |    CIDR                |
|:--------------------:|:---------------:|:----------------------------:|:----------------------:|
| 210                  | Management      |172.28.0.1 /24                |     /24                |
| 211                  |                 |172.28.1.1 /24 - 172.28.1.254 |     /24              |
| 212                  |                 |172.28.2.1 /24 - 172.28.2.254 |      /24           |
| 213                  |                 |172.28.3.1 /24 - 172.28.3.254 |        /24             |


## Définition d'un nom de domaine et création d'un compte SSH sur SWITCH sisco

### Création d'un nom de domaine ##
![Commandes_domaine_cisco](domaine.png)

### Génération de la paire de clés asymétriques RSA
![Generate_key_RSA](keyRSA.png)

### Activation du protocole SSH sur le switch ou routeur Cisco
![Compte_SSH1](SSH1.png)

![Compte_SSH2](SSH2.png)

### Test de connexion SSH avec PuTTy
![Test_PuTTy_SSH](putty.png)

# En résumé :

### Voici toutes les commandes à utiliser pour configurer une connexion SSH à un switch ou routeur Cisco
![Resume_Commandes_SSH](resume.png)

