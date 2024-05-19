

## Atualização de Dados na Tabela `Clientes`

Para atualizar dados na tabela `Clientes`, utilize a seguinte sintaxe:

```sql
UPDATE Clientes 
SET Email = 'novoEmail@.com'
WHERE Id = 1;
```

Nesse exemplo, estamos atualizando o email para 'novoEmail@.com' para o cliente com `Id = 1`. 

Ao usar a instrução `UPDATE`, primeiro indicamos o nome da tabela que queremos atualizar (`Clientes`). Em seguida, usamos a cláusula `SET` para especificar qual coluna queremos atualizar e qual será o novo valor. Por fim, utilizamos a cláusula `WHERE` para indicar qual registro será atualizado. É importante utilizar a cláusula `WHERE` para evitar atualizar todos os registros na tabela inadvertidamente.

Se você precisar atualizar mais de uma coluna, basta separar cada atribuição de valor com vírgula, assim:

```sql
UPDATE Clientes 
SET 
    Email = 'novoEmail@.com',
    AceitaComunicados = 1
WHERE Id = 1;
```

Neste exemplo, estamos atualizando tanto o email quanto a flag `AceitaComunicados` para o cliente com `Id = 1`.
