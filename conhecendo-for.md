# Conhecendo For

### Criação da função tabuada com loop FOR

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$
    BEGIN
        FOR multiplicador IN 1..9 LOOP
            RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
            multiplicador := multiplicador + 1;
        END LOOP;
    END;
$$ LANGUAGE plpgsql;
```

### Criação da função instrutor_com_salario

```sql
CREATE OR REPLACE FUNCTION instrutor_com_salario(OUT nome VARCHAR, OUT salario_ok VARCHAR) RETURNS SETOF record AS $$
    DECLARE
        instrutor instrutor;
    BEGIN
        FOR instrutor IN SELECT * FROM instrutor LOOP
            nome := instrutor.nome;
            salario_ok := salario_ok(instrutor.id);

            RETURN NEXT;
        END LOOP;
    END;
$$ LANGUAGE plpgsql;
```