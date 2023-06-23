# Parâmetros compostos

### Criação da tabela instrutor

```sql
CREATE TABLE instrutor (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    salario DECIMAL(10, 2)
);
```

### Populando tabela instrutor

```sql
INSERT INTO instrutor (nome, salario) VALUES ('Vinicius Dias', 100);
```

### Criação da função dobro_do_salario

```sql
CREATE FUNCTION dobro_do_salario(instrutor) RETURNS DECIMAL AS $$
    SELECT $1.salario * 2 AS dobro;
$$ LANGUAGE SQL;
```

### Invocando função dobro_do_salario passando dados do instrutor como parâmetro

```sql
SELECT nome, dobro_do_salario(instrutor.*) FROM instrutor;
```