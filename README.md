# laravel-cheatlist
cheatlist for laravel installation
# Installing laravel and creating new app:
    # cd /var/www/html
    # composer global require laravel/installer - // downloads 
    // laravel installer
    # composer create-project --prefer-dist laravel/laravel 
    appName 
        OR 
    # laravel new appName- // creates new laravel app with name "appName" 
    // with the newest laravel version available. If isues appear change
    // permissions to html folder - "sudo chmod -R 777 html"

# Check if app is corectly installed
    # go to /var/www/html/appName
    # chmod -R 777 storage bootstrap/cache
    # php artisan serve
    # go to localhost:8000 - welcome page should be displayed

# Installing phpmyadmin
    # sudo apt update
    # sudo apt install phpmyadmin php-mbstring php-gettext
    # sudo phpenmod mbstring - // enables PHP mbstring extension to
    // apache server
    # sudo service apache2 restart - // restarts apache server

# Check if phpmyadmin is corectly installed
    # go to localhost/phpmyadmin
    # login with username and password you definded in the installation

# Create new database in mysql server and grant permissions to phpmyadmin
    # sudo mysql -u root -p - // login as root in mysql server
    # create database laravel; - // creates new database called laravel
    # use laravel; - // switch to laravel database
    # GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost'
    WITH GRANT OPTION; -// grants root permisssions on user phpmyadmin
    // to database laravel

# Add created database to laravel app
    # open /var/www/html/appName/.env with text editor
    # add database settings and save
    # if permission denied change permissions with:
      sudo chmod -R 777 /var/www/html/appName

# Add laravel app as site in apache server
    # cd /etc/apache2/sites-available - // goes to apache settings
    # sudo nano laravel.conf - // creates new site conf file with this content
    /*
    
      <VirtualHost *:80>
        ServerName yourdomain.tld

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html/appName/public

        <Directory /var/www/html/appName>
            AllowOverride All
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
      </VirtualHost>
      
    */
    
    # a2ensite laravel.conf - // enables the new conf file
    # a2dissite 000-default.conf - // disables the old conf file
    # sudo a2enmod rewrite - // enables rewrite mode on the server
    # sudo service apache2 restart - // restarts the apache server

# Installing npm packages to laravel app and running npm server
    # go to app root folder
    # npm install - // installs npm packages to the app
    # npm run dev - // build created app
    # npm run watch - // serves laravel app with npm and watches for
    // changes in the files

# Check if site is working 
    # go to localhost - the Welcome page should be opened


