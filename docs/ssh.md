# 4/ Définition d'un nom de domaine et création d'un compte SSH sur SWITCH cisco

[Connexion SSH](https://www.astarox.com/blog/connexion-ssh-a-un-switch-ou-un-routeur-cisco-b12.html)


# En résumé :

### Voici toutes les commandes que nous avons utilisé pour configurer une connexion SSH à notre switch Cisco

`>en`

`#show run`

`#conf t`
## Création des noms d'hôte et de domaine, et d'un mot de passe pour le mode privilégié

La création d’un nom d’hôte et d’un nom de domaine est indispensable à la configuration d’une connexion SSH. Vous devez donc être en mode configuration et réaliser les commandes suivantes :

`hostname <sw-Chateauroux>`

`ip domain-name <chateauroux.sportludique.fr>`

Ici, nous avons choisi de donner pour nom d’hôte sw-Chateauroux et pour nom de domaine chateauroux.sportludique.fr.

Pour créer un mot de passe pour le mode privilégié, il faut se placer dans le mode configuration et entrer la commande :

`#enable password <P@ssw0rd123456!>`

## Génération de la paire de clés asymétriques RSA

RSA est une méthode de chiffrement dite asymétrique. Elle est composée de deux clés, une privée et une publique, chiffrées sur 768 bits minimum pour le SSH v2, et permet d’assurer une sécurité optimale. Pour générer cette paire de clés, il suffit d’entrer la commande :

`crypto key generate rsa`

`exit`

Il est également demandé d’entrer la taille souhaitée de la clé en bits. Il est préférable de choisir une taille supérieure à 768 bits pour assurer une plus grande sécurité. Nous avons ici choisi des clés de 1024 bits.

`How many bits in the modulus [512] : <1024>`

## Activation du protocole SSH sur le switch ou routeur Cisco

`(config)#ip ssh version 2`

`(config)#line vty 0 4`

`(config-line)#transport input ssh`

`(config-line)#transport output ssh`

`(config-line)#login local`

`(config-line)#exit`

`(config)#username <admin> password <P@ssw0rd123456!>`

`(config)#exit`

`#show run`

