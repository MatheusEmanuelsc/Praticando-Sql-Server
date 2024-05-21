# Uso de `GROUP BY` no SQL Server

O comando `GROUP BY` no SQL Server é utilizado para agrupar linhas que possuem valores iguais em colunas especificadas em conjuntos de resumo, como contagens, somas, médias, etc. É especialmente útil em consultas que envolvem funções agregadas.

## Sintaxe Básica

```sql
SELECT coluna1, coluna2, ..., função_agregada(coluna)
FROM tabela
WHERE condição
GROUP BY coluna1, coluna2, ...;
```

### Regras Importantes:
1. **WHERE** sempre vem antes do **GROUP BY**.
2. Todas as colunas no `SELECT` que não são usadas em uma função agregada devem estar no `GROUP BY`.

## Exemplo de Uso do `GROUP BY`

Vamos considerar a seguinte consulta SQL para entender como funciona o `GROUP BY`:

```sql
SELECT tamanho, COUNT(*) AS Quantidade
FROM Produtos
WHERE tamanho <> ' '
GROUP BY tamanho;
```

### Explicação:

- **SELECT tamanho, COUNT(*) AS Quantidade**: Seleciona a coluna `tamanho` e conta o número de ocorrências de cada tamanho. `COUNT(*)` é uma função agregada que conta todas as linhas.
- **FROM Produtos**: Especifica a tabela `Produtos` de onde os dados serão recuperados.
- **WHERE tamanho <> ' '**: Filtra os resultados para excluir linhas onde `tamanho` está vazio.
- **GROUP BY tamanho**: Agrupa os resultados pela coluna `tamanho`. Cada grupo conterá todas as linhas com o mesmo valor em `tamanho`.

### Resultado Esperado:

A consulta retornará uma lista de tamanhos de produtos junto com a quantidade de produtos disponíveis para cada tamanho, excluindo quaisquer registros onde `tamanho` está vazio.

### Exemplo Prático:

Suponha que a tabela `Produtos` tenha os seguintes dados:

| ProdutoID | Nome        | Tamanho | Preco |
|-----------|-------------|---------|-------|
| 1         | Camiseta    | M       | 20.00 |
| 2         | Calça       | L       | 30.00 |
| 3         | Camiseta    | M       | 20.00 |
| 4         | Jaqueta     | S       | 50.00 |
| 5         | Calça       | L       | 30.00 |
| 6         | Camiseta    |         | 20.00 |

Após executar a consulta, o resultado será:

| Tamanho | Quantidade |
|---------|------------|
| M       | 2          |
| L       | 2          |
| S       | 1          |

## Outras Funções Agregadas com `GROUP BY`

Além do `COUNT()`, outras funções agregadas que podem ser usadas com `GROUP BY` incluem:

- **SUM()**: Soma dos valores.
- **AVG()**: Média dos valores.
- **MIN()**: Menor valor.
- **MAX()**: Maior valor.

### Exemplo com `SUM()`:

```sql
SELECT tamanho, SUM(Preco) AS TotalPreco
FROM Produtos
WHERE tamanho <> ' '
GROUP BY tamanho;
```

Este exemplo calcula a soma dos preços dos produtos para cada tamanho.

## Conclusão

O `GROUP BY` é uma poderosa ferramenta no SQL Server para agrupar dados e calcular resumos. Ele é frequentemente usado junto com funções agregadas para gerar relatórios e análises a partir dos dados armazenados no banco de dados.