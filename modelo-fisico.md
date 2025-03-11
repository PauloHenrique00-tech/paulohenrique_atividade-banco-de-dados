```sql 
CREATE DATABASE tecinternet_escola_paulo CHARACTER SET utf8mb4;
```

```sql
CREATE TABLE cursos(
    id INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    carga_horaria INT NOT NULL,
    professor_id INT NULL
);
```

```sql
CREATE TABLE professores(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    area_de_atuacao ENUM('design', 'desenvolvimento', 'infra'),
    curso_id INT NOT NULL
);
```

```sql
INSERT INTO cursos(titulo, carga_horaria) 
VALUES(
    'Front-End',
    40
);

INSERT INTO cursos(titulo, carga_horaria) 
VALUES(
    'Back-End',
    80
), (
    'UX/UI Design',
    30
), (
    'Figma',
    10
), (
    'Redes de computadores',
    100
);
```

```sql
INSERT INTO professores (nome, area_de_atuacao, curso_id) 
VALUES 
    ('Jon Oliva', 'Infra', 5),
    ('Lemmy Kilmister', 'Design', 4),
    ('Neil Peart', 'Desenvolvimento', 3),
    ('Ozzy Osbourne', 'Design', 2),
    ('David Gilmour', 'Desenvolvimento', 1);
```

```sql
CREATE TABLE alunos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    data_de_nascimento DATE,
    primeira_nota DECIMAL,
    segunda_nota DECIMAL,
    curso_id INT NOT NULL
);
```

```sql
UPDATE cursos SET professor_id = 1 WHERE titulo = 'Front-End';
```

```sql
UPDATE cursos SET professor_id = 2 WHERE titulo = 'Back-End';
```

```sql
UPDATE cursos SET professor_id = 3 WHERE titulo = 'UX/UI Design';
```

```sql
UPDATE cursos SET professor_id = 4 WHERE titulo = 'Figma';
```

```sql
UPDATE cursos SET professor_id = 5 WHERE titulo = 'Redes de computadores';
```

```sql
-- Front-End id = 1;
-- Back-End id = 2;
-- UX/UI Design id = 3;
-- Figma id = 4;
-- Redes de Computadores id = 5;
```

```sql
INSERT INTO alunos (nome, data_de_nascimento, primeira_nota, segunda_nota, curso_id) 
VALUES 
    ('Jon', '2005-09-04', 10, 10, 1),
    ('Tuco', '2001-01-25', 8, 7, 3),
    ('Agostinho Carrara', '1997-08-06', 7,7, 4),
    ('Lineuzinho', '1998-11-23', 10, 9, 2),
    ('Mendonça', '1996-05-14', 8, 9, 5),
    ('Floriano Carrara', '2005-12-25', 7, 5, 2),
    ('Oliver', '2006-04-08', 6, 6, 1),
    ('Dennis', '1999-08-10', 10, 8, 4),
    ('Gabriel', '2007-04-18', 9, 6, 5),
    ('Beiçola', '1998-01-25', 7, 5, 3);
```

```sql
SELECT nome, DATE_FORMAT(data_de_nascimento, '%d%/%m%/%y%') AS data_nascimento_formatada FROM alunos;
```

```sql
SELECT nome, data_de_nascimento FROM alunos;
```

```sql
UPDATE alunos SET data_de_nascimento = '2001-01-25' WHERE nome = 'Tuco';
```

```sql
UPDATE alunos SET data_de_nascimento = '1998-11-23' WHERE nome = 'Lineuzinho';
```

```sql
UPDATE alunos SET data_de_nascimento = '1996-05-14' WHERE nome = 'Mendonça';
```

```sql
UPDATE alunos SET data_de_nascimento = '2005-12-25' WHERE nome = 'Floriano Carrara';
```

```sql
UPDATE alunos SET data_de_nascimento = '1998-01-25' WHERE nome = 'Beiçola';
```

```sql
ALTER TABLE cursos
    -- Adicionando uma restrição indicando o nome do relacionamento
    ADD CONSTRAINT fk_cursos_professores

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primária (id) de OUTRA TABELA (fabricantes)
    FOREIGN KEY (professor_id) REFERENCES professores(id);
```


```sql
ALTER TABLE professores
    -- Adicionando uma restrição indicando o nome do relacionamento
    ADD CONSTRAINT fk_professores_cursos

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primária (id) de OUTRA TABELA (fabricantes)
    FOREIGN KEY (curso_id) REFERENCES cursos(id);
```


```sql
ALTER TABLE alunos
    -- Adicionando uma restrição indicando o nome do relacionamento
    ADD CONSTRAINT fk_alunos_cursos

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primária (id) de OUTRA TABELA (fabricantes)
    FOREIGN KEY (aluno_id) REFERENCES alunos(id);
```