# TechReview Hub - Multi-tenancy Platform

<p align="center">
    <a href="https://laravel.com" target="_blank">
        <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo">
    </a>
    <br>
    <a href="https://tenancyforlaravel.com/docs/v3/tenants/" target="_blank">
        <p>Documentación Oficial Tenancy for Laravel</p>
    </a>
</p>

## Descripción

Plataforma multi-tenancy para la gestión de reseñas tecnológicas. Este proyecto permite a múltiples inquilinos (tenants) gestionar sus propias reseñas de productos tecnológicos de manera independiente.

## Requisitos

-   PHP >= 8.1
-   Composer
-   MySQL 5.7+ o PostgreSQL
-   Node.js & NPM
-   Redis (opcional para caché y colas)

## Instalación

1. Clonar el repositorio:

```bash
git clone [URL_DEL_REPOSITORIO]
cd techreviewtenancy
```

2. Instalar dependencias de PHP:

```bash
composer install
```

3. Instalar dependencias de Node.js:

```bash
npm install
npm run dev
```

4. Configurar el archivo .env:

```bash
cp .env.example .env
php artisan key:generate
```

5. Configurar la base de datos en el archivo `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=techreview_central
DB_USERNAME=root
DB_PASSWORD=
```

6. Ejecutar migraciones centrales:

```bash
php artisan migrate --path=database/migrations/central
```

## Gestión de Tenants

### Usando Tinker (CLI interactivo)

Para crear un nuevo tenant manualmente:

```bash
php artisan tinker
>>> $tenant = App\Models\Tenant::create(['id' => 'dealer']);
>>> $tenant->domains()->create(['domain' => 'prueba.exampleTenancy.test']);
```

#### Comandos útiles:

```bash
php artisan tenants:list
php artisan tenants:migrate
php artisan tenants:seed
php artisan tenants:run route:list
```

## Licencia

Este proyecto está bajo la [licencia MIT](LICENSE).
