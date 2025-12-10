ApiEmpresas

API REST para cadastro e gestão de empresas e funcionários, construída com C# e .NET 8. Fornece endpoints para CRUD, validação básica e documentação automática via Swagger.

Tecnologias

C# (.NET 8)

Entity Framework Core

MySQL

Swagger / OpenAPI

VS Code

Docker & Docker Compose (opcional)

Funcionalidades principais

Cadastro, leitura, atualização e exclusão (CRUD) de empresas.

CRUD de funcionários vinculados a empresas.

Relacionamentos (ex.: funcionários pertencem a empresas).

Documentação interativa via Swagger.

Migrations automáticas com EF Core.

Requisitos

.NET 8 SDK instalado

MySQL (local ou container)

Git

Docker & Docker Compose (opcional, recomendado para facilitar)

Estrutura de arquivos (exemplo)
/ApiEmpresas
 ├─ Controllers/
 ├─ Data/
 ├─ Models/
 ├─ Migrations/
 ├─ appsettings.json
 ├─ Program.cs
 └─ README.md

Variáveis de configuração (appsettings.json)

Exemplo mínimo — não comite senhas em repositórios públicos:

{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Port=3306;Database=ApiEmpresasDb;Uid=root;Pwd=12345678;"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  },
  "AllowedHosts": "*"
}


Dica: prefira usar variáveis de ambiente em produção (ex.: DOTNET_ config ou Docker secrets).

Como executar (modo rápido — local)

Clone o repositório:

git clone <url-do-repositorio>
cd ApiEmpresas


Ajuste a string de conexão em appsettings.json ou use variável de ambiente.

Aplique as migrations (cria o esquema no MySQL):

dotnet ef database update


Execute a aplicação:

dotnet run


Abra a documentação Swagger:

http://localhost:5000/swagger/index.html


(A porta pode variar — ver saída do dotnet run.)

Executando com Docker (recomendado se você recebeu um .zip)
Exemplo de docker-compose.yml (MySQL + app)
version: '3.8'
services:
  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: 12345678
      MYSQL_DATABASE: ApiEmpresasDb
    ports:
      - "3306:3306"
    volumes:
      - db_data:/var/lib/mysql

  api:
    build: .
    depends_on:
      - db
    environment:
      - ConnectionStrings__DefaultConnection=Server=db;Port=3306;Database=ApiEmpresasDb;Uid=root;Pwd=12345678;
    ports:
      - "5193:80" # exemplo: mapeia para 5193
    command: ["dotnet", "ApiEmpresas.dll"]

volumes:
  db_data:

Passo a passo (se recebeu .zip)

Descompacte e abra a pasta no VSCode.

Abra um terminal (ou CMD) na pasta do projeto.

Suba containers:

docker compose up --build


Após o banco ficar pronto, execute a API (se necessário dentro do container ou localmente):

dotnet run


Acesse Swagger:

http://localhost:5193/swagger/index.html

Migrations e problemas comuns

Gerar migration:

dotnet ef migrations add InitialCreate


Aplicar:

dotnet ef database update


Se ocorrer erro de conexão, verifique:

Usuário e senha do MySQL

Host/porta (no Docker o host do container do API deve ser db como no docker-compose)

Se o MySQL está aceitando conexões (time to start)

Endpoints (resumo)

Consulte a documentação Swagger para exemplos e modelos de request/response.

GET /api/empresas — listar empresas

GET /api/empresas/{id} — obter empresa por id

POST /api/empresas — criar empresa

PUT /api/empresas/{id} — atualizar empresa

DELETE /api/empresas/{id} — excluir empresa

GET /api/funcionarios — listar funcionários

GET /api/funcionarios/{id} — obter funcionário por id

POST /api/funcionarios — criar funcionário (associar a empresa)

PUT /api/funcionarios/{id} — atualizar funcionário

DELETE /api/funcionarios/{id} — excluir funcionário

Testes (opcional)

Adicione testes unitários com xUnit / NUnit e testes de integração apontando para um banco em memória ou container MySQL.

Boas práticas e sugestões

Não commit appsettings.json com credenciais reais.

Use variáveis de ambiente para conexão e segredos.

Habilite dotnet user-secrets em desenvolvimento para credenciais temporárias.

Considere Health Checks e middleware de tratamento de exceções.

Versione a API (ex.: api/v1/empresas) se planeja evoluir breaking changes.

Contribuição

Sinta-se à vontade para abrir issues e pull requests. Para mudanças grandes, abra uma issue primeiro explicando a motivação.