---
title: "How to migrate a website from a shared web hosting to a VPS"
excerpt: "Discover how to migrate your website from a shared hosting to an OVHcloud VPS"
updated: 2025-10-20
---

## Objective

Your website is evolving, and its resource consumption has become such that your web hosting no longer meets your performance needs or capacity to handle increasingly complex tasks. Migrating to a VPS improves the speed and responsiveness of your website, increases available computing resources (CPU, RAM, etc.), and provides greater control over the server environment. This guide focuses on the essential steps to migrate effectively to a VPS while ensuring service continuity.

**Discover how to migrate your website from a shared hosting to a VPS.**

## Requirements

- Have an active [web hosting offer](/links/web/hosting).
- Have subscribed to a [VPS](/links/bare-metal/vps) in your OVHcloud account.
- Be logged into your [OVHcloud Control Panel](/links/manager).

## Instructions

> [!warning]
>
> OVHcloud provides services whose configuration, management, and responsibility lie with you. It is therefore your responsibility to ensure their proper functioning.
> 
> We provide this guide to assist you with common tasks. However, we recommend contacting a [specialized service provider](/links/partner) if you encounter difficulties. Indeed, we will not be able to provide assistance. More information is available in the [" Go further "](#go-further) section of this guide.
>

### Step 1 - Backup your website files and database <a name="step1"></a>

The first step is to back up all your website files, typically via the **F**ile **T**ransfer **P**rotocol (**FTP**), as well as its database.

If you use WordPress, follow our guide " [Backup your WordPress site](/pages/web_cloud/web_hosting/how_to_backup_your_wordpress) " to learn how to back up the files and database of your WordPress website, then proceed to [step 2](#step2).

#### Step 1.1 - Connect to your web hosting's FTP storage

Follow the steps in our guide "[Connect to your web hosting's FTP storage](/pages/web_cloud/web_hosting/ftp_connection)" to connect to your web hosting's FTP storage.

#### Step 1.2 - Backup files via FTP <a name="step1.2"></a>

If you do not use a CMS (WordPress, Joomla!, Drupal, PrestaShop, etc.), download a complete backup of all files in your FTP space to your local device. This includes all HTML, CSS, JavaScript, image, and configuration files (`config.php`, `.env`, etc.) that make up your website. Ensure you retrieve all folders and files from the root directory (often named `public_html` or `www`) to save all content necessary for your website's operation.

If you use a CMS and need to back up its files, choose the appropriate backup method for your CMS by clicking on the relevant tab.

> [!tabs]
> PrestaShop
>>
>> For PrestaShop, back up the critical directories such as:
>> 
>> - `/admin` : for back-office files.
>> - `/modules` : for installed modules.
>> - `/img` : for all images and icons.
>> - `/themes` : for your site's theme files.
>>
>> For more details on PrestaShop's file structure, consult their [official technical documentation](https://docs.prestashop-project.org/welcome).
>>
> Joomla!
>>
>> For Joomla!, the important files to back up include the directories:
>>
>> - `/administrator` : for the administration interface.
>> - `/components`, `/plugins` : for installed extensions.
>> - `/images` : for your site's media files.
>>
>> Find more information on Joomla! file structure in the [official Joomla! documentation](https://docs.joomla.org/).
>>
> Drupal
>>
>> For Drupal, the important directories to back up are:
>>
>> - `/sites` : containing site-specific files.
>> - `/modules` : and `/themes` : for custom modules and themes.
>>
>> For more information, refer to the [official Drupal documentation](https://www.drupal.org/docs).

> [!primary]
>
> Once all your website files are downloaded, ensure they are stored in a clearly identifiable local folder to facilitate their transfer to the VPS later.

#### Step 1.3 - Backup the database

> [!primary]
>
> If you already use a Web Cloud Database for your website, you can continue using it without migrating it. Your VPS will connect to the Web Cloud Database to manage the data.

If you plan to migrate the database to the VPS, follow the steps in our guide "[Retrieve the backup of a web hosting's database](/pages/web_cloud/web_hosting/sql_database_export)" to back up your database.

### Step 2 - Configure your VPS <a name="step2"></a>

> [!primary]
>
> If you do not yet have a VPS, consult the [OVHcloud VPS product page](/links/bare-metal/vps) to purchase one. Ensure you choose a VPS that meets your website's resource requirements (RAM, CPU, storage, etc.) and the technical specifications of your CMS. If you are unfamiliar with VPS, consult our guide "[Getting started with a VPS](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps)".

#### Step 2.1 - Connect to your VPS

Refer to the "Connect to your VPS" section of our guide "[Getting started with a VPS](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps)" to connect to your VPS.

#### Step 2.2 - Install and configure a web server on your VPS <a name="step2.2"></a>

Once connected to your VPS, install and configure a web development environment on your VPS. This step is essential to ensure your server is ready to host your website once the files and database are transferred.

To install this web environment, consult our guide "[Install a web development environment on a VPS or dedicated server](/pages/bare_metal_cloud/virtual_private_servers/install_env_web_dev_on_vps)".

### Step 3 - Transfer your website files via SFTP

Using the **S**ecure **F**ile **T**ransfer **P**rotocol (**SFTP**) is the recommended method for transferring your website files to your VPS. It offers a higher level of security than FTP by utilizing encryption provided by the SSH service, which is already enabled by default on your OVHcloud VPS.

#### Step 3.1 - Connect to your VPS via SFTP

Follow our [guide on using FileZilla](/pages/bare_metal_cloud/dedicated_servers/comment-deposer-ou-recuperer-des-donnees-sur-un-serveur-dedie-via-sftp) and enter the following details:

- **Host** : use your VPS's IP address.
- **Username** and **Password** : your SSH user account credentials on the VPS.
- **Port** : use port 22 (default port for SFTP).

#### Step 3.2 - Transfer your website files to the VPS

Once connected to your VPS, the local file tree appears on the left side of the FileZilla interface, and your VPS's file tree on the right.

The web directory (or web root) is where your website files will be stored to be accessible on the internet. **By default, it may be a folder named `/var/www/html` or another directory configured during your web server installation in [step 2.2](#step2.2)**. Ensure your files are placed in the directory configured as the **web root** to ensure your site functions correctly.

> [!warning]
>
> If you are connected via SFTP with a non-root user (e.g., `debian`), you will not have permission to write directly into `/var/www/html`.

**Simple procedure: drop into `/home` then move with `sudo`**

##### In FileZilla (SFTP)

- On the "Remote Site" side (right panel), go to: `/home/debian/`
- Drag and drop your database file (e.g., `backup.sql`) into `/home/debian/`. **Do not place this backup in the folder you will copy to the web root** (e.g., `/home/debian/site/`) **or in the web root** (e.g., `/var/www/html`), as it could be publicly downloadable.
- Create a `site` folder in `/home/debian/` (right-click → `Create a directory`{.action}), then open it.
- Select all your website files (the database file should no longer be there) and drag and drop them into `/home/debian/site/`. **Do not drop your SQL dumps into this folder**. Keep them outside the web root, (e.g., `/home/debian/backup.sql`).

##### On your VPS

Connect to the VPS via SSH by referring to the "Connect to your VPS" section of our guide "[Getting started with a VPS](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps)".

Run the following commands:

> [!warning]
>
> In this example, the web root is `/var/www/html`. If your web root is different (configured in step 2.2), replace `/var/www/html` with your actual path.

Create the web root if it does not exist:

```bash
sudo mkdir -p /var/www/html
```

Copy the contents of `/home/debian/site/` to the web root while preserving the directory structure and metadata:

```bash
sudo rsync -a /home/debian/site/ /var/www/html/
```

Alternative if `rsync` is not installed:

```bash
sudo cp -a /home/debian/site/. /var/www/html/
```

Assign ownership of the files to the web service (`www-data` for Nginx/Apache on Debian/Ubuntu):

```bash
sudo chown -R www-data:www-data /var/www/html
```

Set directory permissions to `755` (navigable) and file permissions to `644` (readable):

```bash
sudo find /var/www/html -type d -exec chmod 755 {} \;
sudo find /var/www/html -type f -exec chmod 644 {} \;
```

### Step 4 - Import the database onto your VPS (optional)

> [!warning]
>
> If your database is already hosted on a Web Cloud Databases service, it is not necessary to migrate it to the VPS. You can keep the database on the Web Cloud Databases service and configure your VPS to connect to this database ([step 5](#step5)).

#### Before you begin

- Your backup file (`.sql`) was placed in step 3.2 (e.g., `/home/debian/backup.sql`).
- The **S**ystem **G**estion de **B**ase de **D**onnées (**SGBD**) (MySQL / MariaDB) and its command-line client were installed in step 2.2, along with the database `db_name`. If not, create the database (and user if needed) by following the guide "[Install a web development environment on a VPS or dedicated server](/pages/bare_metal_cloud/virtual_private_servers/install_env_web_dev_on_vps)".

#### Before you begin

- Your backup file (`.sql`) was placed in step 3.2 (e.g., `/home/debian/backup.sql`).
- The **S**ystem **G**estion de **B**ase de **D**onnées (**SGBD**) (MySQL / MariaDB) and its command-line client were installed in [step 2.2](#step2.2).
- The database **`db_name`** :
    - **already exists** if you created it during step 2.2 (or via your admin panel).
    - **can be created automatically** if your backup `.sql` contains `CREATE DATABASE`.
    - **otherwise, create it before importing** :

    ```bash
    sudo mysql -e "CREATE DATABASE db_name CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
    ```

    (replace `db_name` with your desired name).

#### Import the database

1. Connect to the VPS via SSH by referring to the "Connect to your VPS" section of our guide "[Getting started with a VPS](/pages/bare_metal_cloud/virtual_private_servers/starting_with_a_vps)".
2. Launch the import using the SGBD client:

    In the example below, we use MySQL as the SGBD. Use the official documentation of the SGBD you installed during [step 2.2](#step2.2) to use the appropriate command for importing the database onto your VPS.

    ```bash
    mysql -u user_name -p db_name < /home/debian/backup.sql
    ```

    - Replace `user_name` with your MySQL (MySQL/MariaDB) username, not your SSH login.
    - Replace `db_name` with the name of the database to import.

3. Enter the SGBD user password when prompted and wait for the import to complete.

### Step 5 - Configure your website's configuration files <a name="step5"></a>

After transferring your website files and, if applicable, importing the database onto your VPS, it is important to update your website's configuration files to ensure proper functionality. The main variables to adjust are often the database connection information and directory paths. Here are the specific configurations to update for the main CMS platforms.

> [!tabs]
> WordPress
>>
>> Modify the following variables in the `wp-config.php` file :
>> 
>> - **DB_NAME** : the database name.
>> - **DB_USER** : the database user.
>> - **DB_PASSWORD** : the user's password.
>> - **DB_HOST** : the database host (usually localhost on a VPS).
>>
>> For more details, consult the [official WordPress documentation](https://fr.wordpress.org/support/article/editing-wp-config-php/).
>>
>> To avoid any security issues, consult the official documentation on [file permissions for WordPress](https://wordpress.org/support/article/changing-file-permissions/)
>>
> PrestaShop
>>
>> Modify the following variables in the `parameters.php` file :
>> 
>> - **database_host** : the database host.
>> - **database_name** : the database name.
>> - **database_user** : the database user.
>> - **database_password** : the database password.
>>
>> For more details, consult the [official PrestaShop documentation](https://devdocs.prestashop-project.org/8/development/configuration/configuring-prestashop/).
>>
>> To avoid any security issues, consult the [official documentation](https://devdocs.prestashop-project.org/) on file permissions for PrestaShop.
>>
> Joomla!
>>
>> Modify the following variables in the `configuration.php` file :
>> 
>> - **public $host** : the database host (often localhost).
>> - **public $db** : the database name.
>> - **public $user** : the database user.
>> - **public $password** : the database password.
>>
>> For more details, consult the [official Joomla! documentation](https://docs.joomla.org/).
>>
>> To avoid any security issues, consult the official documentation on [file permissions for Joomla!](https://docs.joomla.org/What_are_the_recommended_file_and_directory_permissions%3F)
>>
> Drupal
>>
>> Modify the following variables in the `settings.php` file :
>> 
>> - **host** : the database host (often localhost).
>> - **database** : the database name.
>> - **username** : the database user.
>> - **password** : the database password.
>>
>> For more details, consult the [official Drupal documentation](https://www.drupal.org/documentation).
>>
>> To avoid any security issues, consult the official documentation on [file permissions for Drupal](https://www.drupal.org/docs/administering-a-drupal-site/security-in-drupal/securing-file-permissions-and-ownership)
>>
> No CMS
>>
>> **1. Update the database connection information** 
>>
>> Identify the configuration files (e.g., `config.php` or `.env`). Some may be located in subdirectories. In these files, search for database connection parameters and modify them according to the new VPS connection values:
>>
>> - **DB_HOST** : database server address.
>> - **DB_NAME** : database name.
>> - **DB_USER** : database user.
>> - **DB_PASSWORD** : password.
>>
>> **2. Configure file access paths** 
>>
>> Some websites use absolute paths (e.g., `/home/user/public_html/`) for specific files or resources such as images, CSS files, etc. Ensure these paths are correctly adapted to the server structure on the VPS, e.g., `/var/www/html/`.
>>
>> To avoid file loading errors or broken links, ensure these paths are adjusted in all configuration files, `.htaccess`, or other scripts containing links to these resources. This ensures the website correctly finds all necessary elements for proper operation, even after migration.
>>
>> **3. Modify the .htaccess file**  (optional)
>>
>> Ensure the `.htaccess` file is properly configured for the new environment. If you use rewrite rules (`RewriteRule`) to customize URLs, verify that the paths are adapted to your VPS structure (e.g., `/var/www/html/` instead of `/public_html/`). This ensures the correct functioning of redirects and access.
>>
>> If the `.htaccess` file includes access restrictions or security settings, such as disabling directory listing or configuring caching, modify these settings to match the security configurations and conditions of your new server.
>>
>> **4. Configure file and directory permissions** 
>>
>> Ensure the permissions (e.g., `chmod`) of files and directories are correctly set to avoid access errors. On a VPS, recommended permissions are often `755` for directories and `644` for files, but this may vary depending on your security needs.

If you use a Web Cloud Databases, verify that your VPS is allowed to connect to it. To do this, add the VPS's IP address to the list of authorized IP addresses. This configuration secures access to the database and prevents connection issues. Refer to the "Allow an IP address" section of our guide "[Getting started with the Web Cloud Databases service](/pages/web_cloud/web_cloud_databases/starting_with_clouddb)".

### Step 6 - Associate your domain name with the VPS's IP address

> [!primary]
>
> Before modifying your DNS zone records to point to the VPS's IP address, it is recommended to reduce the **T**ime **T**o **L**ive (**TTL**). This accelerates the propagation of changes, as DNS servers will update information more quickly. Follow the "Propagation time" step of our guide "[Edit an OVHcloud DNS zone](/pages/web_cloud/domains/dns_zone_edit)" to adjust the TTL and configure the records to point the domain name to the VPS.

To direct your website's domain name to your VPS, configure the domain's DNS records to route traffic to your VPS's public IP address. Follow our guide "[Edit an OVHcloud DNS zone](/pages/web_cloud/domains/dns_zone_edit)" for instructions.

### Step 7 - Verify your website's proper functioning

Once the migration is complete, test your website to ensure it works as expected. Check all essential features (forms, user logins, online payments, etc.) and ensure all pages display correctly.

### Step 8 - Secure your VPS

After migrating your website to your VPS, it is crucial to secure your server to protect your data and ensure the smooth operation of your services. Here are some measures to enhance your VPS's security:

- Change the SSH password and default SSH access port provided by OVHcloud.
- Configure a firewall.
- Set up two-factor authentication (2FA).
- Monitor logs.
- Etc.

For a complete list of security best practices, consult our guide "[Secure a VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps)".

## Go further <a name="go-further"></a>

For specialized services (SEO, development, etc.), contact [OVHcloud partners](/links/partner).

Join our [community of users](/links/community).