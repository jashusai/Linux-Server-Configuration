This project is about Linux-Server-Configuration
#### My Server Details
  Server Ip Address:35.154.136.233
#### site url:
    http://35.154.136.233.xip.io/
#### grader password:
      1
#### to update to latest versions:
      sudo apt-get update
      sudo apt-get dist-upgrade
#### grader key:
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEA79meIUVsys61bU2xBmXXrDKkiTLWYuNhGr8FA672ezx3puvM
BrRraZwdQBk737UBLR5nHY7zLn/UjVoX4rLlrbqRYlUgRSKZVZw9jCK4JFIqNEuG
E55OHM4BeZHbbmoQVEtmaNsZNB6l19h+Lc0vrsbh8l9adqhzjw/vhTL7qW0wrj0L
yQSWnWaJnZDfBnWdFkNq1iFmZlKhp3z0ireLaY3JlMiiW5690SlKKtwSdUk7uhqK
ucncs52HbQV10aXmcjntr4nNR6h9foNTODt9E9mEj2Gd6muBql5JiYrEUb5QbaeM
cGCKaCu/552s8B96NGz3zuNwQ2kURXQBzm0zMwIDAQABAoIBADCBrE9CQRxK7bor
Si/nDNUQcOImW+En5w2HsDXsfoCx2+jwKxT4C/kRz4CVGdzGOHStf2Ek9d1jkNL9
c3Mvhu+5mYlvedVBiA0eSfw7UU5XJ53n4De7fkSpDPdPHjeYT7EchpuSI+i8ggHD
ENGme4w3QJ7J1fvFWYmHSYOAqhC7VjDGsTcQH1epYigofmZ9JmcaqKbZCI49aWTJ
HQl2q/FG2Jt9xd3FRjZS9KaZuX+/eiMqYKMLa+x7AfbPkjxiVTgSS0WkvcnynWmP
hg0xcm0HzPj4uDW+QvuUYy9rYFeWySiHNT0CrxXEa/qhmzWC3s869FEhqKXykwSZ
SRQ7jeECgYEA9/yVEgWjm2VrAvLbNhINUJsGrciYT81Gm+4YkeBjJYLWlTW82qrY
tzF9dp5Hx2ESrEue+yle2sXe0HoaQdX7RVs1XI88fNQm0nFw5oEE0Fudv5+U6hWf
VIbwJacUs89JqDmVbWrbhvegxZ3N8WM013F8Oq7nK08hJIJnQp9aXBsCgYEA95m6
K6OZaWUqWVMB3apc2Nt7emMlM/h2m/OsvhdPYzyc+iZKmsXX6W1kJi/cQj4vVrXm
OLxDAcasFiLn8Bx9q/nI0bdr9W0MKyTtWPZEZUiqhWAuBuBgnebo0FT84yO2qTiV
We2ILeKWdKW4SZIhSnOjS2+GVjDUOLYGkn+axskCgYBPyaa027eeIe1iT30UUo6S
Jq7pbycCVgun09134fhEc2pTK60NtfZwSq4RYi+6CJOXd+U47kCkpxFfhkm4cP6d
fBEZLMTLbP7oqrMmltBTsYZ5xwCEqFxRN/FATBevGryaMZzQTZdAP6AstO80ATVZ
NBxCTU/3cUg6lPJgTyEljQKBgAjB6THN8YkmyN6r7u72LZ6F9NIZW6GA8kEF12BJ
1sb9x9eZLx5WTRK2icpH+xRkuqvodyIelogjjMajqWx2tYM1rIKuaCUgHEQSZEq3
OygR7+YTxsz7dq9fEXD88IzgIH/PvoiVvDFTSFsL2X7QqljFykrKwQefZoIy/fyE
gubxAoGAdIcrWjgGwnSktjnTOgH3T1zjdzuvEZ85YEIbbZv+FeLpn4quoNZdBUKO
GN7v9AHQckA/1+sKDh6tgV6h10dvZSf5rNseKWnR4QX/rci0tlki0Zii7uEl25cZ
k7+tPyi2MIXL7h6N2J8bazEArhLagCEQTn9amlnLemOmzQdWh70=
-----END RSA PRIVATE KEY-----


#### Steps to connect to grader:
#### Creating user grader:
             sudo adduser grader
#### grant all permissions to the new user:
              sudo nano /etc/sudoers
#### add the below line after the root:
               grader  ALL=(ALL:ALL) ALL
#### Creating a new instance for ubuntu:
            log into lightsail.aws.amazon.com with your aws accounts
            There create a new instance along with a static ip for that instance
