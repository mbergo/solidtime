# Time-tracking project

## Setup the Project

System Requirements:
* Docker
* PHP 8.2
* Composer

```bash
composer install

cp .env.example .env

./vendor/bin/sail up -d

./vendor/bin/sail artisan key:generate

./vendor/bin/sail artisan migrate:fresh --seed

./vendor/bin/sail npm install

./vendor/bin/sail npm run build

```

Make sure to set the APP_PORT and VITE_PORT inside your `.env` file to a port that is not already used by your system.

## Setup with Reverse Proxy

Additional System Requirements:
* Traefik 2 Reverse-Proxy (https://github.com/korridor/reverse-proxy-docker-traefik)

Add the following entry to your `/etc/hosts`

```
127.0.0.1 timetracker.test
127.0.0.1 playwright.timetracker.test
```

## Running E2E Tests

`./vendor/bin/sail up -d ` will automatically start a Playwright UI server that you can access at `https://playwright.timetracker.test`. 
Make sure that you use HTTPS otherwise the resources will not be loaded correctly.

## Recording E2E Tests

To record E2E tests, you need to install and execute playwright locally using: 

```bash
npx playwright install
npx playwright codegen timetracker.test
``` 

## Contributing

This project is in a very early stage. The structure and APIs are still subject to change and not stable. 
Therefore we do not currently accept any contributions, unless you are a member of the team.

As soon as we feel comfortable enough that the application structure is stable enough, we will open up the project for contributions.