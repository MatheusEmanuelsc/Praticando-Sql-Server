


## Deletando Registros da Tabela `Clientes`

Para deletar registros da tabela `Clientes`, utilize a seguinte sintaxe:

```sql
DELETE FROM Clientes
WHERE Id = 1001;
```

Neste exemplo, estamos deletando o registro cujo `Id` é igual a 1001.

Ao utilizar a instrução `DELETE`, primeiro especificamos `DELETE FROM` seguido do nome da tabela (`Clientes`). Em seguida, utilizamos a cláusula `WHERE` para indicar quais registros devem ser deletados. É crucial utilizar a cláusula `WHERE` para evitar deletar todos os registros da tabela por engano.

Se você deseja deletar todos os registros de uma tabela, pode omitir a cláusula `WHERE`, mas tenha cuidado ao fazer isso, pois todos os registros serão removidos:

```sql
DELETE FROM Clientes;
```

Lembre-se sempre de ser cuidadoso ao usar a instrução `DELETE`, especialmente sem a cláusula `WHERE`, para evitar a perda acidental de dados.
