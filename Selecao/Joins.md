# Índice e Resumo sobre JOINs no SQL Server

## Parte 1: Índice com Resumo dos JOINs

### 1. INNER JOIN
O `INNER JOIN` retorna registros que possuem valores correspondentes em ambas as tabelas envolvidas na junção.

### 2. LEFT JOIN (ou LEFT OUTER JOIN)
O `LEFT JOIN` retorna todos os registros da tabela à esquerda e os registros correspondentes da tabela à direita. Se não houver correspondência, os resultados da tabela à direita serão `NULL`.

### 3. RIGHT JOIN (ou RIGHT OUTER JOIN)
O `RIGHT JOIN` retorna todos os registros da tabela à direita e os registros correspondentes da tabela à esquerda. Se não houver correspondência, os resultados da tabela à esquerda serão `NULL`.

### 4. FULL JOIN (ou FULL OUTER JOIN)
O `FULL JOIN` retorna registros quando há uma correspondência em uma das tabelas. Ele combina os resultados de `LEFT JOIN` e `RIGHT JOIN`.

### 5. CROSS JOIN
O `CROSS JOIN` retorna o produto cartesiano das duas tabelas, combinando todas as linhas da primeira tabela com todas as linhas da segunda tabela.

### 6. SELF JOIN
O `SELF JOIN` é uma junção de uma tabela com ela mesma. É útil para relacionamentos hierárquicos.

## Parte 2: Exemplos e Explicação

### 1. INNER JOIN

#### Exemplo:

```sql
SELECT 
    A.ID,
    A.Nome,
    B.Curso
FROM 
    Alunos A
INNER JOIN 
    Cursos B ON A.CursoID = B.ID;
```

#### Explicação:
- **INNER JOIN**: Junta as tabelas `Alunos` e `Cursos` onde o `CursoID` em `Alunos` corresponde ao `ID` em `Cursos`.
- **Resultado**: Somente alunos que estão inscritos em cursos existentes serão retornados.

### 2. LEFT JOIN

#### Exemplo:

```sql
SELECT 
    A.ID,
    A.Nome,
    B.Curso
FROM 
    Alunos A
LEFT JOIN 
    Cursos B ON A.CursoID = B.ID;
```

#### Explicação:
- **LEFT JOIN**: Retorna todos os registros da tabela `Alunos`, e os cursos correspondentes da tabela `Cursos`.
- **Resultado**: Todos os alunos serão retornados, mesmo aqueles que não estão inscritos em nenhum curso (neste caso, o campo `Curso` será `NULL`).

### 3. RIGHT JOIN

#### Exemplo:

```sql
SELECT 
    A.ID,
    A.Nome,
    B.Curso
FROM 
    Alunos A
RIGHT JOIN 
    Cursos B ON A.CursoID = B.ID;
```

#### Explicação:
- **RIGHT JOIN**: Retorna todos os registros da tabela `Cursos`, e os alunos correspondentes da tabela `Alunos`.
- **Resultado**: Todos os cursos serão retornados, mesmo aqueles que não têm alunos inscritos (neste caso, os campos de `Alunos` serão `NULL`).

### 4. FULL JOIN

#### Exemplo:

```sql
SELECT 
    A.ID,
    A.Nome,
    B.Curso
FROM 
    Alunos A
FULL JOIN 
    Cursos B ON A.CursoID = B.ID;
```

#### Explicação:
- **FULL JOIN**: Retorna todos os registros quando há uma correspondência em uma das tabelas.
- **Resultado**: Todos os alunos e todos os cursos serão retornados. Se um aluno não estiver inscrito em nenhum curso, os campos de `Cursos` serão `NULL`, e vice-versa.

### 5. CROSS JOIN

#### Exemplo:

```sql
SELECT 
    A.Nome,
    B.Curso
FROM 
    Alunos A
CROSS JOIN 
    Cursos B;
```

#### Explicação:
- **CROSS JOIN**: Combina todas as linhas da tabela `Alunos` com todas as linhas da tabela `Cursos`.
- **Resultado**: Cada aluno será combinado com cada curso, resultando em um número muito grande de combinações (produto cartesiano).

### 6. SELF JOIN

#### Exemplo:

```sql
SELECT 
    A1.ID AS ID1,
    A1.Nome AS Nome1,
    A2.ID AS ID2,
    A2.Nome AS Nome2
FROM 
    Alunos A1
INNER JOIN 
    Alunos A2 ON A1.ID = A2.MentorID;
```

#### Explicação:
- **SELF JOIN**: Junta a tabela `Alunos` consigo mesma. Aqui, estamos assumindo que há uma coluna `MentorID` que referencia o `ID` de outro aluno que é mentor do primeiro.
- **Resultado**: Retorna pares de alunos onde um aluno é mentor do outro.

## Conclusão

Os diferentes tipos de `JOIN` no SQL Server permitem combinar dados de múltiplas tabelas de diversas maneiras, atendendo a diferentes necessidades de consulta. Cada tipo de `JOIN` tem suas características e usos específicos, permitindo uma flexibilidade significativa na recuperação de dados relacionados em um banco de dados relacional.S