# 7/ Routeur 

## <span style="color: black"> **Installation du Routeur** ##

Pour commencer **l'installation du routeur**, on a besoin de **reset sa configuration** :

**`confreg 0x2142`**

**`reset`**

**`confreg 0x2102`**

**`reset`**

Ensuite **la configuration du port ou on connectera reseau local** : 

Quand la question "**Quelle interface on souhaite choisir**", on y selectionne :

**`GigabitEthernet 0/1`** (pour notre cas)

### <span style="color: black"> **Connexion SSH** ###

#### <span style="color: black"> **Nom de domaine** ####

On commence par **configurer un nom de domaine** au routeur :

**`enable`**

**`conf t`**

**`hostname R1_CHX`**

**`ip domain-name chateauroux.sportludique.fr`**

#### <span style="color: black"> **Configuration routeur pour SSH** ####

**`enable`**

**`conf t`**

**`crypto key generate rsa general-keys modulus 1024`**

**`ip ssh version 2`**

#### <span style="color: black"> **Options facultatif** ####

**`ip ssh logging events`** Pour enregistrer les évènements associés aux connexions ssh sont enregistrés dans les logs

**`ip ssh time-out 60`** Un timeout de 60 secondes est ajouté en cas d'inactivité durant l'authentification.

**`ip ssh authentication-retries 3`** Nous laissons trois essais pour la connexion au routeur. Suite à ces essais, la connexion sera fermée.

### <span style="color: black"> **Configuration de la gateway du routeur** ###

#### <span style="color: black"> **R1** ####

Gateway : **`172.28.3.253 /24`**

#### <span style="color: black"> **R2** ####

Gateway : **`172.28.3.252 /24`**

### <span style="color: black"> **Configuration du protocole GLBP** ###

GLBP, qui signifie "Gateway Load Balancing Protocol" (Protocole d'équilibrage de charge de passerelle), est un protocole de routage de premier saut (First Hop Routing) développé par Cisco Systems. Il est principalement utilisé pour répartir la charge du trafic entre plusieurs routeurs ou passerelles dans un réseau local (LAN) afin d'améliorer la disponibilité et la performance des passerelles par défaut.

Pour configurer le protocole, il faudra accéder à l'un des routeurs puis saissir cette commande :

#### <span style="color: black"> ** R1 et R2 ** ####

**`enable`**

**`conf t`**

**`interface g0/1`**

**`glbp 1 ip 172.28.3.254`**

**`glbp 1 load-balancing round-robin`**

On peut ensuite verifier si la commande s'est bien appliquée en vérifiant avec la commande:

**`show run`**
