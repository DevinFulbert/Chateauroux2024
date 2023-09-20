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
