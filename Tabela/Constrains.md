# Índice e Resumo sobre Constraints no SQL Server

## Parte 1: Índice

1. [PRIMARY KEY](#primary-key)
    - **Resumo**: Garante a unicidade e não permite valores nulos em uma coluna ou conjunto de colunas.
2. [FOREIGN KEY](#foreign-key)
    - **Resumo**: Mantém a integridade referencial entre duas tabelas.
3. [UNIQUE](#unique)
    - **Resumo**: Garante a unicidade dos valores em uma coluna ou conjunto de colunas, permitindo valores nulos.
4. [CHECK](#check)
    - **Resumo**: Impõe uma condição booleana para os valores em uma coluna.
5. [DEFAULT](#default)
    - **Resumo**: Define um valor padrão para uma coluna quando nenhum valor é especificado.
6. [NOT NULL](#not-null)
    - **Resumo**: Garante que uma coluna não possa conter valores nulos.
7. [Removendo Constraints](#removendo-constraints)
    - **Resumo**: Instruções sobre como remover diferentes tipos de constraints.

## Parte 2: Resumo Completo com Exemplos e Explicação

### PRIMARY KEY

#### Resumo
A constraint `PRIMARY KEY` garante que os valores em uma coluna (ou conjunto de colunas) sejam únicos e não nulos. Cada tabela pode ter apenas uma chave primária.

#### Exemplo:

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    Nome NVARCHAR(50)
);
```

#### Explicação:
- **PRIMARY KEY**: Cria uma chave primária na coluna `ID`, garantindo que todos os valores de `ID` sejam únicos e não nulos.
- **Resultado**: Cada valor de `ID` deve ser distinto e deve estar presente (não nulo).

#### Remoção:

```sql
ALTER TABLE TabelaExemplo
DROP CONSTRAINT PK_TabelaExemplo;
```

### FOREIGN KEY

#### Resumo
A constraint `FOREIGN KEY` mantém a integridade referencial entre duas tabelas, garantindo que o valor em uma coluna ou conjunto de colunas corresponda a um valor em uma coluna chave primária de outra tabela.

#### Exemplo:

```sql
CREATE TABLE TabelaPai (
    ID INT PRIMARY KEY,
    Nome NVARCHAR(50)
);

CREATE TABLE TabelaFilha (
    ID INT PRIMARY KEY,
    TabelaPaiID INT,
    CONSTRAINT FK_TabelaFilha_TabelaPai FOREIGN KEY (TabelaPaiID)
    REFERENCES TabelaPai(ID)
);
```

#### Explicação:
- **FOREIGN KEY**: Cria uma chave estrangeira na coluna `TabelaPaiID` na `TabelaFilha`, referenciando a coluna `ID` na `TabelaPai`.
- **Resultado**: Garante que cada valor de `TabelaPaiID` em `TabelaFilha` corresponda a um valor existente de `ID` em `TabelaPai`.

#### Remoção:

```sql
ALTER TABLE TabelaFilha
DROP CONSTRAINT FK_TabelaFilha_TabelaPai;
```

### UNIQUE

#### Resumo
A constraint `UNIQUE` garante que todos os valores em uma coluna ou conjunto de colunas sejam únicos. Diferente da `PRIMARY KEY`, uma tabela pode ter várias constraints `UNIQUE`.

#### Exemplo:

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    Email NVARCHAR(100) UNIQUE
);
```

#### Explicação:
- **UNIQUE**: Assegura que os valores na coluna `Email` sejam únicos.
- **Resultado**: Nenhum valor duplicado é permitido na coluna `Email`.

#### Remoção:

```sql
ALTER TABLE TabelaExemplo
DROP CONSTRAINT UQ_TabelaExemplo_Email;
```

### CHECK

#### Resumo
A constraint `CHECK` impõe uma condição booleana para os valores em uma coluna ou conjunto de colunas.

#### Exemplo:

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    Idade INT,
    CONSTRAINT CK_Idade CHECK (Idade >= 18)
);
```

#### Explicação:
- **CHECK**: Impõe que os valores na coluna `Idade` devem ser maiores ou iguais a 18.
- **Resultado**: Garante que todos os valores de `Idade` satisfaçam a condição especificada.

#### Remoção:

```sql
ALTER TABLE TabelaExemplo
DROP CONSTRAINT CK_Idade;
```

### DEFAULT

#### Resumo
A constraint `DEFAULT` define um valor padrão para uma coluna quando nenhum valor é especificado durante a inserção.

#### Exemplo:

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    DataCriacao DATE DEFAULT GETDATE()
);
```

#### Explicação:
- **DEFAULT**: Define `GETDATE()` como o valor padrão para a coluna `DataCriacao`.
- **Resultado**: Se nenhum valor for especificado para `DataCriacao` ao inserir uma nova linha, a data atual será usada.

#### Remoção:

```sql
ALTER TABLE TabelaExemplo
DROP CONSTRAINT DF_TabelaExemplo_DataCriacao;
```

### NOT NULL

#### Resumo
A constraint `NOT NULL` garante que uma coluna não possa conter valores nulos.

#### Exemplo:

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    Nome NVARCHAR(50) NOT NULL
);
```

#### Explicação:
- **NOT NULL**: Assegura que a coluna `Nome` não contenha valores nulos.
- **Resultado**: Cada registro deve ter um valor presente na coluna `Nome`.

#### Remoção:

```sql
ALTER TABLE TabelaExemplo
ALTER COLUMN Nome NVARCHAR(50) NULL;
```

### Removendo Constraints

#### Resumo
As constraints podem ser removidas usando o comando `ALTER TABLE... DROP CONSTRAINT`. Cada tipo de constraint deve ser identificada pelo seu nome ao ser removida.

#### Exemplos de Remoção:

1. **PRIMARY KEY**:
    ```sql
    ALTER TABLE TabelaExemplo
    DROP CONSTRAINT PK_TabelaExemplo;
    ```

2. **FOREIGN KEY**:
    ```sql
    ALTER TABLE TabelaFilha
    DROP CONSTRAINT FK_TabelaFilha_TabelaPai;
    ```

3. **UNIQUE**:
    ```sql
    ALTER TABLE TabelaExemplo
    DROP CONSTRAINT UQ_TabelaExemplo_Email;
    ```

4. **CHECK**:
    ```sql
    ALTER TABLE TabelaExemplo
    DROP CONSTRAINT CK_Idade;
    ```

5. **DEFAULT**:
    ```sql
    ALTER TABLE TabelaExemplo
    DROP CONSTRAINT DF_TabelaExemplo_DataCriacao;
    ```

6. **NOT NULL**:
    ```sql
    ALTER TABLE TabelaExemplo
    ALTER COLUMN Nome NVARCHAR(50) NULL;
    ```

## Conclusão

As constraints no SQL Server são ferramentas essenciais para garantir a integridade e consistência dos dados. Elas impõem regras que os dados devem seguir, assegurando a aplicação correta das regras de negócio no banco de dados. Saber como criar, usar e remover essas constraints é fundamental para a gestão eficaz de um banco de dados relacional.S