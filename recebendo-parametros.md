# Recebendo parâmetros

### Criação de função que soma dois números

```sql
CREATE FUNCTION soma_dois_numeros(numero_1 INTEGER, numero_2 INTEGER) RETURNS INTEGER AS '
    SELECT numero_1 + numero_2;
' LANGUAGE SQL;
```

### Chamada da função soma_dois_numeros

```sql
SELECT soma_dois_numeros(2, 3); -- 5
```

### Criação da função soma_dois_numeros_posicao

```sql
CREATE FUNCTION soma_dois_numeros_posicao(INTEGER, INTEGER) RETURNS INTEGER AS '
    SELECT $1 + $2;
' LANGUAGE SQL;
```

### Chamada da função soma_dois_numeros_posicao

```sql
SELECT soma_dois_numeros_posicao(2, 4); -- 6
```

### Comando para excluir uma função

```sql
DROP FUNCTION soma_dois_numeros_posicao;
```