# Symfony project 

Installation de symfony (latest = 6.*) 

curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash
sudo apt install symfony-cli

##  Start project 👏

git clone git@github.com:clara-lancelle/symfoProject.git

### Changer le DATABASE_URL dans le fichier .env 

exemples : 

- to use mysql
DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name?serverVersion=5.7"

- to use mariadb:
DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name?serverVersion=mariadb-10.5.8"

- to use postgresql:
DATABASE_URL="postgresql://db_user:db_password@127.0.0.1:5432/db_name?serverVersion=11&charset=utf8"


### Création de la base de donnée par doctrine : 

php bin/console doctrine:database:create


## Insertion de notre admin user : 

hasher le futur mot de passe : 

symfony console security:hash-password

Acceder au bash mysql et inserer l’utilisateur dans la table user : 

mysql -uusername -ppassword

USE your_database;

INSERT INTO user (username, roles, password) VALUES('your_admin_name' , '[\"ROLE_ADMIN\"]', 'your_hash_password');

## Then Serve

symfony serve