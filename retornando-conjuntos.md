# Retornando conjuntos

### Populando tabela instrutor

```sql
INSERT INTO instrutor (nome, salario) VALUES ('Diogo Mascarenhas', 200);
INSERT INTO instrutor (nome, salario) VALUES ('Nico Steppat', 300);
INSERT INTO instrutor (nome, salario) VALUES ('Juliana', 400);
INSERT INTO instrutor (nome, salario) VALUES ('Priscila', 500);
```

### Criação da função instrutores_bem_pagos utilizando setof

```sql
CREATE FUNCTION instrutores_bem_pagos(valor_salario DECIMAL) RETURNS SETOF instrutor AS $$
    SELECT * FROM instrutor WHERE salario > valor_salario;
$$ LANGUAGE SQL;
```

### Criação da função instrutores_bem_pagos utilizando table

```sql
CREATE FUNCTION instrutores_bem_pagos(valor_salario DECIMAL)
RETURNS TABLE (id INTEGER, nome VARCHAR, salario DECIMAL) AS $$
    SELECT * FROM instrutor WHERE salario > valor_salario;
$$ LANGUAGE SQL;
```