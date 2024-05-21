```markdown
# Índice

1. [Funções Escalares](#funções-escalares)
   - Breve resumo: Funções que retornam um único valor, baseadas em um ou mais valores de entrada.
2. [Funções de Agregação](#funções-de-agregação)
   - Breve resumo: Funções que realizam cálculos em um conjunto de valores e retornam um único valor.
3. [Funções de Data e Hora](#funções-de-data-e-hora)
   - Breve resumo: Funções específicas para manipulação de valores de data e hora.
4. [Funções de Texto](#funções-de-texto)
   - Breve resumo: Funções utilizadas para manipulação e análise de strings de texto.
5. [Gerenciamento de Funções](#gerenciamento-de-funções)
   - Breve resumo: Como criar, alterar e remover funções no SQL Server.

---

## Funções Escalares

### Funções Escalares
Funções escalares no SQL Server retornam um único valor, geralmente baseado em um ou mais valores de entrada.

#### Exemplos e Explicação
```sql
-- Função UPPER: Converte uma string para letras maiúsculas
SELECT UPPER('sql server');

-- Função LOWER: Converte uma string para letras minúsculas
SELECT LOWER('SQL SERVER');
```

## Funções de Agregação

### Funções de Agregação
Funções de agregação realizam cálculos em um conjunto de valores e retornam um único valor. Elas são comumente usadas com a cláusula `GROUP BY`.

#### Exemplos e Explicação
```sql
-- Função SUM: Soma de todos os valores
SELECT SUM(Price) FROM Products;

-- Função AVG: Média de todos os valores
SELECT AVG(Price) FROM Products;

-- Função COUNT: Contagem de todos os valores
SELECT COUNT(*) FROM Products;
```

## Funções de Data e Hora

### Funções de Data e Hora
Essas funções permitem a manipulação e formatação de valores de data e hora no SQL Server.

#### Exemplos e Explicação
```sql
-- Função GETDATE: Retorna a data e hora atuais
SELECT GETDATE();

-- Função DATEADD: Adiciona um intervalo de tempo a uma data
SELECT DATEADD(day, 10, GETDATE());

-- Função DATEDIFF: Calcula a diferença entre duas datas
SELECT DATEDIFF(day, '2023-01-01', '2023-12-31');
```

## Funções de Texto

### Funções de Texto
Funções de texto são usadas para manipular e analisar strings de texto no SQL Server.

#### Exemplos e Explicação
```sql
-- Função CONCAT: Concatena duas ou mais strings
SELECT CONCAT('SQL', ' ', 'Server');

-- Função SUBSTRING: Extrai uma parte de uma string
SELECT SUBSTRING('SQL Server', 1, 3);

-- Função LEN: Retorna o comprimento de uma string
SELECT LEN('SQL Server');
```

## Gerenciamento de Funções

### Gerenciamento de Funções
Esta seção cobre como criar, alterar e remover funções no SQL Server.

#### Criar Função
```sql
-- Criando uma função escalar
CREATE FUNCTION dbo.GetFullName (@FirstName NVARCHAR(50), @LastName NVARCHAR(50))
RETURNS NVARCHAR(100)
AS
BEGIN
    RETURN @FirstName + ' ' + @LastName;
END;
```

#### Alterar Função
```sql
-- Alterando uma função existente
ALTER FUNCTION dbo.GetFullName (@FirstName NVARCHAR(50), @LastName NVARCHAR(50))
RETURNS NVARCHAR(100)
AS
BEGIN
    RETURN @FirstName + ' ' + @LastName + ', SQL Developer';
END;
```

#### Remover Função
```sql
-- Removendo uma função
DROP FUNCTION dbo.GetFullName;
```

Se precisar adicionar mais informações sobre funções específicas ou outros tipos de funções, esta estrutura pode ser expandida conforme necessário.
```S