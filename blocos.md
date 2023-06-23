# Blocos

### Criação da função primeira_pl com mais de um bloco

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER DEFAULT 3;
    BEGIN
        primeira_variavel := primeira_variavel * 2;
        DECLARE
            primeira_variavel INTEGER;
        BEGIN
            primeira_variavel := 7;
            -- Depois do END desse bloco, variável deixa de existir, e o valor 6 é retornado
        END;

        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```

### Criação da função primeira_pl sem segundo bloco DECLARE (Valor 7 será retornado, pois não foi inicializada uma nova variável dentro do bloco)

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER DEFAULT 3;
    BEGIN
        primeira_variavel := primeira_variavel * 2;
        BEGIN
            primeira_variavel := 7;
        END;

        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```