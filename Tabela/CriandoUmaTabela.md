
# Criando uma Tabela no SQL Server

## Exemplo de Criação de Tabela: `PRODUTOS`

Para criar uma tabela chamada `PRODUTOS`, utilize a seguinte sintaxe:

```sql
CREATE TABLE PRODUTOS(
    Id int IDENTITY(1,1) NOT NULL,
    Nome varchar(255) NOT NULL,
    Cor decimal(12,2),
    Tamanho varchar(5) NOT NULL,
    Genero char(1)
);
```

### Explicação dos Campos:

- **Id int IDENTITY(1,1) NOT NULL**:
  - `Id`: Nome da coluna.
  - `int`: Tipo de dado inteiro.
  - `IDENTITY(1,1)`: Especifica que esta coluna é um identificador único que será incrementado automaticamente, começando do 1 e incrementando de 1 em 1 para cada novo registro.
  - `NOT NULL`: Indica que esta coluna não pode ter valores nulos.

- **Nome varchar(255) NOT NULL**:
  - `Nome`: Nome da coluna.
  - `varchar(255)`: Tipo de dado que armazena cadeias de caracteres de tamanho variável até 255 caracteres.
  - `NOT NULL`: Indica que esta coluna não pode ter valores nulos.

- **Cor decimal(12,2)**:
  - `Cor`: Nome da coluna.
  - `decimal(12,2)`: Tipo de dado que armazena números decimais com até 12 dígitos no total, dos quais 2 são após a vírgula decimal.

- **Tamanho varchar(5) NOT NULL**:
  - `Tamanho`: Nome da coluna.
  - `varchar(5)`: Tipo de dado que armazena cadeias de caracteres de tamanho variável até 5 caracteres.
  - `NOT NULL`: Indica que esta coluna não pode ter valores nulos.

- **Genero char(1)**:
  - `Genero`: Nome da coluna.
  - `char(1)`: Tipo de dado que armazena uma cadeia de caracteres de tamanho fixo de 1 caractere.

### Informações Adicionais:

- **IDENTITY**:
  - Utilizado para colunas que devem ter valores únicos e incrementais, muito comum para chaves primárias.

- **NOT NULL**:
  - As colunas definidas com `NOT NULL` são obrigatórias, ou seja, não podem conter valores nulos. Isso garante que todos os registros terão valores válidos nessas colunas.

Este exemplo cria uma tabela `PRODUTOS` com cinco colunas: `Id`, `Nome`, `Cor`, `Tamanho`, e `Genero`. Cada coluna é definida com seu respectivo tipo de dado e restrições.

Use esta estrutura para criar e gerenciar suas tabelas no SQL Server, garantindo a integridade e a consistência dos dados.
```

