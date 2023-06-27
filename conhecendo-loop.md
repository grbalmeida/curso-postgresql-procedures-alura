# Conhecendo Loop

### Criação da função tabuada com loop

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF INTEGER AS $$
    DECLARE
        multiplicador INTEGER DEFAULT 1;
    BEGIN
        -- Multiplicador que começa com 1, e vai até < 10
        -- numero * multiplicador
        -- multiplicador := multiplicador + 1

        LOOP
            RETURN NEXT numero * multiplicador;
            multiplicador := multiplicador + 1;
            EXIT WHEN multiplicador = 10;
        END LOOP;
    END;
$$ LANGUAGE plpgsql;
```

### Criação da função tabuada retornando setof formatado

```sql
DROP FUNCTION tabuada;

CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$
    DECLARE
        multiplicador INTEGER DEFAULT 1;
    BEGIN
        LOOP
            RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
            multiplicador := multiplicador + 1;
            EXIT WHEN multiplicador = 10;
        END LOOP;
    END;
$$ LANGUAGE plpgsql;
```