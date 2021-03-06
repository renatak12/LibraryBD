# Dicionário de Dados

## Tabela: Operation

| Nome do campo         | Chave                | Tipo de dado | Descrição do Campo                                                | Tamanho do Campo(bytes) |
|-----------------------|----------------------|--------------|-------------------------------------------------------------------|-------------------------|
| id                    | Primária             | NUMERIC      | Identificador incremental do esquema de trabalho.                 | 4                       |
| day                   | NOT NULL             | NUMERIC      | Número correspondente ao dia da semana, Domingo - 1 : Sábado - 7. | 4                       |
| horary_start          | NOT NULL             | TIME         | Horário de abertura com time zone.                                | 12                      |
| horary_start          | NOT NULL             | TIME         | Horário de fechamento com time zone.                              | 12                      |
| workload              | NOT NULL             | NUMERIC      | Carga horário do funcionário.                                     | 4                       |
| operation_functionary | NOT NULL FOREIGN KEY |              | Referência para um ou vários funcionários.                        |                         |

# Tabela: Sessão

| Nome do campo      | Chave            | Tipo de dado | Descrição do Campo                                 | Tamanho do Campo(bytes) |
|--------------------|------------------|--------------|----------------------------------------------------|-------------------------|
| id                 | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de sessão.    | 4                       |
| name               | NOT NULL         | CHAR[100]    | Nome, pode ser abreviado. Limite de 100 caracteres.| 100                     |
| session_category   | NOT NULL FOREIGN |              | Referência para uma ou mais categorias.            |                         |

# Tabela: Usuário

| Nome do campo | Chave            | Tipo de dado      | Descrição do Campo                                      | Tamanho do Campo(bytes) |
|---------------|------------------|-------------------|---------------------------------------------------------|-------------------------|
| id            | NOT NULL PRIMARY | NUMERIC           | Identificador incremental do esquema de sessão.         | 4                       |
| username      | NOT NULL         | NUMERIC           | Identificador único do livro.                           | 8                       |
| name          | NOT NULL         | CHAR[100]         | Nome, pode ser abreviado. Limite de 100 caracteres.     | 100                     |
| registration  | NOT NULL         | NUMERIC AUTO INC  | Mátricula auto incremental do usuário.                  | 4                       |
| telephone     | NOT NULL         | CHAR[14]          | Telefone com formatação: (XX)XXXXX-XXXX                 | 14                      |
| email         | NOT NULL         | CHAR[256]         | Email seguindo o limite padrão de 256 caracteres.       | 256                     |
| password      | NOT NULL         | CHAR[32]          | Senha alfanumérica de até 32 caracteres.                | 32                      |
| status        | NOT NULL         | NUMERIC           | Status de validade para empréstimo.                     | 4                       |
| user_loan     | NOT NULL FOREIGN |                   | Referência para nenhum ou vários empréstimo realizados. |                         |
| user_adress   | NOT NULL FOREIGN |                   | Referência para um endereço.                            |                         |

## Tabela: Biblioteca

| Nome do campo     | Chave            | Tipo de dado | Descrição do Campo                                    | Tamanho do Campo(bytes) |
|-------------------|------------------|--------------|-------------------------------------------------------|-------------------------|
| library_operation | NOT NULL FOREIGN |              | Referência para um ou mais esquemas de funcionamento. |                         |
| library_user      | NOT NULL FOREIGN |              | Referência para um ou mais usuários.                  |                         |
| library_session   | NOT NULL FOREIGN |              | Referência para uma ou mais sessões.                  |                         |

## Tabela: Funcionário

| Nome do campo         | Chave            | Tipo de dado | Descrição do Campo                                   | Tamanho do Campo(bytes) |
|-----------------------|------------------|--------------|------------------------------------------------------|-------------------------|
| id                    | PRIMARY          | NUMERIC      | Identificador incremental do esquema de funcionário. | 4                       |
| name                  | NOT NULL         | CHAR[100]    | Nome, pode ser abreviado. Limite de 100 caracteres.  | 100                     |
| cpf                   | NOT NULL         | CHAR[14]     | CPF com formatação: XXX.XXX.XXX-XX                   | 14                      |
| telephone             | NOT NULL         | CHAR[14]     | Telefone com formatação: (XX)XXXXX-XXXX              | 14                      |
| email                 | NOT NULL         | CHAR[256]    | Email seguindo o limite padrão de 256 caracteres.    | 256                     |
| salary                | NOT NULL         | DOUBLE       | Salário em reais e centavos.                         | 8                       |
| functionary_operation | NOT NULL FOREIGN |              | Chave para um ou mais esquemas de trabalho.          |                         |
| functionary_adress    | NOT NULL FOREIGN |              | Chave para um endereço.                              |                         |

