# Curso na categoria

### Criação das tabelas

```sql
CREATE TABLE aluno (
    id SERIAL PRIMARY KEY,
	primeiro_nome VARCHAR(255) NOT NULL,
	ultimo_nome VARCHAR(255) NOT NULL,
	data_nascimento DATE NOT NULL
);

CREATE TABLE categoria (
    id SERIAL PRIMARY KEY,
	nome VARCHAR(255) NOT NULL UNIQUE
);

CREATE TABLE curso (
    id SERIAL PRIMARY KEY,
	nome VARCHAR(255) NOT NULL,
	categoria_id INTEGER NOT NULL REFERENCES categoria(id)
);

CREATE TABLE aluno_curso (
	aluno_id INTEGER NOT NULL REFERENCES aluno(id),
	curso_id INTEGER NOT NULL REFERENCES curso(id),
	PRIMARY KEY (aluno_id, curso_id)
);
```

### Criação da função cria_curso, que recebe o nome do curso e o nome da categoria, caso a categoria não exista, a categoria é criada

```sql
CREATE FUNCTION cria_curso(nome_curso VARCHAR, nome_categoria VARCHAR) RETURNS void AS $$
    DECLARE
        id_categoria INTEGER;
    BEGIN
        SELECT id INTO id_categoria FROM categoria WHERE nome = nome_categoria;

        IF NOT FOUND THEN
            INSERT INTO categoria (nome) VALUES (nome_categoria) RETURNING id INTO id_categoria;
        END IF;

        INSERT INTO curso (nome, categoria_id) VALUES (nome_curso, id_categoria);
    END;
$$ LANGUAGE plpgsql;
```

### Inclusão dos cursos

```sql
select cria_curso('MySQL', 'Banco de Dados');
select cria_curso('PostgreSQL', 'Banco de Dados');
select cria_curso('Oracle', 'Banco de Dados');
select cria_curso('MariaDB', 'Banco de Dados');
select cria_curso('MongoDB', 'Banco de Dados');
```