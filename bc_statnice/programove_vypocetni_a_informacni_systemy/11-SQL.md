# SQL
- syntaxe a sémantika příkazů
- příkazy pro dotazování a aktualizaci dat
- agregační funkce
- triggery
- uložené procedury
- příkazy pro definici dat
- integritní omezení

## Syntax
- připomíná angličtinu
- příkazy se píšou verzálkami
- názvy objektů se obalují [, ] nebo '
- za příkazem může být středník
- řádkový komentář: --
- blokový příkaz /* ... */

Příkazy lze zapsat pomocí syntaktických diagramů.

## Doménové typy v SQL
- char(n) = řetězec fixní délky
- varchar(n) = řetězec maximální délky n
- int
- smallint
- numeric(p, d) = přesnost p a počet desetinných míst d
- real, double precision = přesnost závisí na stroji
- float(n) = přesnost alespoň n číslic

## Příkazy pro dotazování a aktualizaci dat

- SELECT (SELECT id FROM student)
    - vybírá data z databáze
    - odpovídá projekci z relační algebry
- UPDATE (UPDATE student SET name='Nika' WHERE id=1)
    - upraví záznamy z jedné tabulky podle zadané podmínky
- DELETE (DELETE FROM student where id=1)
    - odstraní záznamy z tabulky, které odpovídají podmínce
- INSERT (INSERT INTO student(id, name) VALUES (2, 'Bob'))
    - vloží záznam do tabulky
    - hodnoty musí splňovat podmínky pro sloupce, jinak nastane syntax error
- DISTINCT
    - eliminue duplicity po příkazu SELECT
- ALL
    - ponechává duplicity po příkazu SELECT
- WHERE
    - definuje podmínku
    - odpovídá selekci v relační algebře
- FROM
    - vybere všechny záznamy, případně kartézský součin všech relací, co jsou uvedeny
    - odpovídá operaci kartézský součin v relační algebře
- ORDER BY (ORDER BY column1 ASC)
    - seřadí data sestupně (DESC) nebo vzestupně (ASC)
- GROUP BY (SELECT ..., AVG(...) FROM ... GROUP BY ..)
    - agregační funkce
- JOIN
    - NATURAL JOIN
    - NATURAL LEFT OUTER JOIN
    - NATURAL RIGHT OUTER JOIN
    - INNER JOIN (Select column from table1 INNER JOIN table2 on table1.id = table2.id)
    - FULL OUTER JOIN
- AS
    - přejmenování
- HAVING (... GROUP BY name HAVING podmínka ...)
    - podmínka, která se používá s agregačními funkcemi
- LIKE
    - používá se ve WERE klauzuli pro specifikaci
    - % = reprezentace libovolného počtu znaků
    - _ = reprezentace právě jednoho znaku (nebo taky ?)

## Agregační funkce
- COUNT = počet
- MAX = maximum
- MIN = minimum
- SUM = suma
- AVG = průměr

## Uložené procedury
- databázové objekty obsahující programy, které se mají vykonávat v databázi, běží na serveru
- lze s nimi manimulovat (CREATE, UPDATE, DELETE) stejně jako s objekty v databázi
- pro jejich psaní se používá konkrétní jazyk dané databáze - rozšíření SQL (např. PL/SQL, T-SQL, ...)
- obsahují posloupnosti příkazů SQL, které manimulují s tabulkami (např. triggery)
- umožňují složitější  operace, minimum kolií, odlehčení klienta, zabezpečení (práva ke spouštění procedur)
- nevýhoda: nový jazyk

## Triggery
_trigger_ = příkaz, který je vykonán automaticky systémem, jako vedlejší efekt modifikace databáze (INSERT, DELETE, UPDATE)

Při vytváření tiggeru musíme specifikovat:

- podmínku, za které se spustí
- akci, kterou vykoná

Příklad: aktualizace získaných kreditů při složení zkoušky

CREATE TRIGGER credits_total AFTER UPDATE OF zkousky

## Příkazy pro definici dat
- CREATE TABLE r (A_1, D_1, A_2, D_2, ... A_N, D_N (integritní omezení1), ... (integritní omezeníM)).
    - vytvoří tabulku r, kde A_x je jméno atributu a D_x je jeho datový typ
- AS
    - přejmenování
- INSERT INTO tabulka VALUES(sloupec1, ... sloupecN)
    - vloží nový záznam do tabulky
- UPDATE r SET A1=e .. WHERE ...
    - aktualizujeme záznam v tabulce
- DELETE FROM tabulka
    - smazání veškerého obsahu tabulky
- DELETE FROM tabulka WHERE podmínka
    - smaže záznamy splňující podmínku
- DROP TABLE tabulka
    - smaže celou tabulku
- ALTER TABLE r ADD a d
    - přidá nový atribut a a jeho doménu d
- ALTER TABLE r DROP a
    - smaže atribut a z tabulky r

## Integritní omezení
- zabraňují náhodnému poškození databáze, např. věk nesmí být záporné číslo

- NOT NULL
    - atribut nesmí být null
- UNIQUE (A1, A2, ... AN)
    - atributy A1, A2, ... AN tvoří kandidátní klíč
- CHECK (P); CHECK(semester in ('fall', 'spring'))
    - ověří, jestli je splněn predikát P
- PRIMARY KEY
    - stejný, jako UNIQUE, ale atributy nesmí být NULL
