# Task Manager - Angular + ASP.NET Core + SQL Server
Projeto simples de cadastro e gerenciamento de tarefas.

## Tecnologias

- Front-end: Angular
- Back-end: ASP.NET Core Web API
- Banco de dados: SQL Server
- ORM: Entity Framework Core
- Comunicação: REST API com JSON

## Estrutura

- `backend/TaskManager.Api`: API ASP.NET Core com CRUD de tarefas
- `frontend/task-manager-ui`: aplicação Angular com listagem, criação, edição e exclusão

## Entidade

A entidade principal é `Tarefa` com os campos:

- `Id` (int, gerado automaticamente)
- `Titulo` (string)
- `Descricao` (string)
- `Status` (string: `Pendente` ou `Concluida`)
- `DataCriacao` (DateTime)

## Funcionalidades implementadas

### Back-end

- GET `/api/tasks`
- GET `/api/tasks/{id}`
- POST `/api/tasks`
- PUT `/api/tasks/{id}`
- DELETE `/api/tasks/{id}`
- Entity Framework Core
- SQL Server
- Migrations prontas para criação do banco
- CORS habilitado para o Angular
- Validações simples

### Front-end

- Listagem de tarefas
- Cadastro de tarefa
- Edição de tarefa
- Exclusão de tarefa
- Filtro por status
- Validação simples de formulário
- Mensagens de sucesso e erro
- Consumo da API com `HttpClient`
- Organização em components e services

## Como executar

### Pré-requisitos

- .NET 8 SDK
- Node.js 20+
- Angular CLI 17+
- SQL Server

### 1. Banco de dados

Crie um banco no SQL Server ou use o nome definido na connection string.

Connection string padrão em `backend/TaskManager.Api/appsettings.json`:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=TaskManagerDb;Trusted_Connection=True;TrustServerCertificate=True;"
}
```

Se necessário, ajuste para sua máquina.

### 2. Rodar o back-end

```bash
cd backend/TaskManager.Api

dotnet restore
dotnet ef database update
dotnet run
```

A API ficará disponível em algo como:

- `https://localhost:7143`
- `http://localhost:5143`

Swagger estará disponível em `/swagger`.

### 3. Rodar o front-end

```bash
cd frontend/task-manager-ui
npm install
ng serve
```

Aplicação Angular:

- `http://localhost:4200`

## Configuração do front-end

A URL base da API está em:

- `frontend/task-manager-ui/src/environments/environment.ts`

Valor padrão:

```ts
apiUrl: 'https://localhost:7143/api'
```

Se a sua API subir em outra porta, ajuste esse valor.

## Endpoints

### Listar tarefas

```http
GET /api/tasks
```

### Buscar por ID

```http
GET /api/tasks/{id}
```

### Criar tarefa

```http
POST /api/tasks
Content-Type: application/json

{
  "titulo": "Estudar Angular",
  "descricao": "Criar a tela de cadastro",
  "status": "Pendente"
}
```

### Atualizar tarefa

```http
PUT /api/tasks/{id}
Content-Type: application/json

{
  "id": 1,
  "titulo": "Estudar Angular",
  "descricao": "Atualizar a tela de edição",
  "status": "Concluida",
  "dataCriacao": "2026-04-29T10:00:00"
}
```

### Excluir tarefa

```http
DELETE /api/tasks/{id}
```

## Observações

- O projeto foi mantido simples, sem autenticação e sem arquitetura avançada.
- O objetivo é demonstrar CRUD, integração entre front-end e back-end e organização básica de código.
- Os nomes dos campos no front foram mantidos próximos do domínio em português para facilitar leitura.

## Sugestão de commits

- `feat(api): create tasks CRUD endpoints`
- `feat(db): add entity framework and sql server configuration`
- `feat(ui): create task list and form screens`
- `feat(ui): add status filter and feedback messages`
- `docs: add setup instructions`
