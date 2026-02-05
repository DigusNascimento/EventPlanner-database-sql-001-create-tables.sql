---

## 📄 **sql/001-create-tables.sql**

```sql
CREATE TABLE event (
    id SERIAL PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    descricao TEXT,
    data_inicio TIMESTAMP NOT NULL,
    data_fim TIMESTAMP NOT NULL,
    local VARCHAR(255),
    capacidade_maxima INT,
    status VARCHAR(50) NOT NULL
);

CREATE TABLE participant (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    documento VARCHAR(50),
    telefone VARCHAR(50)
);

CREATE TABLE reservation (
    id SERIAL PRIMARY KEY,
    evento_id INT NOT NULL REFERENCES event(id),
    participante_id INT NOT NULL REFERENCES participant(id),
    status VARCHAR(50) NOT NULL,
    data_reserva TIMESTAMP NOT NULL DEFAULT NOW()
);
