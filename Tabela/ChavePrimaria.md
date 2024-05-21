# Chaves Primárias (Primary Keys) no SQL Server

Uma chave primária (primary key) no SQL Server é uma constraint usada para identificar unicamente cada registro em uma tabela. Uma chave primária deve conter valores únicos e não pode conter valores nulos. A criação de uma chave primária garante a integridade dos dados e a eficiência das operações de consulta.

## Características das Chaves Primárias

- **Unicidade**: Cada valor na chave primária deve ser único.
- **Não Nulo**: Valores nulos não são permitidos.
- **Índice Clusterizado**: Por padrão, a criação de uma chave primária cria um índice clusterizado, ordenando fisicamente os dados na tabela com base na chave primária.

## Criação de Chaves Primárias

### Sintaxe Básica

Uma chave primária pode ser criada no momento da criação da tabela ou adicionada posteriormente usando o comando `ALTER TABLE`.

### Criação no Momento da Criação da Tabela

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY,
    Nome NVARCHAR(50)
);
```

### Criação com Índice Não Clusterizado

Para criar uma chave primária com um índice não clusterizado, especifique explicitamente o tipo de índice.

```sql
CREATE TABLE TabelaExemplo (
    ID INT PRIMARY KEY NONCLUSTERED,
    Nome NVARCHAR(50)
);
```

### Adicionando a Chave Primária Posteriormente

```sql
ALTER TABLE TabelaExemplo
ADD CONSTRAINT PK_TabelaExemplo PRIMARY KEY (ID);
```

## Chaves Primárias Compostas

Uma chave primária pode ser composta por mais de uma coluna. Isso é útil quando uma única coluna não é suficiente para garantir a unicidade.

### Exemplo de Chave Primária Composta

```sql
CREATE TABLE TabelaExemplo (
    Coluna1 INT,
    Coluna2 INT,
    Nome NVARCHAR(50),
    CONSTRAINT PK_TabelaExemplo PRIMARY KEY (Coluna1, Coluna2)
);
```

## Considerações sobre Índices Clusterizados

- **Índice Clusterizado**: Por padrão, a criação de uma chave primária cria um índice clusterizado. Isso significa que os dados na tabela são fisicamente organizados de acordo com a chave primária.
- **Índice Não Clusterizado**: Se necessário, a chave primária pode ser criada com um índice não clusterizado.

### Exemplo de Criação com Índice Clusterizado Especificado

```sql
CREATE TABLE TabelaExemplo (
    ID INT,
    Nome NVARCHAR(50),
    CONSTRAINT PK_TabelaExemplo PRIMARY KEY CLUSTERED (ID)
);
```

## Verificando e Removendo Chaves Primárias

### Verificar Chaves Primárias

Para listar todas as chaves primárias no banco de dados, pode-se usar a consulta abaixo:

```sql
SELECT 
    tc.TABLE_NAME, 
    kcu.COLUMN_NAME
FROM 
    INFORMATION_SCHEMA.TABLE_CONSTRAINTS AS tc
JOIN 
    INFORMATION_SCHEMA.KEY_COLUMN_USAGE AS kcu
ON 
    tc.CONSTRAINT_NAME = kcu.CONSTRAINT_NAME
WHERE 
    tc.CONSTRAINT_TYPE = 'PRIMARY KEY';
```

### Remover Chave Primária

Para remover uma constraint de chave primária, usa-se o comando `ALTER TABLE... DROP CONSTRAINT`.

```sql
ALTER TABLE TabelaExemplo
DROP CONSTRAINT PK_TabelaExemplo;
```

## Benefícios e Considerações

### Benefícios

- **Integridade dos Dados**: Garante que cada registro na tabela seja único.
- **Performance**: Melhora a performance das consultas devido ao índice clusterizado.

### Considerações

- **Escolha da Chave**: Escolher a chave primária corretamente é crucial. Ela deve ser estável (não mudar ao longo do tempo) e única.
- **Impacto no Desempenho**: O uso de índices clusterizados pode impactar a performance das operações de inserção e atualização.

## Conclusão

A chave primária é um componente fundamental no design de bancos de dados relacionais, assegurando a integridade e unicidade dos dados. Compreender como criar, gerenciar e utilizar chaves primárias no SQL Server é essencial para construir bancos de dados robustos e eficientes.