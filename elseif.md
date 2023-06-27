# ElseIf

### Criação da função salario_ok

```sql
CREATE OR REPLACE FUNCTION salario_ok(id_instrutor INTEGER) RETURNS VARCHAR AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        SELECT * FROM instrutor WHERE id = id_instrutor INTO instrutor;

        -- Se o salário do instrutor for maior do que 300, está ok. Se for 300 reais, então pode aumentar.
        -- Caso contrário o salário está defasado.

        IF instrutor.salario > 300 THEN
            RETURN 'Salário está ok';
        ELSE
            IF instrutor.salario = 300 THEN
                RETURN 'Salário pode aumentar';
            ELSE
                RETURN 'Salário está defasado';
            END IF;
        END IF;
    END;
$$ LANGUAGE plpgsql;
```

### Criação da função salario_ok sem if's aninhados

```sql
CREATE OR REPLACE FUNCTION salario_ok(id_instrutor INTEGER) RETURNS VARCHAR AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        SELECT * FROM instrutor WHERE id = id_instrutor INTO instrutor;

        IF instrutor.salario > 300 THEN
            RETURN 'Salário está ok';
        ELSEIF instrutor.salario = 300 THEN
            RETURN 'Salário pode aumentar';
        ELSE
            RETURN 'Salário está defasado';
        END IF;
    END;
$$ LANGUAGE plpgsql;
```