Aqui está o documento em markdown reformulado para incluir botões de navegação no índice que redirecionam para as seções correspondentes:

```markdown
# Índice

- [Introdução](#introdução)
- [Criando uma Stored Procedure](#criando-uma-stored-procedure)
- [Executando uma Stored Procedure](#executando-uma-stored-procedure)
- [Alterando uma Stored Procedure](#alterando-uma-stored-procedure)
- [Removendo uma Stored Procedure](#removendo-uma-stored-procedure)
- [Mais sobre Stored Procedures](#mais-sobre-stored-procedures)

## Introdução

Stored Procedures são rotinas armazenadas no banco de dados SQL Server que podem ser reutilizadas e facilitam a execução de tarefas repetitivas. Elas melhoram a performance e a manutenção do código.

[Voltar ao Índice](#índice)

## Criando uma Stored Procedure

Para criar uma Stored Procedure no SQL Server, usa-se a instrução `CREATE PROCEDURE`.

### Exemplo:

```sql
CREATE PROCEDURE ObterUsuarios
AS
BEGIN
    SELECT * FROM Usuarios;
END;
```

### Explicação:
- `CREATE PROCEDURE` define o início da criação de uma nova stored procedure.
- `ObterUsuarios` é o nome da stored procedure.
- `AS BEGIN ... END` contém o bloco de comandos SQL que a procedure executará.

[Voltar ao Índice](#índice)

## Executando uma Stored Procedure

Para executar uma stored procedure, usa-se a instrução `EXEC` ou `EXECUTE`.

### Exemplo:

```sql
EXEC ObterUsuarios;
```

### Explicação:
- `EXEC` ou `EXECUTE` chama a stored procedure `ObterUsuarios` para execução.

[Voltar ao Índice](#índice)

## Alterando uma Stored Procedure

Para alterar uma stored procedure existente, usa-se a instrução `ALTER PROCEDURE`.

### Exemplo:

```sql
ALTER PROCEDURE ObterUsuarios
AS
BEGIN
    SELECT Nome, Email FROM Usuarios;
END;
```

### Explicação:
- `ALTER PROCEDURE` permite modificar a stored procedure existente `ObterUsuarios`.

[Voltar ao Índice](#índice)

## Removendo uma Stored Procedure

Para remover uma stored procedure, usa-se a instrução `DROP PROCEDURE`.

### Exemplo:

```sql
DROP PROCEDURE ObterUsuarios;
```

### Explicação:
- `DROP PROCEDURE` exclui a stored procedure `ObterUsuarios` do banco de dados.

[Voltar ao Índice](#índice)

## Mais sobre Stored Procedures

Stored Procedures podem aceitar parâmetros para maior flexibilidade.

### Exemplo com parâmetros:

```sql
CREATE PROCEDURE ObterUsuariosPorStatus
    @Status VARCHAR(20)
AS
BEGIN
    SELECT * FROM Usuarios WHERE Status = @Status;
END;
```

### Explicação:
- `@Status` é um parâmetro de entrada que a stored procedure utiliza para filtrar os resultados.

### Executando com parâmetros:

```sql
EXEC ObterUsuariosPorStatus @Status = 'Ativo';
```

Stored Procedures também podem retornar valores de saída, usar transações e lidar com erros, tornando-se uma ferramenta poderosa para gerenciar a lógica de negócios no SQL Server.

### Exemplo com valor de saída:

```sql
CREATE PROCEDURE ContarUsuariosAtivos
    @Total INT OUTPUT
AS
BEGIN
    SELECT @Total = COUNT(*) FROM Usuarios WHERE Status = 'Ativo';
END;
```

### Executando e capturando o valor de saída:

```sql
DECLARE @TotalUsuariosAtivos INT;
EXEC ContarUsuariosAtivos @Total = @TotalUsuariosAtivos OUTPUT;
PRINT @TotalUsuariosAtivos;
```

### Explicação:
- `@Total` é um parâmetro de saída que armazena o resultado da contagem de usuários ativos.
- `OUTPUT` especifica que o parâmetro é de saída.
- `DECLARE` cria uma variável para capturar o valor de saída.
- `PRINT` exibe o valor da variável.

Stored Procedures podem ser complexas, incluindo lógica condicional, loops e chamadas para outras procedures, permitindo uma ampla gama de funcionalidades e otimizações de desempenho no SQL Server.
