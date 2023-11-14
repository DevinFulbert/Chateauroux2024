# 10/ DMZ Privé 

## <span style="color: black"> **Serveur HTTP sous Debian 12** ##

###Installation de Apache2###

`sudo apt update` : Mettre à jour les bibliothèques

`sudo apt install apache2` : Installation du service Apache

`sudo systemctl status apache2` : Vérification du service Apache

###Installation de PHP###

`sudo apt install php libapache2-mod-php php-mysql` : Installation de PHP pour Wordpress

`php -v` : Vérification

## <span style="color: black"> **VM MariaDB** ##

###Installation de MariaDB et Création d'une DB Wordpress###

`sudo apt update`

`sudo apt install mariadb-server` : Installation du service

`sudo mysql_secure_installation` : Execution du script de sécurité

###Création d'un utilisateur MariaDB###

`sudo mariadb` : Entrer dans MariaDB

`GRANT ALL ON *.* TO 'wordpress_user'@'%' IDENTIFIED BY 'Passw0rd123456!' WITH GRANT OPTION;` : Création de l'utilisateur

`FLUSH PRIVILEGES;`

`exit`

###Création d'une base de données###

`sudo mysql` : Entrer dans MariaDB

`CREATE DATABASE wordpress_db;` : Création de la base de données

`GRANT ALL ON wordpress_db.* TO 'wordpress_user'@'%' IDENTIFIED BY 'Passw0rd123456!';` : Attribuer les droits à un utilisateur

`FLUSH PRIVILEGES;` : Appliquer les privilèges

###Installation de Wordpress###

`sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/wordpress.conf` : Copier le fichier par défaut de la conf afin de la modifier

`sudo nano /etc/apache2/sites-available/wordpress.conf` : Modification du fichier conf

`ServerName blog.chateauroux.sportludique.fr`

`DocumentRoot /var/www/wordpress`

`sudo a2ensite wordpress.conf` : Rendre actif le site

`wget -O /tmp/wordpress.tar.gz https://wordpress.org/latest.tar.gz` : Télécharger Wordpress

`sudo tar -xzvf /tmp/wordpress.tar.gz -C /var/www` : Etraire Wordpress

`sudo chown -R www-data.www-data /var/www/wordpress` : Donner la propriété au User Apache sur le répertoire

`sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf` : Pour changer la bind address