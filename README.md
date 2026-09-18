# IpsilonLibs

Biblioteca PHP reutilizável para construir aplicações com estrutura de framework, incluindo carregamento de classes, roteamento, modelos, acesso a banco de dados e utilitários HTTP.

## Visão geral

O projeto reúne componentes essenciais para um ecossistema de aplicação PHP, com foco em organização, reutilização e convenções baseadas em namespaces e autoload PSR-4.

Ele inclui módulos para:

- carregamento automático de classes e inicialização do kernel
- rotas e listeners HTTP
- modelos e entidades para abstração de dados
- conexão e consulta com banco de dados
- request/response HTTP
- renderização de views
- anotações para controllers, middlewares e mapeamentos

## Estrutura do projeto

```text
IpsilonLibs/
├── Kernel/
│   ├── Command/
│   ├── Model/
│   ├── Router/
│   ├── ClassLoader.php
│   ├── EnvLoad.php
│   ├── Kernable.php
│   └── Kernel.php
├── Libs/
│   ├── Annotations/
│   ├── DataBase/
│   ├── Engine/
│   ├── Exception/
│   └── Http/
├── composer.json
├── vendor/
└── README.md
```

## Requisitos

- PHP >= 8.0
- Composer

## Instalação

```bash
composer require yurigabriel/myframeworklibs
```

Ou, se estiver trabalhando diretamente no repositório local:

```bash
composer install
```

## Autoload

O projeto utiliza PSR-4 com o namespace `Framework\\`:

```json
{
  "autoload": {
    "psr-4": {
      "Framework\\": ""
    }
  }
}
```

## Exemplos de uso

### Conexão com banco de dados

```php
<?php

use Framework\Libs\DataBase\Conection;

$db = new Conection();

if ($db->connected) {
    $result = $db->run("SELECT * FROM users");
    var_dump($result);
}
```

### Request HTTP

```php
<?php

use Framework\Libs\Http\Request;

$request = new Request();
$value = $request->getInputValue("name");
```

### Renderização de view

```php
<?php

use Framework\Libs\Engine\Render;

Render::render("home");
```

## Modulos principais

### Kernel

Responsável pela carga inicial e execução da base da aplicação. Contém classes para:

- carregamento automático de classes
- organização da aplicação em kernel principal
- execução da infraestrutura principal da aplicação

### Router

Conjunto para definição e processamento de rotas e parâmetros HTTP, incluindo:

- `Route.php`
- `RouteMethod.php`
- `RoutesKernel.php`
- `RequestListener.php`
- `ParamParser.php`

### Model

Estrutura para entidades e modelos com suporte à abstração de tabelas, chaves primárias, colunas e relacionamento entre entidades.

### Libs/Http

Utilitários para manipulação de requisições e respostas HTTP, incluindo:

- `Request.php`
- `Response.php`
- `HTTP_STATUS.php`
- `Interceptable.php`

### Libs/DataBase

Camada de acesso ao banco de dados com classes de conexão e repositórios, além de consultas estruturadas.

### Libs/Annotations

Anotações para marcar controllers, middlewares, mapeamentos e instâncias, ajudando a modelar o comportamento da aplicação sem acoplamento direto.

## Licença

Este projeto não possui licença declarada no repositório no momento, portanto o uso, modificação e distribuição devem seguir as regras da organização do projeto e do responsável pelo repositório.

## Autor

Yuri-Gabriel

## Observações

Este repositório parece ser uma biblioteca/framework base para projetos PHP e ainda pode evoluir com documentação mais detalhada, exemplos de rotas e estrutura de aplicação.

Se quiser, posso também criar uma versão mais completa com:

- documentação de rotas
- exemplos de controllers e modelos
- seção de troubleshooting
- badges e guia de contribuição
