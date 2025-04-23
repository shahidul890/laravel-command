To set up **multiple PHP versions** on one **Ubuntu** system (e.g., for running different applications with different requirements), follow these steps:

---

### ✅ Step-by-step Guide to Install and Switch Between PHP Versions

#### 1. **Add the `ondrej/php` PPA**
This repository provides multiple PHP versions.

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

---

#### 2. **Install Multiple PHP Versions**

For example, to install PHP 7.4, 8.1, and 8.2:

```bash
sudo apt install php7.4 php7.4-cli php7.4-fpm
sudo apt install php8.1 php8.1-cli php8.1-fpm
sudo apt install php8.2 php8.2-cli php8.2-fpm
```

You can also install the necessary extensions like:

```bash
sudo apt install php7.4-mysql php8.1-mysql php8.2-mysql
```

---

#### 3. **Switch Between PHP Versions (CLI)**

Use the `update-alternatives` command:

```bash
sudo update-alternatives --install /usr/bin/php php /usr/bin/php7.4 74
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.1 81
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.2 82
```

To switch:

```bash
sudo update-alternatives --config php
```

Then choose the version you want from the list.

---

#### 4. **Configure PHP-FPM for Web Server (Apache or Nginx)**

##### For **Apache**:
Enable PHP version module:

```bash
sudo a2dismod php8.1
sudo a2enmod php7.4
sudo systemctl restart apache2
```

##### For **Nginx**:
You need to change the PHP socket in your site configuration. Example:

```nginx
location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.1-fpm.sock;
}
```

Then reload Nginx:

```bash
sudo systemctl reload nginx
```

---

#### 5. **Check PHP Version**

```bash
php -v
```

---

Let me know if you're using Apache or Nginx, and I can tailor the setup steps accordingly.
