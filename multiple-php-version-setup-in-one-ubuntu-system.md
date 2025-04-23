Here's a **detailed, beginner-friendly explanation** of how to **install and manage multiple PHP versions** on one **Ubuntu** machine. This is useful if you have different applications that require different versions of PHP.

---

## ✅ Step 1: Add the `ondrej/php` PPA Repository

### What it is:
Ubuntu’s default repositories don't always have all PHP versions. The **`ondrej/php` PPA** is a trusted third-party repository that provides multiple PHP versions.

### How to do it:

Open your terminal and run the following commands one by one:

```bash
sudo apt update
```
> This updates your list of available packages.

```bash
sudo apt install software-properties-common
```
> Installs a helper tool that lets you manage PPAs.

```bash
sudo add-apt-repository ppa:ondrej/php
```
> Adds the `ondrej/php` repository to your system.

```bash
sudo apt update
```
> Refreshes the list again to include packages from the new repository.

---

## ✅ Step 2: Install Multiple PHP Versions

Now, you can install any PHP version like 7.4, 8.1, 8.2, etc.

For example, to install PHP 7.4, 8.1, and 8.2 with basic CLI and FPM support:

```bash
sudo apt install php7.4 php7.4-cli php7.4-fpm
sudo apt install php8.1 php8.1-cli php8.1-fpm
sudo apt install php8.2 php8.2-cli php8.2-fpm
```

> Each command installs:
> - `phpX.X` – the core package
> - `phpX.X-cli` – command-line interface for that version
> - `phpX.X-fpm` – PHP FastCGI Process Manager (used by web servers like Nginx or Apache with mpm_event)

### ✅ Optional: Install Common Extensions

You might need extensions like `mysqli`, `curl`, `mbstring`, etc. Here’s how to install them for each version:

```bash
sudo apt install php7.4-mysql php7.4-curl php7.4-mbstring
sudo apt install php8.1-mysql php8.1-curl php8.1-mbstring
sudo apt install php8.2-mysql php8.2-curl php8.2-mbstring
```

You can customize this based on your application needs.

---

## ✅ Step 3: Switch Between PHP Versions (CLI)

By default, the system can only use **one version of PHP at a time in the terminal**. To switch versions:

### Step 3.1: Register the versions using `update-alternatives`:

```bash
sudo update-alternatives --install /usr/bin/php php /usr/bin/php7.4 74
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.1 81
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.2 82
```

### Step 3.2: Choose the Active CLI Version:

```bash
sudo update-alternatives --config php
```

You'll see a list like this:

```
There are 3 choices for the alternative php (providing /usr/bin/php).

  Selection    Path             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/php8.1   81        auto mode
  1            /usr/bin/php7.4   74        manual mode
  2            /usr/bin/php8.1   81        manual mode
  3            /usr/bin/php8.2   82        manual mode

Press <enter> to keep the current choice[*], or type selection number:
```

Type the number of the version you want to use and press **Enter**.

### Check the active version:

```bash
php -v
```

---

## ✅ Step 4: Set Up PHP for Your Web Server

Depending on whether you're using **Apache** or **Nginx**, setup is a little different.

---

### 🔵 For Apache Users

#### 4.1 Disable the current PHP module:
```bash
sudo a2dismod php8.1
```

#### 4.2 Enable the new one (e.g., PHP 7.4):
```bash
sudo a2enmod php7.4
```

#### 4.3 Restart Apache:
```bash
sudo systemctl restart apache2
```

> Apache will now use the selected PHP version.

---

### 🟢 For Nginx Users

Nginx does **not** use PHP directly. It talks to **PHP-FPM**, so you have to point it to the right PHP-FPM version.

#### 4.1 Find the PHP-FPM socket path:
For example:
```bash
/run/php/php7.4-fpm.sock
/run/php/php8.1-fpm.sock
/run/php/php8.2-fpm.sock
```

#### 4.2 Edit your Nginx site config:
Open your Nginx site config (usually in `/etc/nginx/sites-available/`), and find this section:

```nginx
location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.1-fpm.sock;
}
```

Change the `fastcgi_pass` to the version you want (e.g., `php7.4-fpm.sock`).

#### 4.3 Restart Nginx:
```bash
sudo systemctl reload nginx
```

---

## ✅ Step 5: Confirm Everything

### For CLI:
```bash
php -v
```

### For Web (Create a `phpinfo()` file):
In your web server's root (e.g., `/var/www/html`), create a file called `info.php`:

```php
<?php
phpinfo();
?>
```

Visit `http://your-server-ip/info.php` in your browser and check the PHP version.

---

Would you like me to help you set this up for a specific stack like **Nginx + Laravel** or **Apache + WordPress**?
