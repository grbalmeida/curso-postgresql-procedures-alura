# Case When

### Criação da função salario_ok com CASE WHEN

```sql
CREATE OR REPLACE FUNCTION salario_ok(id_instrutor INTEGER) RETURNS VARCHAR AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        SELECT * FROM instrutor WHERE id = id_instrutor INTO instrutor;

        CASE
            WHEN instrutor.salario = 100 THEN
                RETURN 'Salário muito baixo';
            WHEN instrutor.salario = 200 THEN
                RETURN 'Salário baixo';
            WHEN instrutor.salario = 300 THEN
                RETURN 'Salário ok';
            ELSE
                RETURN 'Salário ótimo';
        END CASE;
    END;
$$ LANGUAGE plpgsql;
```

### Criação da função salario_ok com CASE WHEN, sem repetição de instrutor.salario

```sql
CREATE OR REPLACE FUNCTION salario_ok(id_instrutor INTEGER) RETURNS VARCHAR AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        SELECT * FROM instrutor WHERE id = id_instrutor INTO instrutor;

        CASE instrutor.salario
            WHEN 100 THEN
                RETURN 'Salário muito baixo';
            WHEN 200 THEN
                RETURN 'Salário baixo';
            WHEN 300 THEN
                RETURN 'Salário ok';
            ELSE
                RETURN 'Salário ótimo';
        END CASE;
    END;
$$ LANGUAGE plpgsql;
```