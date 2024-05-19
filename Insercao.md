
## Inserção de Dados na Tabela `Clientes`

Para inserir dados na tabela `Clientes`, utilize a seguinte sintaxe:

```sql
INSERT INTO Clientes (Nome, Sobrenome, Email, AceitaComunicados, DataCadastro)
VALUES 
('Ken', 'Sánchez', 'email@email.com', 0, '2009-01-07T00:00:00'),
('Terri', 'Duffy', 'email@email.com', 1, '2008-01-24T00:00:00');
```

Nesse exemplo, estamos inserindo dois registros de uma vez, especificando os valores para cada coluna na ordem correta. Os valores são fornecidos entre parênteses, separados por vírgulas, e os registros são separados por vírgulas também.

Outra maneira de fazer a inserção é omitindo as colunas. Nesse caso, os valores devem ser fornecidos na mesma ordem das colunas na tabela:

```sql
INSERT INTO Clientes
VALUES 
('Ken', 'Sánchez', 'email@email.com', 0, '2009-01-07T00:00:00'),
('Terri', 'Duffy', 'email@email.com', 1, '2008-01-24T00:00:00');
```

Nesta forma de inserção, não especificamos as colunas, então os valores devem ser fornecidos para todas as colunas na ordem em que foram definidas na tabela.
