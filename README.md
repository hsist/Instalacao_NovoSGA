# Instalacao_NovoSGA
Tutorial para instalação do sistema NovoSGA

==============================================================
1 - INSTALAR APACHE2

sudo apt update
sudo apt install apache2
sudo a2enmod rewrite env
sudo service apache2 restart
sudo chmod -R 777 /etc/apache2/
sudo systemctl restart apache2

==============================================================
2 - INSTALAR PHP 7.4

sudo apt-add-repository ppa:ondrej/php
sudo apt update
sudo apt install php7.4 php7.4-mysql php7.4-curl php7.4-zip php7.4-intl php7.4-xml php7.4-mbstring 
sudo chmod -R 777 /etc/php/

==============================================================
3 – Instalar MySQL 5.7 e criar banco de dados

sudo apt install mariadb-server
sudo service mysql start
sudo mysql_secure_installation

Acessar o mysql:

sudo mysql -u root -p

CREATE DATABASE novosga_db;
CREATE USER 'novosga_us'@'%' IDENTIFIED BY '123456';
GRANT ALL PRIVILEGES ON novosga_db.* TO 'novosga_us'@'%' IDENTIFIED BY '123456';
FLUSH PRIVILEGES;
exit;

==============================================================
4 – Baixar o Composer

sudo wget https://getcomposer.org/download/1.10.26/composer.phar
sudo chmod +X composer.phar

IMPORTANTE: não execute como root os comandos abaixo

export LANGUAGE=pt_BR
php composer.phar create-project "novosga/novosga:2.0.8" ~/novosga
php composer.phar update -d ~/novosga

Mover diretório

Verificar se a pasta novosga esta na area de trabalho, se não ela esta
na home, pasta pessoal

sudo mv novosga /var/www/html/
sudo chmod -R 777 /var/www/html/novosga/

==============================================================
5 – Preparar o cache da aplicação para o ambiente de produção

cd /var/www/html/novosga
sudo bin/console cache:clear --no-debug --no-warmup --env=prod
sudo bin/console cache:warmup --env=prod

==============================================================
6 – Alterar diretório raiz e habilitar

sudo sed -i 's|AllowOverride None|AllowOverride All|g' /etc/apache2/apache2.conf

Agora altere o arquivo: /etc/apache2/sites-available/000-default.conf

sudo nano /etc/apache2/sites-available/000-default.conf

Insira o seguinte no final do arquivo:

<Directory /var/www/html>
AllowOverride All
</Directory>

==============================================================
7 – Criar e editar o arquivo .htaccess

pode copiar e colar tudo abaixo

echo 'Options -MultiViews
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ index.php [QSA,L]
SetEnv APP_ENV prod
SetEnv LANGUAGE pt_BR
SetEnv DATABASE_URL mysql://novosga_us:123456@localhost:3306/novosga_db
' > /var/www/html/novosga/public/.htaccess

==============================================================
8 – Configurar o timezone

sudo echo 'date.timezone = America/Sao_Paulo' > /etc/php/7.4/apache2/conf.d/datetimezone.ini

reiniciar serviço do Apache2:
sudo service apache2 restart

==============================================================
9 – Comando install do Novo SGA.

sudo chmod -R 777 /var/www/html/novosga/
APP_ENV=prod \
LANGUAGE=pt_BR \
DATABASE_URL="mysql://novosga_us:123456@localhost:3306/novosga_db" \
bin/console novosga:install

**************************************************************
--------------------------------------------------------------
**************************************************************

Instalar Painel WEB

Efetuar o download do Painel WEB
wget https://github.com/novosga/painel-web/releases/download/v2.0.1/painel-web-2.0.1.zip

Descompactar o arquivo
unzip painel-web-2.0.1.zip

Mover a pasta para /var/www/html/painel
mv painel-web-2.0.1 /var/www/html/painel

Feito isso é só acessar o painel
Ex: http://"ipdoservidor"/painel
