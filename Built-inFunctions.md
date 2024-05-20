# Índice de Funções Built-in do SQL Server

1. [COUNT](#count)
   - Conta o número de registros em uma tabela.
2. [SUM](#sum)
   - Calcula a soma de valores em uma coluna.
3. [MAX](#max)
   - Encontra o valor máximo em uma coluna.
4. [MIN](#min)
   - Encontra o valor mínimo em uma coluna.
5. [CONCAT](#concat)
   - Concatena valores de colunas.
6. [UPPER](#upper)
   - Converte texto para maiúsculas.
7. [LOWER](#lower)
   - Converte texto para minúsculas.
8. [AVG](#avg)
   - Calcula a média dos valores em uma coluna.
9. [LEN](#len)
   - Retorna o comprimento de uma string.
10. [GETDATE](#getdate)
    - Retorna a data e hora atuais.
11. [ROUND](#round)
    - Arredonda um valor numérico para um número específico de decimais.
12. [SUBSTRING](#substring)
    - Extrai uma parte de uma string.
13. [REPLACE](#replace)
    - Substitui todas as ocorrências de uma substring por outra substring.
14. [DATEDIFF](#datediff)
    - Calcula a diferença entre duas datas.
15. [ISNULL](#isnull)
    - Substitui valores nulos por um valor especificado.
16. [COALESCE](#coalesce)
    - Retorna o primeiro valor não nulo em uma lista de argumentos.
17. [CAST](#cast)
    - Converte um valor de um tipo de dado para outro.
18. [CONVERT](#convert)
    - Converte um valor de um tipo de dado para outro, com formatação opcional.
19. [NEWID](#newid)
    - Gera um identificador único (GUID).
20. [PATINDEX](#patindex)
    - Retorna a posição inicial de um padrão em uma expressão de texto.

# Detalhamento das Funções Built-in do SQL Server

## COUNT
### Descrição:
A função `COUNT` é utilizada para contar o número de registros em uma tabela.

### Exemplo:
```sql
SELECT COUNT(*) AS QuantidadeProdutos FROM Produtos;
```

Você também pode usar a cláusula `WHERE` para filtrar os registros contados:
```sql
SELECT COUNT(*) AS QuantidadeProdutos FROM Produtos WHERE Categoria = 'Eletrônicos';
```

## SUM
### Descrição:
A função `SUM` calcula a soma total dos valores de uma coluna específica.

### Exemplo:
```sql
SELECT SUM(Preco) AS PrecoTotal FROM Produtos;
```

## MAX
### Descrição:
A função `MAX` retorna o valor máximo de uma coluna.

### Exemplo:
```sql
SELECT MAX(Preco) AS PrecoMaximo FROM Produtos;
```

## MIN
### Descrição:
A função `MIN` retorna o valor mínimo de uma coluna.

### Exemplo:
```sql
SELECT MIN(Preco) AS PrecoMinimo FROM Produtos;
```

## CONCAT
### Descrição:
A função `CONCAT` é usada para concatenar (juntar) valores de colunas.

### Exemplo:
```sql
SELECT Nome + ' = ' + Cor AS NomeCor FROM Produtos;
```

## UPPER
### Descrição:
A função `UPPER` converte todos os caracteres de uma coluna de texto para maiúsculas.

### Exemplo:
```sql
SELECT UPPER(Nome) AS NomeMaiusculo FROM Produtos;
```

## LOWER
### Descrição:
A função `LOWER` converte todos os caracteres de uma coluna de texto para minúsculas.

### Exemplo:
```sql
SELECT LOWER(Nome) AS NomeMinusculo FROM Produtos;
```

## AVG
### Descrição:
A função `AVG` calcula a média dos valores de uma coluna numérica.

### Exemplo:
```sql
SELECT AVG(Preco) AS PrecoMedio FROM Produtos;
```

## LEN
### Descrição:
A função `LEN` retorna o comprimento de uma string (número de caracteres).

### Exemplo:
```sql
SELECT LEN(Nome) AS TamanhoNome FROM Produtos;
```

## GETDATE
### Descrição:
A função `GETDATE` retorna a data e hora atuais do sistema.

### Exemplo:
```sql
SELECT GETDATE() AS DataAtual;
```

## ROUND
### Descrição:
A função `ROUND` arredonda um valor numérico para um número específico de decimais.

### Exemplo:
```sql
SELECT ROUND(Preco, 2) AS PrecoArredondado FROM Produtos;
```

## SUBSTRING
### Descrição:
A função `SUBSTRING` extrai uma parte de uma string a partir de uma posição inicial por um número especificado de caracteres.

### Exemplo:
```sql
SELECT SUBSTRING(Nome, 1, 3) AS NomeAbreviado FROM Produtos;
```

## REPLACE
### Descrição:
A função `REPLACE` substitui todas as ocorrências de uma substring por outra substring.

### Exemplo:
```sql
SELECT REPLACE(Nome, ' ', '-') AS NomeComHifen FROM Produtos;
```

## DATEDIFF
### Descrição:
A função `DATEDIFF` calcula a diferença entre duas datas, retornando o resultado em unidades especificadas (como dias, meses, anos).

### Exemplo:
```sql
SELECT DATEDIFF(day, '2023-01-01', GETDATE()) AS DiasDesdeInicioDoAno;
```

## ISNULL
### Descrição:
A função `ISNULL` substitui valores nulos por um valor especificado.

### Exemplo:
```sql
SELECT ISNULL(Descricao, 'Descrição não disponível') AS Descricao FROM Produtos;
```

## COALESCE
### Descrição:
A função `COALESCE` retorna o primeiro valor não nulo em uma lista de argumentos.

### Exemplo:
```sql
SELECT COALESCE(Descricao, Observacoes, 'Nenhuma informação disponível') AS Informacao FROM Produtos;
```

## CAST
### Descrição:
A função `CAST` converte um valor de um tipo de dado para outro.

### Exemplo:
```sql
SELECT CAST(Preco AS VARCHAR(10)) AS PrecoTexto FROM Produtos;
```

## CONVERT
### Descrição:
A função `CONVERT` converte um valor de um tipo de dado para outro, com formatação opcional.

### Exemplo:
```sql
SELECT CONVERT(VARCHAR, GETDATE(), 103) AS DataFormatada; -- Formato DD/MM/YYYY
```

## NEWID
### Descrição:
A função `NEWID` gera um identificador único (GUID).

### Exemplo:
```sql
SELECT NEWID() AS NovoID;
```

## PATINDEX
### Descrição:
A função `PATINDEX` retorna a posição inicial de um padrão em uma expressão de texto.

### Exemplo:
```sql
SELECT PATINDEX('%produto%', Descricao) AS Posicao FROM Produtos WHERE Descricao LIKE '%produto%';
```