## Tabela: Endereço

| Nome do campo | Chave            | Tipo de dado | Descrição do Campo                                | Tamanho do Campo(bytes) |
|---------------|------------------|--------------|---------------------------------------------------|-------------------------|
| id            | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de endereço. | 4                       |
| street        | NOT NULL         | CHAR[50]     | Rua limitada a 50 caracteres.                     | 50                      |
| neighborhood  | NOT NULL         | CHAR[50]     | Bairro limitado a 50 caracteres.                  | 50                      |
| zipcode       | NOT NULL         | NUMERIC      | CEP/Zip code, entrada numérica.                   | 4                       |
| city          | NOT NULL         | CHAR[50]     | Nome da Cidade limitada a 50 caracteres.          | 50                      |
| state         | NOT NULL         | CHAR[5]      | Acrônimo do estado até 5 caracteres.              | 5                       |
| country       | NOT NULL         | CHAR[50]     | País limitado até 50 caracteres.                  | 50                      |
| number        | NOT NULL         | NUMERIC      | Número da residência.                             | 4                       |

# Tabela: Categoria

| Nome do campo | Chave            | Tipo de dado | Descrição do Campo                                 | Tamanho do Campo(bytes) |
|---------------|------------------|--------------|----------------------------------------------------|-------------------------|
| id            | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de Categoria. | 4                       |
| name          | NOT NULL         | CHAR[100]    | Nome, pode ser abreviado. Limite de 100 caracteres.| 100                     |
| category_book | NOT NULL FOREIGN |              | Referência para um ou mais livros.                 |                         |

# Tabela: Livro

| Nome do campo  | Chave            | Tipo de dado | Descrição do Campo                              | Tamanho do Campo(bytes) |
|----------------|------------------|--------------|-------------------------------------------------|-------------------------|
| id             | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de sessão. | 4                       |
| isbn           | NOT NULL         | NUMERIC      | Identificador único do livro.                   | 4                       |
| unity          | NOT NULL         | NUMERIC      | Identificador da unidade.                       | 4                       |
| title          | NOT NULL         | CHAR[100]    | Titulo do livro limitado a 100 caracteres.      | 100                     |
| subtitle       | NOT NULL         | CHAR[50]     | Sub-titulo do livro limitado a 50 caracteres.   | 50                      |
| status         | NOT NULL         | NUMERIC      | Status numérico.                                | 4                       |
| book_gender    | NOT NULL FOREIGN |              | Referência para um ou mais gêneros.             |                         |
| book_author    | NOT NULL FOREIGN |              | Referência para um ou mais autores.             |                         |
| book_publisher | NOT NULL FOREIGN |              | Referência para uma editora.                    |                         |

# Tabela: Empréstimo

| Nome do campo | Chave            | Tipo de dado | Descrição do Campo                              | Tamanho do Campo(bytes) |
|---------------|------------------|--------------|-------------------------------------------------|-------------------------|
| id            | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de sessão. | 4                       |
| deadline      | NOT NULL         | NUMERIC      | Identificador único do livro.                   | 8                       |
| expedition    | NOT NULL         | NUMERIC      | Identificador da unidade.                       | 8                       |
| loan_book     | NOT NULL FOREIGN |              | Referência para um livro.                       |                         |
| loan_user     | NOT NULL FOREIGN |              | Referência para um usuário.                     |                         |

# Tabela: Editora

| Nome do campo  | Chave            | Tipo de dado | Descrição do Campo                                 | Tamanho do Campo(bytes) |
|----------------|------------------|--------------|----------------------------------------------------|-------------------------|
| id             | NOT NULL PRIMARY | NUMERIC      | Identificador incremental do esquema de Categoria. | 4                       |
| name           | NOT NULL         | CHAR[100]    | Nome, pode ser abreviado. Limite de 100 caracteres.| 100                     |
| cnpj           | NOT NULL         | CHAR[100]    | Nome, pode ser abreviado. Limite de 100 caracteres.| 100                     |
| telephone      | NOT NULL         | CHAR[14]     | Telefone com formatação: (XX)XXXXX-XXXX            | 14                      |
| email          | NOT NULL         | CHAR[256]    | Email seguindo o limite padrão de 256 caracteres.  | 256                     |
| publisher_book | NOT NULL FOREIGN |              | Referência para um ou mais livros.                 |                         |


### Referências

[Exemplo de Dicionário - IBM](https://publib.boulder.ibm.com/tividd/td/ITMFTP/GC23-4803-00/pt_BR/HTML/TMTPmst80.htm)

