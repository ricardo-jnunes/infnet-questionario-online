# infnet-questionario-online
## Sistema de Questionário Online com .NET framework.

## Sobre
#### Sistema de Questionários Online para pesquisas públicas em larga escala, desenvolvido com .NET 10.
> Trabalho Acadêmico - Projeto de disciplina Arquitetura de Software .NET do Instituto Infnet (2025).

Nome: Ricardo José Nunes


---

## 1. APRESENTAÇÃO DO PROJETO
Este projeto é um sistema de uestionários online desenvolvido com ASP.NET Core 9, seguindo os princípios do Domain-Driven Design (DDD). Ele oferece uma API RESTful para realizar operações CRUD (Create, Read, Update, Delete) em dados de pesquisa, e geração de relatórios dos resultados das pesquisas.

### Objetivo Principal e Escopo
O objetivo principal deste projeto é demonstrar a aplicação prática de conceitos avançados de arquitetura de software, como DDD, padrões de projeto e Entity Framework Core, no seguinte cenário:  Um sistema de questionários online, que terá como finalidade principal a elaboração de pesquisas públicas. Um dos alvos da startup é pesquisa pública sobre as eleições, onde seriam feitos anúncios em diversas redes sociais convidando as pessoas a responderem a pesquisa. O questionário teria uma estrutura simples de perguntas com resposta no modelo múltipla escolha. Como o alvo das pesquisas são milhões de pessoas, é preciso se preocupar com questões de escala também. Depois do período de coleta de respostas, o sistema deve disponibilizar de forma sumarizada, para alguns usuários, o resultado da pesquisa.

## 2. Como Executar

### Docker (Recomendado)

```bash
# Iniciar todos os serviços
docker compose up -d

# Verificar logs
docker compose logs -f

# Parar serviços
docker compose down
```

### Desenvolvimento Local

```bash
# Restaurar dependências
dotnet restore

# Executar API
dotnet run --project src/OnlineSurvey.Api

# Executar Frontend (em outro terminal)
dotnet run --project src/OnlineSurvey.Web

# Executar testes
dotnet test
```

## Acessos

| Serviço | URL |
|---------|-----|
| Frontend | http://localhost:5000 |
| API | http://localhost:8080 |
| Swagger | http://localhost:8080 |
| PostgreSQL | localhost:5432 |

## API Endpoints

### Surveys

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | `/api/surveys` | Criar pesquisa |
| GET | `/api/surveys` | Listar pesquisas (paginado) |
| GET | `/api/surveys/active` | Listar pesquisas ativas |
| GET | `/api/surveys/{id}` | Obter pesquisa por ID |
| PUT | `/api/surveys/{id}` | Atualizar pesquisa |
| POST | `/api/surveys/{id}/activate` | Ativar pesquisa |
| POST | `/api/surveys/{id}/close` | Encerrar pesquisa |
| DELETE | `/api/surveys/{id}` | Excluir pesquisa |

### Responses

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | `/api/responses` | Enviar resposta |
| GET | `/api/surveys/{id}/results` | Obter resultados |

## Variáveis de Ambiente

| Variável | Descrição | Padrão |
|----------|-----------|--------|
| `POSTGRES_DB` | Nome do banco de dados | `onlinesurvey` |
| `POSTGRES_USER` | Usuário do PostgreSQL | `postgres` |
| `POSTGRES_PASSWORD` | Senha do PostgreSQL | `postgres` |

## Testes

```bash
# Executar todos os testes
dotnet test

# Executar com cobertura
dotnet test --collect:"XPlat Code Coverage"
```

## Documentação

- [Arquitetura do Sistema](docs/arquitetura.md) - Diagramas C4, justificativas técnicas e modelo de dados