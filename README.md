## Configuração do ambiente

### Pré-requisitos

- Java 21
- PostgreSQL
- Maven 

### Variáveis de ambiente

A aplicação utiliza variáveis de ambiente para configurar a conexão com o banco de dados e selecionar o ambiente de execução.

Crie um arquivo `.env` na raiz do projeto, seguindo o modelo abaixo:

```dotenv
SPRING_PROFILES_ACTIVE=dev

DB_URL=jdbc:postgresql://localhost:5432/navalha
DB_USERNAME=postgres
DB_PASSWORD=sua_senha
```

Substitua os valores pelas credenciais e configurações do seu ambiente local.

**Importante:** o arquivo `.env` contém informações sensíveis e não deve ser versionado. Utilize o arquivo `.env.example` como referência para documentar as variáveis necessárias.

### Profiles

A aplicação possui dois profiles do Spring Boot:

| Profile | Descrição |
|---|---|
| `dev` | Ambiente de desenvolvimento, com logs SQL habilitados e atualização automática do esquema do banco. |
| `prod` | Ambiente de produção, com logs SQL desabilitados e validação do esquema do banco. |

As configurações específicas de cada ambiente estão nos arquivos:

- `application-dev.properties`
- `application-prod.properties`

As configurações gerais estão em `application.properties`.

O profile ativo é definido pela variável `SPRING_PROFILES_ACTIVE`, utilizando `dev` como valor padrão.

### Executando localmente

Após configurar as variáveis de ambiente e criar o banco de dados no PostgreSQL, execute a aplicação com:

```dotenv
SPRING_PROFILES_ACTIVE=prod
DB_URL=jdbc:postgresql://host:5432/navalha
DB_USERNAME=usuario
DB_PASSWORD=senha
```

```bash
./mvnw spring-boot:run
```
