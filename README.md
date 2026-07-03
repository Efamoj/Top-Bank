# Top-Bank

Um projeto para prática de Gitlab Flow e CI/CD

## Stack
![Python](https://img.shields.io/badge/-Python-1a2a40?style=for-the-badge&logo=python)
![Docker](https://img.shields.io/badge/-Docker-1a2a40?style=for-the-badge&logo=docker)
![Pydantic](https://img.shields.io/badge/-Pydantic-1a2a40?style=for-the-badge&logo=pydantic)
![Pytest](https://img.shields.io/badge/-Pytest-1a2a40?style=for-the-badge&logo=pytest)
![Ruff](https://img.shields.io/badge/-Ruff-1a2a40?style=for-the-badge&logo=ruff)
![UV](https://img.shields.io/badge/-UV-1a2a40?style=for-the-badge&logo=uv)

## Funcionalidades

- **Cadastrar Conta** - Criação de contas dos tipos: normal, bônus e poupança
- **Consultar Saldo** - Exibição do saldo atual da conta
- **Consultar Dados** - Exibição de dados completos da conta (tipo, saldo, pontuação)
- **Crédito** - Adição de valores à conta (com bonificação para conta bônus)
- **Débito** - Retirada de valores da conta
- **Transferência** - Transferência de valores entre contas (com bonificação para conta bônus destino)
- **Render Juros** - Aplicação de taxa de juros em todas as contas poupança

## Linguagem e Stack de Desenvolvimento

- **Python:**  Linguagem principal do projeto;
- **Docker:** Docker container para padronizar o ambiente de desenvolvimento;
- **UV:** Gerenciador de dependências do projeto;
- **Pydantic:** Para criação de DTOs;
- **Pytest:** Framework para testes unitários;
- **Ruff:** Para formatação e correções de sintaxe no código.

## Estrutura do projeto

````
Top-Bank/
├── .github/workflows/    # Pipelines de CI/CD
├── .devcontainer/        # Configuração para desenvolvimento isolado (VS Code)
├── src/                  # Código fonte principal
│   ├── domain/           # Regras de negócio
│       └── account_types.py
│       └── bank_service.py
│   ├── persistence/      # Comunicação com dados
│       └── account_repo.py
│   ├── presentation/     # Rotas HTTP e Schemas
│       └── balance_router.py
│       └── dependencies.py
│       └── schemas.py
│   └── main.py           # Entrypoint da aplicação
├── tests/                # Testes unitários
│   └── test_bank_service.py
├── Dockerfile            # Receita de containerização da API
├── Makefile              # Orquestrador de comandos úteis do projeto
└── pyproject.toml        # Configurações do projeto e dependências
├── README.md
````


## Pre-Requisitos
- Instale o docker
- Instale o devcontainer no VS Code
- Clone o repositório
```sh
git clone https://github.com/jomasii/Top-Bank.git
```
- Reabra em container

## Run

### Local

```sh
make run
```

API disponível em `http://localhost:8000`

### Docker

```sh
docker pull jomasii/topbank:latest
docker run -p 8080:8080 jomasii/topbank:latest
```
API disponível em `http://localhost:8080`

Imagem no Docker Hub: https://hub.docker.com/repository/docker/jomasii/topbank

## Endpoints

| Método | Rota | Descrição |
|--------|------|-----------|
| `POST` | `/banco/conta/` | Criar conta |
| `GET` | `/banco/conta/{account_id}` | Buscar conta |
| `GET` | `/banco/conta/{account_id}/saldo` | Consultar saldo |
| `PUT` | `/banco/conta/{account_id}/credito` | Realizar crédito |
| `PUT` | `/banco/conta/{account_id}/debito` | Realizar débito |
| `PUT` | `/banco/conta/transferencia` | Transferência entre contas |
| `PUT` | `/banco/conta/rendimento` | Aplicar rendimento |

Documentação interativa: `http://localhost:8080/docs`

## Autor
- **João Marcos:** [jomasii](https://github.com/jomasii)