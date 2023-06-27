# Return Next

### Criação da função tabuada

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF INTEGER AS $$
    DECLARE
    BEGIN
        RETURN NEXT numero * 1;
        RETURN NEXT numero * 2;
        RETURN NEXT numero * 3;
        RETURN NEXT numero * 4;
        RETURN NEXT numero * 5;
        RETURN NEXT numero * 6;
        RETURN NEXT numero * 7;
        RETURN NEXT numero * 8;
        RETURN NEXT numero * 9;
    END;
$$ LANGUAGE plpgsql;
```