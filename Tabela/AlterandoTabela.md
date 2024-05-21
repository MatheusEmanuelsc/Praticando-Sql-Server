# Alteração de Colunas no SQL Server

Modificar colunas em uma tabela no SQL Server é uma tarefa comum na administração de bancos de dados, seja para ajustar o tipo de dados, mudar o nome da coluna, definir novos valores padrão ou outras necessidades. Este guia fornece um resumo abrangente sobre como realizar essas alterações.

## Alterando o Tipo de Dados de uma Coluna

Para alterar o tipo de dados de uma coluna existente, utiliza-se o comando `ALTER TABLE... ALTER COLUMN`. É importante considerar que essa operação pode falhar se os dados existentes não forem compatíveis com o novo tipo de dados.

### Exemplo:

```sql
ALTER TABLE nome_da_tabela
ALTER COLUMN nome_da_coluna NOVO_TIPO_DE_DADO;
```

**Nota:** Certifique-se de que o novo tipo de dado é compatível com os dados atuais na coluna.

## Alterando o Nome de uma Coluna

Para renomear uma coluna, utiliza-se o comando `sp_rename`. Este comando permite mudar o nome de uma coluna existente em uma tabela.

### Exemplo:

```sql
EXEC sp_rename 'nome_da_tabela.nome_da_coluna_antiga', 'nome_da_coluna_nova', 'COLUMN';
```

## Alterando o Valor Padrão de uma Coluna

Para alterar o valor padrão de uma coluna, primeiro é necessário remover o `DEFAULT` constraint existente e depois adicionar um novo.

### Passos:

1. Identifique o nome do `DEFAULT` constraint:
    ```sql
    SELECT name
    FROM sys.default_constraints
    WHERE parent_object_id = OBJECT_ID('nome_da_tabela')
      AND parent_column_id = (
          SELECT column_id
          FROM sys.columns
          WHERE name = 'nome_da_coluna'
            AND object_id = OBJECT_ID('nome_da_tabela')
      );
    ```

2. Remova o `DEFAULT` constraint:
    ```sql
    ALTER TABLE nome_da_tabela
    DROP CONSTRAINT nome_do_constraint;
    ```

3. Adicione um novo `DEFAULT` constraint:
    ```sql
    ALTER TABLE nome_da_tabela
    ADD CONSTRAINT nome_do_novo_constraint
    DEFAULT valor_padrao_para_a_coluna FOR nome_da_coluna;
    ```

## Adicionando e Removendo Constraints

### Adicionando Constraints

Para adicionar uma constraint como `CHECK` ou `UNIQUE` a uma coluna, utiliza-se o comando `ALTER TABLE... ADD CONSTRAINT`.

#### Exemplo de `CHECK` Constraint:

```sql
ALTER TABLE nome_da_tabela
ADD CONSTRAINT nome_da_constraint
CHECK (nome_da_coluna > 0);
```

#### Exemplo de `UNIQUE` Constraint:

```sql
ALTER TABLE nome_da_tabela
ADD CONSTRAINT nome_da_constraint
UNIQUE (nome_da_coluna);
```

### Removendo Constraints

Para remover uma constraint, utiliza-se o comando `ALTER TABLE... DROP CONSTRAINT`.

#### Exemplo:

```sql
ALTER TABLE nome_da_tabela
DROP CONSTRAINT nome_da_constraint;
```

## Adicionando e Removendo Colunas

### Adicionando Colunas

Para adicionar uma nova coluna a uma tabela, utiliza-se o comando `ALTER TABLE... ADD`.

#### Exemplo:

```sql
ALTER TABLE nome_da_tabela
ADD nova_coluna TIPO_DE_DADO;
```

### Removendo Colunas

Para remover uma coluna de uma tabela, utiliza-se o comando `ALTER TABLE... DROP COLUMN`.

#### Exemplo:

```sql
ALTER TABLE nome_da_tabela
DROP COLUMN nome_da_coluna;
```

**Nota:** A remoção de colunas pode resultar em perda de dados, portanto, execute esse comando com cuidado.

## Considerações de Performance

- **Bloqueios:** Alterações em colunas podem causar bloqueios significativos, especialmente em tabelas grandes.
- **Rebuild de Índices:** Algumas alterações podem requerer a reconstrução de índices, o que pode ser um processo demorado.
- **Backup:** Realize backups antes de realizar alterações significativas em tabelas para prevenir perda de dados em caso de erros.

