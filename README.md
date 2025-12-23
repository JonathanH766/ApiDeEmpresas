# 🚀 API de Empresas e Funcionários

API REST desenvolvida para o **gerenciamento de empresas e funcionários**, permitindo operações completas de **cadastro, consulta, atualização e exclusão (CRUD)**.

O projeto foi criado utilizando **C# e .NET 8**, com persistência de dados via **Entity Framework Core**, banco **MySQL** e documentação automática através do **Swagger**, seguindo o padrão de arquitetura **MVC**.

---

## 🛠️ Tecnologias Utilizadas

- 💻 C#
- ⚙️ .NET 8
- 🗄️ Entity Framework Core
- 🐬 MySQL 9.5
- 🐳 Docker
- 📄 Swagger
- 🧑‍💻 Visual Studio Code

---

## ▶️ Como Executar o Projeto

### 1️⃣ Clonar o repositório
```bash
git clone <url-do-repositorio>
cd ApiEmpresas
````

---

### 2️⃣ Configurar o banco de dados

* Certifique-se de que o **MySQL** esteja em execução.
* Crie um banco de dados chamado:

```text
ApiEmpresasDb
```

* Verifique a string de conexão no arquivo `appsettings.json`:

```json
"DefaultConnection": "Server=localhost;Port=3306;Database=ApiEmpresasDb;Uid=root;Pwd=12345678;"
```

> Ajuste usuário, senha ou porta conforme necessário.

---

### 3️⃣ Aplicar as migrations

```bash
dotnet ef database update
```

---

### 4️⃣ Executar a aplicação

```bash
dotnet run
```

---

## 🐳 Execução com Docker (opcional / caso o projeto tenha sido recebido em .zip)

### Passo a passo

1. Descompacte o projeto e abra a pasta no **VS Code**
2. Inicie o **Docker**
3. No Windows Explorer, dentro da pasta do projeto, digite `cmd` na barra de endereço
   (recomendado executar como administrador)
4. Execute o comando:

```bash
docker compose up --build
```

⏳ Aguarde a criação da imagem e a inicialização do container do banco de dados.

5. No **VS Code**, abra o terminal (`Ctrl + "`) e execute:

```bash
dotnet run
```

---

## 📄 Documentação Swagger

Após iniciar a aplicação, acesse:

```text
http://localhost:5193/swagger/index.html
```

---

## ✨ Funcionalidades

* 📁 Cadastro, consulta, atualização e exclusão de **Empresas**
* 👥 Cadastro, consulta, atualização e exclusão de **Funcionários**
* 🔗 Relacionamento entre empresas e funcionários
* 📄 Documentação interativa via Swagger

---

## 🧾 Estrutura das Entidades

### 🏢 Empresa

* ID
* Nome
* Data de Inscrição
* CNPJ
* Faturamento Anual
* Endereço Comercial

### 👤 Funcionário

* ID
* Nome
* Data de Admissão
* CPF
* Salário Anual
* Endereço Residencial

---

## 🧩 Padrão de Projeto

* Arquitetura **MVC (Model-View-Controller)**
* Separação de responsabilidades
* Organização em camadas

---

## 📁 Estrutura do Projeto

```bash
ApiEmpresas
├── Controllers
├── Data
├── Models
├── Migrations
├── appsettings.json
├── Program.cs
└── README.md
```

---

## 📸 Evidências

Foram realizados testes completos das operações de **CRUD** de **Empresas** e **Funcionários**, com registros visuais (prints) demonstrando o correto funcionamento da API.

---

## 📌 Observações Finais

Projeto desenvolvido com **finalidade acadêmica**, aplicando conceitos de:

* Desenvolvimento de APIs REST
* Persistência de dados com Entity Framework Core
* Integração com banco de dados relacional
* Boas práticas em projetos .NET

```
