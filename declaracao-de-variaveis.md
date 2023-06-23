# Declarações de variáveis

### Criação da função primeira_pl com variáveis

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER DEFAULT 3;
    BEGIN
        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```

### Criação da função primeira_pl com reatribuição de valor da variável

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER DEFAULT 3;
    BEGIN
        primeira_variavel := primeira_variavel * 2;
        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```

### Criação da função primeira_pl com valor default sem palavra reservada

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER := 3;
    BEGIN
        primeira_variavel := primeira_variavel * 2;
        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```

### Criação da função primeira_pl com sinal de igual

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
    DECLARE
        primeira_variavel INTEGER = 3;
    BEGIN
        primeira_variavel = primeira_variavel * 2;
        RETURN primeira_variavel;
    END
$$ LANGUAGE plpgsql;
```