# taxPOD Landing Page in Wordpress
## Concept of Site Architecture
- Implemented [https://deliciousbrains.com/storing-wordpress-in-git](https://deliciousbrains.com/storing-wordpress-in-git)

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
    - > <VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/tp-home-web2-wp/wordpress"
    ServerName taxpod2.wp
        <Directory "C:/xampp/htdocs/tp-home-web2-wp/wordpress">
            AllowOverride All
            Require all granted
        </Directory>
</VirtualHost> 
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
1. Download WPvivid Backup
  1. Login live server.
  1. Go to WPvivid Backup.
  1. Download the latest backup file from live server.
  1. (OR) Get the file from project leader.
1. Upload backup
  1. Go to WPvivid Backup > Upload > Select Files
  1. Select all parts of the backup file
  1. Click "Upload"
1. Restore backup
  1. Go to WPvivid Backup > Backups
  1. Click "Restore" on the latest backup file
  1. Click "Restore"
  1. Click "OK"
  1. Wait patiently
  1. Click "OK"
1. Restore database
  1. Delete database tp-home-db
  1. Recreate database tp-home-db
  1. Import tp-home-db.sql
1. Update wp-config.php, add at the end of the file
  1. > define( 'WP_HOME', 'http://taxpod2.wp' );
define( 'WP_SITEURL', 'http://taxpod2.wp' );

## Unresolved Issues
- Will be forcefully redirect to https in admin panel
define('FORCE_SSL_ADMIN', false);
not working yet
- still have some files in backup need to be deleted

## Setup in Remote Server (INCOMPLETE)
1. Modify git to not alter line end
  1. > git config core.autocrlf false
  1. > git config core.eol lf
1. > sudo chown -R azureuser:www-data /var/www/tp-home-web1-wp