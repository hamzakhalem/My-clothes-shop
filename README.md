# My Clothes Shop

An online clothing shop set up on [Aimeos](https://aimeos.org/), the e-commerce package for Laravel. Aimeos provides the catalogue, product pages, basket, checkout and admin panel, and Laravel Breeze handles customer accounts.

## Features

- Product catalogue with categories, search and product detail pages
- Basket and checkout
- Customer sign-up, login and profile with Laravel Breeze
- Aimeos admin panel to manage products, categories, stock, orders and customers
- Docker setup with Laravel Sail

## Built with

- PHP 8.1, Laravel 10
- Aimeos (aimeos/aimeos-laravel 2023.10)
- Laravel Breeze, Tailwind CSS, Vite
- MySQL, Laravel Sail (Docker)

## Run it locally

You need PHP 8.1+, Composer, Node.js and MySQL, or Docker for Sail.

```bash
git clone https://github.com/hamzakhalem/My-clothes-shop.git
cd My-clothes-shop
composer install
npm install
npm run build
cp .env.example .env
php artisan key:generate
```

Set `DB_DATABASE`, `DB_USERNAME` and `DB_PASSWORD` in `.env`, then install the shop tables and demo data, and create an admin account:

```bash
php artisan migrate
php artisan aimeos:setup --option=setup/default/demo:1
php artisan aimeos:account --super you@example.com
php artisan serve
```

The shop is at http://127.0.0.1:8000/shop and the admin panel at http://127.0.0.1:8000/admin.

With Docker, run `./vendor/bin/sail up -d` instead of `php artisan serve`, and prefix the artisan commands with `./vendor/bin/sail`.

## Project structure

```
config/shop.php     Aimeos shop configuration
routes/web.php      Shop and admin routes from Aimeos
resources/views/    Breeze account pages and the shop layout
docker-compose.yml  Laravel Sail services
```
