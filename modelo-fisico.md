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
    '40h'
);

INSERT INTO cursos(titulo, carga_horaria) 
VALUES(
    'Back-End',
    '80h'
), (
    'UX/UI Design',
    '30h'
), (
    'Figma',
    '10h'
), (
    'Redes de computadores',
    '100h'
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
    ('Jon', '09/04/2005', 10, 10, 1),
    ('Tuco', '25/01/2001', 8, 7, 2),
    ('Agostinho Carrara', '08/06/1997', 7,7, 3),
    ('Lineuzinho', '25/11/1998', 10, 9, 4),
    ('Mendonça', '14/05/1996', 8, 9, 5)
    ('Floriano Carrara', '25/12/2005', 7, 5, 2),
    ('Oliver', '04/08/2006', 6, 6, 1),
    ('Dennis', '10/08/1999', 10, 8, 4),
    ('Gabriel', '18/04/2007', 9,6, 5)
    ('Beiçola', '25/01/1998', 7,5, 3);
```