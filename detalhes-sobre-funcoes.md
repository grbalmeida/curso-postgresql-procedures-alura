# Detalhes sobre funções

### Criação da tabela a

```sql
CREATE TABLE a (nome VARCHAR(255) NOT NULL);
```

### Criação da função cria_a

```sql
CREATE FUNCTION cria_a(nome VARCHAR) RETURNS VARCHAR AS '
    INSERT INTO a (nome) VALUES (cria_a.nome);

    SELECT nome;
' LANGUAGE SQL;
```

### Recriação da função cria_a

```sql
CREATE OR REPLACE FUNCTION cria_a(nome VARCHAR) RETURNS VARCHAR AS '
    INSERT INTO a (nome) VALUES (cria_a.nome);

    SELECT nome;
' LANGUAGE SQL;
```

### Mudar tipo de retorno da função

```sql
-- É necessário excluir a função e recriá-la

DROP FUNCTION cria_a;

CREATE OR REPLACE FUNCTION cria_a(nome VARCHAR) RETURNS VOID AS '
    INSERT INTO a (nome) VALUES (cria_a.nome);
' LANGUAGE SQL;
```

### Criação da função cria_a com dólar como delimitador

```sql
CREATE OR REPLACE FUNCTION cria_a(nome VARCHAR) RETURNS VOID AS $$
    INSERT INTO a (nome) VALUES ('Patricia');
$$ LANGUAGE SQL
```