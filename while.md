# WHILE

### Criação da função tabuada com WHILE

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$
    DECLARE
        multiplicador INTEGER DEFAULT 1;
    BEGIN
        WHILE multiplicador < 10 LOOP
            RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
            multiplicador := multiplicador + 1;
        END LOOP;
    END;
$$ LANGUAGE plpgsql;
```