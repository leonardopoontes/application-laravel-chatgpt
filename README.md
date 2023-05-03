
# Laravel ChatGPT

### Aplicação Laravel integrada ao ChatGPT da OpenAI, com Autenticação.

Neste projeto, temos uma aplicação Laravel 10 com PHP 8.1, com sessão de login e acesso à API ChatGPT da OpenAI, além disso, existe uma aplicação de cache para evitar o consumo de consultas realizadas recentemente.

# Iniciar

<h4>Obrigatório:</h4>

-   PHP 8.1+
-   OpenAI conta para API Key

<h4>Instalação:</h4>

-   Clone esse repositório
-   Execute `composer install`
-   Crie o arquivo .env na raiz do projeto
-   Execute o comando `php artisan key:generate` para gerar uma chave de criptografia para o aplicativo.
-   Execute o comando `php artisan migrate` para executar as migrações do banco de dados.
-   Inicie o servidor Apache do XAMPP.
-   Acesse o aplicativo Laravel no navegador digitando http://localhost na barra de endereços.


# Tutorial


<h1>Comos esse projeto foi feito!</h1>

-   Instalar laravel breeze para autenticação

```bash
composer require laravel/breeze --dev
```

-   Instalar Laravel Breeze

```bash
php artisan breeze:install
```

-   Rode todas as migrations, incluindo migrations do breeze

```bash
php artisan migrate
```

-   Instalar npm dependências 

```bash
npm install
```

-   Run npm para testar a aplicação

```bash
npm run dev
```
-   Para adicionar sessão de autenticação no aplicativo

```bash
php artisan breeze:install --dark
```

-   Instale as dependências do Nuno Maduro para suporte no OpenAI, com todos os recursos da API.

```bash
composer require openai-php/client
```

-   Adicionar a key da OpenAI em .env

```bash
echo -e '\nOPEN_AI_KEY="CHANGE_TO_YOUR_KEY..."' >> .env
```

-   Gerar OpenAIController

```bash
sail artisan make:controller OpenAIController
```

-   Execute novamente o NPM para scripts de compilação automática após as alterações

```bash
npm run dev
```

-   Nova rota no arquivo web.php, na autenticação da sessão, adicione a rota:

```php
    Route::get('/openai', [OpenAIController::class, 'index'])->name('openai.index');
```

-   Novo Link para acesso ao menu, no arquivo ./resources/views/layouts/navigation.blade.php:

    ```html
    <div class="hidden space-x-8 sm:-my-px sm:ml-10 sm:flex">
        <x-nav-link
            :href="route('openai.index')"
            :active="request()->routeIs('openai.index')"
        >
            {{ __('OpenAI') }}
        </x-nav-link>
    </div>
    ```

-   Novo arquivo ./app/Http/Controllers/OpenAIController.php

-   Novo arquivo ./resources/views/openai/index.blade.php
