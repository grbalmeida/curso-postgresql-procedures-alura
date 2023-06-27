# If - Else

### Criação da função salario_ok

```sql
CREATE FUNCTION salario_ok(instrutor instrutor) RETURNS VARCHAR AS $$
    BEGIN
        -- Se o salário do instrutor for maior do que 200, está Ok. Senão, pode aumentar
        IF instrutor.salario > 200 THEN
            RETURN 'Salário está ok';
        ELSE
            RETURN 'Salário pode aumentar';
        END IF;
    END;
$$ LANGUAGE plpgsql;
```

### Criação da função salario_ok, recebendo id do instrutor como parâmetro
### (N+1 Problem)

```sql
DROP FUNCTION salario_ok;

CREATE FUNCTION salario_ok(id_instrutor INTEGER) RETURNS VARCHAR AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        SELECT * FROM instrutor WHERE id = id_instrutor INTO instrutor;

        IF instrutor.salario > 200 THEN
            RETURN 'Salário está ok';
        ELSE
            RETURN 'Salário pode aumentar';
        END IF;
    END;
$$ LANGUAGE plpgsql;
```