```sql (1)
SELECT * FROM alunos
WHERE data_de_nascimento < '2009-01-01';
```

```sql  (2)
SELECT
    nome,
    primeira_nota,
    segunda_nota,
    ROUND((primeira_nota + segunda_nota) / 2, 2) AS media
FROM alunos;
```

```sql (3)
SELECT
    titulo,
    carga_horaria,
    (carga_horaria * 0.25) AS limite_faltas
FROM cursos
ORDER BY titulo ASC;
```

```sql (4)
SELECT * FROM professores
WHERE area_de_atuacao = 'desenvolvimento';
```

```sql (5)
SELECT area_de_atuacao, COUNT(*) AS quantidade_de_professores
FROM professores
GROUP BY area_de_atuacao;
```

```sql (6)
SELECT 
    alunos.nome AS aluno,
    cursos.titulo AS curso,
    cursos.carga_horaria
FROM alunos
INNER JOIN cursos ON alunos.curso_id = cursos.id;
```

```sql (7)
SELECT
    professores.nome AS professor,
    cursos.titulo AS curso
FROM cursos
INNER JOIN professores ON cursos.professor_id = professores.id
ORDER BY professor_id ASC;
```

```sql (8)
SELECT
    alunos.nome AS aluno,
    cursos.titulo AS curso,
    professores.nome AS professor
FROM alunos
INNER JOIN cursos ON alunos.curso_id = cursos.id
INNER JOIN professores ON cursos.professor_id = professores.id;    
```

```sql (9)
SELECT
    cursos.titulo AS curso,
    COUNT(alunos.id) AS quantidade_de_alunos 
FROM cursos
LEFT JOIN alunos ON alunos.curso_id = cursos.id
GROUP BY cursos.id
ORDER BY quantidade_de_alunos DESC;
```

```sql (10)
SELECT 
    alunos.nome,
    alunos.primeira_nota,
    alunos.segunda_nota,
    ROUND((alunos.primeira_nota + segunda_nota) / 2, 2) AS media,
    cursos.titulo
FROM alunos
INNER JOIN cursos ON alunos.curso_id = cursos.id
WHERE curso_id IN (1, 2)
ORDER BY alunos.nome;
```

```sql (11)
    UPDATE cursos WHERE titulo,carga_horaria 'Figma', 10
    SET titulo 'Adobe XD', carga_horaria = 15;
    --SET titulo = 'Adobe XD', carga_horaria = 15 
   -- WHERE titulo = 'Figma';
```

```sql (12)
    DELETE FROM alunos 
    WHERE curso_id IN (
        SELECT id FROM cursos WHERE titulo IN ('Redes de Computadores', 'UX;UI Design')
    )
    LIMIT 2;
```

```sql (13)
    SELECT 
    alunos.nome AS nome, 
    cursos.titulo AS curso
    FROM alunos
    INNER JOIN cursos ON alunos.curso_id = cursos.id
    ORDER BY alunos.nome;
```

```sql (Desafio 1)
SELECT
    nome AS nome,
    data_de_nascimento,
    TIMESTAMPDIFF(YEAR, data_de_nascimento, CURDATE()) AS Idade
FROM alunos;
```

```sql (Desafio 2)
SELECT
    primeira_nota,
    segunda_nota,
    ROUND((primeira_nota + segunda_nota) / 2, 2) AS media
FROM alunos
HAVING media >= 7;
```

```sql (Desafio 3)
SELECT
    primeira_nota,
    segunda_nota,
    ROUND((primeira_nota + segunda_nota) / 2, 2) AS media
FROM alunos
HAVING media <= 7;
```

```sql (Desafio 4)
SELECT
    nome,
    ROUND((primeira_nota + segunda_nota) / 2, 2) AS media
FROM alunos
HAVING media >= 7;
```