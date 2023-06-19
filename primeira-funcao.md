# Primeira função

### Criação da função primeira_funcao que retorna o número 4

```sql
CREATE FUNCTION primeira_funcao() RETURNS INTEGER AS '
    SELECT (5 - 3) * 2
' LANGUAGE SQL;
```

### Chamada da função primeira_funcao

```sql
SELECT primeira_funcao();
SELECT * FROM primeira_funcao();
```

### Chamada da função primeira_funcao com alias numero

```sql
SELECT primeira_funcao() AS numero;
```