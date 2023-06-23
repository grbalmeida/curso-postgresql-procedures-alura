# Retornos em PLs

### Reescrita da função primeira_funcao com plpgsql

```sql
CREATE OR REPLACE FUNCTION primeira_funcao() RETURNS INTEGER AS $$
    DECLARE
        primeiro_numero INTEGER DEFAULT 5;
        segundo_numero INTEGER DEFAULT 3;
        terceiro_numero INTEGER DEFAULT 2;
    BEGIN
        RETURN (primeiro_numero - segundo_numero) * terceiro_numero;
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função soma_dois_numeros com plpgsql

```sql
CREATE OR REPLACE FUNCTION soma_dois_numeros(numero_1 INTEGER, numero_2 INTEGER) RETURNS INTEGER AS $$
    BEGIN
        RETURN numero_1 + numero_2;
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função cria_a com plpgsql

```sql
DROP FUNCTION cria_a;

CREATE OR REPLACE FUNCTION cria_a(nome VARCHAR) RETURNS void AS $$
    BEGIN
        INSERT INTO a (nome) VALUES (nome);
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função dobro_do_salario com plpgsql

```sql
CREATE OR REPLACE FUNCTION dobro_do_salario(instrutor) RETURNS DECIMAL AS $$
    BEGIN
        RETURN $1.salario * 2 AS dobro;
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função cria_instrutor_falso com plpgsql com ROW

```sql
CREATE OR REPLACE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
    BEGIN
        RETURN ROW(22, 'Nome falso', 200::DECIMAL)::instrutor;
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função cria_instrutor_falso com plpgsql

```sql
CREATE OR REPLACE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
    DECLARE
        retorno instrutor;
    BEGIN
        SELECT 22, 'Nome falso', 200::DECIMAL INTO retorno;

        RETURN retorno;
    END
$$ LANGUAGE plpgsql;
```

### Reescrita da função instrutores_bem_pagos com plpgsql

```sql
DROP FUNCTION instrutores_bem_pagos;

CREATE FUNCTION instrutores_bem_pagos(valor_salario DECIMAL) RETURNS SETOF instrutor AS $$
    BEGIN
        RETURN QUERY SELECT * FROM instrutor WHERE salario > valor_salario;    
    END
$$ LANGUAGE plpgsql;
```