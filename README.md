# SQL-Server--Procedures-and-Programming

**SQL Query: Stored Procedure**

Stored procedure: is a group of sql statements that are grouped together under 
a single heading which can then be reused and shared by multiple programs.

```sql
CREATE PROCEDURE spFilmList 
AS
BEGIN
	SELECT
		FilmName,
		FilmReleaseDate,
		FilmRunTimeMinutes
	FROM
		tblFilm
	ORDER BY
		FilmName ASC
END

-- Modify store procedure | Use ALTER 
ALTER PROCEDURE spFilmList 
AS
BEGIN
	SELECT
		FilmName,
		FilmReleaseDate,
		FilmRunTimeMinutes
	FROM
		tblFilm
	ORDER BY
		FilmName DESC
END

-- Deleting a store procedure 
DROP PROC spFilmList

/* Adding parameters*/
CREATE PROCEDURE spFilmCriteria(@MinLength AS INT, @MaxLength AS INT, @Title AS VARCHAR(MAX))
AS
BEGIN
	SELECT
		FilmName,
		FilmRunTimeMinutes
	FROM
		tblFilm
	WHERE
		FilmRunTimeMinutes >=@MinLength AND
		FilmRunTimeMinutes <=@MaxLength AND
		FilmName LIKE '%' + @Title +'%'
	ORDER BY
		FilmRunTimeMinutes ASC
END

--Executing the stored procedure
EXECUTE spFilmCriteria @MinLength=120,@MaxLength=180 , @Title='star'
```
