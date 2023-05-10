# taxPOD Landing Page in Wordpress
## Concept of Site Architecture
- Implemented [https://deliciousbrains.com/storing-wordpress-in-git](https://deliciousbrains.com/storing-wordpress-in-git)

## Setup in Local Machine
1. Clone the project
1. Run
  - > composer install
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
1. Setup wpvivid plugin
  1. Login at local machine at taxpod2.wp/wp-admin
1. Download backup
  1. Login live server.
  1. Go to WPvivid Backup.
  1. Download the latest backup file from live server.
1. Upload backup
1. Restore backup
1. Restore database
  1. Delete all tables in database
  1. Import tp-home-db.sql

## Setup in Remote Server (INCOMPLETE)
1. Modify git to not alter line end
  1. > git config core.autocrlf false
  1. > git config core.eol lf
1. > sudo chown -R azureuser:www-data /var/www/tp-home-web1-wp