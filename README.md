# EXERC-CIO-01---JOIN
# Exercício - Views (SQL)

Resolução dos exercícios sobre criação de **views** em SQL.

---

## a) CDs gravados pela gravadora 2

```sql
CREATE VIEW v_cd_gravadora2 AS
SELECT * FROM cd
WHERE grav_id = 2;
```

---

## b) CDs e suas gravadoras

```sql
CREATE VIEW v_cd_gravadora AS
SELECT cd.cd_nome, gravadora.grav_nome
FROM cd, gravadora
WHERE cd.grav_id = gravadora.grav_id;
```

---

## c) Músicas e seus autores

```sql
CREATE VIEW v_musica_autor AS
SELECT musica.mus_nome, autor.autor_nome
FROM musica, autor
WHERE musica.autor_id = autor.autor_id;
```

---

## d) Músicas, duração e CD

```sql
CREATE VIEW v_musica_cd AS
SELECT musica.mus_nome, musica.mus_duracao, cd.cd_nome
FROM musica, item_cd, cd
WHERE musica.mus_id = item_cd.mus_id
AND item_cd.cd_id = cd.cd_id;
```

---

## e) Autores e gravadoras onde possuem CD

```sql
CREATE VIEW v_autor_gravadora AS
SELECT DISTINCT autor.autor_nome, gravadora.grav_nome
FROM autor, musica, item_cd, cd, gravadora
WHERE autor.autor_id = musica.autor_id
AND musica.mus_id = item_cd.mus_id
AND item_cd.cd_id = cd.cd_id
AND cd.grav_id = gravadora.grav_id;
```

---

## Como usar

Para consultar uma view, utilize `SELECT`:

```sql
SELECT * FROM v_cd_gravadora2;
SELECT * FROM v_cd_gravadora;
SELECT * FROM v_musica_autor;
SELECT * FROM v_musica_cd;
SELECT * FROM v_autor_gravadora;
```

Para excluir uma view:

```sql
DROP VIEW v_cd_gravadora2;
```

---

## Observação

Foram utilizados apenas:
- `CREATE VIEW`
- `SELECT`
- `FROM` com múltiplas tabelas
- `WHERE` para relacionar as tabelas
- `DISTINCT` para evitar duplicatas no último exemplo

---
