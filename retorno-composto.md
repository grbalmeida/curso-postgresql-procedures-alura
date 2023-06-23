# Retorno composto

### Criação da função cria_instrutor_falso

```sql
CREATE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
    SELECT 22, 'Nome falso', 200;
$$ LANGUAGE SQL;
```

### Criação da função cria_instrutor_falso com alias

```sql
DROP FUNCTION cria_instrutor_falso;

CREATE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
    SELECT 22 AS id, 'Nome falso' AS nome, 200 AS salario;
$$ LANGUAGE SQL;
```

### Criação da função cria_instrutor_falso com cast para decimal

```sql
CREATE OR REPLACE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
    SELECT 22 AS id, 'Nome falso' AS nome, 200::DECIMAL AS salario;
$$ LANGUAGE SQL;
```