#### Installing putty:
            We need to generate a private key with the default file in lightsail accounts.
      In virtual machine(putty) change to user grader:
            su - grader
#### Creating a new directory for authorized_key generation:
          mkdir .ssh
#### creating a file in that folder:
            sudo nano .ssh/authorized_keys
#### permissions for the directory:
             chmod 700 .ssh
              chmod 644 .ssh/authorized_keys
#### restart 
            service ssh restart
#### changing the port:
            ssh -i .ssh/id_rsa grader@ipaddress(in editor)
            sudo nano /etc/ssh/sshd_config
            restart the ssh server:
             service ssh restart
#### firewall safety:
      add the port 2200,123 in your instance nertwork settings
#### Login into grader :
              ssh -i .ssh/id_rsa -p 2200 grader@ipaddress
#### disabling root as login:
              sudo nano /etc/ssh/sshd_config
              sudo apt-get update
              sudo apt-get dist-upgrade
#### prohibiting root:
               PermitRootLogin Prohibited Pasword to "no"
#### Deny all incoming requests except for SSH(2200), HTTP and NTP:
              sudo ufw default deny incoming

#### Firewall safety commands:
                sudo ufw default deny incoming
                sudo ufw allow 2200/tcp
                sudo ufw allow 80/tcp
                sudo ufw allow 123/udp
                sudo ufw enable
#### check status
        run "sudo ufw status"
#### Again update if any pakages are pending:
      sudo apt-get update
      sudo apt-get dist-upgrade
#### Installing Apache2:
        sudo apt-get install apache2
        sudo apt-get install python-setuptools libapache2-mod-wsgi
        sudo a2enmod wsgi
#### creating a new directory:
          sudo mkdir FlaskApp
          cd FlaskApp
#### git Installation:
            sudo apt-get install git
#### cloning the app from github:
            sudo git clone https://github.com/name/item_catalog.git
#### changing main file name to __init__.py:
            sudo mv project.py __init__.py
#### Adding json file:
           sudo nano __init__.py
          PROJECT_ROOT = os.path.realpath(os.path.dirname(__file__))
          json_url = os.path.join(PROJECT_ROOT, 'client_secrets.json')
        then save it and exit:
             ctrl+o
             ctrl+x
#### Create a wsgi file:
                sudo nano mv project.py FlaskApp.wsgi
          Add the following code into the wsgi file:
                #!/usr/bin/python
                import sys
                import logging
                logging.basicConfig(stream=sys.stderr)
                sys.path.insert(0,"/var/www/FlaskApp/")
                from FlaskApp import app as application
                application.secret_key = 'Add your secret key'
### creating a cofiguration file:
                sudo nano /etc/apache2/sites-available/FlaskApp.conf
           Add the following code into the .conf file:
                  <VirtualHost *:80>
                  ServerName mywebsite.com
                  ServerAdmin admin@mywebsite.com
                  WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
                  <Directory /var/www/FlaskApp/FlaskApp/>
                    Order allow,deny
                    Allow from all
                  </Directory>
                  Alias /static /var/www/FlaskApp/FlaskApp/static
                  <Directory /var/www/FlaskApp/FlaskApp/static/>
                    Order allow,deny
                    Allow from all
                  </Directory>
                  ErrorLog ${APACHE_LOG_DIR}/error.log
                  LogLevel warn
                  CustomLog ${APACHE_LOG_DIR}/access.log combined
                    </VirtualHost>
#### softwares installed :
                    pip install sqlalchemy
                    pip install flask
                    pip install oauth2client
                    pip install pyscopg2
                    pip install requests
            
#### Install postgresql:
        sudo apt-get install postgresql
#### login to postgres:
         sudo su - postgres
         psql
#### create a new user in postgres:
        CREATE USER catalog WITH PASSWORD 'password';
#### give the user permissions to create a new database:
         ALTER USER item_catalog CREATEDB;
 #### to create a new database with user :
        CREATE DATABASE catalog WITH user catalog;
#### connect to db:
        \c catalog
#### give permissions to public:
        REVOKE ALL ON SCHEMA public FROM public;
#### grant permissions on schema for catalog:
        GRANT ALL ON SCHEMA public TO catalog;
#### deploying an app can be refrenced from digital ocean:
#### changing the authorization details in developers console of your project:
     Javascript origin 
        http://ip.xip.io
     redirect URI
      http://ip.xip.io\login
      http://ip.xip.io\gconnect
      http://ip.xip.io\callback
      xip.io is a free DNS which will be the same as using IP address
#### Last Step:
       sudo service apache2 restart
#### Refrences I Have used:
      https://www.digitalocean.com
      https://stackoverflow.com/
  
