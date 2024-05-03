# Hostinger: Hosting laravel API

Hosting laravel full stack app is easy but to deploy apis built in Laravel it required some additional steps mentioned below. Once you purchase the shared hosting from hostinger you can check hosting dashboard for that specific domain. You will get access to ssh credentials please use that to ssh using your terminal. Make sure to enable ssh access, as by default ssh access is disabled. You might also have to reset the ssh password before proceeding.

### Steps:

1. SSH into the specific domain’ shared hosting
2. cd into the domains folder: 

```bash
cd domains
```

1. delete the domain for which you want to create the API eg. [tfusion.in](http://tfusion.in) or api.tfusion whicher domain you want to host your API on, remember that domain should exist under the domains folder 

```bash
rm -rf api.example.com
```

1. Install the composer version 2

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

1. Check PHP composer version

```bash
php composer.phar --version
```

1. Create Laravel project using the below command, replace [api.example.com](http://api.example.com) with the domain you want to host

```bash
php composer.phar create-project laravel/laravel api.example.com
```

1. List all the folders in your current working directory

```bash
ls -la
```

1. You should have a new folder with the domain name you specified: Upload your laravel project code inside the newly created folder: api.example.com, you can git clone or upload it using hostinger’s file manager
2. Move composer.phar to the home directory ~/

```bash
mv composer.phar ~/
```

1. change directory to the [api.example.com](http://api.example.com) : PS. change it to your domain

```bash
cd api.example.com/
```

1. Install packages

```bash
php ~/composer.phar install
```

1. Create .env files and add all the necessary .env file from local folder. to edit and create .env file run:

```bash
nano .env
```

1. Next we generate a key

```bash
php artisan key:generate
```

1. If your app use storage than run this command:

```bash
php artisan storage:link
```

1. Create a public folder which is a must as hostinger looks for it

```bash
ln -s public public_html
```

1. Go back to Hostinger dashboard and under databases create a new user & database and password, remember this as we will be using it in the next step
2. Now we migrate the database, so now back to the terminal and run this command inside your domain name, for me its inside the api.example.com

```bash
php artisan migrate
```

## Thats it! It should be working now!

These instruction are from this youtube channel: 

[https://www.youtube.com/watch?v=dpJDV25tptw&ab_channel=TheCodeholic](https://www.youtube.com/watch?v=dpJDV25tptw&ab_channel=TheCodeholic)
