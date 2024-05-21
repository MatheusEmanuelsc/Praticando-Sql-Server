# Manipulação e Formatação de Datas no SQL Server

Trabalhar com datas no SQL Server é uma parte essencial do desenvolvimento e administração de bancos de dados. Este guia cobre os principais aspectos da manipulação e formatação de datas no SQL Server.

## Tipos de Dados de Data e Hora

O SQL Server oferece vários tipos de dados para armazenar informações de data e hora:

- `DATE`: Armazena apenas a data (ano, mês, dia).
- `TIME`: Armazena apenas a hora (hora, minuto, segundo, fração de segundo).
- `DATETIME`: Armazena data e hora, com precisão de até 3 milissegundos.
- `DATETIME2`: Armazena data e hora, com precisão de até 100 nanossegundos.
- `SMALLDATETIME`: Armazena data e hora, com precisão de até 1 minuto.
- `DATETIMEOFFSET`: Armazena data e hora com fuso horário.
- `TIMESTAMP` ou `ROWVERSION`: Não armazena uma data, mas um número binário único que pode ser utilizado para versionamento de linhas.

## Funções de Data e Hora

O SQL Server oferece várias funções para trabalhar com datas e horas. Aqui estão algumas das mais comuns:

### Obtenção da Data e Hora Atual

- `GETDATE()`: Retorna a data e hora atuais do sistema.
- `SYSDATETIME()`: Retorna a data e hora atuais com maior precisão.
- `CURRENT_TIMESTAMP`: Funciona como `GETDATE()`, mas é ANSI SQL.

### Manipulação de Datas

- `DATEADD()`: Adiciona um intervalo de tempo a uma data.
  
  ```sql
  SELECT DATEADD(day, 5, GETDATE()) AS NovaData;
  ```

- `DATEDIFF()`: Calcula a diferença entre duas datas.

  ```sql
  SELECT DATEDIFF(day, '2024-01-01', '2024-05-21') AS Diferenca;
  ```

- `DATEPART()`: Extrai uma parte específica da data (ano, mês, dia, etc.).

  ```sql
  SELECT DATEPART(year, GETDATE()) AS AnoAtual;
  ```

- `DATENAME()`: Retorna a parte textual de uma data (nome do mês, dia da semana, etc.).

  ```sql
  SELECT DATENAME(month, GETDATE()) AS MesAtual;
  ```

## Formatação de Datas

A formatação de datas no SQL Server pode ser realizada usando a função `CONVERT()` ou `FORMAT()`, dependendo da versão do SQL Server que você está utilizando.

### Usando `CONVERT()`

A função `CONVERT()` permite a conversão de datas para diferentes formatos, utilizando um estilo especificado.

```sql
SELECT CONVERT(varchar, GETDATE(), 103) AS DataFormatada; -- dd/mm/yyyy
```

Alguns códigos de estilo comuns:

- 101: `mm/dd/yyyy`
- 103: `dd/mm/yyyy`
- 112: `yyyymmdd`

### Usando `FORMAT()`

A função `FORMAT()` está disponível a partir do SQL Server 2012 e permite formatação mais flexível.

```sql
SELECT FORMAT(GETDATE(), 'dd/MM/yyyy') AS DataFormatada;
```

### Exemplos de Formatação

```sql
SELECT 
    CONVERT(varchar, GETDATE(), 101) AS Formato1, -- mm/dd/yyyy
    CONVERT(varchar, GETDATE(), 104) AS Formato2, -- dd.mm.yyyy
    FORMAT(GETDATE(), 'dddd, MMMM dd, yyyy') AS Formato3 -- Nome completo do dia e mês
```

## Comparação de Datas

A comparação de datas é direta no SQL Server. Pode-se utilizar operadores de comparação comuns como `=`, `>`, `<`, `>=`, `<=`, `<>`.

### Exemplo:

```sql
SELECT *
FROM Eventos
WHERE DataEvento >= '2024-05-21';
```

## Considerações de Fuso Horário

Ao trabalhar com dados que envolvem fusos horários diferentes, `DATETIMEOFFSET` é o tipo de dado recomendado. Ele armazena a data e hora com um deslocamento de fuso horário.

### Exemplo:

```sql
DECLARE @DataComFuso DATETIMEOFFSET = '2024-05-21 10:00:00 -04:00';
SELECT @DataComFuso;
```

## Boas Práticas

- **Uso Consistente de Tipos de Dados**: Utilize tipos de dados de data e hora apropriados conforme a necessidade.
- **Formatação para Exibição**: Formate datas somente no nível de apresentação, mantendo o armazenamento no formato padrão do SQL Server.
- **Validação de Dados**: Valide entradas de data para garantir a integridade dos dados no banco.

