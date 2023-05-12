# taxPOD Landing Page in Wordpress
## Concept of Site Architecture
- Partially implemented [https://deliciousbrains.com/storing-wordpress-in-git](https://deliciousbrains.com/storing-wordpress-in-git)
- Use composer to install wordpress
- Use wordpress admin panel to install plugins
- Use WPvivid Backup to sync plugins
- Use import and export of .sql in phpmyadmin to sync database
- Plugins must be installed by developer in local machine
- Admin shall not install any plugins in live server

## Setup in Local Machine
1. Clone the project
1. Run
  1. > composer install
1. Setup Localhost
  - Right click Notepad to "Run as administrator"
  - Click File > Open
  - Go to folder C:\Windows\System32\drivers\etc\
  - Select "Show all files"
  - Open file "hosts"
  - Insert following code at the end of the file
    - > 127.0.0.1 localhost taxpod2.wp 
1. Setup XAMPP
  - Right click Notepad to "Run as administrator"
  - Click File > Open
  - Go to folder C:\xampp\apache\conf\extra\
  - Select "Show all files"
  - Open file "httpd-vhosts"
  - Insert following code at the end of the file
    - > \<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/tp-home-web2-wp/wordpress"
    ServerName taxpod2.wp
        \<Directory "C:/xampp/htdocs/tp-home-web2-wp/wordpress">
            AllowOverride All
            Require all granted
        \</Directory>
\</VirtualHost> 
  - Note: You have to restart XAMPP apache to see the changes
1. Setup database
  1. Create database with name "tp-home-db"
1. Setup wordpress
  1. Start XAMPP and visit taxpod2.wp
  1. Setup the wordpress
    1. Select English US
    1. Database Name = tp-home-db
    1. Username = (local database username)
    1. Password = (local database password)
  1. Run the installation
    1. Site Title = taxPOD
    1. Username = taxpod
    1. Password = taxpod88!
    1. Confirm use of weak password
    1. Your Email = dev@taxpod.my
    1. Click Install WordPress
    1. Click Log In
1. Install WPvivid plugin
  1. Login at http://taxpod2.wp/wp-login.php
  1. Go to Plugins > Add New > Upload Plugin > Choose File
  1. Select "wpvivid-backuprestore.0.9.84.zip"
  1. Click "Install Now"
  1. Click "Activate Plugin"
1. Upload backup
  1. Get the latest backup file from project leader
  1. Go to WPvivid Backup > Upload > Select Files
  1. Select all files
  1. Click "Upload"
1. Restore backup
  1. Go to WPvivid Backup > Backups
  1. Click "Restore" on the latest backup file
  1. Click "Restore"
  1. Click "OK"
  1. Wait patiently
  1. Click "OK"
1. Restore database
  1. Get the latest .sql file from project leader
  1. Delete database tp-home-db
  1. Recreate database tp-home-db
  1. Import tp-home-db.sql in setup folder/sql
1. Configure wordpress
  1. Copy content of wp-config-sample.php in setup folder, replace wp-config.php content 
  1. You may update these parameters in wp-config.php if required
    1. WP_HOME
    1. WP_SITEURL
    1. FORCE_SSL_ADMIN
1. Update assets URL in database via Consultio
  1. Login at http://taxpod2.wp/wp-login.php
  1. Go to Consultio > Theme Options
  1. Click "Save Changes"
1. DONE

## Setup in Remote Server (INCOMPLETE)
1. Clone the project
1. Run
  1. > composer install
1. Setup database
  1. > mysql -u root -p
  1. Enter password
  1. > CREATE DATABASE `tp-home-db`;
GRANT ALL PRIVILEGES ON `tp-home-db`.* TO 'taxpod'@'localhost';
FLUSH PRIVILEGES;
exit;
1. Setup web server (apache2 or nginx)
  1. Read any guide online
1. Update Permission
  1. > sudo chown -R azureuser:www-data /var/www/tp-home-web2-wp
1. Setuo wordpress
  1. Visit the website via browser
  1. Continue setup wordpress
1. Edit wordpress/wp-config.php
  1. define( 'WP_HOME', 'https://www.taxpod.my' );
  1. define( 'WP_SITEURL', 'https://www.taxpod.my' );
  1. define('FS_METHOD', 'direct');
1. Install WPvivid plugin
  1. Follow "Setup in Local Machine"
1. Upload backup
  1. Follow "Setup in Local Machine"
1. Install backup
  1. Follow "Setup in Local Machine"
1. Update assets URL in database via Consultio
  1. Follow "Setup in Local Machine"
1. DONE