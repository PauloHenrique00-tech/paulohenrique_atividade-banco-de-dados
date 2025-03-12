```sql
SELECT * FROM alunos
WHERE data_de_nascimento < '2009-01-01';
```

```sql
SELECT
    nome,
    primeira_nota,
    segunda_nota,
    ROUND((primeira_nota + segunda_nota) / 2, 2) AS media
FROM alunos;
```

```sql
SELECT
    titulo,
    carga_horaria,
    (carga_horaria * 0.25) AS limite_faltas
FROM cursos
ORDER BY titulo ASC;
```

```sql
SELECT * FROM professores
WHERE area_de_atuacao = 'desenvolvimento';
```

```sql
SELECT area_de_atuacao, COUNT(*) AS quantidade_de_professores
FROM professores
GROUP BY area_de_atuacao;
```

```sql
SELECT area_de_atuacao, COUNT(*) AS quantidade_de_professores
FROM professores
GROUP BY area_de_atuacao;
```