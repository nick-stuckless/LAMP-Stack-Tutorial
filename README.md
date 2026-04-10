📌 ### Project Overview

This guide demonstrates how to:

- Prepare a fresh Linux server

- Install and configure Apache

- Install PHP and enable it within Apache

- Deploy and secure MariaDB

- Create a sample database and table

- Validate the full LAMP stack end‑to‑end

The process is based on a structured Method of Procedure (MOP) originally created for academic and operational use.

🛠️ Prerequisites

Before starting, ensure you have:

- A Linux server (Ubuntu/Debian recommended)

- Root or sudo access

- Basic familiarity with the terminal

- SSH access (public key authentication recommended)

🚀 Installation Steps

1. Update the Server

```bash```

```sudo su root```

```apt-get update```

```apt-get upgrade```

```reboot```

2. Install PHP

```bash```

```sudo apt install php libapache2-mod-php php-mysql -y```

```php -v```

3. Configure Apache to Prioritize PHP

Edit the directory configuration file:

```bash```

```sudo nano /etc/apache2/mods-enabled/dir.conf```

Move index.php to the front of the list, then restart Apache:

```bash```

```sudo systemctl restart apache2```

4. Test PHP

Create a test file:

```bash```

```sudo nano /var/www/html/test.php```

Insert:

php

<?php
phpinfo();
?>

Visit:

http://<your-server-ip>/test.php

Delete the test file afterward:

```bash```
```sudo rm /var/www/html/test.php```

5. Install MariaDB

```bash```

```sudo apt install mariadb-server mariadb-client -y```

```sudo systemctl start mariadb```

```sudo systemctl enable mariadb```

```mysql --version```

7. Secure the SQL Installation

Run the security script:

bash

```sudo mysql_secure_installation```

Recommended responses:

Set root password: Yes

Remove anonymous users: Yes

Disallow remote root login: No

Remove test database: Yes

Reload privileges: Yes

7. Create a Database

Login:

```bash```

```sudo mysql -u root -p```

Create a database and table:

sql

CREATE DATABASE contacts;
USE contacts;

CREATE TABLE directory (
    PersonID INT NOT NULL,
    FirstName VARCHAR(55),
    LastName VARCHAR(55)
);

INSERT INTO directory (PersonID, FirstName, LastName)
VALUES (1, 'Alice', 'Clampett');

SELECT * FROM directory;
