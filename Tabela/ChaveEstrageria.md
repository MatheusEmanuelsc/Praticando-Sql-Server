# Chaves Estrangeiras (Foreign Keys) no SQL Server

Uma chave estrangeira (foreign key) no SQL Server é uma constraint usada para vincular duas tabelas. Ela estabelece um relacionamento entre uma coluna ou conjunto de colunas em uma tabela (a tabela filha) e uma chave primária ou única em outra tabela (a tabela pai). As chaves estrangeiras são fundamentais para manter a integridade referencial no banco de dados, garantindo que os dados em uma tabela estejam relacionados corretamente com os dados em outra tabela.

## Criação de Chaves Estrangeiras

### Sintaxe Básica

A constraint de chave estrangeira pode ser criada no momento da criação da tabela ou adicionada posteriormente usando o comando `ALTER TABLE`.

### Criação no Momento da Criação da Tabela

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

### Adicionando a Chave Estrangeira Posteriormente

```sql
ALTER TABLE TabelaFilha
ADD CONSTRAINT FK_TabelaFilha_TabelaPai
FOREIGN KEY (TabelaPaiID) REFERENCES TabelaPai(ID);
```

## Comportamentos de Exclusão e Atualização

As chaves estrangeiras podem ser configuradas com comportamentos específicos para ações de exclusão (`DELETE`) e atualização (`UPDATE`). Os comportamentos comuns incluem:

- **NO ACTION**: Não permite a exclusão ou atualização da linha pai se houver linhas filhas correspondentes.
- **CASCADE**: Exclui ou atualiza automaticamente as linhas filhas quando a linha pai é excluída ou atualizada.
- **SET NULL**: Define a chave estrangeira como `NULL` quando a linha pai é excluída ou atualizada.
- **SET DEFAULT**: Define a chave estrangeira para um valor padrão quando a linha pai é excluída ou atualizada.

### Exemplo de Comportamento Cascade

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
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

Neste exemplo, se uma linha da `TabelaPai` for excluída, todas as linhas correspondentes na `TabelaFilha` também serão excluídas. Se o `ID` na `TabelaPai` for atualizado, o `TabelaPaiID` correspondente na `TabelaFilha` será automaticamente atualizado.

## Verificando e Removendo Chaves Estrangeiras

### Verificar Chaves Estrangeiras

Para listar todas as constraints de chave estrangeira no banco de dados, pode-se usar a consulta abaixo:

```sql
SELECT 
    fk.name AS ForeignKey,
    tp.name AS ParentTable,
    cp.name AS ParentColumn,
    tr.name AS ReferencedTable,
    cr.name AS ReferencedColumn
FROM 
    sys.foreign_keys AS fk
INNER JOIN 
    sys.foreign_key_columns AS fkc ON fk.object_id = fkc.constraint_object_id
INNER JOIN 
    sys.tables AS tp ON fk.parent_object_id = tp.object_id
INNER JOIN 
    sys.columns AS cp ON fkc.parent_column_id = cp.column_id AND fkc.parent_object_id = cp.object_id
INNER JOIN 
    sys.tables AS tr ON fk.referenced_object_id = tr.object_id
INNER JOIN 
    sys.columns AS cr ON fkc.referenced_column_id = cr.column_id AND fkc.referenced_object_id = cr.object_id;
```

### Remover Chave Estrangeira

Para remover uma constraint de chave estrangeira, usa-se o comando `ALTER TABLE... DROP CONSTRAINT`.

```sql
ALTER TABLE TabelaFilha
DROP CONSTRAINT FK_TabelaFilha_TabelaPai;
```

## Benefícios e Considerações

### Benefícios

- **Integridade Referencial**: Garante que os dados nas tabelas sejam consistentes.
- **Manutenção Automática**: Pode definir comportamentos automáticos para exclusão e atualização de dados relacionados.

### Considerações

- **Performance**: As constraints de chave estrangeira podem impactar a performance em operações de inserção, atualização e exclusão.
- **Complexidade**: Pode adicionar complexidade ao design do banco de dados, especialmente em sistemas com muitos relacionamentos.

## Conclusão

Chaves estrangeiras são um componente crucial no design de bancos de dados relacionais, assegurando a integridade e consistência dos dados. Ao entender como criar, gerenciar e utilizar chaves estrangeiras no SQL Server, você pode construir bases de dados robustas e confiáveis.