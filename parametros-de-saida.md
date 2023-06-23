# Parâmetros de saída

### Criação da função soma_e_produto com parâmetros de entrada e saída

```sql
CREATE FUNCTION soma_e_produto(IN numero_1 INTEGER, IN numero_2 INTEGER, OUT soma INTEGER, OUT produto INTEGER) AS $$
    SELECT numero_1 + numero_2 AS soma, numero_1 * numero_2 AS produto;
$$ LANGUAGE SQL;
```

### Criação da função soma_e_produto com retorno de um tipo

```sql
CREATE TYPE dois_valores AS (soma INTEGER, produto INTEGER);

DROP FUNCTION soma_e_produto;

CREATE OR REPLACE FUNCTION soma_e_produto (IN numero_1 INTEGER, IN numero_2 INTEGER) RETURNS dois_valores AS $$
    SELECT numero_1 + numero_2 AS soma, numero_1 * numero_2 AS produto;
$$ LANGUAGE SQL;
```

### Criação da função instrutores_bem_pagos com retorno record

```sql
DROP FUNCTION instrutores_bem_pagos;

CREATE OR REPLACE FUNCTION instrutores_bem_pagos (IN valor_salario DECIMAL, OUT nome VARCHAR, OUT salario DECIMAL)
RETURNS SETOF record AS $$
    SELECT nome, salario FROM instrutor WHERE salario > valor_salario;
$$ LANGUAGE SQL;
```