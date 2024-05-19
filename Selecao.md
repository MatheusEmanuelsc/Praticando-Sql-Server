
# Guia de SQL para Seleção, Ordenação e Filtragem de Dados

## Criação da Tabela `Clientes`

Primeiro, vamos criar a tabela `Clientes`:

```sql
CREATE TABLE [dbo].[Clientes](
    [Id] [int] IDENTITY(1,1) NOT NULL,
      NULL,
      NULL,
      NULL,
    [AceitaComunicados] [bit] NULL,
      NULL
) ON [PRIMARY]
GO
```

## Inserção de Dados na Tabela `Clientes`

Agora, vamos inserir alguns dados na tabela `Clientes`:

```sql
INSERT INTO Clientes (Nome, Sobrenome, Email, AceitaComunicados, DataCadastro)
VALUES 
('Ken', 'Sánchez', 'email@email.com', 0, '2009-01-07T00:00:00'),
('Terri', 'Duffy', 'email@email.com', 1, '2008-01-24T00:00:00'),
('Roberto', 'Tamburello', 'email@email.com', 0, '2007-11-04T00:00:00'),
('Rob', 'Walters', 'email@email.com', 0, '2007-11-28T00:00:00'),
('Gail', 'Erickson', 'email@email.com', 0, '2007-12-30T00:00:00'),
('Jossef', 'Goldberg', 'email@email.com', 0, '2013-12-16T00:00:00'),
('Dylan', 'Miller', 'email@email.com', 0, '2009-02-01T00:00:00');
```

## Seleção de Dados

### Exemplo de Seleção

Para selecionar todos os dados da tabela `Clientes`, use:

```sql
SELECT * FROM Clientes;
```

### Seleção Específica de Campos

Para selecionar campos específicos, especifique os nomes das colunas:

```sql
SELECT Nome, Sobrenome, Email FROM Clientes;
```

## Ordenação de Dados

### Exemplo de Ordenação

Para ordenar os dados pelo campo `Nome`, use:

```sql
SELECT * FROM Clientes
ORDER BY Nome;
```

### Ordenação Decrescente

Para ordenar os dados pelo campo `Nome` em ordem decrescente, use `DESC`:

```sql
SELECT * FROM Clientes
ORDER BY Nome DESC;
```

### Ordenação por Múltiplos Campos

Para ordenar por mais de um campo, separe os campos por vírgula:

```sql
SELECT * FROM Clientes
ORDER BY Nome, Sobrenome;
```

**Nota**: A cláusula `ORDER BY` deve estar no final da consulta.

## Filtrando Dados na Hora da Seleção

### Exemplo de Filtro

Para selecionar apenas os clientes que aceitaram comunicados (`AceitaComunicados = 1`):

```sql
SELECT * FROM Clientes
WHERE AceitaComunicados = 1;
```

### Filtro por String

Para filtrar por um valor específico em uma coluna de texto, use aspas simples:

```sql
SELECT * FROM Clientes
WHERE Nome = 'Ken';
```

### Filtro com Múltiplas Condições

Para usar múltiplos filtros com `AND` (ambas condições devem ser verdadeiras):

```sql
SELECT * FROM Clientes
WHERE AceitaComunicados = 1 AND Sobrenome = 'Duffy';
```

Para usar múltiplos filtros com `OR` (pelo menos uma condição deve ser verdadeira):

```sql
SELECT * FROM Clientes
WHERE AceitaComunicados = 1 OR Sobrenome = 'Duffy';
```

## Uso do `LIKE` para Filtragem Específica

### Exemplo de Filtro com `LIKE`

Para encontrar nomes que começam com a letra "G":

```sql
SELECT * FROM Clientes
WHERE Nome LIKE 'G%';
```

No exemplo acima, `%` é um curinga que representa zero ou mais caracteres após a letra "G".

### `LIKE` com Curinga no Início

Para encontrar nomes que terminam com "n":

```sql
SELECT * FROM Clientes
WHERE Nome LIKE '%n';
```

### `LIKE` com Curinga no Meio

Para encontrar nomes que contêm "a" em qualquer posição:

```sql
SELECT * FROM Clientes
WHERE Nome LIKE '%a%';
```

### `LIKE` com Sublinhado (`_`)

O sublinhado (`_`) representa exatamente um caractere. Por exemplo, para encontrar nomes que têm exatamente quatro caracteres:

```sql
SELECT * FROM Clientes
WHERE Nome LIKE '____';
```

### `LIKE` com Colchetes (`[ ]`)

Os colchetes (`[ ]`) representam qualquer um dos caracteres dentro dos colchetes. Por exemplo, para encontrar nomes que começam com "A" ou "B":

```sql
SELECT * FROM Clientes
WHERE Nome LIKE '[AB]%';
```

### `LIKE` com Exclamação (`!`)

A exclamação (`!`) dentro dos colchetes representa qualquer caractere que não esteja dentro dos colchetes. Por exemplo, para encontrar nomes que não começam com "A" ou "B":

```sql
SELECT * FROM Clientes
WHERE Nome LIKE '[!AB]%';
```


