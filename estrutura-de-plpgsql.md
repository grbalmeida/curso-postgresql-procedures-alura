# Estrutura de PLpgSQL

### Criação da primeira função com plpgsql

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
	BEGIN
        -- Vários comandos em SQL

        RETURN 1;
    END;
$$ LANGUAGE plpgsql;
```